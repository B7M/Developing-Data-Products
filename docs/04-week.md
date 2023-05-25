# Fourth week

## Swirl Courses

Hello, I'm Sean Cross your instructor for this week's content on Swirl. Swirl is an interactive tool designed to teach R programming and data science concepts directly within the R console. With Swirl, you can learn at your own pace, interactively, and without needing to switch between different environments. Swirlify is an R package that allows you to create your own Swirl courses and lessons. In this lesson, we will demonstrate how to create Swirl courses and lessons using Swirlify.

### Swirl 1.1

We will demonstrate how to create Swirl courses and lessons with Swirlify. Swirl is an R package that transforms the R console into an interactive learning environment. In case you're new to Swirl, we will give you a quick overview. First, you need to load the Swirl package `library(swirl)` and then start Swirl by calling `swirl()` in R consol. As you can see, the console starts prompting with questions. We can select a Swirl course to begin, and then within that course, we can pick a lesson. Swirl provides text prompts in the console and asks you to enter specific R commands. For example, it would ask you to type in `5 + 7`. If you entered the correct answer, Swirl would move on to the next question. If you made a mistake, Swirl would provide a hint to guide you in the right direction.

Swirl offers various types of questions, and we can exit a lesson at any time by pressing the Escape key. Now, let's move on to creating Swirl lessons using Swirlify.

### Swirl 1.2

Here we are going to demonstrate how to write your own swirl courses and lessons using the swirlify package. To begin, you will need to load the swirlify package `library(swirlify)`, if it is not installed on your computer you can install it with `install.packages("swirlify")`. Swirlify is always aware of your current working directory, so make sure you set the working directory to your desired directory. Here, we will set the directory to a special folder on the desktop called "Courses," where we wish to keep our swirl courses and lessons.

You can start writing a new swirl course and lesson using the following template.


```r
setwd(file.path("~", "Desktop/Courses"))
swirlify("Lesson 1", "My First Course")
```

So we set the working directory and name the lesson "Lesson 1" and the course "My First Course". Upon executing this function, several things happen. It generates a few template files for you to create your course, then it will start the Shiny lesson where you can start authoring the app. All swirl lessons are written in YAML, which is a simple markup language. In YAML, each question is demarcated by a hyphen and is followed by key-value pairs that specify each type of question and its content. To give you a look at what we mean, let's go to my "Courses" folder after executing the above code. Inside, you'll see the course that was just created "My First Course" which has one lesson inside it named "Lesson 1". Each course is its own folder, and each lesson is its own folder inside a course.


```r
My_New_Course
- My_First_Lesson
    - lesson.yaml
    - initLesson.R
    - dependson.txt
    - customTests.R
```

Alternatively, you can use the `new_lesson()` function to create your course and lesson. With this approach, you should specify the directory where you want to create the course and lesson. Then run the `new_lesson()` function and specify the name of the lesson and course.


```r
setwd(file.path("~", "Desktop/Courses"))
new_lesson("My First Lesson", "My First Course")
```

