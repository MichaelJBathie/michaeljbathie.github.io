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
- Latest devkit release of Ruby --> [Click me to download](https://rubyinstaller.org/downloads/)
    - This will install Ruby's package manager 'gem' for you. Open a command terminal and type: ```gem install bundler```
- GCC compiler --> [Follow this video tutorial](https://www.youtube.com/watch?v=sXW2VLrQ3Bs)
- Chocolatey package manager --> [Follow this video tutorial](https://www.youtube.com/watch?v=-5WLKu_J_AE)
    - Now use the command terminal against and type: ```choco install make```
- Git Bash --> [Click me to download](https://git-scm.com/download/win)

Final check! You should be able to type `ruby -v`, `gem -v`, `gcc -v`, `g++ -v`, and `make -v` without any errors in the command terminal. They should all return version numbers

## Instructions

### Create GitHub Repository 

This will essentially be a container to hold our code and keep track of its versions

<details><summary><b>Show Instructions</b></summary>

1. Go to github.com and navigate to "Your repositories"
2. From here create a new repository with the name YOUR-USERNAME.github.io
3. You now have the repository that will hold your website

</details>

### Setting up the site

Here we'll execute all the commands necessary to get the base site code in our local repository


<details><summary><b>Show Instructions</b></summary>

1. Open git bash and navigate to the folder your source files are stored in (if you already have a local copy) or where you want them to be stored (if you don't have a local copy).
   -  If you're unfamiliar with the command like you can use the ```ls``` command to list all the contents of the directory you're in and the ```cd DIRECTORY``` command to to 'change directory' into your desired directory.

        ![Git Bash example](./gifs/gitbash.gif)

<br>

2. Initialized your repository
    ```sh
        $ git init REPOSITORY-NAME
    ```
   - REPOSITORY-NAME is the name of *your* repository

<br>
 
3. ```cd``` into that new directory titled with your repository name and type:
    ```sh
        $ jekyll new --skip-bundle .
    ```
    - This creates a jekyll site in your current directory
    - Don't forget the period at the end of that command! It tells the command to be executed in the current directory.

<br>

4. Now we're going to make some changes to the Gemfile that was created. This can be done in one of two ways: use vim that comes with git bash (`vi Gemfile`), or just open it as a text file in your local folder structure. I recommend vim in the long term as it's a very powerful text editor, but has a steep learning curve. Try [this](https://www.openvim.com/) if you want to learn more.

<br>

5. Now that you have the file open add a `#` in front of the `gem "jekyll` line to comment it out.
   - Before: ![Before adding #](./images/before.png)
   - After: ![After adding #](./images/after.png) 

<br>

6. Now uncomment the `gem github-pages` line and change it to `gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins` with GITHUB-PAGES-VERSION being the latest version of github-pages found [here](https://pages.github.com/versions/)
    - Before: ![Before change](./images/before2.png)
    - After: ![After change](./images/after2.png)
      - Here, 219 was the latest version. It might be different for you

<br>

7. Save and close that. Back in your git bash instance in your repository's directory type:
    ```sh
        $ bundle install
    ```

</details>

### Getting our site on github

Here we're moving all our code onto github so others can see and github can begin hosting our new site!

<details><summary><b>Show Instructions</b></summary>

1. Start tracking all of the changes. From your repository's directory:
    ```sh
        $ git add .
    ```
    - Again, remember the '.'.
    - This command will start tracking all the changes in the current directory
  
<br>

2. Tell git that you want to bundle all of your current changes
    ```sh
        $ git commit -m 'Initial Jekyll site'
    ```
    - The '-m' and string there are saying we watch to attach this message to the commit

<br>

3. Now tell GitHub that this folder is going to be a remote repository.
    ```sh
        $ git remote add origin https://github.com/USER/REPOSITORY.git
    ```
    - USER is your username
    - REPOSITORY is the name of your repository

<br>

4. Time to actually move and save those change onto GitHub.
    ```sh
        $ git push -u origin BRANCH
    ```
    - Branch will be the name of your latest stable version. Convention is normally 'main' or 'master'.

</details>

### Testing the site

Let's see if our site is being hosted and rendered correctly

<details><summary><b>Show Instructions</b></summary>

1. Go to your repository on github.com then Settings>Pages> and there should be a link to your website

![Check website tutorial](./gifs/check_site.gif)

</details>

### Configuring the website

Now we'll be focusing on what's on the website and some things you can change. From here on we can simply work from the github repository on github.com to make things a bit easier

<details><summary><b>Show Instructions</b></summary>

1. First lets make sure the resume is formatted correctly in markdown. Open your markdown resume in Visual Studio Code and preview the markdown
    
    ![How to preview markdown](./gifs/markdown_preview.gif)

<br>

2. To get your resume on the homepage open up index.markdown, click edit, and replace everything there with your resume

<br>

3. Change the values in _config.yml that you want to change
    - This includes things like the website title and description. All are labelled in the _config.yml file

<br>

4. Your website should now properly display your resume. Check back at the link in Settings>Pages to see!
    - Sometimes it may take a bit to update, if nothing it happening try to give it ~5 minutes

</details>

## More Resources
- [Markdown tutorial](https://www.markdowntutorial.com/)
- [Jekyll tutorial](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB)
- [Vim tutorial](https://www.openvim.com/) 
- [Etter's Modern Technical Writing](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS)

<br>

## Authors and Acknowledgments
I, Michael Bathie is the one who wrote this documentation. Special thanks to my group members Faith De Leon, Koye Fatoki, Tuan Le, and Andy Tan for help with the peer editing process. And thanks to the authors of github-pages' [slate theme](https://github.com/pages-themes/slate).

<br>

## FAQ
Q: Can I host the website on my own machine for testing?  
A: Yes you can! Just use the command terminal to navigate into you project repository and type:  

    $ bundle exec jekyll serve

- The site should now be deployed on http://127.0.0.1:4000/
- <span style="color:red">NOTE:</span> you may need to change the 'theme' tag in _config.yml to 'remote_theme' and change the value to the github repository. But generally this is only needed for third-party themes

<br>

Q: Why is my website a blank page after changing the theme?  
A: What likely happned is your website before the themes change used certain layouts (say a 'home' layout) while the new themes doesn't use that layout (say it uses 'index'). Go to the github page of the theme and see what layouts they use. 
- I'll also direct you to the Jekyll tutorial in [More Resources](#more-resources) to learn more about layouts
    
