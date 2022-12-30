# 用Go语言实现Monkey解释器



在**命令行cmd**下运行`go run main.go`

即可进入Monkey语言。

```go
E:\monkey>go run main.go
Hello DESKTOP-EHVOK0M\Administrator! This is the Monkey programming language!
Feel free to type in commands
>> puts("Hello World!")
Hello World!
null
```
**实现功能展示**

- 最为简单的3种类型的输入输出。（1.整数字面量 2.布尔类型 3.空值）

```bash
>> 6
6
>> true
true
>>
>>
```

- 前缀表达式

```bash
>> -5
-5
>> -(-5)
5
>> !true
false
```

- 中缀表达式

```bash
>> 5+5
10
>> 2*5+1
11
>> (2+3+2)*2+1
15
```

- 条件语句

```bash
>> if (true) {return 10;}
10
>> if (false) {return 10;}else {return 66;}
66
```

- return语句

```bash
>> return 10
10
>> return "Hello"
Hello
```

- 错误处理

```bash
>> 5+
            __,__
   .--.  .-"     "-.  .--.
  / .. \/  .-. .-.  \/ .. \
 | |  '|  /   Y   \  |'  | |
 | \   \  \ 0 | 0 /  /   / |
  \ '- ,\.-"""""""-./, -' /
   ''-' /_   ^ ^   _\ '-''
       |  \._   _./  |
       \   \ '~' /   /
        '._ '-=-' _.'
           '-----'
Woops! We ran into some monkey business here!
 parser errors:
        no prefix parse function for EOF found
```

- 函数调用

```bash
>> let add=fn(a,b,c,d){return a+b+c+d}
>> add(1,2,3,4)
10
>> let addThree=fn(x){return x+3}
>> addThree(3)
6
>> let max = fn(x, y) { if (x > y) { x } else { y } };
>>  max(5, 10)
10
>> let factorial = fn(n) { if (n == 0) { 1 } else { n * factorial(n - 1) } };
>> factorial(5)
120
>> let callTwoTimes = fn(x, func) { func(func(x)) };
>> callTwoTimes(3, addThree);
9
>> callTwoTimes(3, fn(x) { x + 1 });
5
>> let newAdder = fn(x) { fn(n) { x + n } };
>> let addTwo = newAdder(2);
>> addTwo(2);
4
```

- 基本字符串操作

```
>> let giveHello=fn(){"Hello"}
>> giveHello()
Hello
>>
>> let firstName = "Thorsten";
>> let lastName = "Ball";
>> let fullName = fn(first, last) { first + " " + last };
>> fullName(firstName, lastName);
Thorsten Ball
```

- 数组

```bash
>> let a=[1,1+1,1*2+1]
>> a[0]
1
>> len(a)
3
```

- 哈希字符串

```bash
>> let myHash = {"name": "Jimmy", "age": 72, "band": "Led Zeppelin"};
>> myHash["name"]
Jimmy
>> myHash["age"]
72
>> myHash["band"]
Led Zeppelin
```

- 内置函数

```bash
>> puts("Hello MONKEY!!!")
Hello MONKEY!!!
null
>>
```

具体的注释细节可以查看我的博客！

本项目学习自《用Go语言自制解释器》，respect!!!