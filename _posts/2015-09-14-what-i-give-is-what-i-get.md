---
layout: post
title: 二叉树先序、中序、后序递归遍历算法
date: 2016-03-06
categories: blog
tags: [数据结构与算法]
description: 二叉树先序、中序、后序递归遍历算法的表述及实现

---
## 二叉树先序、中序、后序递归遍历算法
回顾二叉树的递归定义可知，二叉树是由三个基本单元组成：根节点、左子树、右子树。因此，若能依次遍历这三部分，便是遍历了整个二叉树。假如以L、D、R分别表示遍历左子树。访问根节点、遍历右子树，则可有DLR、LDR、LRD、DRL、RLD、RDL六种遍历二叉树的方案。若限定先左后右，则只有前三种情况，分别称之为先（根）序遍历、中（根）序遍历、后（根）序遍历。

##
1．中序遍历的递归算法定义：

　　若二叉树非空，则依次执行如下操作：

　　(1)遍历左子树；

　　(2)访问根结点；

　　(3)遍历右子树。

2．先序遍历的递归算法定义：

　　若二叉树非空，则依次执行如下操作：

　　(1) 访问根结点；

　　(2) 遍历左子树；

　　(3) 遍历右子树。

3．后序遍历得递归算法定义：

　　若二叉树非空，则依次执行如下操作：

　　(1)遍历左子树；

　　(2)遍历右子树；

　　(3)访问根结点

##代码实现

<pre><code>
#include<stdio.h>
#include<malloc.h>
#define M 100
typedef struct node /* 链式存储的指针类型和结点定义 */
{
	char data;
	struct node *lchild,*rchild;

}BTnode;

BTnode * create()/*建立二叉树*/
{
	BTnode *t;
	char ch;
	scanf("%c",&ch);
	if(ch=='#')
		t=NULL;
	else
		{
		t=(BTnode *)malloc(sizeof(BTnode))	;
		t->data =ch;
		t->lchild=create();
		t->rchild=create();
		}
	return t;
}

void preorder(BTnode *t)/*先序遍历二叉树*/
{
 if(t!=NULL)
 printf("%c ",t->data);
 if(t->lchild!=NULL)
 preorder(t->lchild);
 if(t->rchild!=NULL)
 preorder(t->rchild);

}


void inorder(BTnode *t)/*中序遍历二叉树*/
{
  if(t!=NULL)
  {
    if(t->lchild!=NULL)
    inorder(t->lchild);
    printf("%c ",t->data);
    if(t->rchild!=NULL)
    inorder(t->rchild);
  }
}
void postorder(BTnode *t)/*后序遍历二叉树*/
{
  if(t!=NULL)
  { if(t->lchild!=NULL)
    postorder(t->lchild);
    if(t->rchild!=NULL)
    postorder(t->rchild);
    printf("%c ",t->data);
  }
}

void main()
{
	BTnode *t;
	printf("Input data:") ;
	t=create();
	printf("==================The result==========================\n");
	printf("The preorder is:\n");
	preorder(t);
	printf("\n");
	printf("The inorder is:\n");
	inorder(t);
	printf("\n");
	printf("The postorder is:\n");
	postorder(t);
	printf("\n");
	getchar();
}
例如：

        A
      /  \
     B    C
    /    / \ 
   D    E   F
输入：ABD###CE##F##
先序遍历输出：A B D C E F
中序遍历输出：D B A E C F
后序遍历输出：D B E F C A


</code></pre>

---


