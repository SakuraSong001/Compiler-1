# Compiler
### 任务分工
| Task |Performer|
|--------|--------|
| 词法分析生成 Token 序列、符号表子表|     Sakura  |
| 语法分析,符号表总表|Leeeeo|
| 中间代码生成及优化|Loke|
| 目标代码生成|Koala|


### Todo List
- [ ] cout/cin     [Loke]
- [ ] 添加数组      [Leeeeo]
- [ ] 添加结构体  [Leeeeo]
- [ ] 添加函数  [Loke]
- [ ] 图形界面实现  [Leeeeo]

### version 0.0 (Done)
- [x] 黑框框走一遍整体流程


## Index
- [ ] 词法分析器的设计
- [ ] 语义分析器的设计
- [ ] 符号表系统的设计
- [ ] 目标代码生成及虚拟机构建

##文法
### 词法定义
备注：code是种别码，value是相应表中的地址

| 描述 | code |value|
|--------|--------|-------|
|自定义标识符|	0|	|
|字符常量	|1	||
|字符串常量|	2	||
|数字	|3	||
|main	|4	|0|
|while	|5|	0|
|if|	6	|0|
|char|	7	|0|
|int	|8|	0|
|float	|9|	0|
|struct|	10|	0|
|+|	11	|0|
|-|	12	|0
|*|	13	|0
|/|	14||	
|{|	15|	0
|}|	16|	0
|=|	17|	0
|,|	18|	0
|[|	19|	0
|]|	20|	0
|;|	21|	0
|\"|22||
|'|	23|	|
|(|	24|	|
|)|	25|	|
|&|	26|	|
|&#124;|27||	
|!|	28||
|void|	29||	
|else|	30	||
|return|	31||	
|&&|	32	||
|&#124;&#124;|	33	||
|cout|	34	||
|cin|	35	||
|<<|	36	||
|>>|	37	||
|long|	38	||
|short|	39	||
|bool|	40	||
|double|	41	||
|typedef|	42	||
|unsigned|	43	||
|static|	44	||
|enum|	45	||
|for|	46	||
|do|	47	||
|continue|	48	||
|signed|	49	||
|extern|	50	||
|inline|	51	||
|const|	52	||
|default|	53	||
|case|	54	||
|break|	55	||
|switch|	56	||
|sizeof|	57	||
|union|	58	||
|auto|	59	||
|volatile|	60	||
|register|	61	||
|goto|	62	||
|restrict|	63	||
|Complex|	64	||
|Imaginary|	65	||
|==|	66	||
|>|	67	||
|>=|	68	||
|<|	69	||
|<=|	70	||
	||71	||
	||72	||
	||73	||
	||74	||
	||75	||
	||76	||
	||77	||
	||78	||
	||79	||
	||80	||
	||81	||
	||82	||
	||83	||
	||84	||
	||85	||
	||86	||
	||87	|||


### 文法定义(C 语言)
>  程序 -> 多个结构体定义 多个函数定义

>  多个结构体定义 -> {结构体}

>  结构体 -> struct 标识符 { 多个变量声明 } ;


>  多个变量声明 -> {单个变量声明}


> 单个变量声明 -> 变量类型 变量 ;| 变量类型 [长度];


> 变量 -> 标识符


>  变量类型 -> int|float|char


>  多个函数定义 -> {函数定义}


> 函数定义 -> 函数返回值类型 函数名称标识符 ( 参数列表 ) { 复合语句 返回语句 }


> 函数返回值类型 -> 变量类型|void


> 返回语句 -> return 算数表达式E ;|return ;|return 常量 ;


> 函数名称标识符 -> 标识符|main


> 参数列表 -> 变量类型 标识符 , 参数列表|空


>  复合语句 -> 多个变量声明 多个语句


>  多个语句 -> { 语句 }


>  语句 -> 初始化语句|赋值语句|while语句|if语句


>  初始化语句 -> 变量类型 初始化赋值表


>  初始化赋值表 -> 标识符 , 初始化赋值表|标识符 = 算数表达式E , 初始化赋值表|;


>  赋值语句 -> 标识符 = 算数表达式E ;


>  算数表达式


>  > E -> T E1


>  > E1 -> w0 T E1|空


>  > T -> F T1


>  > T1 -> w1 F T1|空


>  > F -> I|( E )

>  while语句 -> while ( 算数表达式 ) { 多个语句 }


>  if语句 -> if ( 算数表达式 ) { 多个语句 } 否则语句


>  否则语句 -> else { 多个语句 }|空


## 词法分析器的设计
输入:源代码
输出: Token 序列
## 语义分析器的设计
输入:Token及语义分析的返回值
输出:一个自定义四元式集合
## 符号表系统的设计
输入: Token 序列
输出:一个自定义的符号表
## 目标代码生成
输入:四元式
输出:汇编代码