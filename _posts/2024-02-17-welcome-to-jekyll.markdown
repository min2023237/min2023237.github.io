---
layout: post
title: "My Github Pages is ready."
date: 2024-02-17 12:10:20 +0900
description:  # Add post description (optional) # 구글에서 검색했을 때 나오는?
img:  # Add image post (optional)
fig-caption: #
tags: [Github, Pages, Blog]
---
After countless hours of installing, deleting, and reinstalling, the moment has finally arrived:my GitHub Pages is officially up and running. This journey, filled with both challenges and discoveries, marks a significant milestone in my personal and professional development. In this post, I want to share the process of creating GitHub Pages. <br><br><br>

### Why GitHub Pages?
Before sharing my own story, I want to explain why I chose GitHub Pages instead of other blogging platforms available. 

#### Seamless Integration with GitHub:
GitHub Pages offers seamless integration with GitHub, enabling developers to easily manage and showcase their projects alongside their code without the need to switch between different platforms or services.

#### Customization and Control:
Unlike many blogging platforms that limit your ability to alter the look and feel of your site, GitHub Pages provides the flexibility to fully customize your site's design.

#### Cost-Effective and Scalable:
GitHub Pages offers an incredibly cost-effective solution for hosting your site. There are no hosting fees, and you can use a custom domain at no extra cost.
<br><br><br>

### The Process
Creating a GitHub Pages site involves a few key steps, including installing Ruby, setting up Jekyll, and applying a theme to make your site visually appealing. Here's a concise guide to get you started on launching your own GitHub Pages site:

#### Step 1: Install Ruby
The first step is to install Ruby, as Jekyll, the engine behind GitHub Pages, is built with Ruby. Ensure your system has Ruby installed by running `ruby -v` in your terminal. If Ruby is not installed, download and install it from the official Ruby website.
<div style="text-align:center;">
        <img src="/assets/img/2024-02-17-welcome-to-jekyll/ruby-installer.jpg" width="500" height="300">
</div>


#### Step 2: Install Jekyll
Once Ruby is installed, the next step is to install Jekyll using gem, Ruby's package management tool. You can install jekyll and bundler (the Ruby package manager) by running the following command in GitBash:

{% highlight Bash %}
gem install bundler
gem install github-pages
gem install jekyll
{% endhighlight %}

If you encounter the following **<span style="color:red">error</span>** during jekyll installation:

{% highlight Bash %}
ERROR:  Error installing jekyll:
        "sass" from sass-embedded conflicts with installed executable from sass
Successfully installed webrick-1.8.1
Successfully installed google-protobuf-3.25.3-x64-mingw-ucrt
Temporarily enhancing PATH for MSYS/MINGW...
Building native extensions. This could take a while...
{% endhighlight %}

Run the following command to see all the gems installed on your system:

{% highlight Bash %}
gem list
{% endhighlight %}

You will most likely be able to find `jekyll`, and you don't need to install it. So you can just move on to the next step.


#### Step 3: Create a New Repository and Clone it
Create a new repository on GitHub, naming it `(your Github username).github.io`. After the repository is created, clone it to your local machine in your desired location using the git clone command.

{% highlight Bash %}
git clone `Repository URL`
{% endhighlight %}

#### Step 4: Choose and Apply a Theme
Discover a wide range of themes on the [Jekyll Themes website](https://jekyllthemes.io). After selecting a theme that suits your preferences, access its GitHub page through the provided "Get [Theme Name] on GitHub" link, and then download the theme's source code as a ZIP file. UnZip the file and copy its contents into the root directory of your cloned repository.
<div style="text-align:center;">
        <img src="/assets/img/2024-02-17-welcome-to-jekyll/move-files.jpg" width="500" height="300">
</div>

#### Setp 5: Build and Test Your Site Locally
After Successfully cloning the repository to your local machine, the next step is to navigate into the cloned repository directory. Open Git Bash and execute the following commands:
{% highlight Bash %}
cd `path/to/your/cloned/repository`
{% endhighlight %}
Make sure to replace `path/to/your/cloned/repository` with the actual path to your cloned repository. 

Next, run the following commands in your Git Bash:
{% highlight Bash %}
bundle install
bundle exec jekyll serve
{% endhighlight %}

The `bundle install` command, utilizing Bundler, installs all gems and dependencies listed in your project's Gemfile, ensuring your environment matches the project's requirements. The Gemfile details the necessary Ruby gems and their versions.

After installation, `bundle exec jekyll serve` compiles your site and launches a local server. To view your site, navigate to `http://localhost:4000` in your web browser.


#### Step 6: Publish Your Site to GitHub Pages
After testing your site locally and you're satisfied with how it looks, it's time to publish it to GitHub Pages. First, let's adjust the baseurl and url in the _config.yml file as follows:

{% highlight YAML %}
baseurl: ""
url: "https://<username>.github.io"
{% endhighlight %}

Then, push your site's content to your GitHub repository, then navigate to the repository on GitHub. Upon accessing your repository, you may notice a yellow dot indicating that your GitHub Pages is currently being built and deployed.

<div style="text-align:center;">
        <img src="/assets/img/2024-02-17-welcome-to-jekyll/github-yellow-dot.jpg" width="500" height="300">
</div>


By clicking on this dot, you can see details about the build and deployment process. Once the dot turns green, your site has been successfully deployed and is now live. You can access your site at `https://<username>.github.io`<br><br><br>


### The Outcome
The final product is a GitHub Pages that not only showcases my projects but also tells the story of my journey as a developer. It's a platform that I can continuously update and evolve as I embark on new projects and acquire new skills.
<br><br><br>

In conclusion, launching my GitHub Pages has been a rewarding experience. It has not only provided a platform for showcasing my work but also offered valuable lessons in web development, project documentation, and personal branding. I encourage every developer to consider creating their own GitHub Pages.