```
#include<iostream>
using namespace std;
void mergesort(int a[],int temp[],int left,int right)
{
  if(left==right)
    return;
  int mid=(left+right)/2;
  mergesort(a,temp,left,mid);
  mergesort(a,temp,mid+1,right);
  for(int i=left;i<=right;i++)
    temp[i]=a[i];
  int i1=left;
  int i2=mid+1;
  for(int curr=left;curr<=right;curr++)
  {
    if(i1==mid+1)
      a[curr]=temp[i2++];
    else if(i2>right)
      a[curr]=temp[i1++];
    else if(temp[i1]<temp[i2])
      a[curr]=temp[i1++];
    else
      a[curr]=temp[i2++];
  }
}
void arrayPrint(int a[],int size)
{
  cout<<"输入的数组按从小到大排序为：\n";
  for(int i=0;i<size;i++)
    cout<<a[i]<<" ";
  cout<<endl;
}
int main()
{
  int *a=NULL;
   int *p=NULL;
  int size;
  cout<<"请输入需要排列的数组长度：（输入数组长度为0时则退出程序）\n";
  cin>>size;
  while(size!=0)
  {
    a=new int[size];
    p=new int[size];
   int element;
   cout<<"请输入需要排序的数组里面的元素！"<<endl;
   for(int i=0;i<size;i++)
   {cin>>element;
     a[i]=element;
     p[i]=0;
     
  }
  
  
  mergesort(a,p,0,size-1);
 arrayPrint(a,size);
  delete []a;
  delete []p;
  a=NULL;
  p=NULL;
  cout<<"\n\n\n";
   cout<<"请输入需要排列的数组长度：（输入数组长度为0时则退出程序）\n";
  cin>>size;
  }
}
```
