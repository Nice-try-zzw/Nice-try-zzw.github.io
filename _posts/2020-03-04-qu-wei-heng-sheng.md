---
layout:     post                    # 使用的布局（不需要改）
title:      "基础算法"               # 标题 
subtitle:   "Hello world" #副标题
date:       2020-03-05              # 时间
author:     "Nice_try"                      # 作者
header-img: "img/blog05.jpg"    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - blog
    - 算法
---

# 基础数据结构

###### 为什么会从算法联想到数据结构？   
因为特定的算法需要在相应的数据结构基础上运行才能发挥良好的性能。     
###### 数据结构是什么？  
数据结构是数据的组织形式和载体。     
###### 算法是什么？  
算法是良好的操作步骤（可以看作套路）  
**综上 学好数据结构是学好算法的前提**

## 1.1顺序表  
最基础最先接触的就是线性表  
**线性表的定义是什么？**  
n个数据元素的有限序列，其中n（n>0）表示线性表的长度。  
**顺序表的定义**  
顺序表是最基础的数据结构之一，就是线性表的一种存储表现形式，在计算机中表示为一块连续的内存空间 一般特性为：  

 1. 顺序表的内存空间是一连串连续的地址空间  
 2. 需要有一个唯一的表名来表示  
 3. 数据在顺序表中按顺序排列，存取时可以根据相对位置进行随机存取  

```cpp
const int defaultSize = 10;
template <typename DataType> class SeqList
{
public:
	//构造函数
	SeqList (int size = defaultSize){
		if (size > 0)//检查赋予的顺序表大小，如果合法则分配相应大小的内存空间
		{
			maxSize = size;
			elements = new DataType[maxSize];//分配内存大小
		}
	}
	//析构函数
	~SeqList()
	{
		delete[] elements;//回收内存空间
	}
private:
	DataType *elements;
	int maxSize;
}
```
**顺序表的基本操作**  
顺粗表主要有插入元素、删除元素、查找元素、获取元素和修改元素五个基本操作。  	

```cpp
const int defaultSize = 10;
template <typename DataType> class SeqList
{
public:
	//构造函数
	SeqList (int size = defaultSize){
		if (size > 0)//检查赋予的顺序表大小，如果合法则分配相应大小的内存空间
		{
			maxSize = size;
			elements = new DataType[maxSize];//分配内存大小
		}
	}
	//析构函数
	~SeqList()
	{
		delete[] elements;//回收内存空间
	}
	bool insertElement(DataType data);//向表尾插入新元素
	bool deleteElement(int location);//删除指定位置的元素
	DataType getElement(int location);//返回指定位置的元素
	bool changeElement(int location,DataType newData);//修改指定位置的元素
private:
	DataType *elements;
	int maxSize;//顺序表最大大小
	int length;//顺序表的有效长度
}
```
**顺序表的插入操作**  
插入操作可以划分为两个步骤 

 1. 检查顺序表是否已满 如果已满就拒绝此次插入操作  
 2. 如果未满 则将新元素插入表尾空间 并更新顺序表的有效长度  
```cpp
template<typename DataType>bool SeqList<DataType>::insertElement(DataType data)
{
	int currentIndex = length;//记录新元素的插入位置
	if (length>maxSize)//判断顺序表是否已满
		return false;
	else
	{
		elements[currentIndex]=data;
		length++;
		return true;
	}
}
```
插入函数返回的bool型变量用以反馈插入操作是否成功  
**顺序表的删除操作**  
删除操作要比插入操作麻烦  因为此处删除是指删除顺序表中指定元素  
删除元素后  此元素后面的元素需移动弥补空缺  

```cpp
template<typename DataType>bool SeqList<DataType>::deleteElement(int location)
{
	if(location>=length||location<0)
		return false;
	else
	{
		for(int i=location;i<length;i++)
			elements[i]=element[i+1];
		length--;
		return true;
	}
}
```
**获取指定位置的元素**

```cpp
template<typename DataType>DataType SeqList<DataType>::getElement(int location)
{
	if(location>=length||location<0)
		return 0;
	else
		return elements[location];
}
```
**修改指定位置的元素**

