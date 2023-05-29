# 物联网20级 希冀平台题目
## 一、熟悉编程环境
### 编程题
#### 实验01-1：熟悉编程环境，实现基本输出设计
在屏幕上输出短句：

```
Programming in C is fun!
```

```c
#include<stdio.h>
int main(){
    printf("Programming in C is fun!");
}
```



#### 实验01-2：熟悉编程环境，实现基本输出设计
在屏幕上输出短句：

```
What is a computer?
```

```c
#include<stdio.h>
int main(){
    printf("What is a computer?");
}
```

#### 实验01-3：熟悉编程环境，实现基本输出设计
在屏幕上输出一个倒三角形，如下列所示：

```c
* * * *
 * * *
  * *
   *
```

```c
#include<stdio.h>
int main(){
    printf("* * * *\n\
 * * *\n\
  * *\n\
   *");
}
```



## 二、格式化输出

### 编程题



#### 实验01-4：简单程序设计，格式化输入输出
【问题描述】计算摄氏温度：输入华氏温度，输出对应的摄氏温度。计算公式如下：  $c=5×(f-32)÷9$​其中，$c$​表示摄氏温度，$f$​表示华氏温度，均使用浮点数存储数据。
【输入形式】输入一个温度值。
【输出形式】输出的**数值结果前带有字符串**“$Celsius=$​”，输出**保留二位小数。**
【样例输入】

```
150
```

【样例输出】

```
Celsius=65.56
```

```c
#include<stdio.h>
int main(){
	double f;
	double c;
	scanf("%lf", &f);
	c = 5.00 * (f - 32) / 9;
	printf("Celsius=%.2lf", c);
}
```



#### 实验01-5：简单程序设计，格式化输入输出
【问题描述】求给定序列$(1+1/2+1/3+……)$前$n$项的和：输入一个正整数$n$​，计算序列$1+1/2+1/3+……$的前$n$项之和；
【输入形式】输入一个整数值，输出一个单精度浮点数。
【输出形式】输出n的值，前面包含字符串"$n=$"；输出逗号"$,$"；输出求和后的结果值，前面包含字符串"$sum=$"，保留$7$位小数
【样例输入】

```
5
```

【样例输出】

```
n=5,sum=2.2833335
```

【补充说明】若结果为总是为1，请仔细思考有关数据类型运算规则的问题。同时思考，若使用双精度浮点输出，结果应该是多少？

```c
#include<stdio.h>
int main(){
	double sum = 1;
	int n;
	scanf("%d", &n);
	printf("n=%d,", n);
	for (int i = 1;i < n;i++){
		sum = sum + 1 / (i + 1);
	}
	printf("sum=%.7f", sum);
}
```



#### 实验01-6：简单程序设计，格式化输入输出
【问题描述】阶梯电价：某电力公司执行“阶梯电价”，居民用电分为两个阶梯：月用电量$50$千瓦时(含$50$千瓦时)以内的，电价为$0.53$元/千瓦时，超过$50$千瓦时的，超出部分的用电量电价上调$0.05$元/每千瓦时。编写程序，输入用户的月用电量(千瓦时)，计算并输出该用户应支付的电费(元)。
【输入形式】用电量(整数数据)
【输出形式】包含用电量及电费数据(浮点型数据，保留两位小数)，可参考样例
【样例输入】

```
40
```

【样例输出】

```
kWh=40,pay=21.20
```

```c
#include<stdio.h>
int main(){
	int a;
	double b;
	scanf("%d", &a);
	if (a <= 50){
		b = a * 0.53;
	}
	else{
		b = 50 * 0.53 + (a - 50) * 0.58;
	}
	printf("kWh=%d,pay=%.2f",a, b);
}
```



#### 实验01-7：大小写字母转换

【问题描述】输入一个字母字符，如果是大写字母，将其转换成相应的小写字母，如果是小写字母，将其转换成及相应的大写字母
【样例输入】

```
a
```

【样例输出】

```
A
```

【样例说明】输入$A$​ 输出$a$​

```c
#include<stdio.h>
#include<ctype.h>
int main(){
	char ch=getchar();
	if (isupper(ch)){
		putchar(tolower(ch));
	}else{
		putchar(toupper(ch));
	}
}
```



## 三、循环
### 编程题
#### 实验03-1：循环：最大公约数和最小公倍数
【问题描述】输入两个数$m$和$n$，输出他们的最大公约数和最小公倍数
【输入形式】下划线为输入内容，"$Inupt m,n:$"为提示信息，需跟换行符
 Input m,n:
 3 7
【输出形式】分别输出最大公约数和最小公倍数，以空格分隔
【样例输入】
Input m,n:
3 7
【样例输出】

```
1 21
```
```c
#include<stdio.h>
int main(){
    int m,n;
    scandf("%d %d",&m,&n);
    printf("%d %d",GCD(m,n),LCM(m,n));
}
int GCD(int a, int b) {
	if(b) while((a %= b) && (b %= a));
	return a + b;
}
int LCM(int a, int b) {
	return a * b / GCD(a, b);
}
```



#### 实验03-2：循环：字符提取

【问题描述】输入一组各类字符，以#号字符作为结尾，输出这组字符中所有的数字。
【输入形式】各类字符一组，以#号字符结束
【输出形式】字符中的数字，连续输出，中间没有间隔
【样例输入】

```
abc123edf4!2#
```

【样例输出】

```
12342
```

```c
#include<stdio.h>
int main(){
	char ch;
	ch = getchar();
	while (ch != '#'){
		if (ch >= '0' && ch <= '9')
			putchar(ch);
		ch = getchar();
	}
}
```



#### 实验03-3：循环：求一组数据中的最小值
【问题描述】输入一个正整数n，再输入n个整数，输出其中最小的值。
【输入形式】先输入一个整数n，再根据n，输入n个数
【输出形式】输出最小值，形式：$min=?$​​​
【样例输入】

```
5
10 22 4 67 2
```

【样例输出】

```
min=2
```

```c
int main()
{
	int n;
	int min,tmp;
	scanf("%d", &n);
	scanf("%d", &min);
	for (int i = 1;i < n;i++){
		if (tmp<=min){
			min = tmp;
		}
	}
	printf("min=%d", min);
}
```



#### 实验03-4：循环：提取整数的各位数字并求和
【问题描述】输入一个整数，求该整数的位数以及各位数字之和。
【输入形式】一个整数
【输出形式】两个整数值，分别是输入整数的位数值及其各位数字之和的值，两个数之间用空格分隔。
【样例输入】

```
1237
```

【样例输出】

```
4 13
```

```c
#include<stdio.h>
#include<string.h>
int main(){
	char buf[10];
	int sum=0;
	scanf("%s", buf);
	printf("%d ",strlen(buf));
	for(int i = 0; i <strlen(buf); i++){
		sum+=(int)(buf[i]-'0');
	}
	printf("%d",sum);
}
```



#### 实验03-5：循环：求出三位数给定区间内的水仙花数
【问题描述】输入两个三位数$m$​和$n(m<n)$​​，求出该区间内所有的水仙花数。
【输入形式】由小到大的两个三位整数
【输出形式】提示信息"$Narc No:$​​"及$0$​​或多个水仙花数，用空格分隔
【样例输入】

```
100  400
```

【样例输出】

```
Narc No:153 370 371
```

```c
#include<stdio.h>
int main(){
	int m,n,a,b,c,i;
		scanf("%d %d",&m,&n);
		printf("Narc No:");
	for (i=m;i<=n;i++){
			a=i/100;
			b=(i%100)/10;
			c=i%10;
		if (i==a*a*a+b*b*b+c*c*c)
			printf("%d ",i);
	}
}
```



#### 实验03-6：循环：输出三角形字符阵列图形
【问题描述】输入一个正整数$n(n<7)$​​​；输出$n$​​​行由大写字符$A$​​​开始的，构成三角形字符阵列图形，具体参考样例。
【输入形式】一个整数$n$​​​​
【输出形式】上三角字符阵列，其字符按由行到列的方式，依次按字母表顺序输出，字母之间有一个空格
【样例输入】

```
4
```

【样例输出】

```
A  B  C  D
E  F  G
H  I
J
```

```c
#include<stdio.h>
int main(){
	int n,i,j,m;
	char ch='A';
		scanf("%d",&n);
	m=n;
	for (j=0;j<m;j++){
		for (i=0;i<n;i++){
			printf("%-2c",ch++);	
		}
		printf("\n");
		n--;	
	}	
}
```



## 四、函数
### 程序片段编程题


#### 实验04-1：求一组数中奇数的和

【问题描述】输入一批正整数，以零或复数为结束标记，求其中所有奇数的和。要求定义和调用函数$even(n)$​判断整数的奇偶性，当$n$​为偶数时返回$1$，否则返回零。
根据程序中的提示，在对应位置编写相关函数及内容。

```c
#include<stdio.h>
//在此处编写函数代码
int even(int n){
    
}
int main(){
	int sum=0,x;
	scanf("%d",&x);
	while(x>0){
		if(even(x)==0)
			sum=sum+x;
		scanf("%d",&x);
	}
	printf("sum=%d\n",sum);
	return 0;
}
```

```c
int even(int n){
	if(n%2==0)
		return 1;
	else
		return 0;
}
```



#### 实验04-2：使用函数计算两点间的距离

【问题描述】给定平面上任意两点坐标$(x1,y1)$​和$(x2,y2)$​，求这两点之间的距离(保留两位小数)。要求定义和调用函数$dist(x1,y1,x2,y2)$计算两点间的距离。
根据程序中的提示，在对应位置编写相关函数及内容。

