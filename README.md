# Want to host your own static website?

## What's the purpose of this README?
Exactly what the title says. I've attempted to host a few websites before and the learning curve at first is pretty steep. So, my entire goal will be to help anyone who's a little lost in the process. Going from beginning to end I'll try to explain the process step by step and I'll include some pointers from Andrew Etter's book Modern Technical Writing.

For some specifics, our software stack will be GFM (GitHub flavoured markdown) for formatting text, Visual Studio Code as a markdown editor, GitHub Pages to host our site, and Jekyll as the static site generator.

If any of those terms confused you I'll give a brief explanation. Markdown is a lightweight markup language that allows you to format text. First of all, this is nice because it's free. Second, it will always work. We can throw markdown into any markdown interpreter (any webpage) and it'll just work. Visual Studio Code is simply a program to write text in with some nice features like markdown previews. Github is a version control system which basically keeps track of all the versions of our code. It is very useful for projects being worked on by more than one person, but is also nice for solo tasks. Github Pages has the server we will host our website on so we don't have to pay for a server or run it on our own machine. Finally, Jekyll will create a lightweight static website template for us that we can easily edit. Static websites are websites that always provide the same pages when someone visits them. They don't need to interact with a database or anything else to determine what to provide. We prefer these because they are cheaper (or even free) to host and they are much faster than dynamic websites.

## Prerequisites
- GitHub account
- GitHub Pages account
- Resume formatted in Markdown (see More Resources to learn more about Markdown)
- Visual Studio Code --> [Click me to download!](https://code.visualstudio.com/)

## Instructions

### Create GitHub Repository to hold site code
1. Go to github.com and navigate to "Your repositories"
2. From here create a new repository with the name YOUR-USERNAME.github.io
3. You now have the repository that will hold your website

### Getting ready for jekyll
1. Install the latest devkit release of ruby from [here](https://rubyinstaller.org/downloads/)
2. That ruby install should install gem for you which is ruby's package manager. Now we can open a command terminal and type `gem install bundler`
3. Now we need the gcc compiler. This can be a little annoying so follow [this](https://www.youtube.com/watch?v=sXW2VLrQ3Bs) video tutorial.
4. Follow [this](https://www.youtube.com/watch?v=-5WLKu_J_AE) video to install the chocolately package manager
5. Now using chocolatey type `choco install make` into your command terminal
6. After all of this installing you should be able to type `ruby -v`, `gem -v`, `gcc -v`, `g++ -v`, and `make -v` without any errors. They should all give version numbers
7. Now you can download [Git Bash](https://git-scm.com/download/win) which is a Bash command like interface to interact with your git repositories.

### Setting up the site
1. Open git bash. If you don't already have a local copy of your repository, navigate to the folder you want to store the source files in. The commands you'll want to know for this are `ls` and `cd` for listing everything in the current folder and change directory to do exactly that. So, in git bash say I want to store my source files in `C:\Users\User\Documents\testfolder`, I would type `cd Documents/testfolder/`.
2. If you haven't initialized your repository (which you shouldn't have if you've been following this exactly) type `git init REPOSITORY-NAME`. Now `cd` into that folder
3. Time to create the site! Type `jekyll new --skip-bundle .` (don't forget the period in that command! It executes the command in the current directory!). This will create a jekyll site in the current directory
4. Now we're going to make some changes to the Gemfile that was created. This can be done in one of two ways: use vim that comes with git bash (`vi Gemfile`), or just open it as a text file in your local folder structure. I recommend vim in the long term as it's a very powerful text editor, but has a steep learning curve. Try [this](https://www.openvim.com/) if you want to learn more.
5. Now that you have the file open add a `#` in front of the `gem "jekyll` line to comment it out.
6. Now uncomment the `gem github-pages` line and change it to `gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins` with GITHUB-PAGES-VERSION being the latest version of github-pages found [here](https://pages.github.com/versions/)
7. Save and close that. Back in your git bash instance in your repository's directory type `bundle install`

### Getting our site on github
1. Type `git add .` to add our changes to the current commit then `git commit -m 'The initial site with Jekyll!` to add that commit to our next push.
2. Now we need to add this as a remote repository so type `git remote add origin https://github.com/USER/REPOSITORY.git`. USER is the username of the repository owner and REPOSITORY is the name of the repository.
3. Now to push our changes `git push -u origin BRANCH`. I personally name the BRANCH 'master'

### Testing the site
1. Now in your repository on github go to settings then pages.
2. It should say your site is publish and you can check it out!

### Set up the resume
1. First we can make sure the resume is being displayed correctly. Open it in Visual Studio Code and click the button in the top right with 2 columns and a magnifying glass. This allows you to preview the markdown.
2. If everything is looking good them lets make a few small starter adjustments to the website. First lets change the values in `_config.yml`. Think of these like some global variables. You can change most of them to whatever you feel most appropriate.
3. Now go into the posts folder and open the post Jekyll made for us. Change the title and category to what you want. Then, replace all the content with your resume.
4. Now back in git bash lets add those changes `git add _config.yml ` and `git add _posts/`
5. commit them `git commit -m 'added resume to website`
6. and push `git push origin master`, master is what I named my branch
7. It might take a bit to update but if you go to your website now and click on the post you'll see your resume!

### To consider after deployment
1. For some more advanced editing needs to can try this [jekyll tutorial](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB).
2. If you'd like to test new features you can actually deploy the website locally on your own machine. In a terminal navigate to your repository's folder. Then type `bundle exec jekyll serve`. Your website should deply to http://127.0.0.1:4000/

## More Resources
- [Markdown tutorial](https://www.markdowntutorial.com/)
