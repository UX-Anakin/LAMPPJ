# Build an entire social network from scratch
We will build this with Ruby on Rails 5,Utilizing  Twitter's own Bootstrap CSS framework.use Git for version control, a free resource for Linux based cloud development called C9.and finally deploy the application to the cloud using Heroku.

## Lesson #1
  **Twitter** is an online news and social networking service where users post and interact with messages,"tweets",restricted to 140 characters,Registered users can post tweets, but those who are unregistered can only read them.Users access Twitter through its website interface,SMS or a mobile device app.
  **Contents**
    1. INTRODUCTION
    2. TABLE OF CONTENTS
    3. GITHUB SETUP
    4. C9 SETUP & CONFIG
    5. PAGES & NAV
    6. USERS
    7. POSTS
    8. STYLING (UI)
    9. FOLLOWERS
    10. POLISH
    11. CLOUD DEPLOY
    12. CONCUSION

## Lesson #3 GITHUB SETUP
## Install Ruby on Rails - Ubuntu Linux
 This in-depth installation guide is used by developers to configure their working environment for real-world Rails development.This guide doesn't cover installation of Ruby on Rails for a **production server**.
 To develop with Rails on Ubuntu, you'll need Ruby (an interpreter for the Ruby programming language) plus **gems** (software libraries) containing the Rails web application development framework.
### Ruby on Rails on Ubuntu
  Ubuntu is a popular platform for Rails development, as are other Unix-based operating systems such as Mac OS X.Installation is relatively easy and widespread help is available in the Rails developer community.
### Use a Ruby Version Manager
  You'll need an easy way to switch between Ruby versions. Just as important, you'll have a dependency mess if you install gems into the system environment.I recommend **RVM** to manage Ruby versions and gems because it is popular, well-supported,and full-featured.If you are an experenced Unix administrator,you can consider alternatives such as **Chruby** or Sam Stephenson's **rbenv**.
### Don't Install Ruby from a Package
  Ubuntu provides a package manager system for installing system software.You'll use this prepare your computer before install Ruby.However, don't use **apt-get** to install Ruby.The package manager will install an outdated version of Ruby.And it will install Ruby at the system level (for all users).It's better to use **RVM** to install within your user environment.
### Hosted Development
  You can use Ruby on Rails without actually installing it on your computer.Hosted development, using a service such as [Cloud 9](https://c9.io/), means you get a computer "in the cloud" that you use from your web browser.Any computer can access the hosted development environment,though you'll need a broadband connection.Cloud9 is a free for small projects.Cloud9 is a good option if you have trouble installing Ruby on Rails on your computer.
### Prepare Your System
  You'll need to prepare your computer with the required system software before installing Ruby on Rails.
  You'll need superuser(root) access to update the system software.
  Update your package manager first:
  ```
  $ sudo apt-get update
  ```
  This must finish without error or the following step will fail.
  Install [Curl](http://en.wikipedia.org/wiki/CURL):
  ```
  $ sudo apt-get install curl
  ```
  You'll use Curl for installing RVM.http://railsapps.github.io/installrubyonrails-ubuntu.html
  
