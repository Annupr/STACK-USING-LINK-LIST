# STACK-USING-LINK-LIST
Here is the program to find stack using link list
#include<stdio.h>
#include<stdlib.h>
#include<limits.h>

struct StackNode{
	int data;
	struct StackNode *next;
};
	
	struct StackNode* newnode(int ele){
		struct StackNode* stacknode=(struct StackNode*)malloc(sizeof(struct StackNode));
		stacknode->data=ele;
		stacknode->next=NULL;
		return stacknode;
	}

	void push(struct StackNode **root,int ele)
	{
		struct StackNode* stacknode=newnode(ele);
		stacknode->next=*root;
		*root=stacknode;
		printf("%d is pushed in the stack...",stacknode->data);
	}
	int isempty(struct StackNode* root)
	{
		return !root;
	}
	int pop(struct StackNode** root)
	{
		if(isempty(*root))
			return;
		struct StackNode* temp=*root;
		int popped=temp->data;
		*root=(*root)->next;
		free(temp);
		return popped;
		
		
	}
	int peek(struct StackNode* root)
	{
		if(isempty(root))
		return INT_MIN;
		
		return root->data;
		
	}
void main()
{
	int op=0,ele=0,x=0;
	struct StackNode *root=NULL;
	
	while(x==0)
	{
		printf("\n1. To push an element:\n2. to pop the element: \n3.to check the element in the top:\n");
		scanf("%d",&op);
		
		switch(op)
		{
			case 1:
					printf("\nEnter the Element you want to push: ");
					scanf("%d",&ele);
					push(&root,ele);
					break;
			case 2:
					printf("\n%d is popped form the Stack...",pop(&root));
					break;
			case 3:
					printf("\nThe element on the top of the stack is %d ...",peek(root));
					break;
			default :
						x++;
						break;		
		}
	}
	
}
