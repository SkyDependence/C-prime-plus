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
