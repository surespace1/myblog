<h1>C语言</h1>
<h2>计算机的内存</h2>
<p>　　‍</p>
<ol>
<li>计算机的内存</li>
</ol>
<p>　　1TB=1024GB</p>
<p>　　1GB=1024MB</p>
<p>　　1MB=1024KB</p>
<p>　　1KB=1024B（Byte字节）</p>
<p>　　1B=8bit（比特）</p>
<p>　　‍</p>
<ol start="2">
<li>内存地址的定义</li>
</ol>
<p>　　为了有效的管理和使用计算机的内存，把内存空间划分为一个个小的内存单元，每个内存但与的大小是1字节，为了能够方便访问到内存的每个单元，我们就给内存单元进行了编号，这些编号也就是内存单元的地址。</p>
<p><img src="assets/image-20260309211259-72xdd66.png" alt="image" /></p>
<p>　　比特单位太小了，所以内存编号为字节</p>
<h2>变量和常量</h2>
<ol start="3">
<li>基本的数据类型</li>
</ol>
<p><img src="assets/image-20260309212228-9fna5ga.png" alt="image" title="基本数据类型" /></p>
<p>　　‍</p>
<ol start="4">
<li>变量的定义</li>
</ol>
<p>　　变量相当于内存种一共数据存储空间的表示，你可以把变量看作一共房间的门牌号，通过门牌号可以找到房间，从而通过变量名访问到变量值。</p>
<p><img src="assets/image-20260309213449-gp8duu7.png" alt="image" /></p>
<p>　　‍</p>
<ol start="5">
<li>变量的命名规则</li>
</ol>
<p>　　变量名只能由字母、数字和下划线组成，但是变量名不能以数字开头</p>
<p>　　变量名区分大小写</p>
<p>　　变量名不能是C语言的关键字</p>
<p>　　‍</p>
<ol start="6">
<li>变量的定义和初始化</li>
</ol>
<p>　　方法一：</p>
<pre><code class="language-c">int age; //定义整型变量
char eva; //定义字符型变量
age = 24; //将变量赋值为24
eva = &quot;A&quot;; //将变量赋值为字符“A”
</code></pre>
<p>　　方法二：</p>
<pre><code class="language-c">int age = 24; //定义整型变量age并赋值
char eva = 'A'; //定义字符型变量并赋值
</code></pre>
<p>　　方法三：</p>
<pre><code class="language-c">double height,weight;
height = 180.5;
weight = 75.5;
</code></pre>
<p>　　方法四：</p>
<pre><code class="language-c">double height = 180.5, weight = 75.5;
</code></pre>
<p>　　方法五：</p>
<pre><code class="language-c">double height = 180.5, weight;
weight = 75.5;
</code></pre>
<p>　　‍</p>
<ol start="7">
<li>分号与注释</li>
</ol>
<p>　　在C语言中分号表示这个语句结束</p>
<p>　　单行注释：以<code>//</code>开头</p>
<p>　　多行注释：以<code>/*</code>​开头，以<code>*/</code>结尾。</p>
<p><img src="assets/image-20260309215927-yzqbt4c.png" alt="image" /></p>
<p>　　‍</p>
<ol start="8">
<li>常量</li>
</ol>
<p>　　常量是指在程序执行过程中其值不会改变的标识符或数值。</p>
<p>　　​<code>define</code>：用于定义标识符常量</p>
<pre><code class="language-c">#define PI 3.14 //define定义标识符常量，注意：这里不用加分号
double circle_area(){
  double r = 3.0; //定义浮点型变量r存储元的半径
  double S = PI * r * r; //定义浮点型变量S存储园的面积
  return S; 
}
</code></pre>
<p>　　‍</p>
<h2>输入与输出</h2>
<ol start="9">
<li>scanf函数输入</li>
</ol>
<p>　　在C语言中，<code>&amp;</code>​是取地址运算符，用于获取变量的地址。当变量在前面使用<code>&amp;</code>时，就会返回该变量在内存的地址。</p>
<p>　　占位符：告诉计算机这个未知的数据类型</p>
<table>
<thead>
<tr>
<th>数据类型</th>
<th>占位符</th>
</tr>
</thead>
<tbody>
<tr>
<td>int</td>
<td>%d</td>
</tr>
<tr>
<td>char</td>
<td>%c</td>
</tr>
<tr>
<td>float</td>
<td>%f</td>
</tr>
<tr>
<td>double</td>
<td>%if</td>
</tr>
</tbody>
</table>
<p>　　注意：（1）使用scanf函数为变量赋值前，需要先定义初始变量，初始化不初始化均可；（2）使用scanf函数为整型、字符型、浮点型变量赋需要在变量名前加取地址符<code>&amp;</code>；（3）占位符和变量的个数与类型一一对应。</p>
<p>　　取地址符示意：</p>
<pre><code class="language-c">int a = 0;
int *p = &amp;a; //取变量a的地址存放到整型指针变量p中
</code></pre>
<p>　　scanf函数为单个变量赋值时：</p>
<pre><code class="language-c">int age;
scanf(&quot;%d&quot;, &amp;age); // 使用scanf函数输入数据，为age变量赋值
</code></pre>
<p>　　scanf函数为多个变量赋值时：</p>
<pre><code class="language-c">int a;
float b;
char c;
scanf(&quot;%d%f%c&quot;,&amp;a,&amp;b,&amp;c);
</code></pre>
<ol start="10">
<li>printf函数输出</li>
</ol>
<p>　　使用printf函数打印整型、字符型、浮点型变量时，不需要再变量名前加取地址符<code>&amp;</code>。</p>
<p>　　占位符和变量的个数与类型一一对应。</p>
<pre><code class="language-c">printf(&quot;我要摆烂，我要打游戏！&quot;)
</code></pre>
<pre><code class="language-c">int age = 24;
flaot weight = 75.0;
char eva = 'A';
print(&quot;小白%d岁了，体重为%f,评价是%c.&quot;);
</code></pre>
<h2>运算符</h2>
<ol start="11">
<li>算数运算符</li>
</ol>
<table>
<thead>
<tr>
<th align="center">算数运算符</th>
<th>说明</th>
<th align="center">使用示例</th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">+</td>
<td>加法</td>
<td align="center">a+b=5</td>
</tr>
<tr>
<td align="center">-</td>
<td>减法</td>
<td align="center">a-b=1</td>
</tr>
<tr>
<td align="center">*</td>
<td>乘法</td>
<td align="center">a*b=6</td>
</tr>
<tr>
<td align="center">/</td>
<td>除法</td>
<td align="center">a/b=1</td>
</tr>
<tr>
<td align="center">%</td>
<td>取余</td>
<td align="center">a%b=1</td>
</tr>
</tbody>
</table>
<p>　　（1）运算符也叫做操作符，表格中的a和b也叫做操作数。</p>
<p>　　（2）当两个操作数都是整型时，其运算结果也为整型，如果结果是小数，则直接舍去小数部分，而不是四舍五入，例如a=2,b=3,a/b=1</p>
<p>　　（3）当操作数有一个为浮点型时，则运算结果为浮点型。</p>
<p>　　（4）取余运算的操作数只能是整型，因为浮点型没有余额。</p>
<p>　　‍</p>
<ol start="12">
<li>赋值运算符</li>
</ol>
<pre><code class="language-c">int a = 3;
</code></pre>
<table>
<thead>
<tr>
<th>赋值运算符</th>
<th>使用示例</th>
<th>说明</th>
<th>变量a的结果</th>
</tr>
</thead>
<tbody>
<tr>
<td>=</td>
<td>a=5;</td>
<td>把右边的值赋给左边的</td>
<td>5</td>
</tr>
<tr>
<td>+=</td>
<td>a+=5;</td>
<td>a=a+5</td>
<td>8</td>
</tr>
<tr>
<td>-=</td>
<td>a-=5；</td>
<td>a=a-5</td>
<td>-2</td>
</tr>
<tr>
<td>*=</td>
<td>a*=5；</td>
<td>a=a*5</td>
<td>15</td>
</tr>
<tr>
<td>/=</td>
<td>a/=5；</td>
<td>a=a/5</td>
<td>0</td>
</tr>
<tr>
<td>%=</td>
<td>a%=5</td>
<td>a=a%5</td>
<td>3</td>
</tr>
</tbody>
</table>
<p>　　（1）C语言中的=是赋值符号，其具有方向性</p>
<p>　　（2）不允许连续赋值。错误方式：<code>int x=y=1;</code>​ 正确方式：<code>int x=1,y=1;</code></p>
<p>　　（3）假设a=3,b=2,执行a=b+3后，b没有改变。</p>
<p>　　‍</p>
<ol start="13">
<li>关系运算符</li>
</ol>
<pre><code class="language-c">int a=3, b=2;
</code></pre>
<table>
<thead>
<tr>
<th>关系运算符</th>
<th>使用示例</th>
<th>说明</th>
<th>表达式真假</th>
</tr>
</thead>
<tbody>
<tr>
<td>&gt;</td>
<td></td>
<td></td>
<td>真</td>
</tr>
<tr>
<td>&gt;=</td>
<td></td>
<td></td>
<td>真</td>
</tr>
<tr>
<td>&lt;</td>
<td></td>
<td></td>
<td>假</td>
</tr>
<tr>
<td>&lt;=</td>
<td></td>
<td></td>
<td>假</td>
</tr>
<tr>
<td>==</td>
<td></td>
<td></td>
<td>假</td>
</tr>
<tr>
<td>!=</td>
<td></td>
<td></td>
<td>真</td>
</tr>
</tbody>
</table>
<p>　　表达式的结果为真则返回1，结果为假则返回0.</p>
<p>　　‍</p>
<ol start="14">
<li>逻辑运算符</li>
</ol>
<table>
<thead>
<tr>
<th>逻辑运算符</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr>
<td>​<code>&amp;&amp;</code></td>
<td>逻辑与（并且）</td>
</tr>
<tr>
<td>​<code>||</code></td>
<td>逻辑或（或者）</td>
</tr>
<tr>
<td>​<code>！</code></td>
<td>逻辑非（反过来）</td>
</tr>
</tbody>
</table>
<p>　　‍</p>
<table>
<thead>
<tr>
<th>a</th>
<th>b</th>
<th>​<code>a&amp;&amp;b</code></th>
<th>​<code>a||b</code></th>
<th>​<code>!a</code></th>
<th>​<code>!b</code></th>
</tr>
</thead>
<tbody>
<tr>
<td>真</td>
<td>真</td>
<td>真</td>
<td>真</td>
<td>假</td>
<td>假</td>
</tr>
<tr>
<td>真</td>
<td>假</td>
<td>假</td>
<td>真</td>
<td>假</td>
<td>真</td>
</tr>
<tr>
<td>假</td>
<td>真</td>
<td>假</td>
<td>真</td>
<td>真</td>
<td>假</td>
</tr>
<tr>
<td>假</td>
<td>假</td>
<td>假</td>
<td>假</td>
<td>真</td>
<td>真</td>
</tr>
</tbody>
</table>
<p>　　（1）C语言中表达式或者变量值如果非0代表为真，0代表为假。</p>
<p>　　（2）表达式的结果为真则返回1，结果为假则返回0.</p>
<p>　　（3）假设有三个整型变量a,b,c，想要判断三个变量是否相等。</p>
<p>　　        错误方式：<code>a==b==c</code></p>
<p>　　        正确方式：<code>(a==b)&amp;&amp;(b==c)</code></p>
<p>　　‍</p>
<ol start="15">
<li>自增运算符和自减运算符</li>
</ol>
<p>　　​<code>++</code>：自增运算符。用于将变量的值增加1.</p>
<p>　　前置++：++i，先让变量i自增1，再使用。</p>
<p>　　后置++：i++，先使用变量i，再让i自增1.</p>
<pre><code class="language-c">int i =0, x,y;
x = ++ i;
y = i ++;
</code></pre>
<p>　　​<code>--</code>：自减运算符。用于将变量的值减去1。</p>
<p>　　前置--举例：--j,先让变量j自减1，再使用。</p>
<p>　　后置--：j--，先使用变量j，再让j自减1.</p>
<p>　　Tips：遇到自增或自减运算符就从左往右看，先看到+或者-，就是要先自增或先自减，先看到变量名就是先使用。自减运算符执行逻辑与自增运算符执行逻辑相同，就不再举例。</p>
<p>　　‍</p>
<ol start="16">
<li>其它运算符</li>
</ol>
<p>　　​<code>&amp;</code>：取地址运算符，用于获取变量的地址</p>
<p>　　在变量前使用<code>&amp;</code>时，它就会返回改变量在内存的地址。</p>
<pre><code class="language-c">int a = 0;
int *p = &amp;a; // 取变量a的地址存放到整型指针变量p中
</code></pre>
<p>　　​<code>sizeof()</code>：用于计算括号内变量或数据类型所占字节数。</p>
<pre><code class="language-c">int a = 0;
print(&quot;%d&quot;,sizeof(a)); //打印变量a所占字节数
</code></pre>
<p>　　​<code>表达式1？表达式2：表达式3；</code></p>
<p>　　条件运算符：若表达式1为真，则执行表达式2；若表达式1为假，则执行表达式3.</p>
<pre><code class="language-c">int a=5,b=3;
int max; //定义变量max记录a和b中较大值
a&gt;b?(max=a):(max=b); //条件运算符比较较大值
</code></pre>
<p>　　‍</p>
<ol start="17">
<li>运算符优先级</li>
</ol>
<p><img src="assets/image-20260311102904-0xfcuar.png" alt="image" /></p>
<h2>条件判断语句</h2>
<ol start="18">
<li>if语句</li>
</ol>
<p><img src="assets/image-20260311103152-w7pb31o.png" alt="image" /></p>
<p>　　tips：（1）<code>{}</code>的作用是将多条语句组成一个代码块。（2）C语言中的缩进是一种代码书写风。（3）if语句执行规则：当表示式为真时，执行代码块中所有代码，当表达式为假时，if语句执行结束。</p>
<pre><code class="language-c">int main() {
    int score;
    printf(&quot;请输入你的数据结构成绩:&quot;);
    scanf(&quot;%d&quot;,&amp;score);
    if (score&gt;100) {
        printf(&quot;你简直是天才！&quot;);
    }
    return 0;
}
</code></pre>
<p>　　‍</p>
<p>　　‍</p>
<ol start="19">
<li>if else语句</li>
</ol>
<p><img src="assets/image-20260311110811-mpi8vj7.png" alt="image" /></p>
<p>　　Tips：当表达式为真时，执行语句1所在代码块内所有代码，当表达式为假时，执行语句2所在代码块内所有代码。</p>
<p>　　‍</p>
<ol start="20">
<li>if else if else语句</li>
</ol>
<p><img src="assets/image-20260311111203-kflurzq.png" alt="image" /></p>
<p><img src="assets/image-20260311111154-tggds4s.png" alt="image" /></p>
<p>　　Tips：当表达式1为真时，执行语句1所在代码块内所有代码；当表达式2为真时，执行语句2所在代码块内所有代码；其它情况执行语句3所在代码块内所有代码。<br />
else if可以有多个。</p>
<p>　　‍</p>
<ol start="21">
<li>嵌套if语句示例</li>
</ol>
<p>　　Tips：如果条件判断语句代码块只有一个条件判断语句或者只有一个循环语句也算一句代码，同样可以省略0。</p>
<p><img src="assets/image-20260311111645-o33xch0.png" alt="image" /></p>
<ol start="22">
<li>switch case语句</li>
</ol>
<pre><code class="language-c">int main(){
  int input;
  scanf(&quot;%d&quot;,&amp;input);
  switch(input){
    case 1:
        printf(&quot;你输入的是1&quot;)；
        break;
    case 2:
        printf(&quot;你输入的是2&quot;)；
        break;
    default:
        printf(&quot;你输入是个啥？&quot;)
  }

}
</code></pre>
<p>　　​<code>break</code>​：跳出<code>switch case</code>语句。</p>
<p>　　‍</p>
<h2>循环语句</h2>
<ol start="23">
<li>while循环</li>
</ol>
<p><img src="assets/image-20260311135221-ghx19m4.png" alt="image" /></p>
<p>　　当表达式为真时，执行花括号内循环体代码，执行完成后再次判断表达式真假，如果为真，则继续重复此过程，直到表达式为假，才可跳出此过程。</p>
<pre><code class="language-c">void print1_1000(){
  int i=1;
  while(i&lt;=1000){
    printf(&quot;%d&quot;, i);
    i++；
  }
}
</code></pre>
<p>　　注意：while循环内需要更新循环变量的值，否则可能会出现死循环的情况。</p>
<p>　　‍</p>
<ol start="24">
<li>while循环中的break和continue</li>
</ol>
<p>　　break的作用：直接结束整个while循环。</p>
<pre><code class="language-c">void print_1_1000(){
  int i = 1;
  while (1){ // 一直执行循环体代码
    printf(&quot;%d&quot;,i); 
    if (i==1000){
      break; //若i为1000，则跳出循环
    }
    else{
      i ++; 
    }
  }
 }
