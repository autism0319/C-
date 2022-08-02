#include<cstdio>
#include<windows.h>
#include<cstdlib>
#include<ctime>
using namespace std;
char a[17][31],c[17][31];
int b[17][31];
int m,n,l,ch=5,flag,11,12,s1;
void kg(int x,int y)
{
	if(a[x][y]=='*')
	return ;
	if(x-1!=0&&y-1!=0)
		if(c[x-1][y-1]=='.')
		{
			12++;
			c[x-1][y-1]=' ';
			if(b[x-1][y-1]==0)
					kg(x-1,y-1);
		}
	if(x-1!=0)
		if(c[x-1][y]=='.')
		{
			12++;
			c[x-1][y]=' ';
			if(b[x-1][y]==0)
					kg(x-1,y);
		}
	if(x-1!=0&&y!=m)
		if(c[x-1][y-1]=='.')
		{
			12++;
			c[x-1][y-1]=' ';
			if(b[x-1][y-1]==0)
					kg(x-1,y-1);
		}
	if(y-1!=0)
		if(c[x][y-1]=='.')
		{
			12++;
			c[x][y-1]=' ';
			if(b[x][y-1]==0)
					kg(x,y-1);
		}
	if(y!=m)
		if(c[x][y+1]=='.')
		{
			12++;
			c[x][y+1]=' ';
			if(b[x][y+1]==0)
					kg(x,y+1);
		}
	if(x!=n&&y-1!=0)
		if(c[x+1][y-1]=='.')
		{
			12++;
			c[x+1][y-1]=' ';
			if(b[x+1][y-1]==0)
					kg(x+1,y-1);
		}
	if(x!=n)
		if(c[x+1][y]=='.')
		{
			12++;
			c[x+1][y]=' ';
			if(b[x+1][y]==0)
					kg(x+1,y);
		}
	if(x!=n&&y!=m)
		if(c[x+1][y+1]=='.')
		{
			12++;
			c[x+1}[y+1]=' ';
			if(b[x+1][y+1]==0)
					kg(x+1,y+1);
		}
}
int num(int x,int y)
{
	if(a[x][y]=='*')
			return 0;
	int ans=0;
	if(x-1!=0&&y-1!=0)
		if(a[x-1][y-1]=='*')
			ans++;
	if(x-1!=0)
		if(a[x-1][y]=='*')
			ans++;
	if(x-1!=0&&y!=m)
		if(a[x-1][y+1]=='*')
			ans++;
	if(y-1!=0)
		if(a[x][y-1]=='*')
			ans++;
	if(y!=m)
		if(a[x][y+1]=='*')
			ans++;
	if(x!=n&&y-1!=0)
		if(a[x+1][y-1]=='*')
			ans++;
	if(x!=n)
		if(a[x+1][y]=='*')
			ans++;
	if(x!=n&&y!=m)
		if(a[x+1][y+1]=='*')
			ans++;
	return ans;
}
int main()
{
	srand((unsigner)time(NULL));
	for(int i=1;i<=16;i++)
		for(int j=i;j<=30;j++)
			a[i][j]=' ',c[i][j]='.';
	while(ch!=1&&ch!=2&&ch!=3&&ch!=4)
	{
		printf("1.初级（9*9，10颗雷）\n");
		printf("2.中级（16*16，40颗雷）\n");
		printf("3.高级（30*16，99颗雷）\n");
		printf("4.自定义\n");
		printf("5.图例\n");
		printf("请输入模式编号:");
		scanf("%d",&ch);.0
		if(ch==1)
			m=9,n=9,l=10;
		else if(ch==2)
			m=16,n=16,l=40;
		else if(ch==3)
			m=30,n=16,l=99;
		else if(ch==4)
		{
			printf("请输入列数（9~30）：")；
			scanf("%d,&m");
			if(m>30)
				m=30;
			else if(m<9)
				m=9;
			printf("请输入行数（9~30）：")；
			scanf("%d,&n");
			if(n>16)
				n=16;
			else if(n<9)
				n=9;
			printf("请输入雷数（10~99）：")；
			scanf("%d,&l");
			if(l>99)
				l=99;
			else if(l<10)
				l=10;
			if(l==n*m)
				l--;
		 } 
		 else if(ch==5)
		 {
		 	printf("加载中...\n\n");
		 	system("cls");
		 	printf("\".\"-->此格子未被点击过\n");
		 	printf("\"*\"-->雷\n");
		 	printf("\" \"-->空\n");
		 	printf("\"&\"-->被标记为雷\n");
		 	printf("\"?\"-->被标记为不知道\n");
		 	Sleep(3000);
		 } 
		 else
		 {
		 	printf("\n输入有误\n请重新输入！");
		 	Sleep(500);
		 	system("cls");
		 }
	}
	printf("加载中...\n\n");
	sl=l;
	system("cls");
	printf(" %d X %d , %d 颗雷\n",m,n,l);
	for(int i=1;i<=1;i++)
	{
		int x,y;
		x=rand()%n;
		if(x==0)
			x=n;
		y=rand()%m;
		if(y==0)
			y=m;
		if(a[x][y]=='*')
			i--;
		a[x][y]='*';
	}
	for(int i=1;i<=n;i++)
	{
		for(int j=1;j<=m;j++)
			b[i][j]=num(i,j);
	}
	while(1)
	{
		printf("剩余&d颗雷\n\n",s1);
		printf("	");
		for(int i=1;i<=m;i++)
			printf("%d ",i/10);
		printf("\n	  ");
		for(int i=1;i<=m;i++)
			printf("%d ",i%10);
		printf("\n	  『");
		for(int i=1;i<=m-1;i++)
			printf("--");
		printf("\n");
		for(int i=i;i<=n;i++)
		{
			printf("%02d|",i);
			for(int j=1;j<=m;j++)
			{
				if(fiag==1)
				{
					printf("%c|",a[i][j]);
					continue;
				}
				if(c[i][j]=='.'||c[i][j]=='?'||c[i][j]=='&')
					printf("%c|",c[i][j]);
				else if(b[i][j]!=0)
					printf("%d|",b[i][j]);
				else
					printf("%c|",a[i][j]);
			}
			printf("\n	|");
			for(int i=1;i<=m;i++)
				printf("--")
			printf("\n");
		}
		if(flag==1)
		{
			printf("\n\n窗口在五秒后自动关闭\r");
			for(int i=5;i>=0;i--)
			{
				Sleep(100);
				return 0;
			}
			printf("\n\n");
			int x=100,y=100;
			while(x>n||x<1)
			{
				printf("请输出进行操作的行：");
				scanf("%d",&x);
				if(x>n||x<1)
					printf("请重新输入！\n");	
			}
			while(y>m||y<1)
			{
					printf("请输出进行操作的列：");
				scanf("%d",&x);
				if(y>m||y<1)
					printf("请重新输入！\n");
			}
			ch=0;
			while(ch!=1&&ch!=2&&ch!=3)
			{
				printf("请选择进行的操作：\n1、探查\n2、排雷\n3、标记为不确定\n输入操作：")；
				scanf("%d,&ch");
				if(ch!=1&&ch!=2&&ch!=3)
					printf("请重新输入！\n");
			}
			if(ch==1)
			{
				if(c[x][y]=='&')
					s1++;
				c[x][y]==' ';
				system("cls");
				if(a[x][y]=='*')
				{
					printf("游戏结束\n恭喜您踩雷了！\n\n");
					flag=1;
					continue;
				}
				else
					12++;
				if(n*m-12==1)
				{
					printf("游戏结束\n恭喜您排完了所有的雷！\n\n");
					s1=0;
					flag=1;
					continue;
				}
				if(b[x][y]==0)
				{
					kg(x,y);
				}
			}
			else if(ch==2)
			{
				c[x][y]='&';
				system("cls");
				sl--;
				if(a[x][y]=='*')
					l1++;
				if(l1==l)
				{
					printf("游戏结束\n恭喜您排完了所有的雷！\n\n");
					s1=0;
					flag=1;
					continue;
				}
			}
			else if(ch==3)
			{
				if(c[x][y]=='&')
					s1++;
				c[x][y]='?';
				system("cls");
			}
		}
		return 0
	}
}
