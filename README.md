
#include<stdio.h>
#include<stdlib.h>
struct node{
	int id;
	char name[50];
	char qua[40];
	char dep[10];
	char sub[30];
	int salary;
	struct node *prev,*next;
};
struct node *head=NULL;

struct node *split(struct node *head);

struct node *merge(struct node *first, struct node *second)
{
    if (!first)
        return second;

    if (!second)
        return first;

    if (first->id < second->id)
    {
        first->next = merge(first->next,second);
        first->next->prev = first;
        first->prev = NULL;
        return first;
    }
    else
    {
        second->next = merge(first,second->next);
        second->next->prev = second;
        second->prev = NULL;
        return second;
    }
}

struct node *mergeSort(struct node *head)
{
    if (!head || !head->next)
        return head;
    struct node *second = split(head);

    head = mergeSort(head);
    second = mergeSort(second);

    return merge(head,second);
}

  void swap(int *A, int *B)
{
    int temp = *A;
    *A = *B;
    *B = temp;
}

struct node *split(struct node *head)
{
    struct node *fast = head,*slow = head;
    while (fast->next && fast->next->next)
    {
        fast = fast->next->next;
        slow = slow->next;
    }
    struct node *temp = slow->next;
    slow->next = NULL;
    return temp;
}


void add_first();
void add_last();
void add_after();
void add_before();
void del();
void search();
void update();
void dis();
int main()
{
	int n;
	char ch;
	x2:
	printf("\n\t\t\t *************  WELCOME TO PROFESSOR'S DATABASE SYSTEM!  *************\n");
	printf("\n\t\t\t =====================================================================\n");
	printf("\n\t\t\t Please enter the action you want to perform! \n");
	printf("\n\t\t\t 1. Add a record:\n");
	printf("\n\t\t\t 2. Search a record:\n");
	printf("\n\t\t\t 3. Update a record:\n");
	printf("\n\t\t\t 4. Delete a record:\n");
	printf("\n\t\t\t 5. Display a record:\n");
	printf("\n\t\t\t 6. Exit:\n");
	printf("\n\t\t\t =====================================================================\n");
	printf("\n\t\t Enter Your Choice: ");
	scanf("%d",&n);
	system("cls");1

	if(n==1)
	{
		x1:
		printf("\n\t\t=> Where do you want to add record?\n");
		printf("\n\t\t ==================================\n");
		printf("\n\t\t 1. Add record at the beginning:\n");
		printf("\n\t\t 2. Add next record:\n");
		printf("\n\t\t 3. Add record After a given record:\n");
		printf("\n\t\t 4. Add record Before a given record:\n");
		printf("\n\t Enter Your Choice: ");
		scanf("%d",&n);
		system("cls");
		if(n==1)
		{
		    system("cls");
			add_first();
			printf("\n\t\tDo You want to go main menu? Press Y or N\n");
			fflush(stdin);
			printf("\n\t\t");
			scanf("%c",&ch);
			if(ch=='y'||ch=='Y')
			{
			    system("cls");
				goto x2;
			}
			else
			{
				exit(1);
			}
		}
		else if(n==2)
		{
			system("cls");
			add_last();
			printf("\n\t\tDo You want to go main menu? Press Y or N\n");
			fflush(stdin);
			printf("\n\t\t");
			scanf("%c",&ch);
			if(ch=='y'||ch=='Y')
			{
			    system("cls");
				goto x2;
			}
			else
			{
				exit(1);
			}
		}
		else if(n==3)
		{
		    system("cls");
			add_after();
			printf("\n\t\tDo You want to go main menu? Press Y or N\n");
			fflush(stdin);
			printf("\n\t\t");
			scanf("%c",&ch);
			if(ch=='y'||ch=='Y')
			{
			    system("cls");
				goto x2;
			}
			else
			{
				exit(1);
			}
		}
		else if(n==4)
		{
		    system("cls");
			add_before();
			printf("\n\t\tDo You want to go main menu? Press Y or N\n");
			printf("\n\t\t");
			fflush(stdin);
			scanf("%c",&ch);
			if(ch=='y'||ch=='Y')
			{
			    system("cls");
				goto x2;
			}
			else
			{
				exit(1);
			}
		}
		else
		{
			printf("\n\t\t WRONG INPUT entered! \n");
			goto x1;
		}
	}
	else if(n==2)
		{
		    system("cls");
			search();
			printf("\n\t\tDo You want to go main menu? Press Y or N\n");
			fflush(stdin);
			printf("\n\t\t");
			scanf("%c",&ch);
			if(ch=='y'||ch=='Y')
			{
			    system("cls");
				goto x2;
			}
			else
			{
				exit(1);
			}
		}
	 else if(n==3)
		{
		    system("cls");
			update();
			printf("\n\t\tDo You want to go main menu? Press Y or N\n");
			fflush(stdin);
			printf("\n\t\t");
			scanf("%c",&ch);
			if(ch=='y'||ch=='Y')
			{
			    system("cls");
				goto x2;
			}
			else
			{
				exit(1);
			}
		}
	else if(n==4)
		{
		    system("cls");
			del();
			printf("\n\t\tDo You want to go main menu? Press Y or N\n");
			fflush(stdin);
			printf("\n\t\t");
			scanf("%c",&ch);
			if(ch=='y'||ch=='Y')
			{
			    system("cls");
				goto x2;
			}
			else
			{
				exit(1);
			}
		}
	else if(n==5)
		{
		    system("cls");
			dis();
			printf("\n\t\tDo You want to go main menu? Press Y or N\n");
			printf("\n\t\t");
			fflush(stdin);
			scanf("%c",&ch);
			if(ch=='y'||ch=='Y')
			{
			    system("cls");
				goto x2;
			}
			else
			{
				exit(1);
			}
		}
	else if(n==6)
		{
			exit(1);
		}
	else
		{
			printf("\n\t\t WRONG INPUT entered! \n");
			goto x2;
		}
	return 0;
}