```c
#include<stdio.h>
#include<math.h>
//在此处编写dist函数
double dist(float x1,float y1,float x2,float y2){

}
int main(){
	float xs,ys,xe,ye,d;
	scanf("%f%f",&xs,&ys);
	scanf("%f%f",&xe,&ye);
	d=dist(xs,ys,xe,ye);
	printf("Distance=%.2f",d);
	return 0;
}
```

```c
double dist(float x1,float y1,float x2,float y2){
	double Distance=sqrt((x1-x2)*(x1-x2)+(y1-y2)*(y1-y2));
return Distance;
}
```



#### 实验04-3：使用函数计算素数并求和

【问题描述】输入两个正整数$m$和$n(m<=1,n<=500)$，统计并输出$m$和$n$之间的素数个数以及这些素数的和。注意：$1$​不是素数，要求定义并调用函数$prime(m)$​判断$m$​是否为素数，当$m$为素数是返回$1$​，否则返回$0$。根据程序中的提示，在对应位置编写相关函数及内容。
```c
#include<stdio.h>
//在此处添加函数声明

int main(){
	int m,n,ct=0,sum=0,i;
	scanf("%d%d",&m,&n);
	if(m<2) m=2;
	for(i=m;i<=n;i++)
		if(prime(i)){
			ct++;
			sum=sum+i;
		}
	printf("count=%d,sum=%d\n",ct,sum);
	return 0;
}
int prime(int m){
//在此处编写函数
}
```

```c
int prime(int m){
	int i=2;
	for(i;i<m;i++){
	    if(m%i==0)
	    break;            
	}
    	if(i==m)
    	    return 1;
    	else
    	    return 0;
}
```



#### 实验04-4：使用函数统计指定数字个数

【问题描述】输入一个整数$m$，再输入一个数字$n$，统计该整数中一共包含了几个数字$n$。输出统计结果。要求定义并调用函数$countdigit(number,digit)$​，它的功能是统计整数$number$​中数字$digit$的个数。根据程序中的提示，在对应位置编写相关函数及内容。
```c
#include<stdio.h>
//根据题意，在此处编写函数代码
int countdigit(int number,int digit){
	
}
int main(){
	int n,d,y;
	scanf("%d%d",&n,&d);
	y=countdigit(n,d);
	printf("Number of digit %d:%d",d,y);
	return 0;
}
```

```c
int countdigit(int number,int digit){
	int sum=0;
	while(number!=0){
		if(number%10==digit)
			sum++;
		number=number/10;	
	}
	return sum;	
}
```



#### 实验04-5：使用函数求余弦函数的近似值

【问题描述】输入精度e，用公式就$cos(x)$的近似值，精确到最后一项的绝对值小于$e$。
求$cos(x)$的公式：$cos(x)=x^0/0! -x^2/2!+x^/4!-x^6/6!+……$​​
要求定义和调用函数$funcos(e,x)$求余弦函数的值。

```c
#include<stdio.h>
#include<math.h>
//在此处编写要求的函数
double funcos(double e,double x){
	
}
int main(){
	double e,x,rz;
	scanf("%lf%lf",&e,&x);
	rz=funcos(e,x);
	printf("sum=%lf",rz);
	return 0;
}
```

```c
double funcos(double e,double x){
	double cosx=0,i=0,k=0,a=1,j=1;
	while(fabs(a)>=e) {
		double b=1;
		for (j=1;j<=i;j++)
			b=b*j;
		a=pow(x,i)*pow(-1,k++)/b;
		cosx=cosx+a;
		i=i+2;
		
	}
	return cosx;
}
```



### 编程题

#### 实验04-6：统计字符串中各类字符个数

【问题描述】输入一行字符,统计其中英文字母､空格､数字和其他字符的个数。
【输入形式】输入一行字符。
【输出形式】输出各类字符串的个数。
【样例输入1】

```
Programming is fun!
```

【样例输出】

```
letter=16,blank=2,digit=0,other=1
```

【样例输入2】

```
13 is a luck digit
```

【样例输出】

```
letter=12,blank=4,digit=2,other=0
```

【样例说明】输入的数据之间以一个空格相隔。英文字母区分大小写。必须严格按样例输入输出。

```c
#include<stdio.h>
int main(){
	char ch;
	int letter=0,blank=0,digit=0,other=0;
	while((ch=getchar())&&ch!='\n'){
		if ((ch>='a'&&ch<='z')||(ch>='A'&&ch<='Z'))
			letter++;
		else if	(ch>='0'&&ch<='9')
			digit++;
		else if (ch==' ')
			blank++;
		else
			other++;
	}
	printf("letter=%d,blank=%d,digit=%d,other=%d",letter,blank,digit,other);
}
```



#### 实验04-7：编程题，输出m ~n 之间所有的Fibonacci 数
【问题描述】
输入$2$​​​个正整数m和$n(m<1，n<=10 000)$​​​​，输出$m-n$​​​ 之间所有的$Fibonacci$​​数｡$Fibonacci$​​数列(第一项起):$1,1,2,3,5,8,13,21,$​​&hellip;｡要求定义并调用函数$fib(n)$​​，它的功能是返回第$n$​项$Fibonacci$​ 数｡例如，$fib(7)$​的返回值是13｡
【输入形式】从键盘输入$2$​个整数$m$​和$n$​​。
【输出形式】输出$m-n$​之间所有的$Fibonacci$ 数。
【样例输入1】

```
Input m: 20
Input n: 100
```

【样例输出1】

```
21 34 55 89
```

【样例输入2】

```
Input m: 50
Input n: 300
```

【样例输出2】

```
55 89 144 233
```

【样例说明】
输入提示符后要加一个空格。例如$Input integers:$​，其中:后要加一个且只能一个空格。输出数据之间有且仅有一个空格。英文字母区分大小写。必须严格按样例输入输出。

```c
#include<stdio.h>
int fib(int n);
int main()
{
	int m,n;
	printf("Input m: ");
	scanf("%d",&m);
	printf("Input n: ");
	scanf("%d",&n);
	int i;
    for(i=1;i<100;i++){
        if(fib(i)>=m&&fib(i)<=n)
            printf("%d ",fib(i));
    }
    return 0;
}
int fib(int n){
	int i,x1=1,x2=1,x;
	if(n == 1 || n == 2){
		return 1;
	}else{
	  	for(i = 3; i <= n; i++){
			x = x1+x2;
			x1 = x2;
			x2 = x;
	  	}
		return x;
	}
}
```



#### 实验04-8：求m~n 之间的所有完数
【问题描述】输入$2$​​ 个正整数$m$​​ 和$n(m>=1,n>=1 000)$​​,输出$m -n$​​ 之间的所有完数,完数就是因子和与它本身相等的数｡要求定义并调用函数$factorsum(number)$​,它的功能是返回$number$ 的因子和｡
例如,$factorsum(12)$​的返回值是$16(1 +2 +3 +4 +6)$​​｡
【输入输出样例1】 (加粗部分为键盘输入，其余部分为程序输出)

```
Input m: <u>1</u>
Input n: <u>100</u>
1    6   28        (输出格式控制符为：%5d)  
```

【输入输出样例2】 (下划线部分为键盘输入，其余部分为程序输出)

```
Input m: <u>1</u>
Input n: <u>500</u>
1    6   28  496   (输出格式控制符为：%5d)
```

【样例说明】输入提示符后要加一个空格。例如"$Input m:$​ "，其中":"后要加一个且只能一个空格。英文字母区分大小写。必须严格按样例输入输出。

```c
#include<stdio.h>
int factorsum(int a);
int main(){
	int m,n;
		printf("Input m: ");
		scanf("%d",&m);
		printf("Input n: ");
		scanf("%d",&n);
	for(;m<=n;m++){
		if(factorsum(m)!=0)
		printf("%5d",factorsum(m));
	}
}
int factorsum(int number){
	if(number == 1)
		return 1;
	int i,sum = 0;
	for(i = 1; i < number/2+1; i++){
		if(number % i == 0)
			sum+=i;
	} 
	if(sum == number)
		return sum;
	return 0;
}
```



#### 实验04-9：求两个正整数之间的水仙花数
【问题描述】输入$2$​​​ 个正整数$m$​​​ 和$n(1<m,n<1000)$​​​​​,输出$m-n$​​之间的所有水仙花数｡水仙花数是指各位数字的立方和等于其自身的数｡要求定义并调用函数$is(number)$​判断$number$​​的各位数字之立方和是否等于其自身｡
【输入形式】输入$2$​个正整数$m$​​ 和$n(1<m,n>1000)$​​
【输入输出样例1】 (下划线部分表示输入)

```
Input m: <u>100</u>
Input n: <u>400</u>
153
370
371
```

【样例说明】
输入提示符后要加一个空格。例如$Input m:$​ ，其中:后要加一个且只能一个空格。英文字母区分大小写。必须严格按样例输入输出。

```c
#include<stdio.h>
int is (int m,int n){
	int a,b,c,i;
	for (i=m;i<=n;i++){
			a=i/100;
			b=(i%100)/10;
			c=i%10;
		if (i==a*a*a+b*b*b+c*c*c)
			printf("%d\n",i);
	}
	return 0;
}
int main(){
	int m,n;
		printf("Input m: ");
		scanf("%d",&m);
		printf("Input n: ");
		scanf("%d",&n);
	is(m,n);
}
```



#### 实验04-10：验证歌德巴赫猜想
【问题描述】任何一个大于$6$的偶数均可表示为$2$个素数之和｡例如$6=3+3,8=3+5$​,...,$18=5+13$｡将$6-100$之间的偶数都表示成$2$个素数之和，打印时一行打印5组｡素数就是只能被1和自身整除的正整数，最小的素数是2｡要求定义并调用函数$prime(m)$判断$m$​是否为素数,当$m$​为素数时返回$1$​，否则返回$0$​​｡
【输入形式】无输入
【输出形式】按从小到大、每组五行。每组的格式为：%4d=%2d+%2d, 等号和加号两侧无空格。

