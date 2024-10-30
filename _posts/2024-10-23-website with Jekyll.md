---
title: Host a static website with Jekyll in Github pages
date: 2024-10-23 12:00:00 -500
categories: [projects]
tags: [website, github] # TAG names should always be lowercase
---

This will show how you can setup a website like this that is hosted in github pages.

> TEST TEST TEST `_tabs/about.md`{: .filepath } and it will show up on this page.
{: .prompt-tip }

There's a couple of things that will be needed

* WLS
* Zsh
* VSCode
* domain
* Ruby

This guide is heavily plagiarized from [Techno Tim: Meet Jekyll - The Static Site Generator](https://technotim.live/posts/jekyll-docs-site/)  
 I used this guide to learn mysel but as I ran into quite a few issues that was not mentioned in the guide  
so I desided to create my own.

## Setup Terminal

Install window terminal from <https://learn.microsoft.com/en-us/windows/terminal/install>  
Launch it

### install WSL (The Windows Subsystem for Linux)

Open a Powershell tab in terminal and run below command to install [WSL](https://learn.microsoft.com/en-us/windows/wsl/install)

```powershell
wsl --install
```

### install ZSH (Oh My Zsh!)

open a new tab with ubuntu, you can also set it as default in terminal

[Oh My Zsh](https://ohmyz.sh/#install)

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Install Dependencies

```bash
sudo apt update
sudo apt install ruby-full build-essential zlib1g-dev git
```

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

After making changes to your site, commit and push then up to git

```bash
git add .
git commit -m "made some changes"
git push
```

## Jekyll Commands

serving your site

```bash
bundle exec jekyll s
```

cat ~/.ssh/id_rsa.pub.
# mac setup 
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