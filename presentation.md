---
title: Creating A Presentation
subtitle: With Markdown and Pandoc
author:
  - Nikola Vidic
theme: metropolis
date: \today
lang: de-DE
---

[//]: # This is a comment inside the markdown file
[//]: # header-includes: | <--- To use LaTeX packages
[//]: #   \usepackage[T1,T2A]{fontenc} <--- To use cyrilic

# Run pandoc on save
To run pandoc on save, run this command in the cli
```bash
ag -l | entr -s \
"pandoc --slide-level 1 --lua-filter dotfilter.lua \
 presentation.md -t beamer -o presentation.pdf"
```

# Text
**bold text**

*italic text*

~~strike-thru~~

# Code
```{.csharp .numberLines}
class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
```

# markdown lists
Markdown for lists

* One
* Two
    * Nested one
* Three
    1. Numerated list
    1. No need to specify number

# Bullet Points
Increment bullet points

> 1. Eat eggs
> 1. Drink coffee

# Pause
Here is a text before the pause.

. . .

After the pause.

# markdown footnote
Just use Markdown to define sections and structure of the document.
Let's finish with a footnote.[^1]

[^1]: I'm a footnote!

# Line blocks
| The limerick packs laughs anatomical
| In space that is quite economical.
|    But the good ones I've seen
|    So seldom are clean
| And the clean ones so seldom are comical

| 200 Main St.
| Berkeley, CA 94718

# Block quotation
> This is a block quote. This
> paragraph has two lines.
>
> 1. This is a list inside a block quote.
> 2. Second item.

# Headings
Term 1
: Definition 1

Term 2
: Definition 2

      { some code, part of Definition 2 }

      Third paragraph of definition 2.

# Headings
Term 1
  ~ Definition 1

Term 2
  ~ Definition 2a
  ~ Definition 2b

# Text
(@)  My first example will be numbered (1).
(@good)  My second example will be numbered (2).

Explanation of examples.

(@)  My third example will be numbered (3).
(@) This is a good example.

As (@good) illustrates, ...

# Image

![caption](img.png){width=60%}

# Table
: Sample grid table.
+---------------+---------------+--------------------+
| Fruit         | Price         | Advantages         |
+===============+===============+====================+
| Bananas       | $1.34         | - built-in wrapper |
|               |               | - bright color     |
+---------------+---------------+--------------------+
| Oranges       | $2.10         | - cures scurvy     |
|               |               | - tasty            |
+---------------+---------------+--------------------+

# Graph
```{#graphviz .dot .process }
digraph dfd2{
  label="graphviz";
  node[shape=record]
  subgraph level0{
  enti1 [style=filled fillcolor=orange label="Customer" shape=box];
  enti2 [label="Manager" shape=box];
  }
  subgraph cluster_level1{
    label ="Level 1";
    proc1 [label="{<f0> 1.0|<f1> One process here\n\n\n}" shape=Mrecord];
    proc2 [label="{<f0> 2.0|<f1> Other process here\n\n\n}" shape=Mrecord];
    store1 [label="<f0>    |<f1> Data store one"];
    store2 [label="<f0>   |<f1> Data store two"];
    {rank=same; proc1, proc2}
  }
  enti1 -> proc1
  enti2 -> proc2
  store1 -> proc1
  store2 -> proc2
  proc1 -> store2
  store2 -> proc1
}
```