```c
#include<stdio.h>
int prime(int m);
int main(){
	for(int m=6;m<=100;m+=2) {
		for(int i=3;i<=m/2;i++) {
			if(prime(i)==1&&prime(m-i)==1){
				printf("%4d=%2d+%2d",m,i,m-i);
				if ((m-4)%10==0)
					printf("\n");
				break;
			}
		}
	}
}
int prime(int m){
	if(m==1)
		return 0;
	int i=2;
	for(i;i<m;i++){
    	if(m%i==0)
    		break;
	}
    if(i==m)
        return 1;
    else
    	return 0;
}
```

#### 实验04-11：求$a +aa +aaa +aa…a$($n$ 个$a$) 之和

【问题描述】输入2个正整数a和n，求a+aa+aaa+aa...a(n个a)之和｡例如，输入2和3，输出246(2+22+222)｡
【输入形式】从键盘输入正整数a和正整数n。
[输入输出样例1]】(下划线部分表示输入)

> Input a, n:
>
> ```
> 8 5
> ```
>
> ```
> s=98760
> ```

【样例说明】输入提示符后要加一个空格。其中":"后要加一个且只能一个空格。输出语句的"="两边无空格。英文字母区分大小写。必须严格按样例输入输出。

```c
#include<stdio.h>
#include<math.h>
int fn(int a,int n){
	int i=0,j=0,sum_1=0,sum_2=0;
	for (j;j<n;j++){
		sum_2=sum_2+a*pow(10,j);
		sum_1=sum_1+sum_2;
	}
	return sum_1;
}
int main(){
	int a,n;
	printf("Input a, n: ");
	scanf("%d%d",&a,&n);
	printf("s=%d",fn(a,n));
}
```

## 五、数组
### 编程题

#### 实验06-1：在有序数组中插入数据并保持有序

【问题描述】已知一个整数数组大小为6，先输入6个有序数据。再输入一个正整数，将输入的整数放入到数组中，并使其依然保持有序(数组只存放6个元素，最大的数据会被舍弃)
【输入形式】

```
1 3 5 7 9 11
8
```

【输出形式】

```
1 3 5 7 8 9
```

```c
#include<stdio.h>
int getArray(int a[]){
	for(int i=0;i<6;i++)
		scanf("%d",&a[i]);
	return 0;
}
int putArray(int a[]){
	for(int i=0;i<6;i++)
		printf("%d ",a[i]);
	return 0;
}
int main()
{
	int t,i,j;
	int a[7];
	getArray(a);
	scanf("%d",&a[6]);
	if(a[6]>a[5]){
		t=a[6];
		a[5]=a[6];
		a[5]=t;
	}
	else{
		for(i=0;i<7;i++){
		for(j=0;j<7;j++){
			if(a[i]<a[j]){
				t=a[i];
				a[i]=a[j];
				a[j]=t;
			}
		}
	}
	}
	putArray(a);
}
```



#### 实验06-2：将数组中的数逆序存放

【问题描述】输入一个正整数n(1<n<10)，再输入n个整数，存入数组中，再将数组中的数，逆序存放并输出
【输入形式】先输入一个整数n，再输入n个整数，用空格间隔
【输出形式】输出n个整数，用空格间隔
【样例输入】

```
5
1 2 3 4 5
```

【样例输出】

```
5 4 3 2 1
```

```c
#include<stdio.h>
int getArray(int a[],int n){
	for(int i=0;i<n;i++) {
		scanf("%d",&a[i]);
	}
	return 0;
}
int putArray(int a[],int n){
	for(int i=n;i>0;i--) {
		printf("%d ",a[i-1]);
	}
	return 0;
}
int main(){
	int n,a[10];
		scanf("%d",&n);
	getArray(a,n);
	putArray(a,n);
}
```



#### 实验06-3：找出不是两个数组共有的元素

【问题描述】输入一个正整数n(1<n<10)，再输入n个整数数放入数组a中；然后输入一个正整数m(1<m<10)，再输入m个整数数放入数组b中，找出所有不属于这两个数组的共有元素并输出。
【输入形式】先输入一个正整数n后，输入n个整数，用空格分隔。再输入一个正整数m，再输入m个整数，用空格分隔。
【输出形式】一组整数，用空格分隔数据
【样例输入】

```
5
1 3 5 7 9
6
1 2 3 4 5 6
```

【样例输出】

```
7 9 2 4 6
```

```c
#include<stdio.h>
int getArray(int a[],int n){
	for(int i=0;i<n;i++)
		scanf("%d",&a[i]);
	return 0;
}
int main(){
	int a[10],b[10],n,m,c[10],num=0,i,j;
	scanf("%d",&n);getArray(a,n);
	scanf("%d",&m);getArray(b,m);
	for(i=0;i<n;i++){        
		for(j=0;j<m;j++){       
			if(a[i]==b[j])break;
		}
		if(j==m){            
			c[num++]=a[i];                   
		}
	}
	for(i=0;i<m;i++){        
		for(j=0;j<n;j++)            
			if(b[i]==a[j])break;    
		if(j==n){            
			c[num++]=b[i];            
		}    
	}
	for(i=0;i<num;i++){
		for(j=0;j<i;j++)            
			if(c[i]==c[j])break; 
		if(j==i)printf("%d ",c[i]);                
	}       
}
```



#### 实验06-4：对数组中的数据进行排序

【问题描述】输入10个数到数组中，对数组中的数按由小到大排序并输出
【输入形式】10个整数，用空格分隔
【输出形式】10个由小到大的整数，用空格分隔
【样例输入】

```
1 3 5 2 9 4 6 0 7 8
```

【样例输出】

```
0 1 2 3 4 5 6 7 8 9
```

```c
#include<stdio.h>
int getArray(int a[],int n){
	for(int i=0;i<n;i++)
		scanf("%d",&a[i]);
	return 0;
}
int putArray(int a[]){
	for(int i=0;i<10;i++)
		printf("%d ",a[i]);
	return 0;
}
	
int main(){
	int a[10],i,j,t,n=10;
	getArray(a,n);
	
	for(i=0;i<10;i++){
		for(j=0;j<10;j++){
			if(a[i]<a[j]){
				t=a[i];
				a[i]=a[j];
				a[j]=t;
			}
		}
	}
	putArray(a);
}
```



#### 实验06-5：寻找二维数组中的鞍点

【问题描述】输入一个4×4的矩阵中的所有元素，设其最多只有一个鞍点，寻找该鞍点，如果有，则输出其下标及对应的值，若没有，则输出"NO"。鞍点是指二维数组中的一个元素，在该行上最大，在该列上最小。
【输入形式】输入16个整数，存放在一个4×4的二维数组中
【输出形式】若有鞍点，则输出其下标(两个整数)和对应的值，若无鞍点，则输出"NO"。
【样例输入】

```
1 7 4 1
4 8 3 6
1 6 1 2
0 7 8 9
```

【样例输出】

```
[2][1]  6
```

```c
#include<stdio.h>
int getArray(int a[4][4]){
	for(int i=0;i<4;i++)
		for(int j=0;j<4;j++)
			scanf("%d",&a[i][j]);
	return 0;
}
int main(){
	int a[4][4],i,j,k,jmax,count=0;
	getArray(a);
	
	for(i=0;i<4;i++){
		int max=a[i][0]; 
		for(j=0;j<4;j++){			
			if(a[i][j]>=max){
				max=a[i][j];
				jmax=j;				
			}
		}
		int flag=1;
		for(k=0;k<4;k++){
			if(a[k][jmax]<max){
				flag=0;break;				
			}
		}
		if(flag){
			printf("[%d][%d] %d",i,jmax,max);
			count++;				
		}	
	}
	if(count==0) printf("None");
}
```



#### 实验06-6：输出螺旋方阵外边

【问题描述】螺旋方阵，是指对任意给定的n，将1到n×n的数字从左上角第一个格子开始，按顺时针螺旋方向顺序填入n×n的方阵里(向内螺旋)。输入一个正整数，输出螺旋方阵的外边内容(仅输出外边内容，有能力的同学可考虑输出整个螺旋方阵)。
【输入形式】一个正整数n(n小于等于6)
【输出形式】螺旋方阵外边。
【样例输入】

```
5
```

【样例输出】

```
1  2  3  4  5
16 0  0  0  6
15 0  0  0  7
14 0  0  0  8
13 12 11 10 9
```

【样例说明】输出每个整数占两个字符位，中间用空格隔开

```c
#include<stdio.h>
int main()
{
	static int map[100][100];
	int n=0,k=0;
	scanf("%d",&n);
//上面那行 
	for(int i=0;i<n;i++) {
		map[0][i-1]=k++;
	}
//右边那行 
	for(int i=0;i<n;i++) {
		map[i][n-1]=k++;
	}
//下面那行	 
	for(int i=n;i>1;i--) {
		map[n-1][i-2]=k++;
	}
//左边那行 
	for(int i=n;i>2;i--) {
		map[i-2][0]=k++;
	}
	for(int i=0;i<n;i++) {
		for(int j=0;j<n;j++) {
			printf("%2d ",map[i][j]);
		}
		printf("\n");
	}
}
```



#### 实验06-7：查找指定字符

【问题描述】输入一个字符，再输入一个以回车结束的字符串(少于80个字符)在字符串中查找该字符。
【输入形式】一个字符后，再输入一个字符串
【输出形式】一个整数，说明该字符在字符串中的位置，若无该字符，则显示"Not Found"
【样例输入】

```
m
programming
```

【样例输出】
7
【样例说明】查找并输出第一个字符的位置，位置从1开始计数。

