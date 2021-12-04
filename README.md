# assignment2
#include <stdio.h>
#include<string.h>

struct player
{
  char name[100];
	int age;
	char country[100];
  char category[100];
	int odi;
	int t20;
  float avg_bat;
  int wickets;

};

void accept(struct player p[],int n)
{
  
    
	for (int i = 0; i < n; i++) {
	  printf("Enter Name of Player %d\n", i + 1);
	  scanf("%s", p[i].name);
	  printf("Enter age\n");
	  scanf("%d", &p[i].age);
	  printf("Enter country\n");
	  scanf("%s", p[i].country);
    printf("Enter category\n");
    scanf("%s",p[i].category);
    printf("no of odi played\n");
    scanf("%d",&p[i].odi);
    printf("no of t20 played\n");
    scanf("%d",&p[i].t20);
    printf("enter average batting\n");
    scanf("%f",&p[i].avg_bat);
    printf("enter wickets\n");
    scanf("%d",&p[i].wickets);
		
		
		
    }
  }

void display(struct player p[],int n)
{
  int i;
  for (i=0;i<n;i++){
    printf("\nDetails of player:%d\n",i+1);
    printf("\nname=%s",p[i].name);
    printf("\nage=%d",p[i].age);
    printf("\ncountry=%s",p[i].country);
    printf("\ncategory=%s",p[i].category);
    printf("\nodi=%d",p[i].odi);
    printf("\nt20=%d",p[i].t20);
    printf("\naverage batting=%f",p[i].avg_bat);
    printf("\nwickets=%d\n",p[i].wickets);

    }
}

void country(struct player p[],int n)
{
    char c[100];
    printf("\nenter country :\n");
    scanf("%s",c);
    int i;
    for (i=0;i<n;i++){
        if(strcmp(c,p[i].country)==0)
        printf("%s\n",p[i].name);
        
    }
}

void avg_batsort(struct player p[],int n)
{
  int t;
  for(int i=0;i<n;i++)
  {
    for(int j=0;j<n-1;j++)
    {
      if(p[j].avg_bat > p[j+1].avg_bat)
      {
        
        t=p[j].avg_bat;
        p[j].avg_bat=p[j+1].avg_bat;
        p[j+1].avg_bat=t;
             
      }
       
    }
    
  }
  printf("-------------------------------------------------------\n");
  for( int i=0; i<n;i++)
  {
    
    printf("\n%s\t%f",p[i].name,p[i].avg_bat);
    
    
}
}


void bowl_country(struct player p[]) {
  int n;
 char b[100];
	printf("Enter Country\n");
	scanf("%s",b);
	printf("Bowlers from %s are\n", b);
	for (int i = 0; i < n; i++) {
		if ((strcmp(b, p[i].country) == 0) &&
			strcmp(p[i].category, "bowler") == 0)
			printf("%s\n", p[i].name);
	}
}

void max_wickets(struct player p[]) {
 int c = p[0].wickets;
 int r=0;
	int n;
	for (int i = 0; i < n; i++) {
		if (p[i].wickets > c) {
			c= p[i].wickets;
      r=i;
			
		}
	}
	printf("Players with most wickets is %s with wickets %d\n",p[r].name, c);
}

void age(struct player p[]) {
 int c = p[0].age;
 int b=0;
	int n;
	for (int i = 0; i < n; i++) {
		if (p[i].age > c) {
			c= p[i].age;
      b=i;
			
		}
	}
	printf("Players with most age is %s with age  %d\n", p[b].name,c);
}


void display_info(struct player p[],int n)
{
char ch[20];
  printf("Enter player's name \n:");
  scanf("%s",ch);
  printf("\nNAME\t\tWICKETS\t\t\tAvg_SCORE\t\t\tCountry\t\t\tAge\n");
   for(int i=0;i<n;i++)
  {
    if((strcmp(ch,p[i].name)==0))
    {
    printf("-------------------------------------------------------\n");
     printf("%s\t\t\t%d\t\t\t%f\t\t\t%s\t\t\t%d\n",
     p[i].name,p[i].wickets,p[i].avg_bat,p[i].country,p[i].age);
    printf("-------------------------------------------------------\n");
    }
  }
}
 
int main()
{
  struct player p[5];
  int n;
  printf("Enter no of players: \n");
	scanf("%d", &n);
  int choice;
  do
  {
    printf("-------------------------------------------------------\n");
    printf("-------------------------------------------------------");
    printf("\n1.Create\n2.Display_all_players\n3.batsman_of_particular_country\n4.sort_avg_bat\n5.Bowler_country\n6.max_wickets\n7.max_age\n9.display_info\n0.exit\n");
    printf("\nEnter your choice\n");
		scanf("%d", &choice);
		switch (choice) {
		case 1:
            accept(p,n);
		  	break;
    case 2:
            display(p,n);
         break;
    case 3:
            country(p,n);
            break;
    case 4:
            avg_batsort(p, n);
            break;
   case 5:
            bowl_country(p);
            break;

    case 6:
            max_wickets(p);
            break;

    case 7:
            age(p);
            break; 

    case 8:
            display_info(p,n);
            break;
                           
  
    default:
            printf("end");
         break; 
    }
  }while(choice!=0);
  
     
      
  
  }

 
  

  
  
  
    