void add_first()
{
    printf("\n\t\t\t *** Adding Record at the beginning! ***\n");
    printf("\n\t\t\t =======================================\n");
	struct node *new_n;
	new_n=(struct node *)malloc(sizeof(struct node));
	printf("\n\t\tEnter Professor's Id: ");
	scanf("%d",&new_n->id);
	fflush(stdin);
	printf("\n\t\tEnter The Professor's Name: ");
	gets(new_n->name);
	fflush(stdin);
	printf("\n\t\tEnter The Professor's Qualification: ");
	gets(new_n->qua);
	fflush(stdin);
	printf("\n\t\tEnter The Professor's Department: ");
	gets(new_n->dep);
	fflush(stdin);
	printf("\n\t\tEnter The Professor's Subject: ");
	gets(new_n->sub);
	fflush(stdin);
	printf("\n\t\tEnter The Professor's Salary: ");
	scanf("%d",&new_n->salary);
	fflush(stdin);
	new_n->next=head;
	new_n->prev=NULL;
	if(head!=NULL)
	{
		head->prev=new_n;
	}
	head=new_n;
	printf("\n\t\tRecord is Generated successfully!\n");

}

void add_last()
{
    printf("\n\t\t\t *** Adding next record! ***\n");
    printf("\n\t\t\t ===========================\n");
	char ch;
	if(head==NULL)
	{
	    system("cls");
		printf("\n\t\tOops! No Records present!\n");
		printf("\n\t\tDo you want to Add a new Record? \n\t\tPress Y or N:");
		fflush(stdin);
		printf("\n\t\t");
		scanf("%c",&ch);
		if(ch=='y'||ch=='Y')
		{
		    system("cls");
			add_first();
			return ;
		}
		else
		{
			exit(1);
		}
	}
	else
	{
		struct node *temp;
		temp=head;
		while(temp->next!=NULL)
		{
			temp=temp->next;
		}
		struct node *new_n;
		new_n=(struct node *)malloc(sizeof(struct node));
		printf("\n\t\tEnter Professor's Id: ");
		scanf("%d",&new_n->id);
		fflush(stdin);
		printf("\n\t\tEnter The Professor's Name: ");
		gets(new_n->name);
		fflush(stdin);
		printf("\n\t\tEnter The Professor's Qualification: ");
		gets(new_n->qua);
		fflush(stdin);
		printf("\n\t\tEnter The Professor's Department: ");
		gets(new_n->dep);
		fflush(stdin);
		printf("\n\t\tEnter The Professor's Subject: ");
		gets(new_n->sub);
		fflush(stdin);
		printf("\n\t\tEnter The Professor's Salary: ");
		scanf("%d",&new_n->salary);
		fflush(stdin);
		new_n->next=NULL;
		temp->next=new_n;
		new_n->prev=temp;
	}
}

