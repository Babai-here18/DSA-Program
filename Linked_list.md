# Singly -> Linked -> List 

### 1.  WAP in C that uses functions to perform the following operations on Singly linked list ? 
> ###	***i) Insertion  ii) Deletion  iii) Display***

> Source Code

```c




#include <stdio.h>  
#include <stdlib.h>  

struct node{  
    int data;  
    struct node *next;  
};      
struct node *head, *tail = NULL;


 
   
          // <--------- Creation in Singly linked list --------->





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


          // <--------- Insertion  in Singly Linked list --------->






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



 
           // <--------- Deletion in singly linked list --------->







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


           // <--------- End of Insertion & Deletion Operations --------->




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

// viii) insertion at any position --->
	any_del();
	display();

    return 0;  
}  
```

<br>

