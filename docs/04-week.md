# Fourth week

## Swirl Courses

### Swirl 1.1
Hello, I'm Sean Cross, and I'll demonstrate how to create Swirl courses and lessons with Swirlify. Swirl is an R package that transforms the R console into an interactive learning environment. In case you're new to Swirl, I'll give you a quick overview. First, I'll load the Swirl package and then start Swirl by using the swirl function. As you can see, the console starts prompting me with questions. We can select a Swirl course to begin, and then within that course, We can pick a lesson. Swirl provides text prompts in the console and asks me to enter specific R commands. For example, I'm asked to type in "5 + 7." If we enter the correct answer, Swirl moves on to the next question. If we make a mistake, Swirl provides a hint to guide me in the right direction. 

Swirl offers various types of questions, and we can exit a lesson at any time by pressing the Escape key. Now, let's move on to creating Swirl lessons using Swirlify.

### Swirl 1.2
I'm going to demonstrate how to write your own swirl courses and lessons using the swirlify package. To begin, you will need to load the swirlify package, which I will do now. Swirlify is always aware of your current working directory, and since my current working directory is my home folder, I need to set my directory to a special folder on my desktop called "Courses," where I like to keep my swirl courses and lessons. 

You can start writing a new swirl course and lesson with the "new_lesson" function. I will name my lesson "Lesson 1" and the course "My First Course". Upon executing this function, several things happen. First, it opens up a YAML file. All swirl lessons are written in YAML, which is a simple markup language. In YAML, each question is demarcated by a hyphen and is followed by key-value pairs that specify each type of question and its content. 

To give you a look at what I mean, let's go to my "Courses" folder. Inside, you'll see the course I just created called "My First Course" which has one lesson inside it named "Lesson 1". Each course is its own folder, and each lesson is its own folder inside a course. Additionally, the "new_lesson" function creates a few files. I will now demonstrate how to create your own swirl courses and lessons using the swirlify package. To get started, you will need to load the swirlify package. swirlify is aware of your current working directory and you can set your directory accordingly. For example, I have a special folder called "Courses" on my desktop where I like to keep some of my swirl courses and develop them. Using the "new lesson" function, you can start writing a new swirl course and lesson. In this example, I named my lesson "Lesson 1" and my course "My First Course". 

Executing the "new lesson" function creates several files. The first file, "customTests.R", is where you can specify your own functions for testing the correctness of swirl questions. The "dependson.txt" text file allows you to list the names of R packages that are on Cram. This is where we check to ensure R is installed before the lesson begins. The "initLesson.R" script is run before a lesson starts, allowing you to load data or create functions that will be used in the lesson. Lastly, the "lesson.yaml" file is where we specify the questions for the lesson. I recommend using RStudio for writing swirl lessons because it allows you to have a text editor and R console side by side. However, different people have different workflows. To add questions, you can use the "wq" series of functions that come with swirl. There are several types of questions you can include in a lesson, including message questions and command questions. A message question is a simple prompt that displays a message to the student. A command question prompts the student to enter R code into the console. When writing a command question, you specify the correct answer and a function to test the correctness of the student's answer. The "Omnitest" function is recommended for most questions. Once you have written some questions, you can test your lesson. To add a lesson to a course, you need to update the course manifest using the add_to_manifest function. This function creates a manifest file that keeps track of the order of lessons in the course and prevents files that are not lessons from appearing in the lesson selection menu. To check the lesson's formatting, use the test lesson function. If no warnings or messages are returned, the lesson passed formatting checks. To preview the lesson, use the demo lesson function, which takes you directly to the lesson without going through swirl's menu. Once you're in the lesson, you can answer the questions and complete it. In this case, the first question is "Welcome to lesson 1," and the second question is "Add 2 and 2 using a plus operator." 


### Swirl 1.3
Now that we have created and tested our first lesson, let's move on to some more complex question types that we can include in a swirl lesson. If we want to start a new lesson, we can simply close the current lesson.yaml file and create a new lesson within the same course. To confirm that we are working in the correct course, we can use the get_current_lesson function, which will return information about the current lesson and course. In this case, our course is called "My First Course" and we will create Lesson 2 within it. It's important to note that the first question generated in a lesson is the meta question, which provides information about the lesson's author and organization. This question is not visible to the students. We can fill out the author and organization fields within the meta question to provide this information. Okay, let's dive into some more advanced question types. For instance, to create a multiple-choice question, we can use the wq_multiple function and specify the question prompt and answer choices. For example, we can ask a question like "Which of these shapes has four sides?" and provide answer choices separated by semi-colons, such as "Square;Circle". We can also specify the correct answer and a hint for the student.

Once we've created the question, we can add it to the course manifest and run the test_lesson and demo_lesson functions to ensure everything works properly. 

To create a figure question, we can use the wq_figure function and specify the message to display to the student, such as "This is a simple graph." Now, let's take a closer look at some of the more complex question types that can be included in a swirl lesson. To start a new lesson in the "My First Course" course, we can close the current "lesson.yaml" file and use the "get_current_lesson" function to confirm which course we're working on. Let's name this new lesson "Lesson 2" and create a multiple-choice question using the "wq_multiple" function. We can provide the question prompt, answer choices separated by semi-colons, the correct answer, and a hint. After adding this lesson to the course manifest and running "test_lesson" and "demo_lesson" with no errors, we can move on to creating a figure type question. Using "wq_figure", we add a new figure question template with the Figure and FigureType fields. The Figure field specifies an R script that will generate the figure, while the FigureType field specifies whether the question will build on an existing figure or create a new one. We create a simple plot and save it as "fig1.R" in the lesson directory, then use "demo_lesson" to display the plot. We can then add another figure question to modify the plot by adding a line. We save the code for adding the line in "fig2.R" and set the FigureType to "add". Finally, we use "demo_lesson" to display the modified plot with the added line.
 


### Course Project