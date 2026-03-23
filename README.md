# Finding-the-middle-Element-And-Loop-in-an-Array

<blr>
  Author ~Mohammed Feroz
  </blr>
This C program creates a singly linked list with dynamic insertion at the beginning. It finds the middle element using the slow and fast pointer method and detects loops using Floyd’s cycle detection algorithm. It takes user input to build the list and displays results accordingly.

<blr>
code 
</blr>
#include <stdio.h>
#include <stdlib.h>
struct node
{
  int data;
  struct node* next;
};
void insertAtBeg(struct node** head,int val)
{
  struct node* newnode=(struct node*)malloc(sizeof(struct node));
  newnode->data=val;
  newnode->next=*head;
  *head=newnode;
}
void findMiddle(struct node* head)
{
  struct node* fast=head;
  struct node* slow=head;
  while(fast!=NULL && fast->next!=NULL)
  {
    fast=fast->next->next;
    slow=slow->next;
  }
  printf("%d\n",slow->data);
}
void findLoop(struct node* head)
{
  struct node* fast=head;
  struct node* slow=head;
  while(fast!=NULL && fast->next!=NULL)
  {
    fast=fast->next->next;
    slow=slow->next;
    if(fast==slow)
    {
      printf("Loop detected");
      return;
    }
  }
  printf("No Loop Detected");
}
int main()
{
    struct node*head=NULL;
    int n,val;
    scanf("%d",&n);
    for(int i=0;i<n;i++)
    {
      scanf("%d",&val);
      insertAtBeg(&head,val);
    }
    findMiddle(head);
    findLoop(head);
}