</code></pre>
<p>　　continue的作用：结束本次while循环，本次循环continue及后面的循环体代码不在执行，直到跳转到判断表达式。</p>
<pre><code class="language-c">void print_1_1000(){
  int i = 1;
  while(i&lt;=1000){
    if (i==500){
      i ++;
      continue; // 若i=500，则跳过本次循环。
    }
    printf(&quot;%d&quot;, i);
    i++;
  } 
}
</code></pre>
<p>　　‍</p>
<ol start="25">
<li>for循环</li>
</ol>
<p><img src="assets/image-20260311141852-1y007k0.png" alt="image" /></p>
<p>　　Tips：先执行表达式1的代码，初始化循环变量，然后判断表达式2是否为真，如果为真，则执行花括号内循环体代码，执行完成后执行表达式3的代码，更新循环变量，然后再次执行表达式2，判断表达式真假，如果为真，则继续重复此过程，直到表达式为假，才可跳出for循环。</p>
<pre><code class="language-c">// 在屏幕上打印整数1-1000.

void print_1_1000(){
  for (int i=1; i&lt;=1000: ++i){
    printf(&quot;%d&quot;,i); // 打印i的值
  }
}
</code></pre>
<p>　　Tips:1.表达式3那里的i++和++i没有区别。2.表达式1所定义的循环变量只能在该for循环内使用，出了for循环，该循环变量就不能用了。3.for循环的表达式3就是用来更新循环变量的，所以在循环体内，尽量不要改变循环变量，否则可能会导致逻辑出问题。</p>
<pre><code class="language-c">void print_1_1000(){
  int i=1;
  for (; i&lt;=1000: ++i){
    printf(&quot;%d&quot;,i); // 打印i的值
  }
}
</code></pre>
<p>　　若for循环不需要初始化，则表达式1可以省略，但分号不能省略。</p>
<pre><code class="language-c">void add1_1000{ //计算1+2+.+100
  int i,j,sum=0;
  for(i=1,j=100;i&lt;=50&amp;&amp;j&gt;=51;i++,j--){
      sum=sum+i;
      sum=sum+j;
      printf(&quot;%d&quot;,sum);
}
</code></pre>
<p>　　for循环可以有多个循环变量，循环变量的初始化和更新代码可以有多个，用逗号隔开。</p>
<p>　　‍</p>
<ol start="26">
<li>for循环中的break和continue</li>
</ol>
<p>　　break的作用：直接结束整个for循环</p>
<pre><code class="language-c">void print(){//打印整数1到10
  for(int i=1;i&lt;=1000;i++){
      printf(&quot;%d&quot;,i);/打印i的值
      if(i==10）{//若i为10，则直接跳出for循环
          break;
      }
  }
}
</code></pre>
<p>　　contiune的作用：结束本次for循环，本次循环continue及后面的循环体代码不再执行，直接跳转到表达式3，更新循环变量。</p>
<pre><code class="language-c">void print1_10000(){//打印整数1到1000，缺少500
  for(int i=1;i&lt;=1000;i++){
    if(i==500）{//若i为500，则直接跳过此次循环
        continue;
    }
    printf(&quot;%d&quot;,i);//打印i的值
  }
}
</code></pre>
<p>　　‍</p>
<p>　　27.省略花括号的示例</p>
<pre><code class="language-c">void print(){
  int i=1;
  while(i&lt;=10)//打印整数1到10
    printf(&quot;%d&quot;,i++);//打印i的值并更新i
  for(intj=1;j&lt;=10;j++)//打印整数1到10
    printf(&quot;%d&quot;j）;//打印j的值
  for(int k=1;k&lt;=10;k++)//打印1到10中的偶数
    if(k%2==0)
      printf(&quot;%d &quot;,k);
}
</code></pre>
<p>　　Tips：如果循环语句的循环体只有一句代码，那该循环体的<code>{}</code>​可以省略。<br />
一个条件判断语句（if-else)或者一个循环语句（while、for）也算一句代码，可以省略<code>{}</code>。</p>
<p>　　‍</p>
<ol start="28">
<li>do while循环示例</li>
</ol>
<pre><code class="language-c">void print1_10000(){
  int i=1;//定义了循环变量i并初始化为1
  do{
    printf（&quot;%d&quot;,i);//打印i的值
    i++;//更新循环变量的值
   }while(i&lt;=1000);
}
</code></pre>
<p>　　Tips：dowhile循环至少执行一次循环体。</p>
<p>　　考研数据结构中从未见过dowhile的使用，可不用掌握。</p>
<p>　　‍</p>
<h2>指针</h2>
<ol start="29">
<li>指针的基本概念</li>
</ol>
<p>　　指针：指针就是地址，通常所说的指针是指指针变量，也就是保存地址的变量。</p>
<pre><code class="language-c">int main(){
  int a; 
  char c;
  int* p = &amp;a;
  char*  q = &amp;c;
  return 0;
}
</code></pre>
<p><img src="assets/image-20260311145958-1cycy7t.png" alt="image" /></p>
<p>　　指针变量保存的是地址。在32位系统中，指针变量大小是4字节，在64位系统中，指针变量大小是8字节。</p>
<p>　　指针变量区分类型的原因是，不同类型指针变量访问内存空间权限不足，整型指针可以访问4个字节，字符型指针可以访问1个字节。</p>
<pre><code class="language-c">int main(){
  int age=24;//定义整型变量age
  char eva='A';//定义字符型变量eva
  int* p=&amp;age;//定义整型指针p
  char* q=&amp;eva;//定义字符型指针q
  *p=25;//将age更新为25
  printf(&quot;age=%d, eva=%c&quot;,*p,*q);
  return O;
}
</code></pre>
<p><img src="assets/image-20260311150942-kqesxt0.png" alt="image" /></p>
<p>　　Tips:<br />
1.指针p记录了变量age的地址，指针q记录了变量eva的地址，就可以说，指针p指向了age，指针q指向了eva。<br />
2.指针就是地址，<em>就好比钥匙，带着钥匙顺着地址就能打开变量的门，也就是可以查看变量值或者改变其值。上图代码中的</em>p就可以看作是变量age，*q就可以看作是变量eva。</p>
<p>　　‍</p>
<ol start="30">
<li>定义指针</li>
</ol>
<p>　　定义指针变量有如下两种方式，两种方式执行逻辑上没有区别，但是各有优缺点。</p>
<p>　　方式一：<code>int* p</code>​ <em>;//</em> 在数据类型后面</p>
<p>　　优点：符合基本数据类型变量的定义习惯，前面是数据类型，后面是变量名，此种方式看起来逻辑清晰。</p>
<p>　　缺点：当定义同一类型的多个指针变量时，容易误写成int<em>p,q,r;需要注意，此句代码定义的p为整型指针变量，q和r都是整型变量，也就是说，</em> 虽然在int后面，但它只会和相邻的p结合，而q和r没有被<em>影响。</em></p>
<p>　　<em>方式二：<em>​</em>​<code>int *p</code>​</em>​;//<em>在变量名前面</em></p>
<p>　　<em>优点：当定义同一类型的多个指针变量时，不容易写错，int</em>p,<em>q,</em> r;这就是定义了p,q,r三个整型指针变量。</p>
<p>　　缺点：不符合基本数据类型变量的定义习惯，此种方式看起来容易误以为*p是变量名，看起来逻辑不清晰。</p>
<p>　　‍</p>
<ol start="31">
<li>malloc函数和free函数</li>
</ol>
<p>　　malloc函数：动态分配指定大小的内存空间 <code>（强制转换起始地址类型）malloc（分配内存空间大小）</code></p>
<p>　　free函数：释放动态分配的内存空间  <code>free（释放内存空间地址）</code></p>
<pre><code class="language-c">int main(){
  int a=0;//静态分配内存，系统自动为变量a申请4个字节内存
  int *p=NULL;//定义整型指针p并初始化
  p=（int*) malloc(sizeof(int);//动态分配4个字节的内存
  *p=3;//为p指向的内存空间赋值
  printf(&quot;p指向地址存储数据为%d&quot;,*p);
  free(p);//释放指针p指向的内存空间
  p=(int*)malloc(sizeof(int)*10);//动态分配10个整型变量内存
  free(p);//释放指针p指向的内存空间
  return O;
}
</code></pre>
<p>　　sizeofO：用于计算括号内变量或数据类型所占字节数。</p>
<p>　　执行<code>free(p)；</code>后，只是把指针p指向的内存空间释放了，而指针p并没有消失，只是此时指针p存储的地址没有意义了，但是指针p可以继续使用。</p>
<h2>数组</h2>
<p>　　‍</p>
<ol start="32">
<li>数组的概念</li>
</ol>
<p>　　数组：用来存储相同类型元素得到集合</p>
<pre><code class="language-c">int main(){
    int score[10];//定义整型数组score
    score[0]=150;//为数组下标0元素赋值
    for(int i=0;i&lt;10;i++){//为数组赋值
        scanf(&quot;%d&quot;,&amp;score[i]);
    }
    for(inti=0;i&lt;10;i++）{//打印数组中元素
        printf(&quot;%d &quot;,score[i]);
    }
return O;
}
</code></pre>
<p><img src="assets/image-20260312121030-xuispcl.png" alt="image" /></p>
<p>　　数组中的各个元素在内存中是连续存储的，第一个元素在低地址，最后一共元素在高地址。</p>
<p>　　在描述数组中的元素所在的位置时，通常有两种描述方式。</p>
<ul>
<li>方式一：第几个。此种方式从1开始。</li>
<li>方式二：下标为几。此种方式从下标0开始。</li>
</ul>
<p>　　第一个for循环是在循环内部定义的循环变量i,所有for循环结束，i就没了，因此，第二个for循环依旧可以再次定义循环变量i。</p>
<p>　　‍</p>
<ol start="33">
<li>数组的定义</li>
</ol>
<p>　　方式一：静态定义数组</p>
<p>　　​<code>数据类型 数组名[元素个数];</code></p>
<p>　　方式二：动态定义数组</p>
<p>　　​<code>(指针类型)malloc(sizeof(数据类型)*元素个数);</code></p>
<pre><code class="language-c">#define MAXSIZE 100
int main(){
    int A[10];//静态定义数组A
    int n;//定义整型变量n，记录数组B元素个数
    scanf(&quot;%d&quot;，&amp;n）;//输入数组B元素个数
    int* B=(int *)malloc(sizeof(int)*n);//动态定义数组B
    char C[MAXSIZE];//静态定义数组C
    for(int i=0;i&lt;10;i++){//初始化数组A
        A[i]=i;
    }
    free(B);
    return O;
}
</code></pre>
<p>　　当知道元素个数时，采用静态定义数组；</p>
<p>　　当不知道元素个数时，采用动态定义数组。</p>
<p><img src="assets/image-20260312121924-cnes2p2.png" alt="image" /></p>
<p>　　‍</p>
<ol start="34">
<li>数组的初始化</li>
</ol>
<p>　　数组初始化是指在创建数组的同时给数组中的元素赋初始值。</p>
<pre><code class="language-c">int main(){
    int A[10];//直接定义整型数组A，不初始化
    char B[3]={'A'，'B'，'C'}；//定义字符型数组B，全部初始化
    int C[10]={0};//定义整型数组C，并全部初始化为0
    int D[10]={0,1,2};//定义整型数组D，部分初始化
    int E[]={0,1,2};//定义整型数组E，全部初始化
    return O;
}
</code></pre>
<p><img src="assets/image-20260312122613-20w59wb.png" alt="image" /></p>
<ol start="35">
<li>变长数组</li>
</ol>
<p>　　在C99标准前定义数组时，口中必须是一个常量，不能使用变量。</p>
<p>　　在C99标准后定义数组时，口允许使用变量了，但不允许初始化。</p>
<pre><code class="language-c">int main(){
    int A[10]={0};//定义整型数组A并初始化
    int n=10;//定义整型变量n，初始化为10
    int B[n];//定义整型数组B，此种定义方式不能初始化
    for（int i=O;i&lt;n;i++){//数组B初始化
        B[i]=0;
    }
    return O;
}
</code></pre>
<p>　　‍</p>
<ol start="36">
<li>字符数组</li>
</ol>
<p>　　字符数组不仅可以存储一个个的单个字符，还可以存储字符串。</p>
<pre><code class="language-c">int main(){
    char A[4]={a，h，u，i};//定义字符型数组A并初始化
    char B[5]=&quot;ahui&quot;;//定义字符型数组B并初始化
    char C[5];//定义字符型数组C
    scanf(&quot;%s&quot;，C);//为数组C赋值字符串
    for（inti=0;i&lt;4;i++）{//打印数组A中的元素值
        printf(&quot;%c&quot;,A[i]);
    }
    printf(&quot;%s&quot;,B);//打印数组B中的元素值
    printf(&quot;%s&quot;,C);//打印数组C中的元素值return O;
}
</code></pre>
<p><img src="assets/image-20260312141217-gxb1vbq.png" alt="image" /></p>
<p>　　字符数组存储字符串时，字符串后面默认跟一个'0'作为字符串的结束符。</p>
<p>　　字符串的占位符为%s。</p>
<p>　　数组名就是数组的地址，所以scanf为数组赋值字符串时，后面不用取地址符，直接写数组名即可，但是在为数组中单个元素赋值时，需要加取地址符，如下所示：</p>
<pre><code class="language-c">scanf(&quot;%s&quot;, C);
scanf(&quot;%c&quot;, &amp;A[0]);
</code></pre>
<p>　　‍</p>
<ol start="37">
<li>二维数组</li>
</ol>
<pre><code class="language-c">int main(){
    int A[3][5];//定义3行5列二维数组A
    for（inti=0;i&lt;3;i++){//初始化二维数组A
        for(int j=0;j&lt;5;j++){
            scanf(&quot;%d&quot;,&amp;A[i][j]);
        }
    }
    for(inti=0;i&lt;3;i++){//遍历二维数组A
        for(int j=0;j&lt;5;j++){
            printf(&quot;%d &quot;,A[i][j]);
        }
    }
    return 0;
}
</code></pre>
<p><img src="assets/image-20260312142441-h3nx498.png" alt="image" /></p>
<p>　　1.二维数组在内存中是连续存储的，但我们为了更直观的理解其存储逻辑，就把它画成3行5列的样子。</p>
<p>　　2.对于二维数组A[j][U]，前面的i是行下标，后面的是列下标。辅助记忆方法：线性代数中学过行列式，所以前面是行，后面是列。</p>
<h2>结构体</h2>
<ol start="38">
<li>结构体的定义</li>
</ol>
<p>　　结构体是一种自定义的数据类型，可以包含不同的数据成员</p>
<pre><code class="language-c">struct student{
    char name[20];//记录学生姓名
    int age;//记录学生年龄
    float weight;//记录学生体重
    int score;//记录学生分数
};
</code></pre>
<pre><code class="language-c">struct student{
    char name[20];//记录学生姓名
    int age;//记录学生年龄
    float weight;//记录学生体重
    int score;//记录学生分数
}a; //声明结构体并定义结构体变量a
</code></pre>
<p>　　结构体里面的内容叫做结构体的成员变量，这些成员可以是不同的数据类型，如整型、浮点型、字符、其它结构体或数组。</p>
<p>　　结构体就相当于自己所定义的一种新的数据类型，上述代码所定义的结构体名字是<code>struct student</code>​，或者说这种新的数据类型是<code>struct student</code>.</p>
<p>　　使用该数据类型定义一共结构体变量，那该结构体变量将包含结构体里的各个成员变量。</p>
<p>　　结构体最后不要忘记分号。</p>
<p>　　‍</p>
<ol start="39">
<li>typedf的使用</li>
</ol>
<p>　　typedef可以为数据类型起一个新名字。</p>
<p>　　使用方法：<code>typedef 原类型名 新类型名;</code></p>
<pre><code class="language-c">typedef struct student {
    char name[20];//记录学生姓名
    int age;//记录学生年龄
    float weight;//记录学生体重
    int score;//记录学生分数
}stu,*stup;
</code></pre>
<p><img src="assets/image-20260312145235-e3ekat4.png" alt="image" /></p>
<p>　　‍</p>
<ol start="40">
<li>结构体的使用</li>
</ol>
<pre><code class="language-c">typedef struct student{
    char name[20];//记录学生姓名
    int age;//记录学生年龄
    float weight;//记录学生体重
    int score;//记录学生分数
}stu,*stup;
</code></pre>
<pre><code class="language-c">int main {
  stu a;//定义结构体变量a
  stup b;//定义结构体指针b
  b=(stup)malloc(sizeof(stu);//创建结构体b
  scanf(&quot;%s&quot;，a.name);//为a中name成员赋值
  a.age=24;//为a中age成员赋值
  a.weight=75.5;//为a中weight成员赋值
  a.score=150;//为a中score成员赋值
  printf(&quot;%s %d %f %d&quot;,a.name,a.age,a. weight,a.score);
  scanf(&quot;%s&quot;，b-&gt;name);//为b中name成员赋值
  b-&gt;age=25;//为b中age成员赋值
  printf(&quot;%s的年龄为%d&quot;,b-&gt;name,b-&gt;age);
  return O;
}
</code></pre>
<p>　　Tips:</p>
<p>　　结构体变量访问结构体内成员需要使用点（<code>.</code>）。</p>
<p>　　结构体指针访问结构体内成员需要使用箭头（<code>-&gt;</code>）。</p>
<p>　　‍</p>
<p>　　‍</p>
<ol start="41">
<li>数据结构中的结构体实例</li>
</ol>
<pre><code class="language-c">#define MAXSIZE 100
typedef struct SqList{//顺序表结构体
    int data[MAXSIZE];
    int length;
}SqList:
</code></pre>
<pre><code class="language-c">#define MAXSIZE100

typedef struct{
    int data[MAXSIZE];
    int length;
}SqList;
</code></pre>
<pre><code class="language-c">typedef struct LNode{//链表结构体
    int data;
    struct LNode *next;
}LNode,*LinkList;
</code></pre>
<p>　　当结构体内含有本结构体成员时，原结构体不能省略，而且结构体指针成员也要写原结构体名，不能写别名。</p>
<p>　　因为此时typedef重命名操作还没有完成。</p>
<p>　　‍</p>
<h2>函数</h2>
<ol start="42">
<li>函数的定义</li>
</ol>
<p>　　函数：将一组能完成一个功能或多个功能的语句放在一起的代码结构。</p>
<pre><code class="language-c">double area(double a,double b){
    double S;
    S=a*b;
    return S;
}

int main(){
    double length,width;
    scanf(&quot;%lf %lf&quot;,&amp;length,&amp;width);
    double S=area(length,width);
    printf(&quot;长方形的面积为%lf。&quot;,S);
    return O;
}
</code></pre>
<p><img src="assets/image-20260312152530-az3ctr6.png" alt="image" /></p>
<p>　　函数命名的硬性规定：<br />
1.函数名只能由字母(A<sub>Z和a</sub>z)、数字(0~9)和下划线（_）组成。但是，函数名必须以字母或下划线开头，不能以数字开头。<br />
2.函数名区分大小写。例如：area和Area是两个不同的函数名。<br />
3.函数名不能是C语言的关键字。例如：int、float、char、struct等关键字不能作为函数名。</p>
<p>　　‍</p>
<ol start="43">
<li>函数的返回类型与返回值</li>
</ol>
<table>
<thead>
<tr>
<th>返回类型</th>
<th>返回值</th>
</tr>
</thead>
<tbody>
<tr>
<td>void</td>
<td>return;(也可省略此句代码)</td>
</tr>
<tr>
<td>int</td>
<td>return整型变量或整型值;</td>
</tr>
<tr>
<td>float</td>
<td>return单精度浮点型变量或浮点数;</td>
</tr>
<tr>
<td>double</td>
<td>return双精度浮点型变量或浮点数;</td>
</tr>
<tr>
<td>char</td>
<td>return字符型变量或单个字符;</td>
</tr>
<tr>
<td>bool</td>
<td>return true或false;</td>
</tr>
<tr>
<td>结构体类型</td>
<td>return结构体变量;</td>
</tr>
<tr>
<td>指针类型</td>
<td>return指针变量或NULL;</td>
</tr>
</tbody>
</table>
<pre><code class="language-c">void area(double a,double b) {
    double S;
    S=a*b;
    printf(&quot;长方形的面积为%lf。&quot;,S);
    return;//此行代码可省略
}
</code></pre>
<p>　　1.函数返回值的类型必须和函数的返回类型相匹配。<br />
2.如果函数没有返回值，则返回类型为void，返回值可以写return；或者直接省略不写返回值。<br />
3.执行return语句将直接结束本次函数的执行，并返回值，不再执行函数内的后续代码。</p>
<p>　　‍</p>
<ol start="44">
<li>函数的参数</li>
</ol>
<p>函数的参数分为形式参数（形参）和实际参数（实参）。<br />
形参是指定义函数时，小括号中的变量，右图代码area函数中的a和b即为形参。<br />
实参是指调用函数时，传给函数的参数，右图代码main函数中的length和width即为实参。</p>
<pre><code class="language-c">double area(double a,double b) {
    double S;
    S=a*b;
    return S;
}
int main(){
    double length=2.0,width=1.0;
    double S=area(length, width);
    printf(&quot;长方形的面积为%lf。&quot;,S);
    return O;
}
</code></pre>
<p>　　‍</p>
<p>　　1.形参写的是想要完成题目要求，题目需要提供给我们的东西。<br />
2.形参可以没有，也可以有多个，多个形参需要用逗号隔开。<br />
3.如果有形参需要写其数据类型和名字。<br />
4.调用函数方法：函数名(实参，…,实参）；示例：area(length,width);<br />
5.调用函数时写实参不需写明数据类型，但实参的数据类型，个<br />
数，顺序应与形参一致。</p>
<p>　　‍</p>
<ol start="45">
<li>主函数</li>
</ol>
<p>　　Tips:<br />
1.主函数是程序执行的起点，其函数名固定为main，返回类型固定为int，不需要写参数，主函数最后返回0代表其正常执行结束。<br />
2.考研数据结构代码一般来说只需写出满足题目要求的自定义函数即可，极少数院校会要求学生写完自定义函数后，再写主函数调用自定义函数。</p>
<p><img src="assets/image-20260312153853-j68s47d.png" alt="image" /></p>
<p>　　‍</p>
<p>　　‍</p>