```cpp
template<typename DataType>bool SeqList<DataType>::changeElement(int location,DataType newdata)
{
	if(location>=length||location<0)
		return false;
	else
	{
		elements[location]=newdata;
		return true;
	}
}
```
## 1.2 链表  
与顺序表一样 链表的数据逻辑组织结构也是一维的 但链表的物理结构与顺序表不同  链表的物理存储结构是一堆地址任意的存储单元（不一定相邻）  
**链表的定义**   
将数据元素存放在不连续的地址空间中的一种线性表。   
其分为单链表、双链表、循环链表几类。   
**单链表**的每个结点都有数据域和指针域，数据域用来存放结点的数据，指针域用来存放下一个结点的地址。   
整个链表会有一个表头 来存放第一个结点的地址。   
每个结点的后面一个节点称为该结点的后继。   
链表也有一个表尾  其没有后继， 指向空指针（NULL）   
![单链表](https://img-blog.csdnimg.cn/20200301225013920.jpg)
从图中可以看出 单链表就具有如下特征：

- 单链表结点的物理位置不一定连续，单链表逻辑上通过指针实现连续。  
- 单链表有一个头结点和一个尾结点 并且只有尾结点没有后继结点，其他结点有且只有一个后继结点   
- 只要知道了链表的头结点  就可以遍历整个链表   

```cpp
template<typename DataType>class LinkList
{
public:
    //
    LinkList()
    {
        head = new ListNode();
    }
    LinkList(ListNode *node)
    {
        head = node;
    }
    ~LinkList()
    {
        delete head;
    }
    bool insertNode(ListNode *q, DataType newData);//插入结点
    bool removeNode(LinkNode *q);//删除结点
    ListNode *findNode(DataType value);//查找指定值的结点并返回位置
    bool clearLink();//清空链表
    DataType getNodeData(ListNode *p);//获取结点数据
private:
    ListNode *head;//头结点
};
template<typename DataType>class ListNode
{
public:
    ListNode()
    {
        next = NULL;
    }
    ListNode(DataType item,ListNode<DataType>*nextNode=NULL)
    {
        data = item;
        next = nextNode;
    }
    ~ListNode()
    {
        next = NULL;
    }
    //获取结点内的数据
    DataType getData()
    {
        return data;
    }
    //获取指针域
    ListNode* getNext()
    {
        return next;
    }
private:
    friend typename LinkList<DataType>;
    //将LinkList设为友元类 方便对node的成员数据和方法的访问
    DataType *next;//指向下一个结点的指针
    DataType data;//结点中的数据
};

```
上面有两个类，一个是表示链表结点的ListNode类  一个是表示链表整体的LinkList类   
在ListNode中将LinkList设为ListNode的友元类  便于链表类对结点的内部成员变量和成员方法的访问   
![一个单向链表包含两个值: 当前节点的值和一个指向下一个节点的链接](https://img-blog.csdnimg.cn/20200302220351210.png)
**链表的基本操作**   
单链表主要执行链表的插入结点、删除结点、查找指定值的结点和清空结点4种操作   
**插入结点**   
可以分为两种插入情况     

 1. 在单链表的末尾添加结点  
 2. 在第i个结点后添加新结点

在第i个结点后添加新结点：   

 1. 创建一个待插入的结点 并分配给其内存空间， 并将指针域设为NULL
 2. 找到单链表的第i个结点位置，获取其地址，将待插入结点插入在结点i与其后继结点之间

![结点插入](https://img-blog.csdnimg.cn/20200302220520915.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3pSTkFfXw==,size_16,color_FFFFFF,t_70)
```cpp
template<typename DataType>bool LinkList<DataType>::insertNode(int i,DataType newData)
{
    ListNode<DataType> *p = head;//设置游标指针，初始化头结点地址
    int j;
    for (j = 1; j <= i - 1;j++)//查找第i个结点 指针需要移动i-1次
    {
        p = p->next;
        if(p==NULL)//如果指针为空 则不存在该结点  或已到链表末尾
        {
            break;
        }
    }
    if(p==NULL&&j<(i-1))//指针为空且没有到第i个位置  说明不存在第i个结点
    {
        std::cout << "插入位置无效" << endl;
        return false;
    }
    ListNode<DataType> *node = new ListNode<DataType>(newData);//建立新结点node
    node->next = p->next;//将node的next指针复制为p的后继结点地址
    p->next = node;//p的后继指针指向node
    return true;
}
```
对于在单链表的末尾添加结点的操作，只需要我们遍历链表找到尾结点，然后将尾结点的后继指针指向新建结点就可以。   
**删除结点**

```cpp
template<typename DataType>bool LinkList<DataType>::removeNode(ListNode<DataType> *q)
{
    if(q==NULL)//判断待删除结点是否存在
    {
        std::cout << "待删除结点不存在" << endl;
        return false;
    }
    ListNode<DataType> *tempPointer = head;//设置游标指针 初始化为头结点
    while(tempPointer->next!=q)//遍历单链表  找到q所指向结点的前驱结点
    {
        tempPointer = tempPointer->next;
    }
    tempPointer->next = q->next;//将q结点的后继结点赋值给其前驱结点的next指针
    delete q;
    return true;
}
```
删除结点的关键是找到该结点在链表中的前驱节点     
**查找特定值的结点**

```cpp
template<typename DataType>ListNode<DataType>* LinkList<DataType>::findNode(DataType value)
{
    ListNode<DataType> *currentPointer = head;//设置游标指针
    //判定游标指针所指的结点是否与value相等
    while(currentPointer!=NULL&&currentPointer->data!=value)
    {
        currentPointer = currentPointer->next;
    }
    if(currenterPointer==NULL)//判断结点是否存在
    {
        std::cout << "没有找到该结点！程序异常退出！" << endl;
        exit(1);
    }
    return currentPointer;//返回找到的结点的指针
}
```
**清空链表**  
清空操作的主要思想就是让头结点head的next指针域为空 回收各个结点的内存空间    

```cpp
template<typename DataType>void LinkList<DataType>::clearLink()
{
    ListNode<DataType> *current = head;//设置游标指针
    while(head->next!=NULL)//判断head的后继结点是否为NULL
    {
        current = head->next;//将current指向head的后继结点
        head->next = current->next;//将current的后继结点赋值给head的next域
        delete current;//回收current结点所占的空间；
    }
}
```



>参考书籍《妙趣横生的算法（C++语言实现）》