```c
#include <stdio.h> 
int main()
{
    char s[81];
	char x=getchar();
	getchar();
	int i=0;
	while((s[i]=getchar())!='\n') 
        i++;
    s[i]='\0';
	for(int i=0;s[i]!='\0';i++) {
		if(x==s[i]){
			printf("%d",i+1);
			return 0;
		}
	}
	printf("Not Found");
}
```



#### 实验06-8：字符串转换成十进制整数

【问题描述】输入一个以'#'结束的字符串，滤去所有的非十六进制字符(不分大小写)，组成一个新的表示十六进制数的字符串，然后将其转化为十进制数后输出。如果过滤后字符串的首字符为'-'，代表的是负数。
【输入形式】一个字符串
【输出形式】一个十进制整数
【样例输入】

```
+P-xf4+-1!#
```

【样例输出】

```
-3905
```

【样例说明】输入的内容，按十六进制数要求将数值(0~9，A~E)和符号(在数值之前的'-')保留，得到-f41，转换为十进制后市-3905
【评分标准】

```c
#include <stdio.h> 
#include<stdlib.h>
int main()
{
	char s[100],m[100],sym;	
//输入字符串 
	int i=0;
	while((s[i]=getchar())!='#') 
        i++;
    s[i]='\0';
//提取符号			"+P-xf4+-1!#"--->"-"
 	for(int i=0;s[i]!='\0';i++) {
 		if(s[i]=='+'||s[i]=='-')
			sym=s[i];
		if((s[i]>='0'&&s[i]<='9')||(s[i]>='A'&&s[i]<='F')||(s[i]>='a'&&s[i]<='f'))
			break;
	}
//提取十六进制 
	int k=0;
	for(int i=0;s[i]!='\0';i++) {
		if((s[i]>='0'&&s[i]<='9')||(s[i]>='A'&&s[i]<='F')||(s[i]>='a'&&s[i]<='f'))
			m[k++]=s[i];
	}
	m[k]='\0';
/*输出十六进制
	for(i=0;m[i]!='\0';i++) {
	 	putchar(m[i]);
	}	
		printf("\n");
*/
//转换十进制		-3905
	long number=0;
	for(i=0;m[i]!='\0';i++){
		if(m[i]>='0'&&m[i]<='9')
			number=number*16+m[i]-'0';
		else if(m[i]>='a'&&m[i]<='f')
			number=number*16+m[i]-'a'+10;
		else
			number=number*16+m[i]-'A'+10;
	}
	if(sym=='+'||sym=='-')
	printf("%c",sym);
	printf("%ld",number);
}
```



#### 实验06-9：求一组整数的最大值及其下标

【问题描述】输入一个正整数n(1<n&le;10)，再输入n个整数,输出最大值及其下标(设最大值唯一,下标从0 开始)｡
【输入形式】从键盘输入一个正整数n和n个整数。
【输入输出样例1】(下划线部分表示输入)

```
Input n: 5
Input 5 integers: 1 2 5 4 0
max=5, index=2
```

【样例说明】
输入提示符后要加一个空格。例如Input n: ，其中:后要加一个且只能一个空格。
等号前后无空格，逗号后有一个空格。
英文字母区分大小写。必须严格按样例输入输出。

```c
#include<stdio.h>
int getArray(int a[],int n){
	printf("Input %d integers: ",n);
	for(int i=0;i<n;i++) {
		scanf("%d",&a[i]);
	}
return 0;
}
int main()
{
	int a[10],n,max=-100,index=0;
		printf("Input n: ");
		scanf("%d",&n);
	getArray(a,n);
	for(int i=0;i<n-1;i++) {
		if(max<a[i])
			max=a[i];
			index=i;
	}
	printf("max=%d, index=%d",max,index-1);
}
```



## 六、指针

### 程序片段编程题


#### 实验07-1：利用指针实现拆分实数

【问题描述】拆分实数的整数和小数部分：要求自定义一个函数void splitfloat(float x,int *intpart,flaot *fracpart)。其中x是要被拆分的实数，intpart和fracpart分别是将实数拆分出来的整数和小数部分。通过定义的主函数，编写对应的splitflaot函数内容。
【样例输入】

```
12.4567
```

【样例输出】

```
The intpart is 12
The fracpart is 0.456700
```


```c
#include<stdio.h>
#include<stdlib.h>
void splitFloat(float x,int *intpart,float *fracpart){

}

int main(){
	float x,fp;
	int ip;
	scanf("%f",&x);
	splitFloat(x,&ip,&fp);
	printf("The intpart is %d\n",ip);
	printf("The fracpart is %f\n",fp);
}
```

```c
void splitFloat(float x,int *intpart,float *fracpart){
	*intpart=abs(x);
	*fracpart=x-abs(x);
}
```



#### 实验07-2：使用函数进行选择法排序

【问题描述】定义函数void sort(int a[], int n)，用选择法对数组a中的元素升序排序。主函数中输入n(n<=10)再输入n个数放入数组，调用函数排序后输出数组内容。
【样例输入】

```
6
1 5 -9 2 4 -6
```

【样例输出】

```
-9 -6 1 2 4 5
```


```c
#include<stdio.h>
void sort(int a[], int n){

}

int main(){
	int a[10],n,i;
	scanf("%d",&n);
	for(i=0;i<n;i++)
		scanf("%d",&a[i]);
	sort(a,n);	
	for(int i=0;i<n;i++)
		printf("%d ",a[i]);
	
}
```

```c
void sort(int a[], int n){
	int t;
	for(int i=0;i<n;i++)
		for(int j=0;j<n;j++)
			if(a[i]<a[j]){
				t=a[i];
				a[i]=a[j];
				a[j]=t;
			}
}
```



#### 实验07-3：在数组中查找指定元素

【问题描述】输入一个正整数n，再输入n个整数存入数组中，再输入一个整数x，在数组中查找x，如果找到则输出相应的下标，否则输出“Not found”。要求定义并调用函数search(list,n,x)，其功能是在数组中查找元素x，若找到则返回相应下标，否则返回-1；
【样例输入】

```
3
1 2 -6
2
```

【样例输出】

```
1
```


```c
#include<stdio.h>
void printArray(int a[],int n){

}
void setArray(int a[],int n){

}
int search(int list[],int n,int x){

}

int main(){
	int a[10],n,r,x;
	scanf("%d",&n);
	setArray(a,n);
	scanf("%d",&x);
	r=search(a,n,x);
	if(r>=0)
		printf("%d\n",r);
	else
		printf("Not found\n");	
}
```

```c
void printArray(int a[],int n){
	for(int i=0;i<n;i++)
		printf("%2d ",a[i]);
	printf("\n");
}
void setArray(int a[],int n){
	for(int i=0;i<n;i++)
		scanf("%d",&a[i]);
}
int search(int list[],int n,int x){
	for(int i=0;i<n;i++) {
		if(x==list[i])
			return i;
	}
return -1;
}
```



#### 实验07-4：字符串逆序

【问题描述】设计一个函数void f(char *p)，对p指向的字符串进行逆序，要求函数不能定义任何数组、不能调用任何字符串处理函数。在主函数中输入字符串，调用f()，输出逆序后的字符串。
【样例输入】

```
abcd
```

【样例输出】

```
dcba
```


```c
#include<stdio.h>
void f(char *p){
}
int main(){
	char st[20];
	scanf("%s",st);
	f(st);
	printf("%s",st);	
}
```

```c
void f(char *p){
char ch;
int i,k=0;
	for(i=0;*(p+i)!='\0';i++)
		k++;
	for(i=0;i<k/2;i++){
    	ch=*(p+i);
    	*(p+i)=*(p+k-i-1);
    	*(p+k-i-1)=ch;
  	}
}
```



#### 实验07-6：使用函数实现字符串复制

【问题描述】输入一个字符串t和正整数m，将字符串t中从第m个字符开始的全部字符复制到字符串s中，再输出字符串s。要求使用字符指针定义并调用函数strmcpy(s，t，m)，其功能是将字符串t中的第m个字符开始的全部字符，复制到串s中。
【样例输入】

```
happy new year
7
```

【样例输出】

```
new year
```



```c
#include<stdio.h>
void strmcpy(char *st,char *tt,int m){
	
}

int main(){
 	char st[20],tt[20],ch;
 	int i=0,m;
 	scanf("%c",&ch);
	while(ch!='\n'){
		tt[i++]=ch;
		scanf("%c",&ch);
	}
	tt[i]='\0';
 	scanf("%d",&m);
 	strmcpy(st,tt,m);
 	printf("%s\n",st);
}
```

```c
void strmcpy(char *st,char *tt,int m){
	for(int i=0;*(tt+m+i-1)!='\0';i++) {
		*(st+i)=*(tt+m+i-1);						
	}
}
```



### 编程题



#### 实验07-5：寻找最长的字符串

【问题描述】输入5个字符串，输出其中最长的字符串。通过输入函数scanf("%s",sx)的形式输入字符串。
【输入形式】

```
li wang zhang jin xian
```

【输出形式】

```
zhang
```

```c
#include<stdio.h>
#include<string.h>
int main()
{
	char string[20],strr[20];
	char *sx=string;
	int max=0;
	for(int i=0;i<5;i++) {
		scanf("%s",sx);
		if(strlen(sx)>max){
			strcpy(strr,sx);
			max=strlen(sx);
		}
	}
	printf("%s",strr);
}
```



## 七、结构体

### 编程题


#### 实验08-1：时间换算

【问题描述】用结构体类型表示时间内容(时间以时分秒表示)输入一个时间数据，在输入一个秒数n(n<60)，以h : m : s的形式输出过了n秒后的时间。(超过24点以0点开始)
【输入形式】输入的时间必须是以"时:分:秒"格式输入
【输出形式】同样以格式"时:分:秒"输出
【样例输入】

