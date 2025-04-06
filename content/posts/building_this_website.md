+++
date = '2025-03-12T17:22:50+08:00'
draft = false
title = 'Building this Website'
+++


I wanna build my site using Hugo. Here are some logs.

I use the Congo theme.

Following the [theme documentation](https://jpanther.github.io/congo/docs/).


First, we need to initialize the site and the theme.

## requirements
- Hugo
- Go

## Installing the site and theme

- Initialize the site
```sh
hugo new site <sitename>
cd <sitename>
# Prepare the theme using Hugo module

# If you're managing your project on GitHub
hugo mod init github.com/<username>/<repo-name>
# If you're managing your project locally
hugo mod init my-project
```

- Add the theme to your configuration
```
mkdir -p config/_default
cd config/_default
touch module.toml
```
- Add the following line into module.toml

```toml
[[imports]]
path = "github.com/jpanther/congo/v2"
```
Start your server using ``hugo server`` and the theme will be downloaded automatically.

## Content

Add content in the ''content/post'' folder.

More information: [Directory structure](https://gohugo.io/getting-started/directory-structure/)

## Hosting

I host this website on github using github pages.

See [Host on GitHub Pages](https://gohugo.io/host-and-deploy/host-on-github-pages/)



## Add Comments system

I use [Giscus](https://giscus.app) for Comments system.