The difference between this approach and the previous approach is that the `new_lesson()` function gives you access to the YML file through R consol, whereas the `swirlify()` function starts a Shiny app which contains YML file and it is self-explanatory. Any changes you make in the Shiny app will be reflected in the YML file. There is also a great tutorial on the swirlify package that you can access in [Youtube](https://www.youtube.com/watch?v=UPL_W-Umgjs).

In the lesson folder, the file, "customTests.R", is where you can specify your own functions for testing the correctness of swirl questions, [example](https://github.com/seankross/Test_Course/blob/master/Test_Lesson/customTests.R). The "dependson.txt" text file allows you to list the names of R packages that are on Cran, [example](https://github.com/seankross/Test_Course/blob/master/Test_Lesson/dependson.txt). This is where we check to ensure the R packages are installed before the lesson begins. The "initLesson.R" script is run before a lesson starts, allowing you to load data or create functions that will be used in the lesson, [example](https://github.com/seankross/Test_Course/blob/master/Test_Lesson/initLesson.R). Lastly, the "lesson.yaml" file is where we specify the questions for the lesson, [example](https://github.com/seankross/Test_Course/blob/master/Test_Lesson/lesson.yaml).

We recommend using RStudio for writing swirl lessons because it allows you to have a text editor and R console side by side. However, different people have different workflows. To add questions, you can use the `wq_` series of functions that come with swirl. To see the list of these questions you can just type in `wq_` in the consol and the different types will automatically show up. There are several types of questions you can include in a lesson, including message questions `wq_message()` and command questions `wq_command()`. A message question is a simple prompt that displays a message to the student. A command question prompts the student to enter R code into the console. You either just execute `wq_message()` and then edit the `put your text output here` in the YML file `Output: put your text output here` or you can execute `wq_message("Welcome to lesson 1")` and it will automatically add the message to the YML file.

When writing a command question, you specify the correct answer and a function to test the correctness of the student's answer. The function has a format like this:


```r
wq_command(output = "explain what the user must do here",
  correct_answer = "EXPR or VAL",
  answer_tests = "omnitest(correctExpr='EXPR', correctVal=VAL)",
  hint = "hint")
```

The `output` argument is the prompt that is displayed to the student. The `correct_answer` argument is the correct answer to the question. The `answer_tests` argument is a function that tests the correctness of the student's answer.The `omnitest` function is recommended for most questions. The `hint` argument is a hint that is displayed to the student if they answer incorrectly. You can either fill in the arguments with the correct values or you can just execute the function and then edit the YML file.
Here is an example of a command question:


```r
- Class: cmd_question
  Output: Add 2 and 2 together using the addition operator.
  CorrectAnswer: 2 + 2
  AnswerTests: omnitest(correctExpr='2 + 2')
  Hint: Just type 2 + 2.
```

Once you have written some questions, and you want to add the lesson to the course, you need to update the course manifest using the add to manifest function `add_to_manifest()`. This function creates a manifest file inside the course directory outside the lesson folder and it keeps track of the order of lessons in the course and prevents files that are not lessons from appearing in the lesson selection menu.
To check the lesson's formatting, use the test lesson function `test_lesson()`. If no warnings or messages are returned, the lesson passed formatting checks. To preview the lesson, use the demo lesson function `demo_lesson()`, which takes you directly to the lesson without going through swirl's menu. Once you're in the lesson, you can answer the questions and complete it. In this case, the first question is "Welcome to lesson 1," and the second question is "Add 2 and 2 using a plus operator."

### Swirl 1.3

Now that we have created and tested our first lesson, let's move on to some more complex question types that we can include in a swirl lesson. If we want to start a new lesson, we can simply close the current lesson.yaml file and create a new lesson within the same course. To confirm that we are working in the correct course, we can use the `get_current_lesson()` function, which will return information about the current lesson and course. In this case, our course is called "My First Course" and we will create Lesson 2 within it. It's important to note that the first question generated in a lesson is the meta question, which provides information about the lesson's author and organization. This question is not visible to the students. We can fill out the author and organization fields within the meta question to provide this information. Okay, let's dive into some more advanced question types. For instance, to create a multiple-choice question, we can use the `wq_multiple()` function and specify the question prompt and answer choices. Here is an example to add a multiple-choice question.


```r
wq_multiple(output = "What is the capital of Canada?",
            answer_choices = c("Toronto","Montreal","Ottawa","Vancouver"),
            correct_answer = "Ottawa",
            answer_tests = "omnitest(correctVal= 'Ottawa')",
            hint = "This city contains the Rideau Canal.")
>
```

Once we've created the question, we can add it to the course manifest and run the `test_lesson()` and `demo_lesson()` functions to ensure everything works properly.

To create a figure question, we can use the `wq_figure()` function and specify the message to display to the student, such as "This is a simple graph."
Example:


```r
wq_figure(output = "This is a simple graph.",
          figure = "sourcefile.R",
          figure_type = "new")
```

To start a new lesson in the "My First Course" course, we can close the current "lesson.yaml" file. You can use the `get_current_lesson()` function to confirm which course you are working on.

Let's start a new lesson and name it "Lesson 2" and create a multiple-choice question using the `wq_multiple()` function. We can provide the question prompt, answer choices separated by semi-colons, the correct answer, and a hint. After adding this lesson to the course manifest and running `test_lesson()` and `demo_lesson()` with no errors, we can move on to creating a figure type question. Using `wq_figure()`, we add a new figure question template with the Figure and FigureType fields. The Figure field specifies an R script that will generate the figure, while the FigureType field specifies whether the question will build on an existing figure or create a new one. We create a simple plot and save it as "fig1.R" in the lesson directory, then use `demo_lesson()` to display the plot.


```r
wq_figure(output = "simple graph", figure = "fig1.R",
          figure_type = "new")
```


```r
# fig1.R
plot(1:10)
```

We can then add another figure question to modify the plot by adding a line. We save the code for adding the line in "fig2.R" and set the FigureType to `add`. Finally, we use `demo_lesson()` to display the modified plot with the added line.


```r
wq_figure(output = "I added a line",
          figure = "fig2.R",
          figure_type = "add")
```


```r
# fig2.R
abline(h=5, col="red", lwd=2)
```

For more information on creating swirl lessons, you can visit the swirl [website](http://swirlstats.com/swirlify/). There you can the documentation. You can also find a link to the swirl course development guide, which contains more detailed information on creating swirl lessons.

### Swirl 1.4

Swirlify makes sharing a swirl course easy. We recommend three different methods for sharing a swirl course.

#### Sharing Your Course as a File

We’ve developed the .swc file type so that you can share your course as a single file. To create your .swc file follow these steps:

1. Set any lesson in the course you want to share as the current lesson using `set_lesson()`.
2. Create an .swc file using the `pack_course()` function.
   Your .swc file will appear in the same directory as the directory that contains the course folder. You can then share the .swc file with others through email, file sharing services, etc. To install the .swc file, the user can use the `install_course()` function and specify the path to the .swc file. The course will then be installed in the user’s home directory. The user can then use the `swirl()` function to start the course.

#### Sharing Your Course on GitHub

We highly encourage you to develop your course on GitHub so that you can get better support if you have questions or need assistance while developing your course.In addition, developing your course on GitHub provides the added benefit that your course will be instantly ready to distribute. Students can install your course from swirl using the
'install_course_github()' function. Make sure that your course directory is the root folder of your
git repository. For examples of courses that have been shared on GitHub you can browse some of the courses on the [Swirl Course Network](http://swirlstats.com/scn/).

#### Sharing Your Course on the Swirl Course Network

The goal of the Swirl Course Network is to list and organize all publicly available swirl courses. Visit the [homepage](http://swirlstats.com/scn/) of the SCN for more information.
After adding your course to the SCN students will be able to install your course using `install_course("[Name of Your Course]")` in swirl.

Briefly, in order to add your course to the SCN:

1. Create an .swc file for your course.
2. Fork https://github.com/swirldev/scn on GitHub.
3. Add the .swc file to your fork.
4. Add an Rmd file to your fork like this one. You can include a description of your course, authors, a course website, and how to install your course.
5. Run rmarkdown::render_site() when your current directory is set to your fork.
6. Add, commit, and push your changes to GitHub, then send us a Pull Request.

### Course Project