```
11:59:40
30
```

【样例输出】

```
12:0:10
```

```c
#include<stdio.h>
struct Time {
    int Hour;
    int Minute;
    int Second;
}time_1,time_2;
int main()
{
    scanf("%d:%d:%d",&time_1.Hour,&time_1.Minute,&time_1.Second);
    int n;
        scanf("%d",&n);
            if(n>=60||n<0)return 0;
    if(time_1.Second+n>60){
        time_2.Second=time_1.Second+n-60;
        time_2.Minute=time_1.Minute+1;
    }
    else{
        time_2.Second=time_1.Second+n;
    }
    if(time_2.Minute==60){
        time_2.Minute=0;
        time_2.Hour=time_1.Hour+1;
    }
    else{
        time_2.Minute=time_1.Minute;
        time_2.Hour=time_1.Hour;
    }
    if(time_2.Hour==24){
        time_2.Hour=0;
    }
    printf("%d:%d:%d",time_2.Hour,time_2.Minute,time_2.Second);
}
```



#### 实验08-2：计算学生信息中成绩的平均值

【问题描述】建立一个学生的结构记录，包含学号、姓名和成绩，输入整数n(n<=10)，再输入n个学时的基本信息，计算并输出他们的平均成绩。
【样例输入】

```
3
1 zhang 70
2 wang 80
3 qian 90
```

【样例输出】

```
80.00
```

```c
#include<stdio.h>
struct student{
	int Student_ID;
	char name[20];
	double Grade;
};
int main()
{
	int n;
	double Average=0,Sum=0;
		scanf("%d",&n);
	struct student s[n];
	for(int i=0;i<n;i++) 
		scanf("%d%s%lf",&s[i].Student_ID,s[i].name,&s[i].Grade);
	for(int i=0;i<n;i++) {
		Sum+=s[i].Grade;
	}
	Average=Sum/n;
	printf("%.2lf",Average);
}
```



#### 实验08-3：从书籍结构体中查找定价最高的书籍

【问题描述】从键盘输入n(n<=10)，本书的名称和定价并存入结构体数组中，从中查找定价最高的和最低的数的名称及定价，并输出，价格输出保留2位小数。
【样例输入】

```
3
Programming_in_c 21.5
Programming_in_VB 18.5
Programming_in_Delphi 25.0
```

【样例输出】

```
18.50,Programming_in_VB
25.00,Programming_in_Delphi
```

```c
#include<stdio.h>
#include<string.h>
struct Book{
	char Book_Name[50];
	double Price;
};
int main()
{
	int n;
	double max=-100,min=200;
	char max_Name[50],min_Name[50];
	scanf("%d",&n);
	struct Book s[n];
	for(int i=0;i<n;i++) 
		scanf("%s %lf",s[i].Book_Name,&s[i].Price);
//查找定价最高的书
	for(int i=0;i<n;i++) {
		if(s[i].Price>max){
			max=s[i].Price;
			strcpy(max_Name,s[i].Book_Name);
		}
	}
//查找定价最低的书
	for(int i=0;i<n;i++) {		
		if(s[i].Price<min){
			min=s[i].Price;
			strcpy(min_Name,s[i].Book_Name);
		}
	}
//输出，价格输出保留2位小数
	printf("%.2lf,%s\n",min,min_Name);
	printf("%.2lf,%s\n",max,max_Name);
}
```



#### 实验08-4：有理数比较

【问题描述】编写函数CompareRational()，比较两个有理数的大学，该函数的参数为两个有理数(结构体类型，包含分子分母两个整数)，若第一个有理数小于第二个，返回一个负数；若相等，返回0；若第一个有理数大于第二个，则返回正数。以分数的形式输入两个有理数，输出比较结果。
【输入形式】两个有理数，分数形式，格式为："分子/分母"
【输出形式】输入的两个有理数，中间用比较运算符连接表示其大小关系。有理数格式同上。
【样例输入】

```
1/2 3/4
```

【样例输出】

```
1/2<3/4
```

```c
#include<stdio.h>
struct Number{
    int a;
    int b;
    double value;
}x1,x2;
int CompareRational(struct Number x1,struct Number x2){
    x1.value=1.000*x1.a/x1.b;
    x2.value=1.000*x2.a/x2.b;
    if(x1.value<x2.value)
        return -1;
    else if(x1.value==x2.value)
        return 0;
    else if(x1.value>x2.value)
        return 1;
    return 0;
}
int main()
{
    int temp=0;
    scanf("%d/%d%d/%d",&x1.a,&x1.b,&x2.a,&x2.b);
    temp=CompareRational(x1,x2);
    if(temp==-1)
        printf("%d/%d<%d/%d",x1.a,x1.b,x2.a,x2.b);
    else if(temp==0)
        printf("%d/%d=%d/%d",x1.a,x1.b,x2.a,x2.b);
    else if(temp==1)
        printf("%d/%d>%d/%d",x1.a,x1.b,x2.a,x2.b);
}
```



## 八、递归函数

### 程序片段编程题



#### 实验09-1：用递归求阶乘的和

【问题描述】输入一个整数n(0<n<=10)，求1!+2!+3!+……+n!。定义并调用函数fact(n)，计算n!，函数类型是double。
【输入形式】一个整数
【输出形式】一个浮点数，但不保留小数部分。
【样例输入】

```
3
```

【样例输出】

```
9
```



```c
#include<stdio.h>
double fact(int x){

}

int main(){
	int i,n;
	double sum=0;
	scanf("%d",&n);
	for(i=1;i<=n;i++)
		sum=sum+fact(i);
	printf("%.0lf",sum);	
}
```

```c
double fact(int x){
    double result;
    if(x==1||x==0)
        result=1;
    else
        result=x*fact(x-1);
    return result;
}
```



#### 实验09-3：十进制转二进制

【问题描述】输入一个正整数n，输出其转换为二进制后的形式。要求定义并调用函数dectobin(n)，其功能是输出n的二进制(在函数中输出)。
【输入形式】一个正整数
【输出形式】该正整数的二进制形式
【样例输入】

```
100
```

【样例输出】

```
1100100
```



```c
#include<stdio.h>
void dectobin(int n){

}
int main(){
	int x;
	scanf("%d",&x);
	dectobin(x);
}
```

```c
void dectobin(int n){
    if(n>1)
        dectobin(n/2);
    printf("%d",n%2);
}
```



#### 实验09-4：递归实现整数的顺序、逆序输出

【问题描述】输入一个正整数，编写两个递归函数，分别实现对其按位顺序、逆序输出。
【输入形式】一个正整数
【输出形式】先顺序输出该整数的每一位值，中间用空格分开；再逆序输出该整数的每一位值，中间用空格分开
【样例输入】

```
1024
```

【样例输出】

```
1 0 2 4
4 2 0 1
```



```c
#include<stdio.h>
void posi(int n){ 

}
void nega(int n){

}
int main(){
	int x;
	scanf("%d",&x);
	posi(x);
	printf("\n");
	nega(x);
}
```

```c
void posi(int n){
    if(n>9)
        posi(n/10);
    printf("%d ",n%10);

}
void nega(int n){
    if(n>0){
        printf("%d ",n%10);
    nega(n/10);
    }

}
```



### 编程题



#### 实验09-2：递归计算函数值Ack(m,n)的值

【问题描述】递归计算函数Ack(m,n)的值，输入两个整数m和n(m和n均大于0 )，输出函数Ack的值。Ack(m,n)的定义为：
当m=0时，Ack(m,n)=n+1；
当n=0且m>0时，Ack(m,n)=Ack(m-1,1)；
当n>0且m>0时，Ack(m,n)=Ack(m-1,Ack(m,n-1))；
【输入形式】两个整数m和n
【输出形式】函数的名称，具体参数和计算结果。
【样例输入】

```
2 3
```

【样例输出】

```
Ack(2,3)=9
```

```c
int Ack(int m,int n){
    if(m==0){
        return ((n)+1);
    }
    if(n==0&&m>0){
        return Ack(m-1,1);
    }
    if(n>0&&m>0){
        return Ack(m-1,Ack(m,n-1));
    }
    return 0;
}
#include<stdio.h>
int main()
{
    int m,n;
    scanf("%d%d",&m,&n);
    printf("Ack(%d,%d)=%d",m,n,Ack(m,n));
}
```



## 九、单链表
### 编程题



#### 实验10-1：单向链表的建立

【问题描述】输人若干个学生信息(包括学号、姓名和成绩)，输人学号为0时输人结束，建立一个单向链表，再输人一个成绩值，将成绩大于等于该值的学生信息输出。试编写相应程序。
【样例输入】

```
1 zhang 78
2 wang 80
3 Li 75
4 zhao 85
0
80
```

【样例输出】

```
2 wang 80
4 zhao 85
```

```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
struct stud_node
{
    int num;
    char name[20];
    int score;
    struct stud_node *next;
};
struct stud_node * Create_Stu_Doc();/* 新建链表 */
void Print_Stu_Doc(struct stud_node * head);/* 遍历 */
int main()
{
    int num,score;
    char name[20];
    int size=sizeof(struct stud_node);
    struct stud_node *head, *tail, *p;
    head=tail=NULL;
        scanf("%d%s%d",&num,name,&score);
    while(1)
    {
        p=(struct stud_node*)malloc(size);
            if(p==NULL)break;               /*小天才撸棒性*/
        p->num=num; 
        strcpy(p->name,name);
        p->score=score;
        p->next=NULL;
        if (head==NULL)
            head=p;
        else
            tail->next=p;
        tail=p;
        scanf("%d",&num);
        if(num==0)break;
        scanf("%s%d",name,&score);
    }

    Print_Stu_Doc(head);
}
/*遍历操作*/
void Print_Stu_Doc(struct stud_node * head)
{   
    struct stud_node *ptr;
    int the_score;
    scanf("%d",&the_score);
    if (head==NULL){
        printf("\nNo Records \n");
        return;
    }
    for(ptr=head;ptr!=NULL;ptr=ptr->next)
        if(ptr->score>=the_score)
        printf("%d %s %d \n",ptr->num,ptr->name,ptr->score);
} 
```



