//# transport_day_of_year
//page182exercise7
#include<stdio.h>

void split_date(int day_of_year, int year, int *month, int *day);

int main(void)
{
	int day_of_year, year,month, day;
	scanf("%d %d", &day_of_year, &year);
	split_date(day_of_year, year, &month, &day);
	printf("\n%d %d", month, day);
	return 0;
}

void split_date(int day_of_year, int year, int *month, int *day)
{
	int lp[2][12] = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31,
		31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 },lpt=0;
	if (year % 100==0)
	{
		if (year / 100 % 4==0)
			lpt = 1;
	}
	else
	{
		if (year % 4==0)
			lpt = 1;
	}

	for (int i = 0; i < 12; i++)
	{
		if (day_of_year > lp[lpt][i])
			day_of_year -= lp[lpt][i];
		else
		{
			*day = day_of_year;
			*month = i + 1;
			return;
		}
	}
}
