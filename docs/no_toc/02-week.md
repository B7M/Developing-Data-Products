


```r
pkgs <- c("plotly", "dplyr","tidyr","leaflet")
install.packages(pkgs)
```

```
Installing packages into '/usr/local/lib/R/site-library'
(as 'lib' is unspecified)
```

```
also installing the dependencies 'gridExtra', 'hexbin', 'raster', 'sp', 'viridis', 'leaflet.providers'
```
# Second week

During this module, we'll learn how to create Quarto files. We'll also explore `leaflet` and `plotly` and their usage to create interactive content.
Learning Objectives 
Create Quarto file
Employ R code in a Quarto file
Create a map using Leaflet
Use Leaflet to add legends, markers, circles, and rectangles to your map

## Quarto

Quarto is an open-source document format and toolchain designed for reproducible research and technical publishing. It aims to provide a seamless workflow for creating dynamic documents that combine code, text, and graphics, allowing users to generate reports, papers, books, and websites. It is based on the popular Pandoc tool. Quarto is a publishing system that allows you to create and publish content to Posit Connect, a publishing platform. With Quarto, you can create and publish your content to Posit Connect, a publishing platform. Quarto content supports executable code in multiple languages, and supports interactivity through a number of technologies.

Here are some key features of Quarto:

- Markdown-based: Quarto documents are written in Markdown, a lightweight markup language that is easy to read and write. Markdown allows you to add formatting, headings, lists, images, and other elements to your document.

- Embeddable code: Quarto allows you to embed code chunks within your Markdown document. These code chunks can be executed, and their output can be included in the final document. Code chunks can contain code from various programming languages such as R, Python, Julia, and more.

- Reproducibility: Quarto emphasizes reproducibility by enabling the capture of code, data, and environment dependencies. This ensures that the document can be reproduced exactly as intended, even if changes are made to the underlying code or data.

- Dynamic documents: Quarto documents are dynamic, meaning that they can be rendered in multiple output formats, such as HTML, PDF, Word, and more. You can easily switch between formats without changing the content of your document.

- Extensible: Quarto provides extensibility through a plugin system. Plugins allow you to add custom functionality and features to your documents, such as additional output formats, syntax highlighting, interactive elements, and more.

To work with Quarto, you'll need to install the Quarto command-line tool (CLI) and have a basic understanding of Markdown and the programming languages you intend to use within your documents. The [Quarto website](quarto.org) provides comprehensive documentation, tutorials, and examples to help you get started with creating dynamic and reproducible documents using Quarto. To start this exciting journey, visit the [get-started](https://quarto.org/docs/get-started/) page on the Quarto website and follow the instructions to install Quarto on your computer.

### Quarto and R Markdown

According to the website, the primary objective of Quarto is to significantly enhance the process of creating and collaborating on scientific and technical documents. Quarto brings together the capabilities of various tools like R Markdown, bookdown, distill, xaringian, and more into a cohesive and comprehensive system. It incorporates the valuable insights gained from the development and use of R Markdown over the past decade. In scientific discourse, the use of different languages and runtimes is extensive, with the Jupyter ecosystem being particularly popular. Quarto is designed to be versatile and adaptable, supporting multiple languages and engines. Currently, it supports Knitr, Jupyter, and Observable, and it has the potential to accommodate additional engines in the future.

Unlike R Markdown, which is closely tied to R, Quarto aims to extend its benefits to a wider range of users. Quarto does not have a dependency or requirement for R, making it accessible to practitioners from various backgrounds. It was developed with multilingual capabilities from the start, supporting languages such as R, Python, JavaScript, and Julia, while remaining adaptable to future languages. Although Quarto is a relatively new system, it is highly compatible with existing content. Most R Markdown documents and Jupyter notebooks can be rendered in Quarto without any modifications. The objective is to make a significant and long-term investment in reproducible research, while ensuring compatibility with existing formats and adaptability to different user environments.
In summary, it is safe to say Quarto is the next generation of R markdown for multiple languages.In the following sections we will be looking into Quarto and its features in more details. It is important to note that Quarto is still in its early stages of development and it is not yet ready for production use. However, it is being actively developed and improved, and we encourage you to try it out. Most of the features we will discuss can be used in R Markdown exactly or with slight syntax modification.

### Quarto 1.1

What makes Quarto/ R Markdown particularly useful is that these embed code, results, and plots from the analysis into the document, making it a self-contained and reproducible unit. In contrast, traditional workflows typically involve separate documents and code files, with manual copying and pasting or saving and importing files, which can create issues with version control and reproducibility. Quarto provides a consistent structure for generating presentations and documents, making it a better option for those concerned with reproducibility. For instance, in a corporate setting where a report needs to be presented routinely, having a script that generates the presentation with the latest data in a version-controlled way would be more efficient and reliable than manually copying and pasting each time. Quarto can be useful for creating recurring or automated presentations, but it has many other uses as well. One important benefit of Quarto is its ability to improve the reproducibility of documents. In the academic community, there have been many instances where papers have been published and subsequent groups have tried to reproduce the results, only to find that it's often not possible. This can lead to disputes and uncertainty over who is right. However, embedding the code in a document using Quarto greatly improves its reproducibility. While there may still be some external factors that impact the results, overall it goes a long way towards creating more reliable and reproducible documents. This class emphasizes the creation of products, and your presentation serves as your product pitch. Therefore, we want your pitch to be in one of the reproducible formats. Given these, let's move on to some examples.