#### 实验10-2：逆序建立链表

【问题描述】输人若干个正整数(输人-1为结束标志)，要求按输人数据的逆序建立一个链表，并输出。试编写相应程序。
【样例输入】

```
1 2 3 4 5 6 7 -1
```

【样例输出】

```
7 6 5 4 3 2 1
```

```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
struct Number
{
    int num;
    struct Number *next;
};
void Print_Num(struct Number * head);  
int main()
{
    int num;
    int size=sizeof(struct Number);
    struct Number *head, *p;
    head=NULL;
            scanf("%d",&num);
    while (num>0)
    {
        p=(struct Number*)malloc(size);
            if(p==NULL)break;             
        p->num=num;
        p->next=head;
        head=p;
        scanf("%d",&num);
    }
    Print_Num(head);
}
void Print_Num(struct Number *head)
{
    struct Number *p;
    for(p=head;p!=NULL;p=p->next)
        printf("%d ",p->num);
}
```



#### 实验10-3：删除单项链表偶数节点

【问题描述】输人若干个正整数(输入-1 为结束标志)，并建立个单向链表，将其中的偶数值结点删除后输出。试编写相应程序。
【样例输入】

```
1 2 3 4 5 6 7 -1
```

【样例输出】

```
1 3 5 7
```

```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
struct Number
{
    int num;
    struct Number *next;
};
struct Number * Delete_Num(struct Number *head);               /* 删除 */
void Print_Num(struct Number * head);    /* 遍历 */
int main()
{
    int num;
    int size=sizeof(struct Number);
    struct Number *head, *tail, *p;
    head=tail=NULL;
        scanf("%d",&num);
    while(num!=-1)
    {
        p=(struct Number*)malloc(size);
            if(p==NULL)break;               /*小天才撸棒性*/
        p->num=num; 
        p->next=NULL;
        if (head==NULL)
            head=p;
        else
            tail->next=p;
        tail=p;
        scanf("%d",&num);
    }
    Delete_Num(head);
    Print_Num(head);
}
/*删除操作*/
struct Number*Delete_Num (struct Number * head)
{
    struct Number *ptr1,*ptr2;
    /*要被删除结点为表头结点*/
    while (head!=NULL&&head->num%2==0){ 
        ptr2=head;
        head=head->next;
        free(ptr2);
    }
    if(head==NULL)                     /*链表空*/
        return NULL;
    /*要被删除结点为非表头结点*/
        ptr1=head;
        ptr2=head->next;                /*从表头的下一个结点搜索所有符合删除要求的结点*/
        while (ptr2!=NULL){
            if (ptr2->num%2==0){        /*ptr2锁指结点符合删除要求*/
                ptr1->next=ptr2->next;
                free(ptr2);
            }
            else
                ptr1=ptr2;              /*ptr1后移一个结点*/
            ptr2=ptr1->next;             /*ptr2指向ptr1的后一个结点*/
        }
    return head;
}
void Print_Num(struct Number * head)
{
    struct Number *p;
    for(p=head;p!=NULL;p=p->next)
        printf("%d ",p->num);
}
```



#### 实验10-4：链表逆置

【问题描述】输人若千个正整数(输人-1为结束标志)建立一个单向链表，再将链表逆置后输出，即表头置为表尾，表尾置为表头。试编写相应程序。
【样例输入】

```
1 2 3 4 5 6 -1
```

【样例输出】

```
6 5 4 3 2 1
```

```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
struct Number
{
    int num;
    struct Number *next;
};
void Print_Num(struct Number * head);  
int main()
{
    int num;
    int size=sizeof(struct Number);
    struct Number *head, *p;
    head=NULL;
            scanf("%d",&num);
    while (num>0)
    {
        p=(struct Number*)malloc(size);
            if(p==NULL)break;             
        p->num=num;
        p->next=head;
        head=p;
        scanf("%d",&num);
    }
    Print_Num(head);
}
void Print_Num(struct Number *head)
{
    struct Number *p;
    for(p=head;p!=NULL;p=p->next)
        printf("%d ",p->num);
}
```



## 十、文件
### 编程题



#### 将短句“Programming is fun!”写入文件f1.txt.

【问题描述】将短句&ldquo;Programming is fun!&rdquo;写入文件f1.txt.
【输入形式】无
【输出形式】文件f1.txt，内容是：Programming is fun!
【样例输入】
【样例输出】

```
Programming is fun!
```

【样例说明】注意空格。
【评分标准】无

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
    FILE *fp;
    fp=fopen("f1.txt","w");
    fprintf(fp,"Programming is fun!");
    fclose(fp);
}
```



#### 从键盘输入一行字符，写到文件f3.txt中。

【问题描述】从键盘输入一行字符，写到文件f3.txt中。
【输入形式】键盘输入一行字符
【输出形式】文件f3.txt
【样例输入】

```
I love programming!
```

【样例输出】

```
文件f3.txt内容：I love programming!
```

【样例说明】请注意是一行字符。
【评分标准】无

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
    FILE *fp;
    fp=fopen("f3.txt","w");
    char s[100];
	int i=0;
	while((s[i]=getchar())!='\n') 
        i++;
    s[i]='\0';
    fprintf(fp,"%s",s);
    fclose(fp);
}
```



#### 统计文件的行数

【问题描述】读lx12_3.txt文件，显示在屏幕上，如果有大写字母，则改成小写字母再输出，并统计行数。根据回车符统计文件的行数。
【输入形式】读文件
【输出形式】输出到屏幕
【样例输入】文件内容如

```
A
bC
```

【样例输出】

```
a
bc
line is 2
```

【样例说明】
【评分标准】

```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<ctype.h>
int main()
{
    FILE *fp;
    int line=0;
    char ch;
    fp=fopen("lx12_3.txt","r");
    while (!feof(fp))
    {
        ch=fgetc(fp);
        if (ch!=EOF)
        {
            if (isupper(ch))    printf("%c", tolower(ch));
            else if (islower(ch))    printf("%c",ch);
            if (ch=='\n')
            {
                line++;
                printf("\n");
            }
        }
    }
    printf("Line is %d",line);
    fclose(fp);
    
}
```



#### 字符串替换(新)

【问题描述】
编写程序将一个指定文件中某一字符串替换为另一个字符串。要求：(1)被替换字符串若有多个，均要被替换；(2)指定的被替换字符串，大小写无关。
【输入形式】
给定文件名为filein.txt。从控制台输入两行字符串(不含空格，行末尾都有回车换行符)，分别表示被替换的字符串和替换字符串。
【输出形式】
将替换后的结果输出到文件fileout.txt中。
【样例输入】
从控制台输入两行字符串：

```
in
out
```

文件filein.txt的内容为：

```c
#include <stdio.h>
void main()
{
    FILE * IN;
    if((IN=fopen("in.txt","r"))==NULL)
    {
       printf("Can’t open in.txt!");
       return;
    }
    fclose(IN);
}
```
【样例输出】
文件fileout.txt的内容应为：
```c
#outclude <stdio.h>
void maout()
{
    FILE * out;
    if((out=fopen("out.txt","r"))==NULL)
    {
       prouttf("Can’t open out.txt!");
       return;
    }
    fclose(out);
}
```
【样例说明】
输入的被替换字符串为in，替换字符串为out，即将文件filein.txt中的所有in字符串(包括iN、In、IN字符串)全部替换为out字符串，并输出保存到文件fileout.txt中。
【评分标准】
该题要求得到替换后的文件内容，共有5个测试点。上传C语言文件名为replace.c。

```c
#include<stdio.h>
#include<string.h>
void str_replace(char *cp, int n, char *str);
char *Strstr(char *a,const char *b);
int main()
{
    char string_1[10240],string_2[10],string_3[10];
		scanf("%s",string_2);
		scanf("%s",string_3);
    int i=0;
    char c;
   	char *p;
    FILE *fp;											//定义文件指针
	fp=fopen("filein.txt","r+");						//打开文本文件进行读/写
	while(!feof(fp)){
		c=fgetc(fp);
        string_1[i] = c;
		i++;
	}
	string_1[i]='\0';									//将文本文件写入string_1
	p=Strstr(string_1,string_2);						//开始查找字符串
		while(p){
			str_replace(p,strlen(string_2),string_3);	//每找到一个字符串，就替换
			p=p+strlen(string_3);
			p=Strstr(string_1,string_2);
		}
    string_1[strlen(string_1)-1]=0;						//将字符串string_1末尾字符修改为结束符
	FILE *fp_out;
	fp_out=fopen("fileout.txt","w");
	fprintf(fp_out,"%s",string_1);							//将修改后的string_1写入文件
	fclose(fp_out);
	fclose(fp);
}
void str_replace(char *cp, int n, char *str)
{
	int len_of_str;
	char * tmp;
	len_of_str=strlen(str);
	//str3比str2短，往前移动
	if(len_of_str<n){
		tmp=cp+n;
		while(*tmp){
			*(tmp-(n-len_of_str))=*tmp; //n-len_of_str是移动的距离
			tmp++;
		}
		*(tmp-(n-len_of_str))=*tmp; //move '\0'
	}
	else
		//str3比str2长，往后移动
		if(len_of_str>n){
			tmp=cp;
			while(*tmp)tmp++;
			while(tmp>=cp+n){
				*(tmp+(len_of_str-n))=*tmp;
				tmp--;
			}
		}
	strncpy(cp,str,len_of_str);
}
char *Strstr(char *a,const char *b)
{
    int len_b=strlen(b);
    while(*a)
    {
        if(strncasecmp(a,b,len_b)==0)
            return a;
        a++;
    }
    return NULL;
}
```



