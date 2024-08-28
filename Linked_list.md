# Singly -> Linked -> List 

### 1.  WAP in C that uses functions to perform the following operations on Singly linked list ? 
> ###	***i)Creation ii) Insertion  iii) Deletion  iv) Display***

> Source Code

```c




#include <stdio.h>  
#include <stdlib.h>  

struct node{  
    int data;  
    struct node *next;  
};      
struct node *head, *tail = NULL;


 
   
          // <--------- Creation  of Singly linked list --------->





void addNode(int data)  
{  
    struct node*newNode = (struct node *)malloc(sizeof(struct node *));  
    newNode->data = data;  
    newNode->next = NULL;  

    if(head == NULL) {  
       
        head = newNode;  
        tail = newNode; 
        printf("Creation : %d\n",head->data); 
    }  


    else {  
       
        tail->next = newNode;  
        tail = newNode;  
        printf("Creation : %d\n",tail->data); 
    }  
}  


          // <--------- Insertion  of Singly Linked list --------->






  void beginsert(int item)  
    {  
        struct node *ptr = (struct node *)malloc(sizeof(struct node ));  
        if(ptr == NULL)  
        {  
            printf("\nOVERFLOW\n");  
        }  
        else  
        {  
            ptr->data = item;  
            ptr->next = head;  
            head = ptr;  
            printf(" Node inserted in beginning: %d\n",ptr->data);  
        }  
          
    }  





     void randominsert(int item)  
    {  
        struct node *ptr = (struct node *) malloc (sizeof(struct node));  
        struct node *temp,*prv;  
        int i,loc;  
        if(ptr == NULL)  
        {  
            printf("\nOVERFLOW");  
        }  
        else  
        {  
            printf("Enter the location: ");  
            scanf("%d",&loc);             
            ptr->data = item;  
            temp=head;

            if(loc==1)
            {
                ptr->next=head;
                head=ptr;

            }  
            else
            {
            for(i=1;i<loc-1;i++)  
            {  
                temp = temp->next;  
                if(temp == NULL)  
                {  
                    printf("\ncan't insert\n");  
                    return;  
                }  
              
            }  
           prv=temp->next;
           temp->next=ptr;
           ptr->next=prv;

         }  
    }     
 } 





void insert_ending( int data)
{
    if(head == NULL)
    {
        printf("\n List is Empty \n");
    }
    else{
            struct node *newnode = (struct node*)malloc(sizeof(struct node));
            struct node *ptr = head;
            while(ptr->next != NULL)
            {
                ptr = ptr->next;
            }
             ptr->next = newnode;
             newnode->data = data;
             newnode->next = NULL;
             printf("Node inserted in Ending : %d\n",newnode->data);  
    }
} 



 
           // <--------- Deletion of singly linked list --------->







void del_beg()
{
     if(head == NULL)
	 {
		printf("\n List is Empty \n");
	 }

	 else{

		struct node *ptr = head;
		head = ptr->next;
		printf("\n %d Elemets is Deleted in beginning\n",ptr->data);
		free(ptr);
	 }

}





void end_del()
{
	  if(head == NULL)
	 {
		printf("\n List is Empty \n");
	 }

	 else{
			struct node*ptr = head,*prv;

			while (ptr->next != NULL)
			{
				prv = ptr;
				ptr = ptr->next;
			}

			prv->next = NULL;
		printf("\n %d Elemets is Deleted in Ending\n",ptr->data);
		free(ptr);
	 }
}





void any_del()
{
	if(head == NULL)
	{
		printf("\n List is Empty \n");
	 }

	 else{
			int loc,i;
			struct node *ptr, *prv;
		printf("\n Enter location to be deleted a node: ");
		scanf("%d",&loc);
		ptr = head;
		if(loc == 1)
		{
		ptr = head;
		head = ptr->next;
		printf("\n %d Elemets is Deleted\n",ptr->data);
		free(ptr);
		return;
		}

	else{
		 	for(i=1; i<loc; i++)
			{
					prv = ptr;
					ptr = ptr->next;
			if(ptr == NULL)  
            {  
                printf("\nThere are less than %d elements in the list..\n",loc);  
                return;  
            } 
			}
		prv->next = ptr->next;
		printf("\n %d Elemets is Deleted in Any positions\n",ptr->data);
		free(ptr);
	}

}

}


           // <--------- End of Creation & Insertion & Deletion Operations --------->




void display()
{  
    struct node *current = head;  
    if(head == NULL) {  
        printf("List is empty\n");  
        return;  
    }  
    printf("\n Nodes of singly linked list: \n");  
    while(current != NULL) {  
        
        printf("%d -> ", current->data);  
        current = current->next;  
    }  
        printf("NULL\n\n");
}  





  
int main()  
{  
   // i)Creation --->

    addNode(1); 
    addNode(2);  
    addNode(3);  
    addNode(5);
    display();

    
// ii) insertion at beginning ---> 
    beginsert(10);
    beginsert(20);
    display();


// iii) insertion at any position --->
    randominsert(4);
    display();


// iv) insertion at ending --->
    insert_ending(18);
    insert_ending(19);
    display();


// v) Deletion at beginning  --->
	del_beg();
	display();


// vi) Deletion at  ending --->
	end_del();
	display();


// viii) Deletion  at any position --->
	any_del();
	display();
    return 0;  
}  
```

