# Week 4 – Testing and File Manipulation

## Lecture Materials

<!--- [Monday Lecture Handout (Slides)](https://docs.google.com/presentation/d/13piUG-QiDoxMq8X0lbkFT8sOHKj7D2lb/edit?usp=sharing&ouid=109342588918218787603&rtpof=true&sd=true)
- [Monday Lecture Handout (PDF)](https://drive.google.com/file/d/1AJ0cpsywi0aLxS5DiKstIT2Eu8MljNHC/view?usp=sharing)
- [Wednesday Lecture Handout (Slides)](https://docs.google.com/presentation/d/13iOKAl6k-1018WpEJJIRf3UIzYnpfUdm/edit?usp=sharing&ouid=109342588918218787603&rtpof=true&sd=true)-->

### To Read/For Your Reference

- [Bash and Shell Scripting 1](https://missing.csail.mit.edu/2020/course-shell/)
- [Bash and Shell Scripting 2](https://missing.csail.mit.edu/2020/shell-tools/)

### Video Shorts

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/XJBUw3sNeuk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/hIqa1EoqIBM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/ZsCVRkR_nik" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/M_S88_2t1UE?cc_load_policy=1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Lab Tasks

As usual, we publish these ahead of time, but they aren't guaranteed to be final
until the start of lab.

This week in lab, you will find symptoms of bugs by writing tests and then
narrow down the actual bug.

### Forking a Repo

Make a fork of this repository (it's OK if it's public):

[https://github.com/ucsd-cse15l-f23/lab3](https://github.com/ucsd-cse15l-f23/lab3)

The fork button is on the upper right:

![](/images/fork-button.png)

This makes a copy of the repository in your GitHub account. 

Then, clone **the repository that you forked** (not the original!) in Visual Studio Code terminal.

<!--![Screenshot 2024-04-19 at 1 26 04 PM](https://github.com/ucsd-cse15l-s24/ucsd-cse15l-s24.github.io/assets/46422881/ca2fada1-4913-47d4-be24-b511219a9419)-->
```
git clone [URL to your forked repository]
```

**Write down in notes** - Find the exact location of the cloned repository in your computer's file system and write down the entire pathname. It is worthwhile to keep track of where cloned repos are located and to organize your computer.

There are a few relevant files for us:

- `ArrayExamples.java`
- `ArrayTests.java`
- `ListExamples.java`
- `LinkedListExample.java`
- `FileExample.java`

The files that end in `Example` or `Examples` have code in them with bugs for
you to find – in `ListExamples` and `ArrayExamples`, all the methods have bugs.
- In `LinkedListExample` at least one of the methods on `LinkedList` has a bug. 
- In `FileExample`, `getFiles` has a bug. 
  
So many 🐛s!

The file `ArrayTests.java` has some _tests_ for the methods in
`ArrayExamples.java`. It uses a library called
[JUnit](https://junit.org/junit4/) to run tests using methods called
`assertEquals` and `assertArrayEquals` and other `assert...` methods. 
(**Note:** JUnit is already included in the repository so no need to install anything) 

When we run this class with JUnit, it runs each method that has a `@Test` annotation on
it, and reports the success or failure of the `assert` calls.

Since JUnit is an external library, it requires some extra work to compile and
run. These two commands work well, and you should see output like the below when
you run them:
    
MAC USERS:
```
local $ javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
local $ java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
..
Time: 0.006

OK (2 tests)
```
    
WINDOWS USERS:
```
local $ javac -cp ".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar" *.java
local $ java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ArrayTests
..
Time: 0.006

OK (2 tests)
```

- The `*` in the first command tells `javac` to compile *all* the `.java` files
in this directory. It's a shorthand for writing them all out, so it's a useful
notation to start using now whenever we have several Java files to compile.
- The `-cp` command-line argument stands for "classpath". Java uses this
command-line argument to know where to look for classes. It takes paths
separated by `:` / `;` (dependent on your operating system), so the first place it will look is `.`, the current directory.
After that, it will look for classes in the two `.jar` files in the `lib`
directory. A `.jar` file is like a `.zip` file of a bunch of classes, and Java
knows how to work with them.
- While you might think the `..` in the output below `JUnit` has something to do
with a path, it's actually printing a `.` for each test that runs. So if you run
hundreds of tests, you can kinda watch the progress by seeing how the dots count
up.

**Task with your group:** Try running the command of the operating system that *isn't*
yours. (For example, a MAC user trying the Windows command and vise-versa) *Observe* the
output and *discuss* with your partner/group what happens and why? 

### Symptoms and Failure-inducing Inputs

#### Array Methods

The two tests we wrote for you in `ArrayTests.java` pass, but the two implementations of *reverse* methods in `ArrayExamples.java` have bugs! Write more tests in `ArrayTests.java` to demonstrate that the two methods, `reverseInPlace` and `reversed`, have bugs, and identify the bugs.

**Write down in notes** - For each, what was the failure-inducing input (the
test)? What was the symptom (the output when the test failed)? What was the bug
(the problem in the code)? Be as specific as possible when adding the following down to your notes:
1. The code for your tests (copy it into the doc)
2. The output corresponding to each symptom
3. The code change you need to make to fix the bug


**Checkpoint** – After fixing the reverse methods, we want to save these changes to your Github repo. It's really useful to checkpoint your work this way; you will be able to see in the commit history every time you make a change and commit.

In order for these changes to appear on GitHub, we need to **commit** and **push** them. 

First, be sure you are in the correct directory, `lab3`.

After making changes to your files, you need to add them to the staging area. This tells Git which changes you want to include in the next commit. To add all changes in the current directory and its subdirectories to the staging area, run:
```
git add .
```
If you only want to add specific files, you can replace `.` with the file names.

Next, you need to commit them to the repository, which essentially is to save a snapshot of your changes. To commit, run:
```
git commit -m "Some concise message describing the change"
```
Before we can **push** we will need to generate a GitHub Personal Access Token. To do that go to GitHub again and dlick your icon on the top right hand corner and click on **Settings** as shown in this image ![GitHub Settings](image.png)

Next, we will scroll all the way down until we see **<> Developer Settings** as shown in this image: ![GitHub Developer Settings](image-1.png). Click on it and you will see a new page, and this time we will click on **Personal Access Tokens** and **Tokens (classic)** as shown in this image: ![GitHub Personal Access Tokens](image-2.png). Next we will **Generate a new token** as shown in the following image: ![GitHub Generate new token](image-3.png) and click on **Generate new token (classic)** ![GitHub Generate token selection](image-4.png) Once there, go ahead and authenticate. You will then see a new screen. Here you can name your token, I used "My First Token", set it to expire in 90 days, and selected Full control over the repo as shown below: ![GitHub Token settings](image-5.png). Next you will want to generate your new token and you will be able to copy it from the new page as shown below. ![GitHub Generate new token](image-6.png). Next go to your terminal where you will be accessing GitHub via command line and run the following line of code: `git config --global credential.helper manager` followed by `git config --global credential.helper 'cache --timeout=7776000'` where the timeout is set in seconds and 90 days would be 60s * 60m * 24h * 90d

Next, for the changes to actually appear on GitHub, you need to **push** them. 

```
git push origin main
```

Where you will be asked for your username, which will be your GitHub username and password, where the password is your GitHub Personal Access Token (PAT). **Note: When you paste in your token you will not see any changes to your shell, but rest assured you have copied in your token, As shown below:
![GitHub Update chat-server repo](image-7.png)

Now your changes to this repository should be visible in GitHub!

You can see more documentation about git and pushing your changes here:

- [Key definitions about git](https://ucsd-cse15l-w24.github.io/week1/index.html#key-definitions)
- [Github documentation about pushing changes]()

Next, for `averageWithoutLowest`, you will do a similar process as above, making sure to note symptoms, failure-inducing inputs, and bugs. But, this time, **your lab partner will brainstorm one of the tests for you to write, describe it to you at a high level, and then you will implement it.** Complete these steps as described below.
1. **Write down in notes** - Come up with a high level description of a test that your lab partner should implement (without using any code!). Also include: Which symptom/bug is this testing for? Why is this test useful?
2. Implement and run the test devised by your lab partner

If you're having trouble thinking of tests, try starting from the smallest
possible inputs (an empty array), and then trying increasing sizes of arrays to
structure your thinking.

#### List Methods

There are two methods in `ListExamples`, each of which has a bug. For this
program, create **a new file** called `ListTests.java` with JUnit tests. In `ListTests.java`, write some tests to identify and demonstrate the bugs in `ListExamples`. You should carefully design your tests to get failing inputs, symptoms,
and eventually identify the bugs. Keep in mind that most of the time we can find
relatively *small* inputs that trigger the symptom!

Hint – if you're not sure about Java interfaces, there is [review material](https://ucsd-cse11-f21.github.io/lectures/lecture10.html), [and an online textbook with examples (free, you have to make an account)](https://stepik.org/course/100177/promo).

**Write down in notes** – Symptoms, inputs, and bugs.

**Checkpoint** – Commit and push your changes, and don't forget to add the new file! This
is one of the most common mistakes I make with `git` that is annoying for my
collaborators: I add a new file locally and forget to put it on Github for them
to see!

#### Linked List Methods

The file `LinkedListExample.java` has an implementation of a linked list that
is, in fact, buggy. We won't tell you which method(s) have the bugs. Create a
file called `LinkedListTests.java` and write tests in that file.

Note that for this case, your failure-inducing input requires a little more work
to construct: you have to build lists and try out the methods. All of that work
is part of the “failure-inducing input”, and it's useful to have it all written
down in code so that we don't have to remember it or re-type it each time we
want to run the test.

**Write down in notes** – Symptoms, inputs, and bugs.

**Checkpoint** – Commit and push your changes, and don't forget to add the new file! This
is one of the most common mistakes I make with `git` that is annoying for my
collaborators: I add a new file locally and forget to put it on Github for them
to see! This is repeated from last week.

**Reflect, write down in notes** – You've now had to create two new test files
(one for `ListExamples` and one for `LinkedListExample`). What actions did you take in
your editor to do this? How long did it take you? Could you or did you use
copy/paste effectively to avoid lots of typing? Could you or did you use the up
arrow in the terminal to “get back” earlier commands rather than typing them out
again? Any other tricks you could use to make this more painless in the future?

Discuss with your group! The long-term goal here is to learn tips and tricks to
take tasks that might be annoying 5-minute tasks and turn them into 30-second
tasks. It really changes how you think about writing tests if the process of
getting started takes less time!

#### File Methods

The file `FileExample.java` has an implementation of a method that works with
the filesystem and, fortunately for our learning, it's buggy.

This one is interesting because the definition of a "failure-inducing input" is
trickier – this program won't run without us having some files and paths
available to try! There is a comment in `FileExample.java` showing an example file structure for this program. So the first thing you may want to do is _create_ the file structure depicted in the comment in your repository! Then you can
write tests that use `FileExample.java`. You can create this just using VScode's "new
file" and "new folder" buttons/options.

To help you read and understand the program check out the `File` documentation here:

[https://docs.oracle.com/javase/8/docs/api/java/io/File.html](https://docs.oracle.com/javase/8/docs/api/java/io/File.html)

**Write down in notes** – Symptoms, inputs, and bugs. Remember that your input
is not just the code, but also the test files you created.

**Checkpoint** – Commit and push your changes, and don't forget to add the new files,
including the files you created as test input! All these files need to be a part
of the repository so that we can run the tests. (This is a particularly annoying
one to realize you missed later – the test will fail because the input data
doesn't exist!)


**Discuss** – Out of all the bugs above, which was the most interesting bug you
found? Have you ever made bugs like these yourself in your own programs? What
about having JUnit tests written might be useful one or two weeks from now?

#### Bugs and Troubleshooting

Let's test your knowledge of bugs and how to troubleshoot them!

You and your partner should design a bug that you think is _not_ trivial to
catch.  Make sure _you_ agree on what a failure-inducing input for it is. This
could be a new method you make up, or an edit to one of the existing methods in
the lab already.

**Write down in notes** - Then, with another pair who has also done this, swap
the buggy programs you designed (you can copy-paste them into the notes doc to
share). See if you can spot one another's bugs, and catch them with a
well-designed input. Were these easy or hard to catch?

Once both groups have found the issues, try again! Try to stump one another with
plausible, but tough-to-find, bugs.

Share your favorites with your team and tutor. We'll share a few of the best
ones in class.