#### 将文本文件test.txt中所有包含字符串 for 的行输出

【问题描述】编写一程序，用于将文本文件test.txt中所有包含字符串 for 的行输出
【输入形式】文件
【输出形式】屏幕，包含字符串 for 的行输出
【样例输入】文件test.txt内容：

```
I love programming! 
I love my country !
Thank you very much for your favor!
```

【样例输出】

```
The row including 'for' is :3
Thank you very much for your favor!
```

【样例说明】注意输出中的空格
【评分标准】无

```c
#include <stdio.h>
#include <string.h>
int main(){
	char str[200],str1[4]="for";
	FILE *fp;
	int i=0;
	fp=fopen("test.txt","r");
	while (fgets(str,200,fp)){
		i++;
		if(strstr(str,str1)){
			printf("The row including 'for' is : %d\n",i);
			printf("%s",str);
		}
	}
	fclose(fp);
}
```



## 十一、向前冲-期末测试
### 编程题



#### 求1-1/4+1/7-1/10+1/13-1/16+…的前n 项之和

【问题描述】
输入一个正整数n,计算1-1/4+1/7-1/10+1/13-1/16+...的前n 项之和,输出时保留3位小数。
【输入形式】
从键盘输入一个正整数n。
[输入输出样例1] (下划线部分表示输入)
Enter n: 

```
3
```

```
sum=0.893
```

[输入输出样例2] (下划线部分表示输入)
Enter n: 

```
10
```

```
sum=0.819
```

【样例说明】
输入提示符后要加一个空格。其中":"后要加一个且只能一个空格。
输出语句的"="两边无空格。
英文字母区分大小写。必须严格按样例输入输出。

```c
#include<stdio.h>
int main()
{
    int n=0,flag=1,d=1;
    printf("Enter n: ");
        scanf("%d",&n);
    double sum=0.0,temp=0.0;
    
    for (int i = 1; i <=n; i++)
    {
        temp=1.0*flag/d;
        d+=3;
        sum+=temp;
        flag=-flag;
    }
    
    printf("sum=%.3lf",sum);
    
}
```



#### 小数形式与科学计数法转换

【问题描述】
编写一个程序，将用小数或整数形式输入的数据，转换成科学计数法的形式输出。输入的数据没有符号。输入数据全为有效数据，即若输入的数据为小数形式，则末尾不含数字0；并且若输入的数据大于1，则最高位数字不为0。
提示：以字符串形式保存相关数据。
【输入形式】
控制台输入一小数或整数，最后会有回车换行符，所有输入的字符数不会超过100。
【输出形式】
以科学计数法形式输出数据。输出的数据由以下几部分构成：
1.底数部分是一个小数或整数，若为小数，则小数点前后必有数字，而且都为有效数字。即：小数点前只有一位大于0的数字，小数点后的末尾数字不能为0。若为整数，则只有一位数字，不带小数点。
2.必有小写字母&ldquo;e&rdquo;。
3.指数部分是一个整数。若大于等于0，则不带符号；若小于0，则需要带负号&ldquo;-&rdquo;。且整数的最高位数字不为0。
【输入样例1】

```
0.000000000000002
```

【输出样例1】

```
2e-15
```

【输入样例2】

```
898456.23489651700659
```

【输出样例2】

```
8.9845623489651700659e5
```

【输入样例3】

```
367298599999090000000000000000000000000000
```

【输出样例3】

```
3.6729859999909e41
```

【样例说明】
以小数或整数形式输入数据，然后转换成相应的科学计数法形式输出。
【评分标准】
该题要求以科学计数法形式输出数据，提交程序文件名为notation.c。

```c
#include<stdio.h>
#include<string.h>
void delDot(char number[]);
void delZero(char number[]);
void Print(char number[],int flag,int k);
int main()
{
    char number[101];
    scanf("%s",number);
    char *num=number;
    if (number[0]=='0'&&number[1]=='.')
    {
        int i=2,k=0,flag=0;
        while (number[i]!='\0')
        {
            if (number[i]!='0')
            {
                flag=i;
                if (number[i+1]!='\0')
                {
                    Print(number,flag,k);
                    return 0;
                }
            }
            k++;            //统计指数
            i++;
        }
        printf("%se-%d",(num+flag),k);
    }
    else if (number[1]=='.')
    {
        printf("%se0",number);
    }
    else
    {
        int i=1,k=0;
        while (number[i]!='\0')
        {
            if (number[i]=='.')
            {
                delDot(number);
                break;
            }
            k++;
            i++;
        }
        if (number[i-1]=='0')
        {
            delZero(number);
        }
        printf("%c.%se%d",number[0],(num+1),k);
    }
}
void delDot(char number[])
{
    int n=0;
    int m=strlen(number);
    for (int i = 0; number[i]!='\0'; i++)
    {
        if (number[i]=='.')
        {
            for (int j = i; j < m; j++)
            {
                number[j]=number[j+1];
            }
        n++;i--;
        }
    }
    number[m-n]='\0';
}
void delZero(char number[])
{
    int i=strlen(number);
    while(i>0)
    {
        if (number[i-1]=='0')
        {
            number[i-1]='\0';
        }
        else
        {
            return;
        }
        
    i--;
    }
}
void Print(char number[],int flag,int k)
{
    printf("%c.%se-%d",number[k+2],(number+flag+1),k+1);
}
```



#### 超长正整数的减法

【问题描述】编写程序实现两个超长正整数(每个最长80位数字)的减法运算。
【输入形式】
从键盘读入两个整数，要考虑输入高位可能为0的情况(如00083)。

1. 第一行是超长正整数A；

2. 第二行是超长正整数B；

【输出形式】 
输出只有一行，是长整数A减去长整数B的运算结果，从高到低依次输出各位数字。要求：
1、若结果大于0，则只输出结果数字，不输出正号；若结果为负，则输出负号；若结果为0，则只输出一个0。
2、除非结果为0，否则输出的结果的最高位不能为0，并且各位数字紧密输出。
【输入样例】

```
234098
134098703578230056
```

【输出样例】

```
134098703577995958
```

【样例说明】
进行两个正整数减法运算， 234098 - 134098703578230056 = -134098703577995958。
【评分标准】
该题要求输出超长整数减法结果，提交程序文件名为subtract.c或subtract.cpp。



#### 国王的麦粒

【问题描述】
相传国际象棋是古印度舍罕王的宰相达依尔发明的。舍罕王十分喜欢象棋，决定让宰相自己选择何种赏赐。
这位聪明的宰相指着8×8共64格的象棋盘说：陛下，请您赏给我一些麦子吧，就在棋盘的第一个格子中放1粒，第2格中放2粒，第3格放4粒，以后每一格都比前一格增加一倍，依此放完棋盘上的64个格子，我就感恩不尽了。舍罕王让人扛来一袋麦子，他要兑现他的许诺。
国王能兑现他的许诺吗？试编程计算舍罕王共要多少麦子赏赐他的宰相，这些麦子合多少立方米(volume)？
(已知1立方米麦子约1.42e8粒)
总粒数为：

```
sum=1+2+22+23+…+263  
```

函数pow(a,b)表示求a^b

```
double pow(double base, double exponent);
```

需要math.h头文件
【输入形式】
【输出形式】

```
volume: 1.299066e+011
```

```c
#include<stdio.h>
#include<math.h>
int main()
{
    double sum=1,k=0;
    for (int i = 1; i <= 64; i++)
    {
        sum=sum+pow(2,k++);
    }
    double volume=sum/1.42e8;
    int j = 0;
    for (j = 0; volume>10 ; j++)
    {
        volume/=10;
    }
    
    printf("volume: %lfe+%d",volume,j);
}
```



#### 求一个整数中2的个数

【问题描述】
读入一个整数,统计并输出该数中2的个数｡要求定义并调用函数countdigit(number,digit),它的功能是统计整数number 中数字digit 的个数｡例如,countdigit(10090,0) 的返回值是3｡
【输入形式】
输入一个整数
[输入输出样例1] (下划线部分表示输入)
Enter an integer: 

```
21252
```

```
Number of digit 2: 3
```

【样例说明】
输入提示符后要加一个空格。例如Enter an integer: ，其中:后要加一个且只能一个空格。
输出语句的:后要加一个且只能一个空格。
英文字母区分大小写。必须严格按样例输入输出。

```c
#include<stdio.h>
int countdigit(int number,int digit);
int main()
{
    int number=0,digit=2,num=0;
    scanf("%d",&number);
    printf("Enter an integer: ");
    num=countdigit(number,digit);
    printf("Number of digit 2: %d",num);
}
int countdigit(int number,int digit)
{
    int i=0;
    int count=0;
    while (number>0)
    {
        i=number%10;
        if (i==2)
        {
            count++;
        }
        number/=10;
    }
    return count;
}
```



#### 交换最大、最小值

【问题描述】
输入一个正整数n(1 <n&le;10)，再输入n 个整数，将最小值与第一个数交换，最大值与最后一个数交换，然后输出交换后的n 个数｡
【输入形式】
从键盘输入一个正整数n和n个整数。
[输入输出样例1] (下划线部分表示输入)
Input n: 

```
5
```

Input 5 integers:

```
 8 2 5 1 4
```

```
After swapped: 1 2 5 4 8  
```

​    (每个输出数据间有一个空格)
【样例说明】
输入提示符后要加一个空格。例如Input n: ，其中:后要加一个且只能一个空格。
英文字母区分大小写。必须严格按样例输入输出。