<br>


## 2.  Reverse of Singly linked list.

> Source Code

```c

#include <stdio.h>  
#include <stdlib.h>  


struct node{  
    int data;  
    struct node *next;  
};      
   

struct node *head, *tail = NULL;  
   

void addNode(int data) {  
   
    struct node *newNode = (struct node*)malloc(sizeof(struct node));  
    newNode->data = data;  
    newNode->next = NULL;  
      
  
    if(head == NULL) {  
      
        head = newNode;  
        tail = newNode;  
    }  
    else {  
       
        tail->next = newNode;  
    
        tail = newNode;  
    }  
}  
   

void display() {  
   
    struct node *current = head;  
      
    if(head == NULL) {  
        printf("List is empty\n");  
        return;  
    }  
    printf("Nodes of singly linked list: \n");  
    while(current != NULL) {  
        
        printf("%d ", current->data);  
        current = current->next;  
    }  
    printf("\n");  
}  
void reverse(struct node *start)
{
struct node *prev,*ptr,*next;
prev=NULL;
ptr=start;
while(ptr!=NULL)
{
next=ptr->next;
ptr->next=prev;
prev=ptr;
ptr=next;
}
head=prev;
}
      
int main()  
{  
    //Add nodes to the list  
    addNode(1);  
    addNode(2);  
    addNode(3);  
    addNode(4);  

     
      
    //Displays the nodes present in the list

    display();  
	reverse(head);
	display();   
    return 0;  
}
``` 
<br>

# Circular -> Linked -> List 

### 3.  WAP in C that uses functions to perform the following operations on Circular linked list ? 
> ###	***i)Creation ii) Insertion  iii) Deletion  iv) Display***

> Source Code

