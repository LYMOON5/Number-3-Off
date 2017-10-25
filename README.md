#include<stdio.h>
#include<string.h>
#include<stdlib.h>

/*有n个人围成一圈，顺序排号。从第一个人开始报数（从1到3报数），
	报到3的退出圈子，问最后留下来的是原来第几号的那位*/
  
//n个人围成一圈
int cricle(int n)
{   //arr是相当拿数组模拟N个玩家 编号为1-n
	int *arr = (int*)malloc(sizeof(int)*n);
	//数组下标进行遍历
	int index = -1;
	//初始化数组
	for (int i = 1; i < n + 1; ++i)
	{
		arr[i-1] = i;
	}
	//每一个循环剔除一个玩家
	for (int i = 0; i < n - 1; ++i)
	{
		//每3次循环就索引到了要被剔除的玩家
		for (int j = 0; j < 3; ++j)
		{		
			//index先加加  相当于从arr[0];开始找起
			index++;
			//每次index++就要判断是不是到最大数下标  是置为0，进行下一趟循环
			if (index == n)
			{
				index = 0;
			}
			//如果这个数据已经被剔除（置为0）index++,直到找到不为0的数
			while (arr[index] == 0)
			{
				index++;
				if (index == n)
				{
					index = 0;
				}
			}	
			
			if (arr[index] != 0)
			{
				continue;
			}
		}
		//置为0  剔除玩家
		arr[index] = 0;
	}
  
	int rt;
	for (int i = 0; i < n; ++i)
	{
		if (arr[i] != 0)
		{
			 rt = arr[i];
		}
	}
	free(arr);
	return rt;
}

int main()
{
	int n = 5;
	int rt = cricle(n);
  
	return 0;
}
