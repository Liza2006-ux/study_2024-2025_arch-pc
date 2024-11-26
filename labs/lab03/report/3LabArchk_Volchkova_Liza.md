# This is heading 1
## This is heading 2
### This is heading 3
#### This is heading 4

This text is **bold**.

This text is *italic*.

This is text is both ***bold and italic***.

> The drought had lasted now for ten million years, and the reign of the
terrible lizards had long since ended. Here on the Equator, in the
continent which would one day be known as Africa, the battle for existence
had reached a new climax of ferocity, and the victor was not yet in sight.
In this barren and desiccated land, only the small or the swift or the
fierce could flourish, or even hope to survive.

1. First instruction
  1. Sub-instruction
  1. Sub-instruction
1. Second instruction2.
 
* List item 1
* List item 2
* List item 3

1. First instruction
1. Second instruction
1. Third instruction2. 

- List item 1
  - List item A
  - List item B
- List item 2

[Лаб.раб. 3](3_Лаб.Арх.к.Волчкова_Лиза.md)

[Моя ссылка](https://yandex.ru/images/search?from=tabbar&text=%D1%86%D0%B2%D0%B5%D1%82%D0%BE%D0%BA "Цветы")

Формула в тексте 
$\sin^2 (x) + \cos^2 (x) = 1
$

Формула в тексте с сылкой 
$$
\sin^2 (x) + \cos^2 (x) = 1
$$ 
{#eq:eq1} Смотри формулу (`[-@eq:eq1]`)

![Цветок](c:/img/flower.jpg "Flower"){
↪ #fig:fig1 width=70% }

pandoc 3LabArchk_Volchkova_Liza.md -o 3LabArchk_Volchkova_Liza.pdf

pandoc 3LabArchk_Volchkova_Liza.md -o 3LabArchk_Volchkova_Liza.docx

FILES = $(patsubst %.md, %.docx, $(wildcard *.md))
FILES += $(patsubst %.md, %.pdf, $(wildcard *.md))
LATEX_FORMAT =
FILTER = --filter pandoc-crossref
%.docx: %.md
-pandoc "$<" $(FILTER) -o "$@"
%.pdf: %.md
-pandoc "$<" $(LATEX_FORMAT) $(FILTER) -o "$@"
all: $(FILES)
@echo $(FILES)
clean:
-rm $(FILES) *~