void add_after()
{
    printf("\n\t\t\t *** Adding Record after a given record! ***\n");
    printf("\n\t\t\t ===========================================\n");
	char ch;
	int flag;
	if(head==NULL)
	{
		printf("\n\t\tOops! No Records present!\n");
		printf("\n\t\tDo you want to Add a new Record? \n\t\tPress Y or N:");
		fflush(stdin);
		printf("\n\t\t");
		scanf("%c",&ch);
		if(ch=='y'||ch=='Y')
		{
		    system("cls");
			add_first();
			return ;
		}
		else
		{
			exit(1);
		}
	}
	else
	{
		int val;
		printf("\n\t\tEnter ID after which you want to add a new record: ");
		scanf("%d",&val);
		system("cls");
		flag=0;
		struct node *temp,*p;
		temp=head;
		while(temp!=NULL)
		{
			if(temp->id==val)
			{
				struct node *new_n;
				new_n=(struct node *)malloc(sizeof(struct node));
				fflush(stdin);
				printf("\n\t\tEnter Professor's Id: ");
				scanf("%d",&new_n->id);
				fflush(stdin);
				printf("\n\t\tEnter The Professor's Name: ");
				gets(new_n->name);
				fflush(stdin);
				printf("\n\t\tEnter The Professor's Qualification: ");
				gets(new_n->qua);
				fflush(stdin);
				printf("\n\t\tEnter The Professor's Department: ");
				gets(new_n->dep);
				fflush(stdin);
				printf("\n\t\tEnter The Professor's Subject: ");
				gets(new_n->sub);
				fflush(stdin);
				printf("\n\t\tEnter The Professor's Salary: ");
				scanf("%d",&new_n->salary);
				fflush(stdin);
				if(temp->next!=NULL)
				{
					new_n->next=temp->next;
					new_n->prev=temp;
					p=temp->next;
					p->prev=new_n;
					temp->next=new_n;
				}
				else
				{
					new_n->next=temp->next;
					new_n->prev=temp;
					temp->next=new_n;
				}
				flag=1;
			}
			temp=temp->next;
		}
		if(flag==0)
		{
			printf("\n\t\tID is not found!\n");
		}
	}
}

void add_before()
{
    printf("\n\t\t\t *** Adding Record before a given record! ***\n");
    printf("\n\t\t\t ============================================\n");
	char ch;
	int flag;
	if(head==NULL)
	{
		printf("\n\t\tOops! No Records present! \n");
		printf("\n\t\tDo you want to Add a new Record? \n\t\tPress Y or N:");
		fflush(stdin);
		printf("\n\t\t");
		scanf("%c",&ch);
		if(ch=='y'||ch=='Y')
		{
		    system("cls");
			add_first();
			return ;
		}
		else
		{
			exit(1);
		}
	}
	else
	{
		int val;
		printf("\n\t\tEnter ID before which you want to add a new record: ");
		scanf("%d",&val);
		flag=0;
		struct node *temp,*p;
		temp=head;
		if(temp->id==val)
		{
		    system("cls");
			add_first();
			return ;
		}
		else
		{
			while(temp!=NULL)
			{
				if(temp->id==val)
				{
					struct node *new_n;
					new_n=(struct node *)malloc(sizeof(struct node));
					fflush(stdin);
					printf("\n\t\tEnter Professor's Id: ");
					scanf("%d",&new_n->id);
					fflush(stdin);
					printf("\n\t\tEnter The Professor's Name: ");
					gets(new_n->name);
					fflush(stdin);
					printf("\n\t\tEnter The Professor's Qualification: ");
					gets(new_n->qua);
					fflush(stdin);
					printf("\n\t\tEnter The Professor's Department: ");
					gets(new_n->dep);
					fflush(stdin);
					printf("\n\t\tEnter The Professor's Subject: ");
					gets(new_n->sub);
					fflush(stdin);
					printf("\n\t\tEnter The Professor's Salary: ");
					scanf("%d",&new_n->salary);
					fflush(stdin);
					new_n->next=temp;
					new_n->prev=temp->prev;
					p=temp->prev;
					p->next=new_n;
					temp->prev=new_n;
					flag=1;
				}
				temp=temp->next;
			}
			if(flag==0)
			{
				printf("\n\t\tID is not found\n");
			}
		}
	}
}

