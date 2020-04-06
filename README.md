# upload-3
#include <windows.h>
#include <iostream>
#define MAX_THREADS 1
using namespace std;

DWORD WINAPI Prime (LPVOID);
HANDLE hThreads [MAX_THREADS];
DWORD id [MAX_THREADS];
DWORD waiter;

DWORD WINAPI Prime(LPVOID Param)
{
    DWORD Number = *(DWORD*)Param;
    for (DWORD i=0;i<=Number;i++)
    {
        if((Number%2==0) ||(Number%3==0) || (Number%4==0)||(Number%5==0)||(Number%6==0)||  (Number%7==0)||(Number%8==0)||(Number%9==0))
        cout <<"";
        else
        cout<<i;
    }
    return 0;
}

int main(int argc, char* argv[ ])
{
    DWORD ThreadId;
    HANDLE ThreadHandle;
    int Param;

    cout<<"Enter a number:";
    cin>>Param;

    cout<<"Prime numbers less than and equal to your number";

    ThreadHandle=CreateThread(NULL,0,Prime,&Param,0,&ThreadId);

    waiter=WaitForMultipleObjects(MAX_THREADS,hThreads,TRUE,INFINITE);

    for(int i=0;i<MAX_THREADS;i++)
        CloseHandle(hThreads[i]);

    system ("pause");
    return 0;
}
