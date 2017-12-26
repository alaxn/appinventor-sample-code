# appinventor-sample-code

## App inventor介绍

一句话说，就是一个开发简单Android App的积木编程程序。

> App Inventor for Android is an open-source web application originally provided by Google, and now maintained by the Massachusetts Institute of Technology. 
>
> From [Wikipedia](https://en.wikipedia.org/wiki/App_Inventor_for_Android)

一开始是Google负责开发和维护，后来转交给了[MIT](http://appinventor.mit.edu/explore/)。我当年学的时候，还是第一代版本，现在是第二代版本。这种编程模式不需要“打代码”，只需要从提供的模块中拽拖适当的模块进行拼接就可以，对于初学者来说，入门难度较小（实际上，大多数对编程无感的人还是一头雾水）。



## 个人一些App inventor程序分享

### Memory of PAL

利用仙剑素材做的小游戏，内含三个小游戏。里面有一些小bug，后来弃坑了。

<i class="fa fa-download">[源码下载](https://github.com/alaxn/appinventor-sample-code/blob/master/Memory_of_PAL.aia)</i>
<i class="fa fa-download">[Apk下载](https://github.com/alaxn/appinventor-sample-code/blob/master/Memory_of_PAL.apk)</i>



### 冒泡排序

简单的冒泡排序

<i class="fa fa-download">[源码下载](https://github.com/alaxn/appinventor-sample-code/blob/master/BubbleSort.aia)</i>
<i class="fa fa-download">[Apk下载](https://github.com/alaxn/appinventor-sample-code/blob/master/Memory_of_PAL.aia)</i>

```pascal
procedure swap(j:longint);  //交换
begin
  a[j]:=a[j] xor a[j+1];
  a[j+1]:=a[j] xor a[j+1];
  a[j]:=a[j] xor a[j+1];
end;
 
procedure bubblesort;  //排序
var
  i,j:longint;
begin
  for i:=n-1 downto 1 do begin
    for j:=1 to i do begin
      if a[j]>a[j+1] then swap(j);
    end;
  end;
end;
```



### 快速排序

主体框架是快速排序，实现两个功能：1.查找第n小的数，直接查找位置，返回。 2.新增数字，二分法查找适当位置插入。

<i class="fa fa-download">[源码下载](https://github.com/alaxn/appinventor-sample-code/blob/master/qsort.zip)</i>
<i class="fa fa-download">[Apk下载](https://github.com/alaxn/appinventor-sample-code/blob/master/qsort.apk)</i>

```Pascal
program  qsort;
const maxn=99999;
var a:array[0..maxn] of longint;
    time1,time2:longint;
    n:longint;
procedure input;
var
  i:byte;
begin
  read(n);
  randomize;
  for i:=1 to n do begin 
    a[i]:=random(9999);
   end;
end;

procedure quicksort(var a: array of integer; l,r:integer);
var i,j,x,t:integer;
begin
 i:=l; j:=r; x:=a[(l+r) div 2];
 repeat
  while a[i]<x do inc(i);
  while a[j]>x do dec(j);
  if i<=j then
  begin
   t:=a[i]; a[i]:=a[j]; a[j]:=t;
   inc(i); dec(j);
  end;
 until i>j;
 if i<r then quicksort(a,i,r);
 if l<j then quicksort(a,l,j);
end;

function insert(temp:longint):longint;
 var 
     flag:boolean;
     i,j,nn:longint;
 begin 
  flag:=false; 
  i:=1; j:=n;  nn:=(i+j) div 2;
  while not flag do begin 
    if a[nn]<temp then begin 
      i:=nn; nn:=(nn+j) div 2
     end;
    if a[nn]>temp then begin 
      j:=nn; nn:=(nn+i) div 2;
     end;
    if (nn=i) or (nn=j) then begin 
      flag:=true;
      exit(nn);
     end;
   end;
 end;

procedure output;
var i:longint;
 begin 
   for i:=1 to n do begin 
     write(a[i],' ');
   end; 
 end;
procedure work;
 begin 
   input;
   time1:=gettime;
   qsort(a,1,n);
   time2:=gettime;
   output;
   time1:=time1-time2;
   judge;
 end;
 
begin 
  work;
end.
```



### 打飞机

#### 流程

初始化，敌机飞行，打出子弹，碰撞，重启。

#### 具体细节

设计四只敌机和自己的飞机。 
初始化：设置好位置，以及四只敌机的飞行方向和速度。
碰撞：处理好子弹和敌机的碰撞以及子弹到边的情况。
敌机：处理好相应的速度和到边的情况。

<i class="fa fa-download">[源码下载](https://github.com/alaxn/appinventor-sample-code/blob/master/airplane.zip)</i>
<i class="fa fa-download">[Apk下载](https://github.com/alaxn/appinventor-sample-code/blob/master/airplane.apk)</i>



### 模拟撞击

采用0-90，90-180，1800-270，270-360 四种情况处理两颗求的撞击，用随机函数处理球撞击墙壁的情况。

#### 功能

每次撞击都会使球的速度降下来。
撞击到墙壁时速度降低到2。
可以拽拉每一颗球到不同位置。
设置时钟经过一定时间间隔球会加速。

<i class="fa fa-download">[源码下载](https://github.com/alaxn/appinventor-sample-code/blob/master/animation.zip)</i>
<i class="fa fa-download">[Apk下载](https://github.com/alaxn/appinventor-sample-code/blob/master/animation.apk)</i>

