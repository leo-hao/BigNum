//equation.cpp
//
//Created by Leo on 17/1/29
//Copyright © 2017年 Leo. All rights reserved.
//  /Users/Leo/Documents/大二
#include<iostream>
#include<cstring>
#include<string>
using namespace std;
int comparechar(char & a, char & b)//比较字符串的一位数并相减
{
    if(a < b)
    {
        a = char( a + 10 );//借十
        a = char( a - (b - '0') );
    return -1;
    }
    else
    { a = char( a - (b - '0') );
        return 0;

    }
}

void comparestr(string & a, string & b, string &c)//比较两个字符串的长度，并不断比较每位数
{
    int i;
    int j;
    string temp;
    c = "+";
    if(a.length() < b.length())
    {
        temp = a;
        a = b;
        b = temp;
        c = "-";
    }
    if(a.length() == b.length() && a < b)
    {
        temp = a;
        a = b;
        b = temp;
        c = "-";
    }

       for( i = a.size()-1,  j = b.size()-1; j >= 0; i--, j--)
    {
        int t;
        t = comparechar(a[i], b[j]);
        if(t == -1 && i > 0)
           {
               a[i-1]--;
           }
       
    }
    while(i > 0)//借
    {
        if(a[i] < '0')
        {
            a[i] = char (a[i] + 10);
            a[i-1]--;
        }
        i--;
    }
    int index = 0;
    for(i = 0; i < a.size(); i++)//去零
    {
        if(a[i] != '0')
            break;
        index++;
    }
    string s(a, index, a.size()-index);
    a = s;
    
}

int main(int argc, const char * argv[] ){

    string str1,str2,str3;
    str1 = argv[1];
    str2 = argv[2];
    //comparechar(, <#char &b#>)
    comparestr(str1, str2, str3);
    if(str3 == "-")
        cout << str3 + str1 <<endl;
    else
        cout << str1 <<endl;

    return 0;
    
}
