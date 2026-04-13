# Assignment44
#include <stdio.h>
void findWaitingTime(int process[],int n, int bt[], int wt[] ){
    wt[0] = 0;
    for(int i = 1; i<n;i++){
        wt[i] = bt[i-1] + wt[i-1];
    }
}

void findTurnAroundTime(int process[], int n ,int bt[],int wt[], int tat[]){
    for(int i = 0; i < n; i++){
        tat[i] = bt[i] + wt[i];
    }
}

void findCompletionTime(int process[],int n, int bt[],int wt[],int ct[]){

    for(int i = 0; i<n;i++){
        ct[i] = bt[i]+wt[i];
    }
}

void findAvgTime(int process[], int n, int bt[]){
    int wt[n], ct[n], tat[n], total_wt = 0, total_tat = 0;
    int CompletionTime = 0;
    findWaitingTime(process,n,bt,wt);
    findTurnAroundTime(process,n,bt,wt,tat);
    findCompletionTime(process,n,bt,wt,ct);


    for(int  i = 0; i<n;i++){
        total_wt+=wt[i];
        total_tat+= tat[i];
        CompletionTime = ct[i];
        
        printf("\nProcess id : %d\n",(i+1));
        printf("Current Burst Time = %d\n", bt[i]);
        printf("Current waiting time = %d \n",wt[i]);
        printf("Turn Around Time = %d\n",tat[i]);
        printf("Completion Time = %d\n",CompletionTime);

    }
        float s = (float)total_wt/(float)n;
        float t = (float)total_tat/(float)n;

        printf("\nAvg wt time = %f\n",s);
        printf("\nAvg turn around time = %f\n",t);
    

}



int main(){
    int process[] = {0,1,2,3,4};

    int n = sizeof(process)/sizeof(process[0]);

    int burstTime[] = {5,7,6,2,4};
    findAvgTime(process,n,burstTime);
    return 0;
}