```c
#include<stdio.h>
void getArray(int a[],int n);
void doSwap(int a[],int n);
int main()
{
    int n=0;
    printf("Input n: ");
    scanf("%d",&n);
    int a[n];
    getArray(a,n);
    printf("After swapped: ");
    doSwap(a,n);
}
void getArray(int a[],int n)
{
	printf("Input %d integers: ",n);
	for(int i=0;i<n;i++) {
		scanf("%d",&a[i]);
	}
}
void doSwap(int a[],int n)
{
    int min=100,max=-100;
    int min_flag=0,max_flag=0;
    for (int i = 0; i < n; i++)
    {
        if (max<=a[i])
        {
            max=a[i];
            max_flag=i;
        }
    }
    int t=0;
        t=a[n-1];a[n-1]=a[max_flag];a[max_flag]=t;
    for (int i = 0; i < n; i++)
    {
        if (min>=a[i])
        {
            min=a[i];
            min_flag=i;
        }
    }
    t=0;
        t=a[0];a[0]=a[min_flag];a[min_flag]=t;
    for (int i = 0; i < n; i++)
    {
        printf("%d ",a[i]);
    }
    
}
```



#### 将一笔钱换算成1分、2分和5分的硬币组合

【问题描述】
将一笔钱(大于8分，小于1元，精确到分)换算成1分、2分和5分的硬币组合｡输入金额，问有几种换算方法？要求每种硬币至少有一枚｡
【输入形式】
从键盘输入一个正整数n。
[输入输出样例1] (下划线部分表示输入)

```
Input money: 10
count=2
```

【样例说明】
输入提示符后要加一个空格。其中:后要加一个且只能一个空格。
英文字母区分大小写。必须严格按样例输入输出。

```c
#include <stdio.h>
int main()
{
    int a,b,c;
	int money,i;
    printf("Input money:");
    scanf("%d",&money);
    i=0;
    for (a=money/5;a>0;a--) 
	{
		for (b=money/2; b>0; b--) 
		{
            for (c=money; c>0; c--) 
			{
                if (a*5+b*2+c==money) 
					i++;
            }
        }
    }
    printf(" count=%d\n",i);
}
```



#### 多项式加法

【问题描述】编写一个程序实现两个一元多项式相加的运算。
【输入形式】从当前目录下的poly.in文件读入两行以空格分隔的整数，每一行代表一个多项式，且该多项式中各项的系数均为0或正整数，最高幂次不超过50。对于多项式(n<50)的表示方法如下：
  an n an-1 n-1 &hellip;&hellip; a1 1 a0 0
  即相邻两个整数分别表示表达式中一项的系数和指数。在输入文件中只出现系数不为0的项。
  【输出形式】将运算结果输出到当前目录下的poly.out文件中。将系数不为0的项按指数从高到低的顺序输出，每次输出其系数和指数，均以空格分隔。在行的末尾输出一个回车符。
  【输入文件】

```
54 8 2 6 7 3 25 1 78 0
43 7 4 2 8 1
```

  【输出文件】

```
54 8 43 7  2 6  7 3  4 2  33 1  78 0
```

  【样例说明】输入文件的两行分别代表了表达式$54x^8 +2x^6 +7x^3 +25x+78+43x^7 +4x^2 +8x$其和为$54x^8 +43x^7 +2x^6 +7x^3 +4x^2 +33x+78$
  【评分标准】结果正确则该测试点得满分，否则该测试点得0分。上传C语言文件名为 poly.c



####   求m到n之间所有数字的和

  【问题描述】输入一个正整数m和n，输出从m开始到n结束(包含m和n)的所有整数数字的和。
  【输入形式】两个正整数，用空格分隔
  【输出形式】两个正整数之间的整数数字的和，以“sum=?”的形式输出。
  【样例输入】

```
1 100 
```


  【样例输出】

```
sum=5050
```

```c
#include<stdio.h>
int main()
{
    int m=0,n=0,sum=0;
    scanf("%d",&m);
    scanf("%d",&n);
    for (; m <= n; m++)
    {
        sum+=m;
    }
    printf("sum=%d",sum);
}
```



####   学生成绩排序

  【问题描述】
  对某班学生成绩排序。从键盘依次输入某班学生的姓名和成绩(一个班级人数最多不超过50人)并保存，然后分别按学生成绩由高到低顺序输出学生姓名和成绩，成绩相同时，则按输入次序排序。
  【输入形式】
  从键盘依次输入最多不超过50个学生的学生姓名和成绩：
  第一行输入班级学生人数；
  在单独行上输入空格隔开的学生姓名和成绩，其中学生成绩是整数。
  【输出形式】
  按学生成绩由高到低顺序输出学生姓名和成绩，每行输出一位学生的姓名和成绩，其中姓名(英文)占15位，成绩占5位，均按缺省方式对齐。成绩相同时按输入次序排序。
  【输入样例】

```
4
aaa 50
bbb 70
ccc 65
ddd 90
```

  【输出样例】

```
############ddd###90
############bbb###70
############ccc###65
############aaa###50
```

  (注意：其中#号代表空格)
  【样例说明】
  输入了四个学生姓名和成绩，按成绩排序输出。
  【评分标准】
  按成绩顺序输出学生姓名和成绩，完全正确得50分，共五个测试点，每个测试点10分，提交程序名为c02.c。

```c
#include<stdio.h>
struct Student
{
    char name[20];
    int score;
};
int main()
{
    struct Student Excel[50];
    int n=0;
    scanf("%d",&n);
    for (int i = 0; i < n; i++)
    {
        scanf("%s %d",Excel[i].name,&Excel[i].score);
    }
	struct Student t;
	for(int i=0;i<n-1;i++)
		for(int j=0;j<n-i-1;j++)
			if(Excel[j].score<Excel[j+1].score){
				t=Excel[j];
				Excel[j]=Excel[j+1];
				Excel[j+1]=t;
			}    
    for (int i = 0; i < n; i++)
    {
        printf("%15s%5d\n",Excel[i].name,Excel[i].score);
    }
}
```



## 十二、超越自我
### 编程题



#### 求差集1

【问题描述】两个集合的差集定义如下：
集合A、B的差集，由所有属于A但不属于B的元素构成。
输入两个集合A、B，每个集合中元素都是自然数。求集合A、B的差集。
【输入形式】
从标准输入先输入集合元素个数，然后在下一行输入集合中的自然数元素，以空格分隔。
其中，每个集合都不输入重复的元素。
【输出形式】
输出差运算后集合中的元素，以空格分隔。输出元素的顺序与原有集合A输入的顺序一致。
如果A、B的差集为空集，则不输出任何数值。
【样例输入】

```
4
2 8 3 4
4
6 1 4 9
```

【样例输出】

```
2 8 3
```

【样例说明】从标准输入接收集合的元素个数和每个元素，输出集合A、B的差集。
【评分标准】该题要求输出差运算后集合中的元素，共有5个测试点。上传C语言文件名为sets.c。

```c
#include<stdio.h>
int getArray(int a[],int n);
int putArray(int a[],int n);
int main()
{
    int n=0;
    int m=0;
    scanf("%d",&n);
        int a[n];                   //定义集合A
    getArray(a,n);
    scanf("%d",&m);
        int b[m];                   //定义集合B
    getArray(b,m);
    int i=0,j=0;
    for (i = 0; i < n; i++)
    {
        for (j = 0; j < m; j++)
            if (a[i]==b[j])
                break;
        if (j==m)
            printf("%d ",a[i]);
    }
}
int getArray(int a[],int n)
{
	for(int i=0;i<n;i++) {
		scanf("%d",&a[i]);
	}
return 0;
}

```



#### 求孪生数

【问题描述】孪生数定义： 如果 A 的约数(因数，**包含1，但不包含A本身**)之和等于 B ， B 的约数(因数)之和等于 A ， A 和 B 称为孪生数(**A和B不相等**)。试找出正整数 M 和 N 之间的孪生数。
【输入形式】从控制台输入两个正整数M和N(1<=M<N<=20000)，中间用一个空格分隔。
【输出形式】
在标准输出上输出符合题目描述的M和N之间的全部孪生数对(**包括M和N**)。每行输出一对孪生数，用一个空格隔开，小的先输出；各行孪生数按照第一个数从小到大的顺序输出，**一对孪生数只输出一次**。 如果没有符合要求的孪生数对，则输出字符串“**NONE**”。
【输入样例1】

```
20 300
```

【输出样例1】

```
220 284
```

【输入样例2】

```
200 250
```

【输出样例2】

```
NONE
```

【样例说明】
样例1输入的区间为[20,300]，其间有一对孪生数对，即：$220(1+2+4+5+10+11+20+22+44+55+110=284)$和$284(1+2+4+71+142=220)$。样例2输入的区间是$[200,250]$，其间没有孪生数对，所以输出字符串：$NONE$。
【评分标准】
该题要求输出区间中的所有孪生数对，共有5个测试点，提交程序文件名为example1.c或example1.cpp。

```c
#include<stdio.h>
int main()
{
    int a,b,c[20000]={0},flag=0;
    scanf("%d%d",&a,&b);
    for(int i=a;i<=b;i++)
    {
        int sum=0;
        for(int j=1;j<i;j++)
            if(i%j==0)sum+=j;
        if(sum>a&&sum<b)
            c[i]=sum;
    }
    for(int m=a;m<=b;m++)
    {
        if(m==c[c[m]]&&c[m]!='\0'&&c[m]!=m)
        {
            printf("%d %d \n",m,c[m]);
            flag=1;
            c[c[m]]=0;
        }
    }
    if (flag==0)
        printf("NONE");
    return 0;
}
```

