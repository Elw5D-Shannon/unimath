**颜色文字:**
<span style="color:red">红色文字</span>
<span style="color:blue">蓝色文字</span>
<span style="color:#ff0000">另一种红色</span>
<span style='color:orange; font-weight:bold'>加粗橘色</span>
$\color{red} x^2 + \color{blue} y^2 = 1$
```text
只要查一下颜色的编号放进去就可以
<span style="color:red">红色文字</span>
<span style="color:blue">蓝色文字</span>
<span style="color:#ff0000">另一种红色</span>
<span style='color:orange; font-weight:bold'>加粗橘色</span>

数学公式中的颜色文字（虽然大概用不到就是了）
$\color{red} x^2 + \color{blue} y^2 = 1$
```



**章节符号** §
或者这样子 $\S$ `$\S$`

**任务表格**：
- [ ] abc
- [x] def
- [?] asdf
```text
- [ ] abc
- [x] def
- [?] asdf
```


**居中输入**
<div style="text-align: center;">这段文字将居中显示</div>
```text
<div style="text-align: center;">这段文字将居中显示</div>
```

**放大**
<div style='font-size:20px'>这段文字将放大</div>
<span style="font-size: 12px">12px - 小号</span>
<span style="font-size: 14px">14px - 默认大小</span>
<span style="font-size: 16px">16px - 稍大</span>
<span style="font-size: 18px">18px - 大号</span>
<span style="font-size: 20px">20px - 较大</span>
<span style="font-size: 24px">24px - 标题大小</span>
<span style="font-size: 32px">32px - 醒目标题</span>
```text
<div style='font-size:20px'>这段文字将放大</div>
<span style="font-size: 12px">12px - 小号</span>
<span style="font-size: 14px">14px - 默认大小</span>
<span style="font-size: 16px">16px - 稍大</span>
<span style="font-size: 18px">18px - 大号</span>
<span style="font-size: 20px">20px - 较大</span>
<span style="font-size: 24px">24px - 标题大小</span>
<span style="font-size: 32px">32px - 醒目标题</span>
```

# Mermaid
参考：[Mermaid 参考](https://docs.min2k.com/zh/mermaid/syntax)
Obsidian支持 Mermaid 图表，思维导图（但是很丑）：
```mermaid
mindmap
	A["`**根节点** 支持一定的Markdown 🤓`"] 
		B["子节点"] 
		C["子节点"]
			D["子节点的子节点"]
			E["子节点的子节点"]
			F["子节点的子节点"]
```
时序图：
```mermaid
sequenceDiagram
    Alice->>John: Hello John, how are you?
    John-->>Alice: Great!
    Alice-)John: See you later!
```

甘特图：
```mermaid
gantt
    title A Gantt Diagram
    dateFormat YYYY-MM-DD
    section Section
        A task          :a1, 2014-01-01, 30d
        Another task    :after a1, 20d
    section Another
        Task in Another :2014-01-12, 12d
        another task    :24d

```
饼图
```mermaid
pie title Pets adopted by volunteers
    "Dogs" : 386
    "Cats" : 85
    "Rats" : 15

```
统计图
```mermaid
xychart-beta
    title "牛马指数"
    x-axis [jan, feb, mar, apr, may, jun, jul, aug, sep, oct, nov, dec]
    y-axis "指数" 4000 --> 11000
    bar [5000, 6000, 7500, 8200, 9500, 10500, 11000, 10200, 9200, 8500, 7000, 6000]
    line [5000, 6000, 7500, 8200, 9500, 10500, 11000, 10200, 9200, 8500, 7000, 6000]

```

饼干图
```mermaid
block-beta
  columns 3
  a["饼干1"] b["饼干2"]:2 c["饼干3"]:2 d["饼干4"]
```
何意味：
```mermaid
stateDiagram
    [*] --> Still
    Still --> [*]

    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
```
目前正在研究如何使其变得更美观。


>[!quote] Cym10x
>666把 Obsidian 沙盒搬进来了

>[!quote] WKN
>666你上课在做这个东西 $\uparrow$

