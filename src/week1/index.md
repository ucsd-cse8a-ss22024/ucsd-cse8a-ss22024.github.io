# Week 1 – GitHub, PrairieLearn, Variables, String Functions and Operators

## Lecture Materials

- [Monday Lecture & Discussion Notes (PDF)](https://drive.google.com/file/d/1heSQZJd1mWS3z6JV8f2ffFuHoAjEYlNt/view?usp=sharing)
- [Monday Colab Notebook](https://colab.research.google.com/drive/1sjCAChvyubvIzYFHw646Re8mkzSCS6bY?usp=sharing)
- [Tuesday Slides (PDF)](https://drive.google.com/file/d/1v4HYi01Ec9_H6yXJZsS1pyBnzi3PplLH/view?usp=sharing)
- [Tuesday Lecture Handout (PDF)](https://drive.google.com/file/d/1JO_NZiKmnqYod221WzlTje-cL0Y0wJMh/view?usp=sharing)
- [Wednesday Prints&BasicArithmetic Colab Notebook](https://colab.research.google.com/drive/14CRcBD7GUWOH8O-srJtLNZshO1t9tgvM?usp=sharing)
- [Wednesday Prints&BasicArithmetic2 Colab Notebook](https://colab.research.google.com/drive/10GnujOhq7tfF3EAiAdWL35xrVPlRN1vy?usp=sharing)
- [Wednesday Swapping&MoonWeight Colab Notebook](https://colab.research.google.com/drive/1qopr8ne6a0t8MjizELZS8EUEZvKX94WL?usp=sharing)
- [Wednesday Lecture Handout (PDF)](https://drive.google.com/file/d/1Owz_s2-uJqBDsKdmVe79SBd_Gd2css8T/view?usp=drive_link)
- [Thursday Input&Output Colab Notebook](https://colab.research.google.com/drive/1lWpwTPRnrJKsI5RQSpc3_xaUfaaDsJDE?usp=sharing)

## Part 1: Getting to Know Your Peers, Ice Breaker Activity (5 mins)

We will split into groups of 3-4 students. Choose your groups wisely, as these are your groups for the rest of the quarter! You will have a tutor or TA assigned to your group for help.

In your groups, share:
- How you'd like people to refer to you (pronounce your name/nickname, pronouns like he/her/they, etc)
- Your major
- One of:
    - A UCSD student organization you're a member of or interested in
    - Your favorite place you've found on campus so far
    - A useful campus shortcut or trick you know
- Your answer to the following question. Discuss why you chose that answer. ![Image](../images/rulers.png)

## Part 2: Setting up a GitHub Account

Having a professional portfolio website for yourself can be useful in many, many
ways. It's a useful URL to put at the top of your resume/CV where potential
employers can learn more about you.  Lots of great work in CS is published only on
someone's personal page, or is at least most accessible there.  Most CS faculty
have such a page ([just](https://roseyu.com/) [a
few examples](https://cseweb.ucsd.edu/~tzli/) [from new](http://kvaccaro.com/) CSE
faculty), for example.

Github ([https://www.github.com](github.com)) is a web service for storing and
sharing code, along with a huge number of services surrounding that code. It
uses a tool and protocol called `git` [https://git-scm.com/](https://git-scm.com) to store and
retrieve that code.

If you do not have a GitHub account already, please go ahead and create one now! Ask your TAs and tutors if you have any questions about setting it up.

## Part 3: GitHub Codespaces

GitHub Codespaces is a great way to quickly set up a programming environment directly from GitHub.

**Important Note:** Make sure you apply for your Github Student Account in order to get access to the codespaces (which comes with the GitHub Student Developer Pack). You can sign up [here](https://education.github.com/discount_requests/application)! This may take a few days, so if you are not yet approved, you will not be able to create a Codespace this week. However, please make sure to apply for it today, since we will be using Codespaces in the future.

*Once you have set up Codespaces,* go to this [repository](https://github.com/ucsd-cse8a-ss22024/lab1) on GitHub. Click “<> Code”, click then "Codespaces", then "Create codespace on main".
Now, you have a full programming development environment, which you can use to edit files and run code!


## Part 4: Introduction to PrairieLearn

PrairieLearn is an platform where you will be completing programming assignments and skill demonstrations. For today's lab, log into [PrairieLearn](https://www.prairielearn.com/). You will need to make an account if you haven't done so already! Make sure to select CSE8A SSII2024 when you enroll. 

Navigate to the CSE 8A course and click on "Lab 1". There are several questions to work through, which you may do in pairs. As always, ask your tutors or TA if you have any questions!

<!--
- [Tuesday Colab Notebook]()
- [Wednesday Lecture Handout (Slides)]()
- [Wednesday Lecture Handout (PDF)]()
- [Wednesday Colab Notebook]()
- [Thursday Lecture Handout (Slides)]()
- [Thursday Lecture Handout (PDF)]()
- [Thursday Colab Notebook]()
-->
<!--
## Related Links

- [About Git](https://docs.github.com/en/get-started/using-git/about-git)
- [Github](https://github.com/)
- [Github Pages](https://pages.github.com/)
- [Github Desktop](https://desktop.github.com/)
- [Markdown cheat sheet](https://commonmark.org/help/)
- [What is Markdown?](https://www.markdownguide.org/getting-started/)
- [Git](https://git-scm.com/)
- [Lab Doc](https://docs.google.com/spreadsheets/d/1otg_99XZKDlf7_rpDagsQmmb3jqUd0qvWUjhWcX-sVY/edit?usp=sharing)

## Key Definitions

- **git repository**: A folder that tracks the history of edits to its files
- **Github repository**: A git repository online, like a Google Drive folder with history
- **Github pages**: A service that takes a Github repository and builds a
website from it (usually relying on conventions, like `index.md`)
- **Markdown**: A way to write plain text files with a little bit of formatting
- **commit**: A set of changes to a file or multiple files in a repository. A
repository history is made up of commits
- **git clone**: A git action to copy a repository from one place to another
(usually from somewhere like Github to our computer). Copies the contents of the
folder _and_ the entire history – the whole repository.
- **git commit**: A git action to take some changes we've made to files and
turn them into a commit in the repository's history
- **git push**: A git action to send commits from one place to another (usually
from our computer to Github)

## Lab Tasks

In this lab you'll make a professional website for yourself where you can post
your lab reports for the course. Please contact the instructor
(`esolares@ucsd.edu`) if for
personal privacy or security reasons you do not want to publish a public
website, even under a pseudonym.

### Part 1 – Meet Your Group!

We will split into groups of 5-8 students. For week 1, you may sit
wherever you want and choose who you want to work with. Starting week 2, we will have
assigned seating and groups. These
groups will be somewhat stable throughout the quarter, though some small changes
will likely happen. You will have a tutor or TA assigned to your group for help
and discussion.

Your discussion leader (the tutor/TA in your lab) will share a Google Doc with
your group where you can fill in notes as you work; this document is only for
your group. Your discussion leader will _not_ take notes for you. 

**Write down in notes**: In your groups, share, and note in the running notes
document (discussion leaders, you answer these as well!):

- How you'd like people to refer to you (pronounce your name/nickname, pronouns
like he/her/they, etc)
- Your major
- One of:
    - A UCSD student organization you're a member of or interested in
    - Your favorite place you've found on campus so far
    - A useful campus shortcut or trick you know
- Your answer to the following question. Discuss why you chose that answer. ![Image](../../images/rulers.png)

### Part 2 – Opening [Google Colab](https://colab.research.google.com/)

### Part 3 - Opening [Prairielearn.com](http://us.prairielearn.com/)
