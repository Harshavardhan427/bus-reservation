# bus-reservation
#include<conio.h>
#include<cstdio>
#include<iostream>
#include<string.h>
#include<cstdlib>
using namespace std;
static int p = 0;
class a
{
	char busn[5],driver[10],araival[5],depart[5],from[10],to[10],seat[8][4][10];
	public:
		void install();
		void allotment();
		void empty();
		void show();
		void avail();
		void position (int i);
		
}
bus[10];
void vline (char ch)
{
	for(int i=80;i>0;i--)
	cout<<ch;
}

void a ::install()

{
	cout<<"enter bus no : ";
	cin>>bus[p].busn;
	cout<<"\n enter the driver name : ";
	cin>>bus[p].driver;
	cout<<"\n enter araival time : ";
	cin>>bus[p].araival;
	cout<<"\n enter departure time : ";
	cin>>bus[p].depart;
	cout<<" \n from  : \t\t\t";
	cin>>bus[p].from;
	cout<<"\n to : \t\t\t";
	cin>>bus[p].to;
	bus[p].empty();
	p++;
}

void a :: allotment()
{
	int seat;
	char number[5];
	top:
	cout<<"bus no : ";
	cin>> number[5];
	int n ;
	for(n=0;n<=p;n++)
	{
		if(strcmp(bus[n].busn,number)==0)
		break;
	}
	while(n<=p)
	{
		cout<<"\n seat number : ";
		cin >>seat;
		if (seat<32)
		{
			cout<<"\n there are only 32 seats available in this bus";
		}
		else
		{
			if(strcmp(bus[n].seat[seat/4][(seat%4)-1],"empty")==0)
			{
				cout<<"enter the passengers name : ";
				cin>>bus[n].seat[seat/4][(seat%4)-1];
				break;
			}
			else
			cout<<"the seat no.is alraedy resrved. \n";
		}
	}
	if(n>p)
	{
		cout<<"enter correct bus no. \n";
		goto top;
	}
}

void a :: empty()
{
	for(int i=0;i<8;i++)
	{
		for (int j=0;j<4;j++)
		{
			strcpy(bus[p].seat[i][j],"empty");
		}
	}
}

void a :: show()
{
	int n;
	char number[5];
	cout<<"enter the bus no. : ";
	cin>>number;
	for(n=0;n<=p;n++)
	{
		if(strcmp(bus[n].busn,number)==0)
		break;
	}
	while(n<=p)
	{
		vline('*');
		cout<<"bus no :\t" <<bus[n].busn;
		cout<<"\n driver : " <<bus[n].driver;
		cout<<"\t araival time : " <<bus[n].araival;
		cout<<"\t departure time : " <<bus[n].depart;
		cout<<"\n from : \t\t" <<bus[n].from ; 
		cout<<"\t\t to : \t\t " <<bus[n].to;
		cout<<"\n";
		vline('*');
		bus[0].position(n);
		int a =1;
		for(int i=0;i<8;i++)
		{
			for(int j=0;j<4;j++)
			{
				a++;
				if(strcmp(bus[n].seat[i][j],"empty")!=0)
				cout <<"\n the seat no"<<(a-1)<<"is reserved for"<<bus[n].seat[i][j]<<".";
			}
		}
		break;
	}
	if(n>p)
	cout<<"enter correct bus no. : ";
}
void a :: position(int i)
{
	int s=0,p=0;
	for (int i=0;i<8;i++)
	{
		cout<<"\n";
	for(int j=0;j<4;j++)
	{
		s++;
	
	if(strcmp(bus[i].seat[i][j],"empty")==0)
	{
		cout.width(5);
		cout.fill('_');
		cout<<s <<".";
		cout.width(10);
		cout.fill('_');
		cout<< bus[i].seat[i][j];
		p++;
	}
	else
	{
	
	cout.width(5);
	cout.fill('_');
	cout<<s <<".";
	cout.width(10);
	cout.fill('_');
	cout<< bus[p].seat[i][j];
    }
   }
  }
    cout<<"\n there are "<<p<<"seats empty in bus no"<<bus[p].busn;
}

void a :: avail()
{
	for (int n=0;n<p;n++)
	{
		vline('*');
		cout<<"bus no :"<<bus[n].busn;
		cout<<"\n driver : "<<bus[n].driver;
		cout<<"\t arrival time : "<<bus[n].araival;
		cout<<"\t departure time : "<<bus[n].depart;
		cout<<"\n from : \t\t"<<bus[n].from;
		cout<<"\t\t to : \t\t"	<<bus[n].to;
		cout<<"\n";
		vline('*');
		vline('_');
	}	
}

int main()
{
	system ("cls");
	int w;
	while(1)
	{
		cout<<"\n\n\n\n\n\n";
		cout<<"\t\t1.install \n \t\t"<<"2.reservation \n \t\t"<<"3.show\n \t\t"<<"4.buses available \n \t\t"<<"5.exit";
		cout<<"\n \t\t enter your choice:-->";
		cin>>w;
		switch(w)
		{
			case 1:bus[p].install();
			break;
			case 2:bus[p].allotment();
			break;
			case 3:bus[0].show();
			break;
			case 4:bus[0].avail();
			break;
			case 5: exit(0);
			
		}
	}
	return 0;
}
  
  output:
  





                1.install
                2.reservation
                3.show
                4.buses available
                5.exit
                 enter your choice:-->1
enter bus no : 1

 enter the driver name : hhh

 enter araival time : 6.00

 enter departure time : 6.30

 from  :                        hyd

 to :                   brd






                1.install
                2.reservation
                3.show
                4.buses available
                5.exit
                 enter your choice:-->5

--------------------------------
Process exited after 80.62 seconds with return value 0
Press any key to continue . . .