### Quarto 1.2

We encourage you to download [Download hello.qmd](https://quarto.org/docs/get-started/hello/rstudio/_hello.qmd) and familiarize yourself with the Quarto environment.
Quarto offers multiple options for creating output formats, including HTML, PDF, Word, and more. It also provides you with variety of formats for creating presentations such as [revealjs](https://quarto.org/docs/presentations/revealjs/), [Powerpoint](https://quarto.org/docs/presentations/powerpoint.html) and [Beamer](https://quarto.org/docs/presentations/beamer.html). In this class, we'll focus on HTML, and Revealjs. Revealjs stands out as the most feature-rich format and is highly recommended for creating presentations. However, you are encouraged to explore the other options [here](https://quarto.org/docs/output-formats/html-basics.html).

Now, we will create a new html. To do so, we need to go to File > New File > Quarto Document... As we mentioned earlier Quarto is a work in progress, we noticed sometimes you might not see Quarto Document... under New File, in that case you could create an empty R script save it and before working on it change the name extension to .qmd then open the file and start working on it. Once you have your Quarto document opened, you should make sure you have the yml section, which looks like:


```r
---
title: "My first Quarto document"
author: "Brian Caffo"
format: html
editor: visual
---
```

Let's take a look at the preamble section surrounded by three dashes. It is extremely important to start your YAML part with `---` and end it with `---`. The title is the title of your document, and the format is the output format. However, if you prefer a PDF output, it requires the installation of MiKTeX on Windows, MacTeX on OS X, or TeX Live on Linux. These installations are easy to set up but can be quite large. The editor is the editor you want to use. You can use the visual editor, which is the default, or you can use the code editor. The code editor is a bit more advanced, which means you will be dealing with text entirely. The visual editor is a bit more limited, but it is easier to use. Once the YAML file is set up, let's compile it to see what it looks like. To compile the document you should click on the Render button. And there you go, it's running and the output is "My first Quarto document" and the line below that shows the author name. Your homework is to create a new presentation using the template, compile it once, and then we'll move on to adding content.

### Quarto 1.3

In body part you see two main sections these two the text section and code chunks. The code chunks are like a window to R and you will generate the results of your analysis and graphs using the code chunks. You can start a code chunk using using the following structure:


```r
---
title: "Title of your document"
author: "The author"
format: html
editor: visual
---
```

```r
# your code
```
````

If you just make a Quarto file with the provided template and render it you will see there are two files created in the same directory as your Quarto file. The first one is the HTML file, the second one is a folder with `_files` in its name. The HTML file is the output of your Quarto file. The folder is where all the images and plots will be saved and it is necessary to open the html file properly. However; we usually are interested in one single file that is self contained. To address this issue we need to edit the YAML part to look like the following:

```
---
title: "Title of your document"
author: "The author"
format:
    html:
        self-contained: true
editor: visual
---
```

It is important to note that the YAML part is very sensitive to indentation and you should be careful about it. Now if you render your Quarto file you will see there is only one HTML file created. This is the file you can share with others and it is self contained.

Now let's take a look at creating presentations in Quarto. In order to make presentations you need to swap the format from html to revealjs. The YAML part should look like the following:

```
---
title: "Title of your document"
author: "The author"
format:
    revealjs:
        self-contained: true
editor: visual
---
```

To create a new slide with title, add two pound signs `##` and then the slide title, such as "My New Slide" and for slides without title use `***`.

```
---
title: "Title of your document"
author: "The author"
format:
    revealjs:
        self-contained: true
editor: visual
---

## My New Slide
This is part of the content for "My New Slide".

***
This slide has no title!

```

Now if you render the code you will see a slide with some content and a slide without a title. As you can see, we used two pound signs to create a slide with a title, and three asterisks to create a slide without a title. Now, let's add a few features to our presentation. We encourage you render your file after adding each of the features to understand what is happening.

- To add pause to the presentation we'll use `. . .`
- To add a list with a few bullet points use `- bullet point' on single line.
- By default, number and bullet lists within slides are shown in their entirety. However, you have the option to explicitly control whether a list appears incrementally or all at once. To achieve this, you can enclose the list within a div element and assign it a specific class that defines the desired mode.


```r
::: {.incremental}
- Item 1
- Item 2
:::
```

- If you wish to have a numbered list you can use the following structure:


```r
::: {list}
1. Numbered list item 1
2. Numbered list item 2
:::
```

- Sometimes you have a long list of bullet points and you want to keep those in one slide. To add legibility to your slide you can make the slide scrollable by adding scrollable class the slide. `## Slide Title {.scrollable}`

The following code summarizes all the mentioned points and you can use it as a template for your presentations.


```r
---
title: "Title of your document"
author: "The author"
format:
    revealjs:
        self-contained: true
editor: visual
---

## My New Slide
This is part of the content for "My New Slide".

***
This slide has no title!

## My second slide

This is part of the content for "My second slide".

. . .

This part will show up after a click because of the implemented **pause**.


## My third slide

Here are some bullet points:

- Bullet 1
- Bullet 2
- Bullet 3

We also show a numbered list:

::: {list}
1. Numbered list item 1
2. Numbered list item 2
:::

As you can see, the bullet points are not animated.

## My fourth slide

Here are some animated bullet points:

::: {.incremental}
- Bullet 1
  - sub bullet 1
  - sub bullet 2
- Bullet 2
- Bullet 3
:::


## Scrollable slide {.scrollable}

- Bullet 1
  - sub bullet 1
  - sub bullet 2
- Bullet 2
- Bullet 3
- Bullet 4
- Bullet 5
- Bullet 6
- Bullet 7
- Bullet 8
- Bullet 9
- Bullet 10
```

Now, it's time to create some slides with your own content. Add titles, bulleted and ordered lists to your slides.

### Quarto 1.4

Let's take a look at some formatting options. For instance, if we write plain text, `*italicized text*`, and `**bold text**`, you can see that it's automatically syntax highlighted. Additionally, we can add some code, such as `1:10`, by using single right-facing quotation marks. Remember that to use italics, you need to have one asterisk next to the leading character, and to use bold, you need two asterisks next to the leading character. It's important to note that the asterisks must be next to the leading character for it to work correctly. In order to add breaks between the lines we use `<br><br>` because using the `Enter` key will not have effect on the output. One simple option that can add to readability of your document is adding table of content to the document especially when using html output. You can achieve this by editing the YAML part and adding `toc: true` right below the `self-contained: true`.
If you are interested in having different themes than the default you have options! You can find the list of available themes [here](https://quarto.org/docs/presentations/revealjs/#themes). To change the theme you need to edit the YAML part and add `theme: name of the theme` right under `revealjs:` section.

To check these effects you can copy and run the following example and see the results.


```r
---
title: "Title of your document"
author: "The author"
format:
    revealjs:
        self-contained: true
        theme: dark
        toc: true
editor: visual
---

## My New Slide
This is part of the content for "My New Slide". <br><br>

**bold text**


*italicized text*
```

As the last part in this section, we will cover ways to add images to your presentation. To add an image to your presentation you can either use the local image files or online images. With local image approach, you need to have the image file in the same directory as your Quarto file. Then you can use the following structure to add the image to your presentation.


```r
![The image caption](image_file.png)
```

To specify the image size we will add `{width=300}` right after the image file name. The number 300 is the width of the image in pixels. You can change it to any number you wish. To incorporate online images you can add the image URL instead of the image file name. The rest of the structure is the same as the local image approach. Let's take a look at an example.


```r
![Johns Hopkins | Bloomberg School of Public Health](https://publichealth.jhu.edu/sites/default/files/2021-07/bsph-building-with-logo.jpg){width=300}
```

### Quarto 1.5

Let's add some code to our document. To do so, we will use the structure that we showed you before. For example let's say you are intrested in displaying the `mtcars` dataset in a slide.


```html
---
title: "Title of your document"
author: "The author"
format:
    revealjs:
        self-contained: true
editor: visual
---

## This slide contains R code

```

```r
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
```
````

Now, let's play around with some options. By default, the `echo` option was set to false, which means that it didn't show the code that generated the output. If you wish to include the code in a slide you should set `echo` to `true` and regenerate the presentation, you'll see it shows both the output and the code that generated it.


```html
---
title: "Title of your document"
author: "The author"
format:
    revealjs:
        self-contained: true
editor: visual
---

## This slide contains R code that will be displaye with the results!

```

```r
#| echo: true

head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
```

```r
plot(mtcars$mpg)
```

<img src="02-week_files/figure-html/unnamed-chunk-14-1.png" width="672" />
````

On the other hand, if we want to show the code but not evaluate it, we can set `eval` to `false`.


```r
---
title: "Title of your document"
author: "The author"
format:
    revealjs:
        self-contained: true
editor: visual
---

## This slide contains R code that won't be executed!
```

```r
#| echo: true
#| eval: false

head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
```

```r
plot(mtcars$mpg)
```

<img src="02-week_files/figure-html/unnamed-chunk-16-1.png" width="672" />
````

Now, it's your turn to try it out. Create a slide with some R code and experiment with different options to see how they affect the output. In the next section, we'll cover how to include figures in our presentations.

