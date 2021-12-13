#FIFO

#include<stdio.h>
int main()
{
    int np;
    scanf("%d",&np);
    int nf,pg[np];
    for(int i=0;i<np;i++)
    {
        scanf("%d",&pg[i]);
    }
    scanf("%d",&nf);
    int fr[nf];
    for(int i=0;i<nf;i++)
    {
        fr[i]=-1;
    }
    int avl,j=0,cnt=0;
    for(int i=0;i<np;i++)
    {
        avl=0;
        for(int k=0;k<nf;k++)
        {
            if(fr[k]==pg[i])
            avl=1;
        }
        if(avl==0)
        {
            fr[j]=pg[i];
            j=(j+1)%nf;
            cnt++;
        }
    }
    printf("%d",cnt);
    //pafe fault ratio= cnt/np;
    //hit ratio = 1- page fault ratio
    return 0;
}

CLook

#include<stdio.h>
#include<stdbool.h>
#include<stdlib.h>
int comparator(const void* a, const void* b)
{
    return *(int*)a - *(int*)b;
}
int minIndex(int queue[], int n, int init_pos)
{
    for(int i=n-1; i>=0; i--)
    {
        if(queue[i] <= init_pos) return i;
    }
}
int main()
{
    int total_cylinder,n,init_pos,direction;

    printf("\n Enter the total number of cylinders : ");
    scanf("%d",&total_cylinder);

    printf("\n Enter the number of cylinders : ");
    scanf("%d",&n);

    int queue[n];
    bool visit[n];

    for(int i=0; i<n; i++) visit[i]=false;
    
    printf("\n Enter %d number of cylinders in ready queue : ",n);
    for(int i=0; i<n; i++) scanf("%d",&queue[i]);

    printf("\n Enter the current position of head : ");
    scanf("%d",&init_pos);

    printf("\n Enter the direction of movement : ");
    scanf("%d",&direction);   // 0 = lower side  1 = higher side

    int total_movement=0;

    qsort(queue,n,sizeof(int),comparator);

    int index = minIndex(queue,n,init_pos);

    if(direction == 0)
    {   
        total_movement += abs(init_pos - queue[0]);
        total_movement += abs(queue[0] - queue[n-1]);
        total_movement += abs(queue[n-1] - queue[index+1]);
    }
    else 
    { 
        total_movement += abs(queue[n-1] - init_pos);
        total_movement += abs(queue[0] - queue[n-1]);
        total_movement += abs(queue[0] - queue[index]);  
    }

    printf("\n Total head movement : %d",total_movement);
    printf("\n Average head movement : %.2f",(float)total_movement/n);

    return 0;
}

#LOOK                                         #include<stdio.h>
#include<stdbool.h>
#include<stdlib.h>
int comparator(const void* a, const void* b)
{
    return *(int*)a - *(int*)b;
}
int main()
{
    int total_cylinder,n,init_pos,direction;

    printf("\n Enter the total number of cylinders : ");
    scanf("%d",&total_cylinder);

    printf("\n Enter the number of cylinders : ");
    scanf("%d",&n);

    int queue[n];
    bool visit[n];

    for(int i=0; i<n; i++) visit[i]=false;
    
    printf("\n Enter %d number of cylinders in ready queue : ",n);
    for(int i=0; i<n; i++) scanf("%d",&queue[i]);

    printf("\n Enter the current position of head : ");
    scanf("%d",&init_pos);

    printf("\n Enter the direction of movement : ");
    scanf("%d",&direction);   // 0 = lower side  1 = higher side

    int total_movement=0;

    qsort(queue,n,sizeof(int),comparator);

    if(direction == 0)
    {   
        total_movement += abs(init_pos - queue[0]);
        total_movement += abs(queue[0] - queue[n-1]);
    }
    else 
    { 
        total_movement += abs(queue[n-1] - init_pos);
        total_movement += abs(queue[n-1] - queue[0]);  
    }

    printf("\n Total head movement : %d",total_movement);
    printf("\n Average head movement : %.2f",(float)total_movement/n);

    return 0;
}


