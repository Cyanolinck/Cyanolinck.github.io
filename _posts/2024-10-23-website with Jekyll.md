---
title: Host a static website in Github pages
date: 2040-10-23 12:00:00 +200
categories: [projects]
tags: [website, github] # TAG names should always be lowercase
---

How to setup static website and host it in Gitub. This guide is hosted with this mehtod.

This guide is heavily plagiarized from [Techno Tim: Meet Jekyll - The Static Site Generator](https://technotim.live/posts/jekyll-docs-site/)  
 I used this guide to learn mysel but as I ran into quite a few issues that was not mentioned in the guide, I desided to create my own.

\
&nbsp;

There's quite a few Statis Website engienes that can be used nowdays but for this guide we'll use Jekyll, another is [Hugo](https://gohugo.io/)

There's a couple of things that will be needed

* WLS (Only for windows)
* Zsh
* VSCode
* domain
* Ruby
* Python
* Java

\
&nbsp;

## Setup on Widnows

### Install Terminal

Install window terminal from <https://learn.microsoft.com/en-us/windows/terminal/install>  
Launch Terminal (screenshot of terminal here)

\
&nbsp;

### install [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) (The Windows Subsystem for Linux)

Open a Powershell tab in terminal and run below command to install [WSL](https://learn.microsoft.com/en-us/windows/wsl/install)

```powershell
wsl --install
```

\
&nbsp;

### install [ZSH](https://ohmyz.sh/#install) (Oh My Zsh!)

Open a new tab with ubuntu in Terminal

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

\
&nbsp;

### Install Dependencies

Update system and and install Ruby

```bash
sudo apt update
sudo apt install ruby-full build-essential zlib1g-dev git
```

\
&nbsp;

To avoid installing RubyGems packages as the root user:

```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.zshrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.zshrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

Install Jekyll `bundler`

```bash
gem install jekyll bundler

```

\
&nbsp;

## Creating a site based on Chirpy Starter

Visit <https://github.com/cotes2020/jekyll-theme-chirpy#quick-start>

After creating a site based on the template, clone your repo

```bash
git clone git@<YOUR-USER-NAME>/<YOUR-REPO-NAME>.git
```

then install your dependencies

```bash
cd <YOUR-REPO-NAME>
bundle
```

\
&nbsp;

## Configure Git

Set an email address in Git. You can use your GitHub-provided noreply email address or any email address.

Configure Git
You’ll want to follow this guide for configuring git.Be sure to follow the LINUX version
<https://docs.github.com/en/github/using-git/getting-started-with-git-and-github>

### Set usename i Git

```bash
git config --global user.name "Lincken"
```

Use the command again without your name to check that it's correct

```bash
git config --global user.name
```

Output should be your username like it does below

```bash
git config --global user.name
Lincken
```

\
&nbsp;

#### Set email in Git

```bash
git config --global user.email "your_email@example.com"
```

Use the same command without your email to check that git is configured to use your email

```bash
git config --global user.email
```

\
&nbsp;
\
&nbsp;

### Create SSH key

Now we can generate a ssh key that we can use to access Github

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

\
&nbsp;

```bash
eval $(ssh-agent -s)
```

```bash
git config --global user.email "YOUR_EMAIL"
```

Confirm that you have set the email address correctly in Git:

```bash
git config --global user.email
```

The output should be your email

After making changes to your site, commit and push then up to git

```bash
git add .
git commit -m "made some changes"
git push
```

\
&nbsp;

To open your code in VSCode use below command inside of the pulled github folder

```bash
code .
```

\
&nbsp;

## Jekyll Commands

To start your website locally run below command.

```bash
bundle exec jekyll s
```

If you run into issues with the port already being in use locally, you can change the port to something else, for example 8080

```bash
bundle exec jekyll serve --port 8080
```

<!--
cat ~/.ssh/id_rsa.pub.

## mac setup

Install rbenv and ruby-build:

zsh
Copy code
brew install rbenv
Initialize rbenv: Add the following to your ~/.zshrc to initialize rbenv automatically:

zsh
Copy code
eval "$(rbenv init -)"
Reload your shell to apply these changes:

zsh
Copy code
source ~/.zshrc
Install a New Version of Ruby: Now, install a new version of Ruby (e.g., 3.1.2) through rbenv:

zsh
Copy code
rbenv install 3.1.2
rbenv global 3.1.2
This will use your user directory, avoiding system-protected files.

Reinstall Bundler and Jekyll: With the new Ruby version set up, reinstall Bundler and Jekyll without sudo:

zsh
Copy code
gem install bundler jekyll
Run bundle install in Your Project: Finally, in your project directory:

zsh
Copy code
bundle install

> TEST TEST TEST `_tabs/about.md`{: .filepath } and it will show up on this page.
{: .prompt-tip }

GoodToKnow  
Write names of posts like this, YYYY-MM-DD-Name of post.  
If the date is in the future, the post won't show up until then.
To add local Images, place them in root assets folder, recomendation under a new folder called images. Not in the Site>Assets folder!
That folder is just for when it has built the website, if placing anything directly there is will disaperare when it builds the website.

Java and Python is nessesary.
-->