void del()
{
    printf("\n\t\t\t *** Deleting records! ***\n");
    printf("\n\t\t\t =========================\n");
	char ch;
	if(head==NULL)
	{
		printf("\n\t\tOops! No Records present! \n");
		printf("\n\t\tDo you want to Add a new Record? \n\t\tPress Y or N:");
		fflush(stdin);
		printf("\n\t\t");
		scanf("%c",&ch);
		if(ch=='y'||ch=='Y')
		{
		    system("cls");
			add_first();
			return ;
		}
		else
		{
			exit(1);
		}
	}
	else
	{
		int val;
		printf("\n\t\tEnter the Professor's ID to delete from record: ");
		fflush(stdin);
		scanf("%d",&val);
		system("cls");
		struct node *temp;
		temp=head;
		int flag=0;
		if(temp->id==val)
		{
		    if(temp->next==NULL)
            {
               head=NULL;
               free(head);
               printf("\n\t\tRecord of the Professor's has been deleted and there is no more record left!\n");
               return ;
            }
            else
			{
			    head=temp->next;
			head->prev=NULL;
			flag=1;
			free(temp);
			if(flag==1)
			{
				printf("\n\t\tRecord of the Professor's has been deleted successfully\n");
			}
			return ;
			}
		}
		else
		{
			while(temp!=NULL)
			{
				if(temp->id==val)
				{
					struct node *p,*q;
					if(temp->next==NULL)
					{
						p=temp->prev;
						p->next=NULL;
						flag=1;
						free(temp);
					}
					else
					{
						p=temp->prev;
						q=temp->next;
						p->next=q;
						q->prev=p;
						flag=1;
						free(temp);
					}
				}
				temp=temp->next;
			}
			if(flag==1)
			{
				printf("\n\t\tRecord of the Professor's has been deleted successfully\n");
			}
			else if(flag==0)
			{
				printf("\n\t\tID is not found!\n");
			}
		}
	}
}

void dis()
{
    printf("\n\t\t\t *** Displaying the records! ***\n");
    printf("\n\t\t\t ===============================\n");
	char ch;
	int n;
	if(head==NULL)
	{
		printf("\n\t\tOops! No Records present!\n");
		fflush(stdin);
		printf("\n\t\tDo you want to Add a new Record? \n\t\tPress Y or N:");
		fflush(stdin);
		printf("\n\t\t");
		scanf("%c",&ch);
		if(ch=='y'||ch=='Y')
		{
		    system("cls");
			add_first();
			return ;
		}
		else
		{
			exit(1);
		}
	}
	else
	{
        printf("\n\t\t 1. Display the records in the order it was entered (unsorted):\n");
		printf("\n\t\t 2. Display the records in the organized order of their ID (sorted) :\n");
		fflush(stdin);
		printf("\n\t\t");
		scanf("%d",&n);
		system("cls");
		if(n==2)
	    {head = mergeSort(head);
		struct node *temp;
		temp=head;
		printf("\n\t\tINFORMATION OF PROFESSORS\n\n");
		int num=1;
		while(temp!=NULL)
		{
		    printf("\n\t\t %d.\n",num);
			printf("\n\t\t ID:            \t%d\n",temp->id);
			printf("\n\t\t NAME:          \t%s\n",temp->name);
			printf("\n\t\t QUALIFICATION: \t%s\n",temp->qua);
			printf("\n\t\t DEPARTMENT:    \t%s\n",temp->dep);
			printf("\n\t\t SUBJECT:       \t%s\n",temp->sub);
			printf("\n\t\t SALARY:        \t%d\n\n",temp->salary);
			temp=temp->next;
			num++;
		} }
		else if (n==1)
        {
            struct node *temp;
		temp=head;
		printf("\n\t\tINFORMATION OF PROFESSORS\n\n");
		int num=1;
		while(temp!=NULL)
		{
		    printf("\n\t\t %d.\n",num);
			printf("\n\t\t ID:            \t%d\n",temp->id);
			printf("\n\t\t NAME:          \t%s\n",temp->name);
			printf("\n\t\t QUALIFICATION: \t%s\n",temp->qua);
			printf("\n\t\t DEPARTMENT:    \t%s\n",temp->dep);
			printf("\n\t\t SUBJECT:       \t%s\n",temp->sub);
			printf("\n\t\t SALARY:        \t%d\n\n",temp->salary);
			temp=temp->next;
			num++;
        }
        }
        else
        {
            printf("\n\t\t WRONG INPUT entered!\n\n");
            dis();
        }
	}
}

