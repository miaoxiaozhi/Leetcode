剑指 Offer 05. 替换空格
请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

 

示例 1：

输入：s = "We are happy."
输出："We%20are%20happy."
 



方法一： string类里面的find()和replace()应用
class Solution {
public:
    string replaceSpace(string s) {

        int pos=0;

        while(true)
        {
            pos = s.find(' ');

            if(pos == -1)
            {
                return s;
            }
            else
            {
                s.replace(pos, 1, "%20");
            }
        }

        return s;

    }
};

方法二：双指针法
class Solution {
public:
    string replaceSpace(string s) {

       //指针法
       int count = 0; //记录空格的个数
       int oldsize = s.size();
       if(oldsize == 0) return s;
     for(int i=0; i<oldsize; i++)
     {
         if(s[i] == ' ')
         {
             count++;
         }
     }

     s.resize(oldsize+count*2);//扩充数组大小
     //重后往前遍历
      int i=s.size()-1,  j=oldsize-1;
      while( j<i)
     {
         if(s[j] !=' ')
         {
             s[i]  = s[j];
         }

         else
         {
             s[i] = '0';
             s[i-1] = '2';
             s[i-2] = '%';
             i = i-2;
         }
         j--;
         i--;
     }
     return s;
    }
};
