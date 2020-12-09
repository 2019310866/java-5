# java-5
Java实验5
## 实验目的
掌握字符串String及其方法的使用
掌握文件的读取/写入方法
掌握异常处理结构
## 实验内容
在某课上,学生要提交实验结果，该结果存储在一个文本文件A中。
文件A包括两部分内容：
一是学生的基本信息；
二是学生处理后的作业信息，该作业的业务逻辑内容是：利用已学的字符串处理知识编程完成《长恨歌》古诗的整理对齐工作，写出功能方法，实现如下功能：
每7个汉字加入一个标点符号，奇数时加“，”，偶数时加“。”
允许提供输入参数，统计古诗中某个字或词出现的次数
输入的文本来源于文本文件B读取，把处理好的结果写入到文本文件A
考虑操作中可能出现的异常，在程序中设计异常处理程序


## 实验过程
1 在eclipse创建class，利用println函数创建学生信息。
2 创建文本B将《长恨歌》放入其中。
3 在class中利用循环函数和字符串string将长恨歌对齐。
4 改错并运行。
## 核心方法
```
###一是学生的基本信息
package 实验5;

import java.io.*;
import java.util.Scanner;

public class Monixueshengzuoye {
    public static void main(String args[]) {
        @SuppressWarnings("resource")
		Scanner input = new Scanner(System.in);
        StringBuffer str2 = null;
        new Handle();
        StringBuffer str1 = Handle.Read();
        new Homework();
        str2 = Homework.HW(str1);
        Handle.Write(str2);

        System.out.println("请输入要查询的字符：");
        String z = input.next();
        Handle.getCharMaps(z,str1);

        System.out.println("******************学生信息*********************");
        Student hjh = new Student();
        hjh.setName("何佳航");
        hjh.setAge(20);
        hjh.setNumber(2019310866);
        hjh.setSex("男");
        System.out.println("学生姓名:" + hjh.getName());
        System.out.println("学生年龄:" + hjh.getAge());
        System.out.println("学生编号:" + hjh.getNumber());
        System.out.println("学生性别:" + hjh.getSex());

        System.out.println("作业处理完成");
        System.out.println(z + "出现的次数为："+ z + "次");
    }
}


class Student{
    public Student(){

    }
    public Student(String name,int age,int number,String sex){
        this.name = name;
        this.age = age;
        this.number = number;
        this.sex = sex;
    }

    private String name;
    private int age;
    private int number;
    private String sex;

    public String getName() {
        return name;
    }
    public int getAge() {
        return age;
    }
    public String getSex() {
        return sex;
    }
    public int getNumber() {
        return number;
    }
    public void setName(String name) {
        this.name = name;
    }
    public void setAge(int age) {
        this.age = age;
    }
    public void setNumber(int number) {
        this.number = number;
    }
    public void setSex(String sex) {
        this.sex = sex;
    }

}
###二是学生处理后的作业信息
class Homework{
    public static StringBuffer HW(StringBuffer str1){
        StringBuffer str2 = new StringBuffer(str1);
        int j=0;int z;
        for(int i = 7;i < str2.length()-45;i= i+7){
            z = i +j;
            if(i%2 == 0){
                str2.insert(z,"。\n");
                j = j+2;
            }
            else{
                str2.insert(z,"，");
                j= j+1;
            }
        }
        System.out.println(str2);
        return str2;
    }

}

class Handle{
    public static StringBuffer Read(){
        String str1 = "";
        StringBuffer str2 = new StringBuffer(str1);
        try {
            File file = new File("C:/Users/14739/Desktop/B.txt");
            FileReader fr = new FileReader(file);
            BufferedReader bReader = new BufferedReader(fr);
            while ((str1 =bReader.readLine()) != null) {
                str2.append(str1);
            }
            fr.close();


        } catch (IOException e) {
            e.printStackTrace();
        }
        return  str2;
    }

    public static void Write(StringBuffer s){
        try{
            BufferedWriter bw = new BufferedWriter(new FileWriter("‪C:/Users/14739/Desktop/A.txt"));
            bw.write(s.toString());
            bw.close();
        }catch (IOException e){
        }
    }

    public static int getCharMaps(String z,StringBuffer s) {
        boolean p;
        int w = 0;
        String a = s.toString();
        char[] b = a.toCharArray();
        for (int i = 0; i < a.length(); i++) {
            String x = String.valueOf(b[i]);
            p = z.equals(x);
            if(p == true){
                w = w + 1;
            }

        }
        return w;
    }
}

 ```
 ## 实验结果
汉皇重色思倾国，御宇多年求不得。
杨家有女初长成，养在深闺人未识。
天生丽质难自弃，一朝选在君王侧。
回眸一笑百媚生，六宫粉黛无颜色。
春寒赐浴华清池，温泉水滑洗凝脂。
侍儿扶起娇无力，始是新承恩泽时。
云鬓花颜金步摇，芙蓉帐暖度春宵。
春宵苦短日高起，从此君王不早朝。
承欢侍宴无闲暇，春从春游夜专夜。
后宫佳丽三千人，三千宠爱在一身。
金屋妆成娇侍夜，玉楼宴罢醉和春。
姊妹弟兄皆列士，可怜光采生门户。
遂令天下父母心，不重生男重生女。
骊宫高处入青云，仙乐风飘处处闻。
缓歌慢舞凝丝竹，尽日君王看不足。
渔阳鼙鼓动地来，惊破霓裳羽衣曲。
九重城阙烟尘生，千乘万骑西南行。
<未完，待续>，
请输入要查询的字符：
3
******************学生信息*********************
学生姓名:何佳航
学生年龄:20
学生编号:2019310866
学生性别:男
作业处理完成
3出现的次数为：3次
## 实验感想
这个系统是我独立完成在这次的课程设计中，我学到的一个重要的经验，参考一些资料后使程序设计更加简单，设计代码时目标更加明确，效率更高，以前虽然也知道这些道理，但自己真正使用时出现在问题，学会利用循环函数，还有string函数，加深了印象，在实验中第一次输出结果为乱码，然后从网上寻找了一些解决方法并且成功的解决了问题，让我增加了对编程的兴趣。