```c

#include <stdio.h>  
#include <string.h>  
#include <stdlib.h>   
struct node{  
    int data;  
    struct node *next;  
};  
struct node *head = NULL;  
struct node *tail = NULL;  





          // <--------- Creation of Circular linked list --------->





void add(int data){  
    
    struct node *newNode = (struct node*)malloc(sizeof(struct node));  
    newNode->data = data;  
  
    if(head == NULL){  
      
        head = newNode;  
        tail = newNode;  
        newNode->next = head;  
    }else {  
        
        tail->next = newNode;  
        tail = newNode;   
        tail->next = head;  
    }  
}  






          // <--------- Insertion  of  Circular Linked list --------->





void beg_insert(int item)    
{    
        
    struct node *ptr = (struct node *)malloc(sizeof(struct node));    
    struct node *temp;  
    if(ptr == NULL)    
    {    
        printf("\nOVERFLOW");    
    }    
    else     
    {    
        ptr -> data = item;    
        if(head == NULL)    
        {    
            head = ptr;    
            ptr -> next = head;    
        }    
        else     
        {       
            temp = head;    
            while(temp->next != head)    
            temp = temp->next;    
            ptr->next = head;     
            temp -> next = ptr;     
            head = ptr;  
            printf("Node inserted in beginning: %d\n",ptr->data);    
        }     
    }    
                
} 





void lastinsert( int item)  
{  
 struct node *temp;
 struct node*ptr = (struct node *)malloc(sizeof(struct node));  
    if(ptr == NULL)  
    {  
        printf("\nOVERFLOW\n");  
    }  
    else  
    {  
        ptr->data = item;  
        if(head == NULL) 
        {  
            head = ptr;  
            ptr -> next = head;    
        }  
        else  
        {  
            temp = head;  
            while(temp -> next != head)  
            {  
                temp = temp -> next;  
            }  
            temp -> next = ptr;   
            ptr -> next = head;  
            printf("Node inserted in Ending : %d\n",ptr->data);  
        }  
    }  
  
}





void ins_at_pos()  
{  
    struct node *ptr,*x,*newNode,*z;  
    int c = 1, pos, count = 0;  
   
    newNode = (struct node*)malloc(sizeof(struct node));  
    printf("\nEnter the data for particular position: ");  
    scanf("%d", &newNode->data);  
    printf("Enter the position to be inserted: ");  
    scanf("%d", &pos);  
    x = head;  
    ptr = head;  
if (head == NULL)  
    {  
        printf("cannot enter an element at this place");  
    }  
   else if(pos==1)
   {
   while (ptr->next != head)  
    {  
        ptr = ptr->next;  
    } 
   ptr->next=newNode;
   newNode->next=head;
   head=newNode;      
   }
else
{
    while (ptr->next != head)  
    {  
        count++;  
        ptr = ptr->next;  
    }  
    count++;  
    if (pos > count)  
    {  
        printf("\n\t [OUT OF BOUND] \n");  
        return;  
    }  
    while (c < pos)
    {  
        z = x;    
        x = x->next;  
        c++;  
    }  
    newNode->next = x;  
    z->next = newNode;  
}
}





            // <--------- Deletion of Circular linked list --------->





void beg_delete()  
{  
    struct node *ptr;  
    if(head == NULL)  
    {  
        printf("\nUNDERFLOW\n");      
    }  
    else if(head->next == head)  
    {  
        head = NULL;  
        printf("%d - Elemets is Deleted in beginning\n",head->data);
        free(head);  
    }  
      
    else  
    {     
        ptr = head;   
        while(ptr -> next != head)  
        ptr = ptr -> next;   
        ptr->next = head->next;  
        printf("%d - Elemets is Deleted in beginning\n",head->data);
		free(head);
        head = ptr->next;    
    }  
}  





void last_delete()  
{  
struct node *ptr, *preptr;    
    if(head==NULL)  
    {  
        printf("\nUNDERFLOW\n");  
    }  
    else if (head ->next == head)  
    {  
        head = NULL;  
        printf("%d - Elemets is Deleted in Ending\n",head->data);
        free(head);  
    }  
    else   
    {  
        ptr = head;  
        while(ptr ->next != head)  
        {  
            preptr=ptr;  
            ptr = ptr->next;  
        }  
        preptr->next = ptr -> next;  
        printf("%d - Elemets is Deleted in Ending\n",ptr->data);
        free(ptr);     
    }  
}  





void del_at_pos()  
{  
    struct node *x,*y,*ptr;
    int c = 1, pos, count = 0;  
    printf("\n Enter the position to be deleted: ");  
    scanf("%d", &pos); 
    x=head;

if (head == NULL)  
printf("\n List is empty");     
else if(pos==1)
{
while(x->next!=head)
{
x=x->next;
}
y=head;
x->next=y->next;
head=y->next;
printf("\n %d Elemets is Deleted in Any positions\n",y->data); 
free(y);
}
 else  
    { 
        ptr = head;
        while(ptr->next != head)
        {
            count++;
            ptr = ptr->next;   
        } 
        count++;
         if(pos > count)
         {
         printf("\n\t [OUT OF BOUND] \n");  
         return;  
         }

        x = head;  

        while (c < pos)  
        {  
            y = x;  
            x = x->next;  
            c++;  
        }  
        y->next = x->next; 
        printf("\n %d Elemets is Deleted in Any positions\n",x->data); 
        free(x);  
}      
}





           // <--------- End of Creation & Insertion & Deletion Operations --------->






void display(){  
    struct node *current = head;  
    if(head == NULL){  
        printf("List is empty");  
    }  
    else{  
        printf("Nodes of the circular linked list: \n");  
         do{  
            printf("%d ", current->data);  
            current = current->next;  
        }while(current != head);  
        printf("\n\n");  
    }  
}  






int main()  
{  

// i)Creation --->
   add(3);  
   add(4);  
   add(5);  
   add(6);  
   display(); 
    

// ii) insertion at beginning ---> 
   beg_insert(2);
   beg_insert(1);
   display(); 

   
// iii) insertion at ending --->
   lastinsert(7);
   lastinsert(8);
   display();


// iv) insertion at any position --->
   ins_at_pos();
   display();


// v) Deletion at beginning  --->  
   beg_delete();
   beg_delete();
   display();

// vi) Deletion at  ending --->  
   last_delete();
   last_delete();
   display();


// viii) Deletion  at any position --->
   del_at_pos();
   display();
   return 0;  
}
```
<br>