FCFS DISC SCHEDULING
#include<stdio.h>
#include<math.h>
void fcfs(int a[],int n,int head)
{
    int i;
    int total=0;
    int curr=head;
    int dis[100];
    for(i=0;i<n;i++)
    {
         dis[i]=(abs(curr-a[i]));
        //total+=dis;
        curr=a[i];
    }
    for(int i=0;i<n;i++)
    {
        printf("%d  ",dis[i]);
        total+=dis[i];
    }
    printf("%d",total);
}
int main()
{
    int n;
    scanf("%d",&n);
    int a[n];
    for(int i=0;i<n;i++)
    {
        scanf("%d",&a[i]);
    }
    int head;
    scanf("%d",&head);
    fcfs(a,n,head);
    return 0;
}

#CScan
#include<stdio.h>
#include<stdbool.h>
#include<stdlib.h>

int comparator(const void* a, const void* b)
{
    return *(int*)a - *(int*)b;
}

int minIndex(int queue[], int n, int init_pos)
{
    for(int i=n-1; i>=0; i--)
    {
        if(queue[i] <= init_pos) return i;
    }
}

int main()
{
    int total_cylinder,n,init_pos,direction;

    printf("\n Enter the total number of cylinders : ");
    scanf("%d",&total_cylinder);

    printf("\n Enter the number of cylinders : ");
    scanf("%d",&n);

    int queue[n];
    bool visit[n];

    for(int i=0; i<n; i++) visit[i]=false;
    
    printf("\n Enter %d number of cylinders in ready queue : ",n);
    for(int i=0; i<n; i++) scanf("%d",&queue[i]);

    printf("\n Enter the current position of head : ");
    scanf("%d",&init_pos);

    printf("\n Enter the direction of movement : ");
    scanf("%d",&direction);   // 0 = lower side  1 = higher side

    int total_movement=0;

    qsort(queue,n,sizeof(int),comparator);

    int index = minIndex(queue,n,init_pos);

    if(direction == 0)
    {   
        total_movement += abs(init_pos - 0);
        total_movement += total_cylinder-1;
        total_movement += abs(199 - queue[index+1]);
    }
    else 
    { 
        total_movement += abs(total_cylinder-1 - init_pos);
        total_movement += total_cylinder-1;
        total_movement += abs(0 - queue[index]);  
    }

    printf("\n Total head movement : %d",total_movement);
    printf("\n Average head movement : %.2f",(float)total_movement/n);

    return 0;
}


#Scan Disk 
#include<stdio.h>
#include<stdbool.h>
#include<stdlib.h>

int comparator(const void* a, const void* b)
{
    return *(int*)a - *(int*)b;
}

int main()
{
    int total_cylinder,n,init_pos,direction;

    printf("\n Enter the total number of cylinders : ");
    scanf("%d",&total_cylinder);

    printf("\n Enter the number of cylinders : ");
    scanf("%d",&n);

    int queue[n];
    bool visit[n];

    for(int i=0; i<n; i++) visit[i]=false;
    
    printf("\n Enter %d number of cylinders in ready queue : ",n);
    for(int i=0; i<n; i++) scanf("%d",&queue[i]);

    printf("\n Enter the current position of head : ");
    scanf("%d",&init_pos);

    printf("\n Enter the direction of movement : ");
    scanf("%d",&direction);   // 0 = lower side  1 = higher side

    int total_movement=0;

    qsort(queue,n,sizeof(int),comparator);

    if(direction == 0)
    {   
        total_movement += abs(init_pos - 0);
        total_movement += abs(0 - queue[n-1]);
    }
    else 
    { 
        total_movement += abs(total_cylinder-1 - init_pos);
        total_movement += abs(total_cylinder-1 - queue[0]);  
    }

    printf("\n Total head movement : %d",total_movement);
    printf("\n Average head movement : %.2f",(float)total_movement/n);

    return 0;
}
