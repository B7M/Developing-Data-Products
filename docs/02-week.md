


```r
pkgs <- c("plotly", "dplyr","tidyr","leaflet")
install.packages(pkgs)
```

```
Installing packages into '/usr/local/lib/R/site-library'
(as 'lib' is unspecified)
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


````
---
title: "Title of your document"
author: "The author"
format: html
editor: visual
---

```{r}

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


````
---
title: "Title of your document"
author: "The author"
format:
    revealjs:
        self-contained: true
editor: visual
---

## This slide contains R code

```{r}

head(mtcars)

```
````

Now, let's play around with some options. By default, the `echo` option was set to false, which means that it didn't show the code that generated the output. If you wish to include the code in a slide you should set `echo` to `true` and regenerate the presentation, you'll see it shows both the output and the code that generated it.


````
---
title: "Title of your document"
author: "The author"
format:
    revealjs:
        self-contained: true
editor: visual
---

## This slide contains R code that will be displaye with the results!

```{r}
#| echo: true

head(mtcars)
plot(mtcars$mpg)

```
````

On the other hand, if we want to show the code but not evaluate it, we can set `eval` to `false`.


````
---
title: "Title of your document"
author: "The author"
format:
    revealjs:
        self-contained: true
editor: visual
---

## This slide contains R code that won't be executed!

```{r}
#| echo: true
#| eval: false

head(mtcars)
plot(mtcars$mpg)

```
````

Now, it's your turn to try it out. Create a slide with some R code and experiment with different options to see how they affect the output. In the next section, we'll cover how to include figures in our presentations.

### A few Ways to Share Quarto Products

If you are dealing with a small group who have access to R you can simply share the R code and the Quarto file or just the Quarto rendered as HTML file and simply email it to a colleague. If they don't have access to R, or you don't wat to share your code you can share the HTML file. Furthermore, if you wish to share the HTML file with a wider audience, you can host it on a website. There are several options for doing this. Quarto provides numerous options for publishing documents, presentations, and websites created with it. As Quarto renders content in standard formats such as HTML, PDFs, MS Word, and more, you can publish your work virtually anywhere.

