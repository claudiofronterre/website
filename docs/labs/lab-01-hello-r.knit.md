---
title: "Lab 01 - Hello R!"
date: "2017-01-18"
output: tint::tintHtml
link-citations: yes
---




# Introduction

<label for="tufte-mn-" class="margin-toggle">&#8853;</label><input type="checkbox" id="tufte-mn-" class="margin-toggle"><span class="marginnote"><span style="display: block;">R is the name of the programming language itself and RStudio is a convenient interface.</span></span>

The main goal of this lab is to introduce you to R and RStudio, which we will be using throughout the course both to learn the statistical concepts discussed in the course and to analyze real data and come to informed conclusions. 

<label for="tufte-mn-" class="margin-toggle">&#8853;</label><input type="checkbox" id="tufte-mn-" class="margin-toggle"><span class="marginnote"><span style="display: block;">git is a version control system (like &quot;Track Changes&quot; features from Microsoft Word on steroids) and GitHub is the home for your Git-based projects on the internet (like DropBox but much, much better).</span></span>

An additional goal is to introduce you to git and GitHub, which is the collaboration and version control system that we will be using throughout the course.

As the labs progress, you are encouraged to explore beyond what the labs dictate; a willingness to experiment will make you a much better programmer. Before we get to that stage, however, you need to build some basic fluency in R. Today we begin with the fundamental building blocks of R and RStudio: the interface, reading in data, and basic commands.

And to make versioning simpler, this is a solo lab. We require that you sit with your team mates and work through the lab with them, but we want to make sure everyone gets a significant amount of time at the steering wheel, hence we're keeping this lab an individual assignment. Next week you'll learn about collaborating on GitHub and produce a single lab report for the team.

# Getting started

Each of your assignments will begin with the following steps. You saw these once in class yesterday, they're outlined in deatil here again. Going forward each lab will start with a "Getting started" section but details will be a bit more sparse than this. You can always refer back to this lab for a detailed list of the steps involved for getting started with an assignment.

