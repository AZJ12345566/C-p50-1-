# C-p50-1-
C语言学习笔记 p50 字符函数&amp;内存函数使用和剖析(1)
#include<stdio.h>
#include<string.h>
#include<assert.h>
int main()
{
    //strncmp-字符串比较
    //函数原型:int strncmp(const char* string1,const char* string2,size_t count);
    const char* p1="abcdef";
    const char* p2="abcqwer";
    int ret=strncmp(p1,p2,3);
    printf("%d\n",ret);
    return 0;
}


//strstr-查找字符串,在p1中找字符串p2
int main()
{
    char* p1="abcdef";
    char* p2="def";
    chaar* ret=strstr(p1,p2);
    if(ret==NULL)
    {
        printf("子串不存在\n");
    }
    else
    {
        printf("%s\n",ret);
    }
    return 0;
}

//strstr模拟实现
char* my_strstr(const char* p1,const char* p2)
{
    assert(p1!=NULL);
    assert(p2!=NULL);
    char* s1=NULL;
    char* s2=NULL;
    char* cur=(char*)p1;
    if(*p2=='\0')
    {
        return (char*)p1;
    }
    while(*cur)
    {
        s1=cur;
        s2=(char*)p2;
        while((*s1!='\0')&&(*s2!='\0')&&(*s1==*s2))
        {
            s1++;
            s2++;
        }
        if(*s2=='\0')
        {
            return cur;//找到子串
        }
        if(*s1=='\0')
        {
            return NULL;
        }
        cur++;
    }
    return NULL;//找不到子串
}
int main()
{
    char* p1="abcdef";
    char* p2="def";
    chaar* ret=my_strstr(p1,p2);
    if(ret==NULL)
    {
        printf("子串不存在\n");
    }
    else
    {
        printf("%s\n",ret);
    }
    return 0;
}
