# LINKEDLIST
learn whole advance linkedlist in one code:///////


```
#include<bits/stdc++.h>
using namespace std;
class node{
  public:
    int val;
    node* next;
    node(int data)
    {
        val = data;
        next = NULL;
    }
};
void insertathead(node* &head,int data)
{
    if(head == NULL)
    {
        head = new node(data);
        return;
    }
    node* d = new node(data);
    d->next = head;
    head = d;
    return;
}
node* reverselist(node* head)
{
    if(head == NULL || head->next == NULL)
        return head;
    node* smallhead = reverselist(head->next);
    node* temp = head->next;
    head->next = NULL;
    temp->next = head;
    return smallhead;
}
int findlength(node* head)
{
     int count = 0 ;
     while(head)
     {
          count++;
          head=head->next;
     }
     return count;
}
void insertattail(node*&head,int data)
{
    if(head == NULL)
    {
        head = new node(data);
        return;
    }
    node*temp = head;
    while(temp->next)
    {
         temp = temp->next;
    }
   node* d = new node(data);
   temp->next = d;
   return;
}
void insertatanyposition(node* &head,int n,int data)
{
   int jump = n-1;
   int len = findlength(head);
   node* temp = head;
   if(n == 0)
   {
        insertathead(head,data);
        return;
   }
   if(n>len)
   {
        insertattail(head,data);
        return;
   }
   while(jump)
   {
       temp = temp->next;
       jump--;
   }
   node* d = new node(data);
   node* tempnext = temp->next;
   temp->next = d;
   d->next = tempnext;
   return;
}
void print(node* head)
{
    while(head!=NULL)
    {
        cout<<head->val<<"->";
        head = head->next;
    }
    cout<<"NULL"<<endl;
    return;
}
node* takeinput()
{
    int d;
    node* head = NULL;
    cin>>d;
    while(d!=-1)
    {
        insertathead(head,d);
        cin>>d;
    }
    return head;
}
ostream& operator<< (ostream &os,node* head)
{
    print(head);
    return os;
}
istream& operator>>(istream &is,node* &head)
{
    head = takeinput();
    return is;
}
int main()
{
    node* head = NULL;
    cin>>head;
    cout<<head;
    node* newhead = reverselist(head);
    cout<<newhead<<endl;
}
```

