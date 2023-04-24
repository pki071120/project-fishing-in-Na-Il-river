
#include <stdio.h>
#include <windows.h>
#include <time.h>
#include <conio.h>
int chi();
int Nacci();
int Sijang();
int legend_fish = 0;
int rare_fish = 0;
int common_fish = 0;

int main()
{
	system("mode con cols=70 lines=25");
	printf("\t\t나일강 낚시터에 오신걸 환영합니다!\n");

	chi();
}

int chi()//메뉴 선택하기
{
	int choice;
	printf("\n원하시는 메뉴를 선택해주세요.\n--------------------------------------------\n1.낚시하기\n2.수산시장가기\n3.그만하기\n>>");	
	scanf("%d", &choice);
	printf("\n");
	while (TRUE)
	{
		if (choice == 1)
			return Naccichoice();
		else if (choice == 2)
			return Sijang();
		else if (choice == 3)
		{
			printf("종료하겠습니다");
			return 0;
		}

		else
		{
			printf("다시 선택해 주십시요 : ");
			scanf("%d", &choice);
		}
	}
}

int Naccichoice()//낚시메뉴 선택창
{
	int choice;
	printf("하고싶은 행동을 선택해 주세요\n1. 낚시하기, 2. 가방보기, 3. 그만하기\n>>");
	reset:
	scanf("%d", &choice);
	
	if (choice == 1)
		Nacci();
	else if (choice == 2)
		printf("아직 구현되지 않았습니다\n");
	else if (choice == 3)
		chi();
	else
	{
		printf("다시 선택해 주십시요 : ");
		goto reset;
	}
}

int Nacci()//낚시
{
	
	char c;
	int key;
	int delay, per;
	reset:
	srand((unsigned)time(NULL));
	printf("낚시대가 흔들리기를 기다리는중...\n");
	delay = rand()%1000000000;
	per = rand() % 101;
	Sleep(delay);
	printf("낚시대가 흔들린다!!(↑를 누르세요)\n");
	while (TRUE) 
	{
		key = getch();
		if (key == 72)
		{
			if (per >= 91)
			{
				printf("전설의 물고기를 낚았다!!\n");
				legend_fish++;
			}
			else if (per < 91 && per >= 61)
			{
				printf("희귀한 물고기를 낚았다!\n");
				rare_fish++;
			}
			else
			{
				printf("물고기를 낚았다!\n");
				common_fish++;
			}
			printf("계속 하시겠습니까? Y/N\n");
			rs:
			scanf("%c", &c);
			if (c == 'Y')
				goto reset;
			else if (c == 'N')
				Naccichoice();
			else
			{
				printf("다시 선택해주세요");
				goto rs;
			}
		}
		else 
		{
			printf("놓쳐버렸습니다.\n");
			printf("종료하시겠습니까?(Y/N) : ");
			scanf(" %c", &c);
			if (c == 'Y')
				Naccichoice();
			else
				goto reset;
		}
		
	}
	



}

int Sijang()//시장가기
{
	printf("아직 구현되지 않았습니다\n");
	chi();
}