Moreover, Quarto offers a convenient "quarto publish" command that enables straightforward publishing to popular services like GitHub, Netlify, Posit Connect, and others. Additionally, there are various tools available to simplify publishing from a Continuous Integration (CI) system.
According to [Quarto websit](https://quarto.org/docs/publishing/) the following are the most common ways to publish Quarto documents:

- [Quarto Pub](https://quarto.org/docs/publishing/quarto-pub.html)
- [GitHub Pages](https://quarto.org/docs/publishing/github-pages.html)
- [Posit Connect](https://quarto.org/docs/publishing/rstudio-connect.html)
- [Netlify](https://quarto.org/docs/publishing/netlify.html)
- [Confluence](https://quarto.org/docs/publishing/confluence.html)

[Quarto Pub](https://quarto.org/docs/publishing/quarto-pub.html) is the recommended method for beginners

To publish your slides on GitHub, you can create a repository and push your Quarto and HTML files to it. When you click on the Quarto file in GitHub, it does a lot of the formatting for you. You can see what the bullets and various points are going to look like. When you click on the HTML file, it shows you the raw HTML, not the rendered presentation. Okay, let's discuss how to render the HTML file. There are different ways to do it, such as using a Chrome or Firefox add-on, but you can also publish your slides through GitHub Pages. If you encounter any issues, read up on [GitHub Pages](https://quarto.org/docs/publishing/github-pages.html).

That's all the information about Quarto we need for this class. We'll see you in the next lesson.

## Plotly

### Plotly 1.1

In this lecture, we will be discussing Plotly - a handy web application and R library. Plotly is a great tool for creating interactive web graphics in R, and it has the added benefit of integrating with multiple languages including MATLAB, Python, and JavaScript. Essentially, Plotly is a web application that enables the creation and sharing of visualizations. In addition to its integration with different languages, Plotly offers a web interface for users who prefer to upload csv files and create plots with point-and-click interactions. Plotly is particularly easy to use with R and RStudio. To install Plotly, users can simply type `install.packages("plotly")` in Rstudio consol. To use it, load it with `library(plotly)`. Plotly plots can be shared through its web interface, which offers free and paid options for private displays and user authentication. Alternatively, users can create HTML graphics that can be shared on their own websites with the Plotly R package. The Plotly web interface offers tools for interactively changing axis labels, a feature that is not available in R. In this lecture, code demonstrations will be used to showcase different types of Plotly plots. It is worth noting that Plotly graphics can be embedded in Quarto documents.

### Plotly 1.2

In this section we will walk you through a Quarto document associated with the Plotly lecture. We will be using the `library(plotly)` function, assuming that you have already installed it. The `plot_ly()` command is straightforward: `plot_ly(mtcars, x = "weight", y = "miles per gallon", mode = "markers")`. The `mtcars` dataset is stored as a dataframe and serves as the data source for this command. The x-axis represents weight, while the y-axis represents miles per gallon, and the mode is set to markers, creating a scatter plot. This code can be replicated for any dataframe to generate a scatter plot. The resulting scatter plot is interactive and can be viewed in the RStudio viewer pane. As you move your cursor over the points, their corresponding x and y values are displayed. In addition, there are various controls at the top of the viewer pane that enable you to download the plot as a PNG, adjust the scale, reset the axes, and modify the hover-over behavior, among other things. The Publish button allows you to publish the plot to RPubs with a single click, generating a web graphic. However, we'll demonstrate other methods for publishing the plot shortly. Another easy way to publish the plot is to click on Export and choose to Save as Web Page. This creates a Web page with the plot and a file with the specified name, which can be referenced and embedded into other projects. Plotly is incredibly user-friendly and straightforward. Your first assignment is to create a simple scatter plot with a different dataset, save it as a webpage, and create graphics in PNG and PDF formats. You can also try publishing the plot to RPubs.

Here is an example of the Quarto document we describe above.


````
---
title: "How Plotly Works"
author: "Your name!"
format:
    revealjs:
        self-contained: true
editor: visual
---

## This slide contains R code!

```{r}
#| echo: true
#| eval: true

library(plotly)
plot_ly(mtcars, x = mtcars$wt, y = mtcars$mpg, mode = "markers")

```
````

### Plotly 1.3

Let's explore some options for scatter plotting in plot_ly, as scatter plots are a common type of visualization. One option is to change the color of the points. For example, we can use the `cyl` variable from the mtcars dataset as a factor variable for coloring the points. To do this, we convert the `cyl` variable to a factor using the function as: `factor(cyl)`. Then, we plot the scatter plot using `plot_ly(mtcars, x = mtcars$weight, y = mtcars$mpg, color = as.factor(cyl), mode = "markers")`. This will create a scatter plot where the points are colored based on the number of cylinders in the car, which is effectively a categorical variable. By default, the legend will display the three values of cyl: 4, 6, and 8. Another option is to use a continuous variable for coloring the points. For example, we can use the `disp` variable from the mtcars dataset, which is a continuous variable. To do this, we plot the scatter plot using `plot_ly(mtcars, x = mtcars$weight, y = mtcars$mpg, color = disp, mode = "markers")`. plot_ly will recognize that `disp` is a continuous variable and use a continuous color gradient to display the points. The color-bar for the gradient will be displayed on the side of the plot.

Currently, the points in the scatter plot appear small, almost invisible when outputted to an HTML file. If you wish to explore the option of changing the point size in scatter plots using plot_ly you can change the size of the points using a continuous variable, in this case, `horsepower`. Each point will have a different size based on its horsepower. Color is already being used to represent the cylinder. By changing the size of the points, we can show four dimensions in the same plot: miles per gallon, weight, cylinders, and horsepower. However, since we're limited to a 2D scatter plot, color and size are the only two dimensions we can display along with the x and y coordinates.

Here is an example of the Quarto document we describe above.


````
---
title: "How Plotly Works"
author: "Your name!"
format:
    revealjs:
        self-contained: true
editor: visual
---

## This slide contains R code!

```{r}
#| echo: true
#| eval: true

library(plotly)
plot_ly(mtcars, x = mtcars$wt, y = mtcars$mpg, color = as.factor(mtcars$cyl), mode = "markers")

```
##
```{r}
#| echo: true
#| eval: true
plot_ly(mtcars, x = mtcars$weight, y = mtcars$mpg, color = mtcars$disp, mode = "markers")

```
````



Continuous color gradient:



Let’s look into a 3D scatterplot. We will show the code and display the plot, and then we will explain what it's doing.


```r
### FALSE
library (plotly)
set.seed(2016-07-21)
temp <- rnorm(100, mean = 30, sd = 5)
pressue <- rnorm(100)
dtime <- 1:100
plot_ly(x = ~temp, y = ~pressue, z = ~dtime,
        type = "scatter3d", color = ~temp)
```

This is another way to add a dimension to a scatter plot. The plot is created using web GL, which is a web-based version of the open GL graphics library. It allows you to embed interactive 3D graphics in webpages. So when you output it as a webpage, it will be interactive just like this. We have three variables in this example: temperature, pressure, and dtime. To create the dataset, we generated 100 random normal values for temperature and pressure, and dtime is just the numbers 1 to 100. We use the same `plot_ly` command as before, specifying the x, y, and z variables and setting type to `scatter3d` and mode to "markers". To add a color gradient to the plot, we use the `color = temp` parameter, which displays a key to the gradient on the side of the plot. This creates a nice interactive 3D scatter plot. For homework, I would like you to create a variety of 2D scatter plots using different plotting attributes, such as color and point shape, to visualize other dimensions. You can also create a 3D scatter plot and output it as a web page to become familiar with working with these types of plots. You may consider publishing your scatter plots on platforms like rpubs to have a public hosting. Give it a try and explore the possibilities.

### Plotly 1.4

Let's discuss a different type of chart, the line graph. To illustrate this, let's use the `airmiles` dataset, which is a time series with values corresponding to each year. We can confirm this by typing `data("airmiles")` and then `time(airmiles)` to see the associated times.


```r
### FALSE
data("airmiles")
time(airmiles)
```

To create the line graph using Plotly, we simply use the `plot_ly` command with the "x" argument set to the time variable and the "y" argument set to "airmiles". Since these variables are in our environment, we don't need to specify a data frame. Once we plot the data, we get a time series chart with the added feature of showing the corresponding x and y values when the mouse hovers over the plot. This type of chart is often used to display market indices, such as the S&P 500.


```r
### FALSE
data("airmiles")
plot_ly(x = ~time(airmiles), y = ~airmiles, type = "scatter", mode = "lines")
```

Now, let's create a multi-line graph using stock market data. We'll need to use the `tidyr` and `dplyr` libraries for data manipulation. The `EuStockMarkets` dataset contains market indices from Germany, Switzerland, France, and Britain. To create the plot, we first convert the dataset into a data frame using the `as.data.frame` command. Then, we use the `gather` command to convert the data into a format suitable for plotting. The resulting data frame can be used with the `plot_ly` command to create a multi-line graph. Note that the original data EuStockMarkets is not a data frame, as you can check by the output of `is.data.frame(EuStockMarkets)`. However, after converting it to a data frame and then applying the `gather` command, we have transformed the data from a short format to a long format. In the long format, there is a variable called index which corresponds to the column name of the data points in the original data. Although this format may not be as convenient for display purposes, it is necessary for plot_ly to display multiple lines, as it requires a single data frame with a factor variable that demarcates the different lines.


```r
### FALSE
library(plotly)
library(tidyr)
library(dplyr)
data("EuStockMarkets")
stocks <- as.data.frame(EuStockMarkets) %>% gather(index, price) %>%
mutate(time = rep(time(EuStockMarkets), 4))

plot_ly(stocks, x = ~time, y = ~price, color = ~index,
type = "scatter", mode = "lines")
```

Therefore, we first need to convert it into a data frame using the command `stocks <- as.data.frame(EuStockMarkets)`. We then use the `gather()` function from `tidyr` to convert the data from a short format to a long format, where each index type is now in a single column called `index`. The final step is to create the time variable using the command `stocks$time <- as.Date(rownames(stocks))`. Once the data is formatted correctly, we can create the plot using plot_ly, where x is time, y is price, and color is the index type. The resulting plot will display the different index types in different colors and allow for interactive hovering over specific points to see the index value at that time. It's worth noting that using `tidyr` and `dplyr` for data manipulation is essential and highly recommended. Give it a try using this data or some other stock market data, and see if you can create your own multi-line stock market graph to display on a webpage.

### Plotly 1.5

The following examples are straightforward, so we won't provide any code demonstrations. Instead, we will show you the resulting output. To create a histogram in plot_ly, you only need to specify the x variable and set the type to `"histogram"`. The output will show the height of the bars as you move the mouse along. Additionally, you can customize the colors, create side-by-side histograms, and perform a variety of other actions in plot_ly.



For a boxplot, you'll need to provide the plot_ly data frame (in this example, it's the iris dataset), set the y variable to petal length, specify the color as species, and set the type to `"box"`. This will generate separate boxplots for each species. When you hover over the boxplot, it'll display values such as the 25th percentile, 75th percentile, and median. The whiskers extend out to 1.5 times the distance between these two values, as per Tukey's idea, which refers back to the normal distribution and the 1.5 times the inter-quartile range. If there's an outlier, plot_ly will display a little point to indicate it.



A heat map is essentially a graphical representation of an image. To create one using plot_ly, generate a matrix with random normal values and specify z=matrix, type="heatmap". The result will be an interactive heat map with a color key on the right-hand side.



As you move your mouse around, plot_ly will display x and y values and the corresponding intensity values. We can create a similar dataset as before, but with different random normal values. Next, instead of plotting the intensity values as colors, we can plot them in a third dimension as a surface. To do this, we set the type as `"surface"` and specify the z values as the intensity values. The row and column values are assigned integers for the x and y values. The resulting plot is a 3D surface.



It's worth noting that when plotting a 3D surface, there is some smoothing involved, so it's important to understand what this smoothing is doing if you plan on using this for real.

### Plotly 1.6

Here we will create a map with some interactive hover-over effects. The code in this example is a bit long, so we won't go over every detail. First, let's create the dataset.


```r
### FALSE
library(plotly)
# Create data frame
state_pop <- data.frame(State = state.abb, Pop = as.vector(state.x77[,1]))

# Create hover text
state_pop$hover <- with(state_pop, paste(State, '<br>', "Population:", Pop))

# Make state borders white
borders <- list(color = toRGB("red"))

# Set up some mapping options
map_options <- list(
scope = 'usa',
projection = list(type = 'albers usa'),
showlakes = TRUE,
lakecolor = toRGB('white')
)
plot_ly(z = ~state_pop$Pop, text = ~state_pop$hover, locations = ~state_pop$State,
        type = 'choropleth', locationmode = 'USA-state',
        color = state_pop$Pop, colors = 'Blues', marker = list(line = borders)) %>%
layout(title = 'US Population in 1975', geo = map_options)
```

As you can imagine, there are 50 rows, each representing a state. For example, the first row is for Alabama and includes its population in millions and some hover-over text. The hover-over text includes the state abbreviation, "AL", a line break, and the population in 1975, which was 3,615,000. We can also add red borders as an option, although it's not necessary. Additionally, the map options will be a list and we will set the scope to the USA. You can experiment with different options to see what works best. To dramatically alter this map for a different region or country, you may have to improvise a bit, but many of the options are self-explanatory. The `Showlakes = TRUE` option simply means that lakes will be displayed, and in this case, the lake color was set to white to avoid blending in with the blue population color.

To break down the code we start by selecting the first couple of rows of the dataset and displaying them to get an idea of what it looks like. It contains the population of each state in millions and some hover-over text which includes the state abbreviation and population in 1975. Next, we set some map options such as showing the lakes, setting the lake color to white, and selecting the USA as the scope. Then we use the `plot_ly` command to create the `choropleth` map. We use the `state_pop` data frame, set the population column as the color variable, and use the state column for locations. We set the type to choropleth and location mode to USA-states. We use a blue color palette and specify that we want to draw markers on the borders. Finally, we pass the output of `plot_ly` to `layout`, which sets a title and includes the map options we previously set.

You can go ahead and run this code now. In our case, it was a bit complicated and the map wouldn't display in the viewer. So, we saved it as a web page and overwrote the template web page that we've been using for this example. Now, when we hover over a state, we can see its population. For example, when we can hover over Alabama and see its population of 3,615,000 in 1975.

If you want to create your own map, start by using this data frame, which has more columns than just population, and try creating different maps with various options. As you experiment with different options, you'll get a better understanding of how they work. To begin with, you can replicate the map we just created and then attempt to create another map using different variables, where the color represents something else. This can be a helpful technique to create interactive maps.

### Plotly 1.7

If you're a fan of `ggplot`, then you might like this code from the Plotly website. We are using the diamond dataset to create a ggplot of carat vs. price. What's cool is that Plotly has a function called `ggplotly` that allows you to easily convert a ggplot into an interactive HTML graphic. The top window shows the ggplot in the RStudio plotting pane, while the bottom window displays it as an HTML graphic in the RStudio viewer pane, just like it would appear in a web browser.


```r
### FALSE
library(ggplot2)
library(plotly)
set.seed (100)
d <- diamonds [sample(nrow (diamonds), 1000), ]

p <- ggplot(data = d, aes(x = carat, y = price)) +
geom_point(size = 4) +
geom_smooth(aes (colour = cut, fill = cut)) +
facet_wrap(~ cut)

gg <- ggplotly(p)
```

To directly post a Plotly graph we will use the above code. We created a ggplot example, labeled gg, which can be displayed in the viewer pane by typing gg in the R prompt. However, if we type `plotly_POST(gg)`, it will post it directly to the Plotly website. You can then use their web-based graphical user interface to edit the graph by clicking on the edit option. Plotly has many tutorials and videos to help you understand how to use it. Before using Plotly, you must set two [environment variables](https://plotly.com/r/getting-started-with-chart-studio/) `plotly username` and `plotly API` key. You can find your API key by going to the settings in Plotly and copying and pasting it from there. If you set these two environment variables in your .Rprofile, you won't be prompted for your credentials every time you start R, making the process seamless.

For more information about plotly, you can visit:

- [The Plolty Website](https://plotly.com)
- [The Plotly R API](https://plotly.com/r/)
- [The Plotly R Package on GitHub](https://github.com/plotly/plotly.R)
- [The Plotly R Cheatsheet](https://images.plot.ly/plotly-documentation/images/r_cheat_sheet.pdf)
- [“Plotly for R” book by Carson Sievert](https://plotly-r.com)

## Leaflet

### Leaflet 1.1

Creating interactive maps is crucial in developing data products. One widely used JavaScript library for this is `Leaflet`, which also has an associated R package that enables the creation of interactive maps in the R environment. Using Leaflet within RStudio is especially convenient as it opens up in the RStudio window. While there are other ways to create interactive maps, such as GoogleVis, Leaflet is popular among the R community. To get started with Leaflet, you should first install the package by running the command `install.packages("leaflet")`. Let's now look at a code example that demonstrates how to create your first Leaflet map in R. To create the map, first load the library by running `library(leaflet)`, and then execute the three commands provided.


```r
### FALSE
library(leaflet)
my_map <- leaflet() %>%
addTiles()

my_map
```

You can then zoom in as much as you like on the resulting map. The code includes piping notation which we use heavily in these lectures. The first command, `leaflet()`, generates the map, while the `addTiles()` command adds the first set of content. We will discuss how to add more useful features, such as markers, later on. For now, try generating a world map and zooming around to ensure that you have successfully installed the Leaflet library.

### Leaflet 1.2

We were able to quickly generate a JavaScript map widget without any knowledge of JavaScript using the Leaflet function, which creates a background layer. The `addTiles()` function adds mapping data from Open Street Map to the background. After adding this content, we can zoom in and explore the map. However, to add markers and direct interactivity, we need to use the `addMarkers()` function, which is very easy to use. We can specify the longitude and latitude of a location and add a label to the marker. In the example, we added a marker for Johns Hopkins hospital with the label "Jeff Leek's office". The piping notation was used, and although it can be a little strange at first, it's a cleaner and easier way to read the code. We can click on the marker to see Jeff Leek's office and zoom in to see the Bloomberg School of Public Health. Additionally, it is worth noting that the Bloomberg School of Public Health is the oldest School of Public Health in the country.


```r
### FALSE
library(leaflet)
my_map <- my_map %>%
addMarkers(lat=39.2980803, lng=-76.5898801, popup="Jeff Leek's Office")

my_map
```

To recap, we were able to generate a map without knowing any JavaScript by using the leaflet function, which creates a background for the map. The `addTiles()` function adds mapping data from OpenStreetMap to the background, and this allows us to zoom in and out and look around. However, to add specific content, like markers, we need to use additional functions. The `addMarkers()` function is used to add markers to the map at specific longitude and latitude points, and we can also give them labels. If you have a map with many markers, you can use this function to add each one with its own set of coordinates and popup text. We will cover more examples in the following sections.

A quick note on the piping notation, we will show you the equivalent code to give you an idea of how it works.


```r
my_map <- my_map %>%
    addMarkers(lat=39.2980803, Ing=-76.5898801,
                popup-"Jeff Leek's Office")

# Equivalent code
my_map = addMarkers (my_map, lat=39.2980803, Ing=-76.5898801, popup="Jeff Leek's Office")
my_map
```

We're using the pipe operator to pass `my_map` as the first argument to the `addMarkers()` function. Then, we assign the result back to `my_map`. Now, you might be wondering why we're doing all of this when we could have just kept the one-liner. Well, the reason is that piping is a powerful tool that you'll want to get used to, especially when you're doing chained operations in tools like `dplyr` or in mapping contexts like this. When you're adding lots of layers and markers, it can become tedious to keep retyping the same set of commands.

### Leaflet 1.3

To add a lot of markers, you can simply put the collection of markers in a data frame. Here's an example.


```r
### FALSE
set.seed(2023-05-29)
df <- data.frame(lat = runif(20, min = 39.2, max = 39.3),
                 lng = runif(20, min = -76.6, max = -76.5))
df %>%
leaflet() %>%
addTiles() %>%
addMarkers()
```

First, let's set the seed so that we get the same results every time we run the code. Then, we'll create a data frame with some random longitude and latitudes. The data frame has 20 rows, and the columns are named "lat" and "lng". We'll pass this data frame as an argument to leaflet to create our map, which will initially be blank. If we run the code up to this point, we'll get a blank map. Next, we'll pass the output of the leaflet argument evaluated at the data frame to the `addTiles()` function. This will add the mapping data to the map, but won't plot anything yet. Finally, we'll pass the map with the mapping data to the `addMarkers()` function to add the markers. You can run the entire code at once instead of in pieces. The resulting map will have multiple markers.
Give it a try by creating your own data frame with random longitude and latitudes and adding it to a map with markers.

### Leaflet 1.4

In this section, we will cover two topics: adding custom markers and separate popups for each marker. We want to achieve this result, where each marker displays the Hopkins logo and has a separate popup. Here is an example of what we're aiming for.


```r
### FALSE
library(leaflet)
hopkinsIcon <- makeIcon(
    iconUrl = "https://brand.jhu.edu/assets/uploads/sites/5/2016/01/university.logo_.small_.vertical.white_.png",
    iconWidth = 31*215/230, iconHeight = 31,
    iconAnchorX = 31*215/230/2, iconAnchorY = 16
)
hopkinsLatLong <- data.frame(
    lat = c(39.2973166, 39.3288851, 39.2906617, 39.297681,39.2824806),
    lng = c(-76.5929798, -76.6206598, -76.5469683, -76.6150537, -76.6016766))

hopkinsLatLong %>%
leaflet() %>%
addTiles() %>%
addMarkers(icon = hopkinsIcon)

hopkinsSites <- c(
    "<a href='http://www.jhsph.edu/'>East Baltimore Campus </a>",
    "<a href='https://apply.jhu.edu/visit/homewood/'>Homewood Campus </a>",
    "<a href='http://www.hopkinsmedicine.org/johns_hopkins_bayview/'>Bayview Medical Center </a>",
    "<a href='http://www.peabody.jhu.edu/'>Peabody Institution </a>",
    "<a href='http://carey.jhu.edu/'>Carey Business School </a>"
)
hopkinsLatLong %>%
leaflet() %>%
addTiles() %>%
addMarkers(icon = hopkinsIcon, popup = hopkinsSites)
```

We first defined our Hopkins icon by specifying its URL, width, height, and anchor points. Then we created a series of latitude and longitude values for buildings at Hopkins. We passed these values to leaflet, which generated a map with markers using the `addTiles` and `addMarkers` functions. However, we also needed to set the icon for each marker to the Hopkins icon. Once we had the markers displaying the Hopkins logo, we wanted to add links to each marker. We created a series of sites, which were text vectors containing HTML commands that created a hyperlink for each building. These sites corresponded to the latitude and longitude values in the same order. Finally, we passed the latitude and longitude values to leaflet, `addTiles`, and `addMarkers` functions, along with the Hopkins icon. We set the popup to display the collection of hopkinsSites.

Once you run the entire code, you will have a map with Hopkins logos at each marker, and separate popups with links for each building.

### Leaflet 1.5

Sometimes you may have multiple points on a map very close to each other. Leaflet offers a great solution for situations when multiple points appear too close together to differentiate. This solution is clustering, where the points are grouped together and will break apart into individual points when the map is zoomed in. To demonstrate this feature, we can define a data frame with 500 latitude and longitude points that are close together and pass it as an argument to leaflet. Then, we can add tiles and markers with default cluster options. The clusters will show the number of points they contain. As we zoom in, the clusters break apart into individual points.

Here is an example of what we're aiming for.


```r
### FALSE
library(leaflet)
df <- data.frame(lat = runif(500, min = 39.25, max = 39.35),
                 lng = runif(500, min = -76.65, max = -76.55))
df %>%
leaflet() %>%
addTiles() %>%
addMarkers(clusterOptions = markerClusterOptions())
```

Additionally, we can add circle markers instead of adding markers or clusters by using the `addCircleMarkers` function. We can create a couple of 20 markers and add circle markers to them. This will display the markers as little circles.


```r
### FALSE
library(leaflet)
df <- data.frame(lat = runif(20, min = 39.25, max = 39.35),
                 lng = runif(20, min = -76.65, max = -76.55))
df %>%
leaflet() %>%
addTiles() %>%
addCircleMarkers()
```

### Leaflet 1.6

Now, let's discuss how to digitally draw shapes on your map. This can be accomplished using commands that allow you to draw circles and rectangles, and even add a legend to your map. These commands will enable you to annotate and draw on your map in useful ways. We will demonstrate how to draw a circle in a way that you might actually want to use. For example, we take a dataset of cities such as Baltimore, Frederick, Rockville, Gaithersburg,... along with their population, latitude, and longitude. We will pass this dataset to leaflet, add tiles to it, and then add circles to it using the addCircles command. We will also provide some important options such as scaling the radius relative to the population of the cities. This is a more reasonable use of adding circles than just having them as markers. Let's go ahead and run the code to see the result.


```r
### FALSE
library(leaflet)
md_cities <- data.frame(name = c("Baltimore", "Frederick", "Rockville", "Gaithersburg", "Bowie", "Hagerstown", "Annapolis", "College Park","Salisbury", "Laurel"),
                        pop = c(619493, 66169, 62334, 61045, 55232, 39890, 38880, 30587,30484, 25346),
                                lat = c(39.2920592, 39.4143921, 39.0840, 39.1434, 39.0068,39.6418,38.9784, 38.9897, 38.3607, 39.0993),
                                lng = c(-76.6077852,-77.4204875, -77.1528,-77.2014, -76.7791,-77.7200, -76.4922, -76.9378,-75.5994, -76.8483))
md_cities %>%
leaflet() %>%
addTiles() %>%
addCircles(weight = 1, radius = sqrt(md_cities$pop)*30)
```

Alright, now we have the circles representing the population of the cities and we can see the relative sizes of the circles. Let's move on to drawing rectangles. We can use the `addRectangles()` command to do that. Here's an example where we're going to draw a rectangle around Baltimore city. For a rectangle, you just need to provide the coordinates of its two opposite corners. In this example, we're creating a rectangle around the Mountain View Corporate Center. So we'll define a bounding box that contains Baltimore and then use that to draw the rectangle.


```r
### FALSE
library(leaflet)

leaflet() %>%
addTiles() %>%
addRectangles(lat1 = 37.3858, lng1 = -122.0595,
                lat2 = 37.3890, lng2 = -122.0625)
```

Let's now add a legend to a map using the `addLegend` function. This is a common task when you want to differentiate between different annotations, such as circles and rectangles, using different colors and symbols, and want to provide a key for users to understand what each one means. When you add markers to your map, you may want to color them differently and add a legend to help the user understand what each color represents. In the following example, we have a data frame with 20 points, colored red, blue, or green. We pass the data frame to `leaflet()` and `add addCircleMarkers()` colored according to the random color we generated. In a real application, you would want to use colors that have a specific meaning. To add a legend, we use the same syntax as the legend command in base R plotting. We define labels, in this case just `LETTERS[1:3]`, and colors, which are blue, red, and green.


```r
### FALSE
library(leaflet)
df <- data.frame(lat = runif(20, min = 39.25, max = 39.35),
                 lng = runif(20, min = -76.65, max = -76.55),
                 col = sample(c("red", "blue", "green"),20,repl = TRUE),
                 stringsAsFactors = FALSE)
df %>%
leaflet() %>%
addTiles() %>%
addCircleMarkers(color = df$col) %>%
addLegend(labels = LETTERS[1:3], colors = c("blue","red","green"))
```

When we run the code, the legend appears at the top of the map.

This is the last lecture on Leaflet. We hope you found it useful. Leaflet is a powerful tool, and when used in conjunction with Shiny, it can create amazing applications. It's also one of the easiest interactive plotting utilities available in R, and definitely worth learning. Thanks for joining us, and we look forward to seeing you in the next chapter.

## Quiz