void search()
{
    printf("\n\t\t\t *** Searching the database! ***\n");
    printf("\n\t\t\t ===============================\n");
	char ch;
	if(head==NULL)
	{
		printf("\n\t\tOops! No Records present!\n");
		printf("\n\t\tDo you want to Add a new Record?\n\t\tPress Y or N:");
		fflush(stdin);
		printf("\n\t\t");
		scanf("%c",&ch);
		if(ch=='y'||ch=='Y')
		{
		    system("cls");
			add_first();
			return ;
		}
		else
		{
			exit(1);
		}
	}
	else
	{
		int val;
		printf("\n\t\tEnter the Professor's ID which you want to search: ");
		scanf("%d",&val);
		system("cls");
		struct node *temp;
		temp=head;
		int flag=0;
		while(temp!=NULL)
		{
			if(temp->id==val)
			{

				printf("\n\t\tINFORMATION OF PROFESSOR FOUND\n\n");

				printf("\n\t\t ID:            \t%d\n",temp->id);
				printf("\n\t\t NAME:          \t%s\n",temp->name);
				printf("\n\t\t QUALIFICATION: \t%s\n",temp->qua);
				printf("\n\t\t DEPARTMENT:    \t%s\n",temp->dep);
				printf("\n\t\t SUBJECT:       \t%s\n",temp->sub);
				printf("\n\t\t SALARY:        \t%d\n\n",temp->salary);

				return ;
			}
			temp=temp->next;
		}
		if(temp==NULL)
            printf("\n\t\tRECORD NOT FOUND!\n\n");
	}
}

void update()
{
    printf("\n\t\t\t *** Updating the record's database! ***\n");
    printf("\n\t\t\t =======================================\n");
	char ch;
	if(head==NULL)
	{
		printf("\n\t\tOops! No Record present! \n");
		printf("\n\t\tDo you want to Add a new Record? \n\t\tPress Y or N:");
		fflush(stdin);
		printf("\n\t\t");
		scanf("%c",&ch);
		if(ch=='y'||ch=='Y')
		{
		    system("cls");
			add_first();
			return ;
		}
		else
		{
			exit(1);
		}
	}
	else
	{
		int val;
		printf("\n\t\t Enter the Professor's ID to Modify:\t");
		scanf("%d",&val);
		system("cls");
		struct node *temp;
		temp=head;
		int flag1=0;
		while(temp!=NULL)
		{
			if(temp->id==val)
			{
			        flag1=1;
					fflush(stdin);
					printf("\n\t\tEnter Professor's Id: ");
					scanf("%d",&temp->id);
					fflush(stdin);
					printf("\n\t\tEnter The Professor's Name: ");
					gets(temp->name);
					fflush(stdin);
					printf("\n\t\tEnter The Professor's Qualification: ");
					gets(temp->qua);
					fflush(stdin);
					printf("\n\t\tEnter The Professor's Department: ");
					gets(temp->dep);
					fflush(stdin);
					printf("\n\t\tEnter The Professor's Subject: ");
					gets(temp->sub);
					fflush(stdin);
					printf("\n\t\tEnter The Professor's Salary: ");
					scanf("%d",&temp->salary);
					fflush(stdin);
			}
			temp=temp->next;
		}
		if(flag1==1)
		printf("\n\t\tRecord has been SUCCESSFULLY updated!");
		else
        printf("\n\t\tRECORD NOT FOUND!\n\n");
	}
}