- Click on the assignment link that you should have received in your email to create your GitHub repository (which we'll refer to as "repo" going forward) for the assignment. This repo contains a template you can build on to complete your assignment.

<p><span class="marginnote shownote"><!--
<div class="figure">-->
<img src="img/01-hello-r/clone-repo-link.png" alt=" " width="265"  />
<!--
<p class="caption marginnote">--> <!--</p>-->
<!--</div>--></span></p>

- On GitHub, click on the green **Clone or download** button, select **Use HTTPS** (this might already be selected by default, and if it is, you'll see the text **Clone with HTTPS** as in the image below). Click on the clipboard icon to copy the repo URL.

<p><span class="marginnote shownote"><!--
<div class="figure">-->
<img src="img/01-hello-r/new-project-from-gh.png" alt=" " width="224"  />
<!--
<p class="caption marginnote">--> <!--</p>-->
<!--</div>--></span></p>

- Go to RStudio Cloud and into the course workspace. Create a **New Project from Git Repo**. You will need to click on the down arrow next to the **New Project** button to see this option.

<p><span class="marginnote shownote"><!--
<div class="figure">-->
<img src="img/01-hello-r/paste-gh-repo-url.png" alt=" " width="500"  />
<!--
<p class="caption marginnote">--> <!--</p>-->
<!--</div>--></span></p>

- Copy and paste the URL of your assignment repo into the dialog box:

- Hit OK, and you're good to go!

- As you make edits/updates, commit and push your changes to your repo. When you're done with the assignment make sure you've committed and pushed everything. It's ok if these words (commit, push, etc.) don't yet mean much to you, you'll get used to them very soon.

For assignments that you will work on individually, this is the process. For team assignments there will be additional steps to ensure you get ("pull") your team mates' changes before you make your own, or that you resolve "merge conflicts". We'll talk more about these next week, so for now, let's get some practice working on our own.

# Housekeeping

<label for="tufte-mn-" class="margin-toggle">&#8853;</label><input type="checkbox" id="tufte-mn-" class="margin-toggle"><span class="marginnote"><span style="display: block;">Your email address is the address tied to your GitHub account and your name should be first and last name.</span></span>

In this first lab we need to take care of some unpleasant, but required, housekeeping. Namely, we need to configure your git so that RStudio can communicate with GitHub. This requires two pieces of information: your email address and your name.

To do so, follow these steps:

- Go to the *Terminal* pane
- Type the following two lines of code, replacing the information in the quotation marks with your info:


```bash
git config --global user.email "your email"
git config --global user.name "your name"
```

For example, for me these are


```bash
git config --global user.email "mine@stat.duke.edu"
git config --global user.name "Mine Cetinkaya-Rundel"
```

To confirm that the changes have been implemented, run the following


```bash
git config --global user.email
git config --global user.name
```

Ok, now we're done with that, and we never have to do it again.

# Warm up

Before we introduce the data, let's warm up with some simple exercises.

- **Project name:** Currently your project is called *Untitled Project*. 😢 Update the name of your project to be "Lab 01 - Hello R".

<div class="figure fullwidth">
<img src="img/01-hello-r/untitled-project.png" alt=" " width="493"  />
<p class="caption marginnote shownote"> </p>
</div>

- **YAML:** Open the R Markdown (Rmd) file in your project, change the author name to your name, and knit the document.

<div class="figure fullwidth">
<img src="img/01-hello-r/yaml-raw-to-rendered.png" alt=" " width="930"  />
<p class="caption marginnote shownote"> </p>
</div>

**Note:** The top portion of your R Markdown file (between the three dashed lines) is called YAML. It stands for "YAML Ain't Markup Language". It is a human friendly data serialization standard for all programming languages. All you need to know is that this area is called the YAML (we will refer to it as such) and that it contains meta information about your document.

- **Commiting changes:** Then Go to the Git pane in your RStudio.

If you have made changes to your Rmd file, you should see it listed here. Click on it to select it in this list and then click on **Diff**. This shows you the *diff*erence between the last committed state of the document and its current state that includes your changes. If you're happy with these changes, write "Update author name" in the **Commit message** box and hit **Commit**.

<div class="figure fullwidth">
<img src="img/01-hello-r/update-author-name-commit.png" alt=" " width="889"  />
<p class="caption marginnote shownote"> </p>
</div>

**Note:** You don't have to commit after every change, this would get quite cumbersome. You should consider committing states that are *meaningful to you* for inspection, comparison, or restoration. In the first few assignments we will tell you exactly when to commit and in some cases, what commit message to use. As the semester progresses we will let you make these decisions.

- **Pushing changes:** Now that you have made an update and committed this change, it's time to push these changes to the web! Or more specifically, to your repo on GitHub. Why? So that others can see your changes. And by others, we mean the course teaching team (your repos in this course are private to you and us, only). 

In order to push your changes to GitHub, click on **Push**. This will prompt a dialogue box where you first need to enter your user name, and then your password. This might feel cumbersome. Bear with me... We *will* teach you how to save your password so you don't have to enter it every time. But for this one assignment you'll have to manually enter each time you push in order to gain some experience with it.

- **Thought exercise:** For which of the above steps (changing project name, making updates to the document, committing, and pushing changes) do you need to have an internet connection? Discuss with your teammates.

# Packages

In this lab we will work with the awesome Datasaurus Dozen datasets. These datasets show us why visualisation is important – summary statistics can be the same but distributions can be very different. 

We will begin by first installing this package, and then loading it. To do so, run the following two commands in the **Console**.

- To install the package type `install.packages("datasauRus")`.
- Then, load the package with `library(datasauRus)`.

Additionally, we will use the tidyverse, so let's install and load that as well:


```r
install.packages("tidyverse")
library(tidyverse)
```

# Data

In this lab we will work with the awesome Datasaurus Dozen datasets. These datasets show us why visualisation is important – summary statistics can be the same but distributions can be very different. 

This package includes a dataset called `datasaurus_dozen`. To find out more about the dataset, type the following in your Console: `?datasaurus_dozen`. A question mark before the name of an object will bring up its help file.

**Exercise 1:** Based on the help file, how many rows and how many columns does the `gapminder` file have? What are the variables included in the data frame?

Let's take a look at what these 12 datasets are. To do so we can make a *frequency table* of the dataset variable:


```r
datasaurus_dozen %>%
  count(dataset) %>%
  print(13)
```

```
## # A tibble: 13 x 2
##       dataset     n
##         <chr> <int>
##  1       away   142
##  2   bullseye   142
##  3     circle   142
##  4       dino   142
##  5       dots   142
##  6    h_lines   142
##  7 high_lines   142
##  8 slant_down   142
##  9   slant_up   142
## 10       star   142
## 11    v_lines   142
## 12 wide_lines   142
## 13    x_shape   142
```

<label for="tufte-mn-" class="margin-toggle">&#8853;</label><input type="checkbox" id="tufte-mn-" class="margin-toggle"><span class="marginnote"><span style="display: block;">Matejka, Justin, and George Fitzmaurice. &quot;Same stats, different graphs: Generating datasets with varied appearance and identical statistics through simulated annealing.&quot; Proceedings of the 2017 CHI Conference on Human Factors in Computing Systems. ACM, 2017.</span></span>

The original Datasaurus (`dino`) was created by Alberto Cairo in [this great blog post](http://www.thefunctionalart.com/2016/08/download-datasaurus-never-trust-summary.html). The other Dozen were generated using simulated annealing and the process is described in the paper *Same Stats, Different Graphs: Generating Datasets with Varied Appearance and Identical Statistics* through Simulated Annealing by Justin Matejka and George Fitzmaurice. In the paper, the authors simulate a variety of datasets that the same summary statistics to the Datasaurus but have very different distributions.

# Data visualization and summary

**Exercise 2:** Plot `y` vs. `x` for the `dino` dataset. Then, calculate the correlation coefficient between `x` and `y` for this dataset.

Below is the code you will need to complete this exercise. Basically, the answer is already given, but you need to include relevant bits in your Rmd document and successfully knit it and view the results.

<label for="tufte-mn-" class="margin-toggle">&#8853;</label><input type="checkbox" id="tufte-mn-" class="margin-toggle"><span class="marginnote"><span style="display: block;">Start with the <code>datasaurus_dozen</code> and filter for observations where <code>dataset == &quot;dino&quot;</code>. Then, pipe the resulting filtered dataframe to <code>ggplot</code>, place the <code>x</code> variable on the x-axis and the y-variable on the y-axis, and use <code>point</code>s to plot the data.</span></span>


```r
datasaurus_dozen %>%
  filter(dataset == "dino") %>%
  ggplot(mapping = aes(x = x, y = y)) +
    geom_point()
```

<div class="figure fullwidth">
<img src="lab-01-hello-r_files/figure-html/unnamed-chunk-12-1.png" alt=" " width="672"  />
<p class="caption marginnote shownote"> </p>
</div>

The summary statistic we will be using is the correlation coefficient. Correlation coefficient, often referred to as $r$ in statistics, measures the linear association between two variables. You will see that some of the pairs of variables we plot do not have a linear relationship between them. This is exactly why we want to visualize first: visualize to assess the form of the relationship, and calculate $r$ only if relevant. In this case, calculating a correlation coefficient really doesn't make sense since the relationship between `x` and `y` is definitely not linear -- it's dinosaurial!

But, for illustrative purposes, let's calculate correlation coefficient between `x` and `y`.

<label for="tufte-mn-" class="margin-toggle">&#8853;</label><input type="checkbox" id="tufte-mn-" class="margin-toggle"><span class="marginnote"><span style="display: block;">Start with the <code>datasaurus_dozen</code> and filter for observations where <code>dataset == &quot;dino&quot;</code>. Then, calculate a summary statistic that we will call <code>r</code> as the <code>cor</code>relation between <code>x</code> and <code>y</code>.</span></span>


```r
datasaurus_dozen %>%
  filter(dataset == "dino") %>%
  summarize(r = cor(x, y))
```

```
## # A tibble: 1 x 1
##             r
##         <dbl>
## 1 -0.06447185
```

*This is a good place to pause, commit changes with the commit message "Added answer for Ex 2", and push.*

**Exercise 3:** Plot `y` vs. `x` for the `star` dataset. You can (and should) reuse code we introduced above, just replace the dataset name with the desired dataset. Then, calculate the correlation coefficient between `x` and `y` for this dataset. How does this value compare to the `r` of `dino`?

*This is another good place to pause, commit changes with the commit message "Added answer for Ex 3", and push.*

**Exercise 4:** Plot `y` vs. `x` for the `circle` dataset. You can (and should) reuse code we introduced above, just replace the dataset name with the desired dataset. Then, calculate the correlation coefficient between `x` and `y` for this dataset. How does this value compare to the `r` of `dino`?

*You should pause again, commit changes with the commit message "Added answer for Ex 2", and push.*

**Exercise 5:** Finally, let's plot all datasets at once. In order to do this we will make use of facetting.


```r
ggplot(datasaurus_dozen, aes(x = x, y = y, color = dataset))+
  geom_point()+
  theme(legend.position = "none") +
  facet_wrap(~ dataset, ncol = 3)
```

And we can use the `group_by` function to generate all the summary correlation coefficients.


```r
datasaurus_dozen %>%
  group_by(dataset) %>%
  summarize(r = cor(x, y)) %>%
  print(13)
```

*Yay, you're done! Commit all changes, use the commit message "Done with Lab 1! 👍" (including the emoji if you know how to use emojis on your computer), and push. Before you wrap up the assignment, make sure all documents are updated on your GitHub repo.*
