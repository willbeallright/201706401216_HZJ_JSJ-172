# 5-21
#include<stdio.h>
int x[1001],w[1001];
int cw,n,c,r,bestw;
void backtrack(int i)
   {
      if (i>n)  
      {
      bestw=cw;
      return;
      }
      r-=w[i];
      if (cw+w[i]<=c)
      {
         x[i]=1; 
         cw+=w[i];
         backtrack(i+1);
         cw-=w[i];      
	  }
      if (cw+r>bestw)  
	  {
         x[i]=0;
         backtrack(i+1);      
	  }
      r+=w[i];
   }
int main()
{
	int i;
while(~scanf("%d",&n))
{
  for(i=1;i<=n;i++)
  {
  scanf("%d",&w[i]);
  x[i]=0;
  r+=w[i];
  }
  scanf("%d",&c);
  cw=bestw=0;
  backtrack(1);
printf("%d\n",bestw);
}
}
