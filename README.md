# C-prime-plus
a probably answer for the program
# 第九章
1. code:
```c
#include <stdio.h>
double min(double, double);
int main(void) {
	printf("%lf", min(8.23, 4.56));
}
double min(double a, double b) {
	if (a > b)
		return b;
	else
		return a;
}
```
2. code:
```c
#include <stdio.h>
void chline(char, int, int);
int main(void) {
	char c;
	int i, j;
	printf("Please enter which character you like:");
	scanf_s("%c",&c);
	printf("Please enter i*j as you like:");
	scanf_s("%d*%d", &i, &j);
	chline(c, j, i);
}
void chline(char ch, int i, int j) {
	for (int a = 0; a < j; a++) {
		for (int b = 0; b < i; b++)
			printf("%c", ch);
		printf("\n");
	}
}
```
3. code:
```c
#include <stdio.h>
void print(char, int, int);
int main(void) {
	char c;
	int i, j;
	printf("Please enter which character you like:");
	scanf_s("%c", &c);
	printf("Please enter i*j as you like:");
	scanf_s("%d*%d", &i, &j);
	print(c, j, i);
}
void print(char ch, int i, int j) {
	for (int a = 0; a < j; a++) {
		for (int b = 0; b < i; b++)
			printf("%c", ch);
		printf("\n");
	}
}
```
4. code:
```c
#include <stdio.h>
double average(double, double);
int main(void) {
	double a, b;
	scanf_s("%lf%lf", &a, &b);
	printf("%lf",average(a, b));
}
double average(double a, double b) {
	return 1.0 / ((1.0 / a + 1.0 / b) / 2.0);
}
```
5. code:
```c
#include <stdio.h>
void larger_of(double*, double*);
int main(void) {
	double a, b;
	scanf_s("%lf%lf", &a, &b);
	larger_of(&a,&b);
	printf("%lf %lf", a, b);
}
void larger_of(double* a, double* b) {
	if (*a > *b)
		*b = *a;
	else
		*a = *b;
}
```
6. code:
```c
#include <stdio.h>
void sort(double*, double*, double*);
int main(void) {
	double a, b, c;
	scanf_s("%lf%lf%lf", &a, &b, &c);
	sort(&a, &b, &c);
	printf("%lf,%lf,%lf", a, b, c);
}
void sort(double* a, double* b, double* c) {
	double temp;
	if (*a < *b) {
		if (*a < *c) {
			if (*b < *c);//a<b<c
			else {//a<c<b
				temp = *c;
				*c = *b;
				*b = temp;
			}
		}
		else {//c<b<a
			temp = *c;
			*c = *a;
			*a = temp;
		}
	}
	else if (*b < *c) {
		if (*a < *c) {//b<a<c
			temp = *a;
			*a = *b;
			*b = temp;
		}
		else {//b<c<a
			double temp1 = *b;
			temp = *a;
			*b = *c;
			*a = temp1;
			*c = temp;
		}
	}
	else {//c<a<b
		double temp1 = *c;
		temp = *a;
		*c = *b;
		*a = temp;
		*b = temp;
	}
}
```
7. code:
```c
#include <stdio.h>
#include <ctype.h>

// 判断字符是否为字母，如果是则返回该字母在字母表中的位置，否则返回-1
int alpha_position(char ch) {
    if (isalpha(ch)) {
        // 将大写字母都转换为小写字母
        ch = tolower(ch);
        return ch - 'a' + 1;
    }
    return -1;
}

int main() {
    char ch;
    int position;

    // 读取标准输入中的字符，直到遇到文件结尾
    while (scanf("%c", &ch) != EOF) {
        if (isalpha(ch)) {
            position = alpha_position(ch);
            printf("%c is a letter, position in alphabet: %d\n", ch, position);
        } else {
            printf("%c is not a letter\n", ch);
        }
    }
    return 0;
}

```
8. code：
```c
void power() {
	double n;
	int p;
	while (scanf_s("%lf%d", &n, &p) == 2) {
		if (n == 0) {
				if (p == 0)
					printf("0的0次幂未定义！因此处理为：");
				else {
					printf("%d\n",0);
					continue;
				}
			}
		double pow = 1;
		for (int i = 1; i <= p; i++)
			pow *= n;
		printf("%lf\n",pow);
	}
	printf("Done\n");
}
```
9. code:
```c
void power1() {
	double n;
	int p;
	if (scanf_s("%lf%d", &n, &p) == 2) {
		if (n == 0) {
			if (p == 0)
				printf("0的0次幂未定义！因此处理为：1");
			else {
				printf("%d\n", 0);
				power1();
			}
		}
		else {
			double pow = 1;
			for (int i = 1; i <= p; i++)
				pow *= n;
			printf("%lf\n", pow);
			power1();
		}
	}
	printf("Done\n");
}
```
10. code:
```c
void to_base_n(int a, int b) {
	while (b < 2 || b>10) {  // 检查进制是否在2~10之间，如果不是则要求重新输入
		printf("Your number is invaild!\n");
		printf("Please enter again:");
		while (getchar() != '\n')continue;  // 清除输入缓存
		scanf_s("%d%d", &a, &b);  // 获取新的输入
	}
	int c = a % b;  // 取余数
	int d = a / b;  // 取商
	if (d >= b)  // 如果商大于等于进制，则递归调用本函数
		to_base_n(d, b);
	else  // 如果商小于进制，则直接输出商
		printf("%d", d);
	printf("%d", c);  // 输出余数
}

```
11. code:
```c
// 这里是计算斐波那契数列的函数，参数i表示要计算的数列项数
int Fibonacci(int i) {
    int sum = 2, f1 = 1, f2;  // 定义三个变量，分别表示当前项的值，上一项的值，和上上一项的值
    if (i == 0)  // 如果要计算的项数为0，直接返回0
        return 0;
    else if (i <= 2)  // 如果要计算的项数小于等于2，直接返回1
        return 1;
    else {  // 如果要计算的项数大于2
        for (int j = 3; j < i; j++) {  // 从第三项开始循环计算每一项的值
            f2 = sum;  // 保存上上一项的值
            sum += f1;  // 计算当前项的值
            f1 = f2;  // 将上一项的值更新为上上一项的值
        }
    }
    return sum;  // 返回计算出的数列值
}

```