# Doubly -> Linked -> List 

### 4.  WAP in C that uses functions to perform the following operations on Doubly linked list ? 
> ###	***i)Creation ii) Insertion  iii) Deletion  iv) Display***

> Source Code

```c

#include <stdio.h>  
#include<stdlib.h>  

struct node{  
    int data;  
    struct node *previous;  
    struct node *next;  
};      
   
struct node *head, *tail = NULL;  




                // <--------- Creation of Doubly linked linked list --------->  




               
void addNode(int data) 

{  

    struct node *newNode = (struct node*)malloc(sizeof(struct node));  
    newNode->data = data;  
      
    if(head == NULL) {  
        
        head = tail = newNode;  
        
        head->previous = NULL;  
       
        tail->next = NULL;  
    }  

    else {  
     
        tail->next = newNode;  
       
        newNode->previous = tail;  
       
        tail = newNode;  
     
        tail->next = NULL;  
    }  
}
                
                
                
                
                
                 // <--------- Insertion  of Doubly Linked list --------->





void insertion_beginning( int item)  
{  
   struct node *ptr;    
   ptr = (struct node *)malloc(sizeof(struct node));  
   if(ptr == NULL)  
   {  
       printf("\nOVERFLOW");  
   }  
   else  
   {  

   if(head==NULL)  
   {  
       ptr->data=item;  
       ptr->next = NULL;  
       ptr->previous=NULL;  
       head=ptr; 
       printf("Node inserted in beginning: %d\n",ptr->data);   
   }  
   else   
   {  
       ptr->data=item;  
       ptr->previous=NULL;  
       ptr->next = head;  
       head->previous=ptr;  
       head=ptr;  
       printf("Node inserted in beginning: %d\n",ptr->data);  
   }    
}     
} 





void insertion_last(int item)  
{  
   struct node *ptr,*temp;  
   ptr = (struct node *) malloc(sizeof(struct node));  
   if(ptr == NULL)  
   {  
       printf("\nOVERFLOW");  
   }  
   else  
   {  

       ptr->data=item;  
       if(head == NULL)  
       {  
           ptr->next = NULL;  
           ptr->previous = NULL;  
           head = ptr;  
            printf("Node inserted in Ending : %d\n",ptr->data); 
       }  
       else  
       {  
          temp = head;  
          while(temp->next!=NULL)  
          {  
              temp = temp->next;  
          }  
          temp->next = ptr;  
          ptr ->previous=temp;  
          ptr->next = NULL; 
          printf("Node inserted in Ending : %d\n",ptr->data);   
          }      
       }  
    } 





void insertion_specified()  
{  
   struct node *ptr,*temp,*prv;  
   int item,loc,i;  
   ptr = (struct node *)malloc(sizeof(struct node));  
   if(ptr == NULL)  
   {  
       printf("\n OVERFLOW");  
   }  
   else  
   {  
       temp=head;  
       printf("Enter the location: ");  
       scanf("%d",&loc);
       if(loc==1)
	   {
		   printf("Enter value: ");  
           scanf("%d",&item); 
           ptr->data=item;		   
		   ptr->next=temp;
		   temp->previous=ptr;
		   ptr->previous=NULL;
		   head=ptr;
	   }		   
	   else
	   {
       for(i=1;i<loc;i++)  
       {   
           prv=temp;
           temp = temp->next;  
           if(temp == NULL)  
           {  
               printf("\n\t [There are less than %d elements] \n\n", loc);  
               return;  
           }  
       } 
       printf("Enter value: ");  
       scanf("%d",&item);  	   
       ptr->data = item;  
       ptr->next=temp;
	   temp->previous=ptr;
	   prv->next=ptr;
	   ptr->previous=prv;
	   }	   
   }  
}





                 // <--------- Deletion in Doubly linked list --------->
 




void beginning_delete()  
{  
    struct node *ptr;  
    if(head == NULL)  
    {  
        printf("\n UNDERFLOW\n");  
    }  
    else if(head->next == NULL)  
    {  
        head = NULL;   
        printf("%d - Elemets is Deleted in beginning\n",head->data);
        free(head);       
    } 

    else  
    {  
        ptr = head;  
        head = head -> next;  
        head -> previous = NULL;  
        printf("%d - Elemets is Deleted in beginning\n",ptr->data);
        free(ptr);    
    }  
}  





void last_delete()  
{  
    struct node *ptr,*temp;  
    if(head == NULL)  
    {  
        printf("\n UNDERFLOW\n");  
    }  
    else if(head->next == NULL)  
    {  
        head = NULL;   
        printf("%d - Elemets is Deleted in Ending\n",head->data);
        free(head);  
    }  
    else   
    {  
        ptr = head;   
        while(ptr->next != NULL)  
        {  
	        temp=ptr;
            ptr = ptr -> next;   
        }  
        temp->next=NULL;
        ptr->previous=NULL;        		
        printf("%d - Elemets is Deleted in Ending\n",ptr->data);
        free(ptr);     
    }  
} 





void delete_anypos()
{
struct node *curnode,*ptr,*temp;
int i,nodes=1,pos;
printf("\nEnter position to be deleted a node: ");
scanf("%d",&pos);
ptr=head;
curnode=head;
while(ptr->next!=NULL)
{
nodes++;
ptr=ptr->next;
}
for(i=1;i<pos && curnode!=NULL;i++)
{
temp=curnode;
curnode=curnode->next;
}
if(pos==1)
{
        ptr = head;  
        head = head -> next;  
        head -> previous = NULL;  
        free(ptr);  
}
else if(pos==nodes)
{
ptr = head;   
        while(ptr->next != NULL)  
        {  
	        temp=ptr;
            ptr = ptr -> next;   
        }  
        temp->next=NULL;
        ptr->previous=NULL;        		
        free(ptr);  
}
else
{
curnode->previous->next=curnode->next;
curnode->next->previous=curnode->previous;
free(curnode);
}
}
            
            
            
            
             // <--------- End of Creation & Insertion & Deletion Operations --------->





void display() {  
 
    struct node *current = head;  
    if(head == NULL) {  
        printf("List is empty\n");  
        return;  
    }  
    printf("Nodes of doubly linked list: \n");  
    while(current != NULL) {  
    
        printf("%d ", current->data);  
        current = current->next;  
    } 
    printf("\n\n");
}  





int main()  
{  


// i)Creation --->    
    addNode(3);  
    addNode(4);  
    addNode(5);  
    display();


// ii) insertion at beginning ---> 
    insertion_beginning(2);
    insertion_beginning(1);
    display();


// iii) insertion at ending --->
    insertion_last(7);
    insertion_last(8);
    display();


// iv) insertion at any position --->
    insertion_specified();
    display();


// v) Deletion at beginning  --->  
    beginning_delete();
    beginning_delete();
    display();


// vi) Deletion at  ending --->    
    last_delete();
    last_delete();
    display();


// viii) Deletion at any position --->
    delete_anypos();
    display();
    return 0;  
}
``` 






