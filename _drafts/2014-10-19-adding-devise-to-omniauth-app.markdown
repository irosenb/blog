---
layout: post
title: "Adding Devise to an Omniauth App"
date: 2014-10-19 15:19
categories: 
---

## Preamble
I have a few apps that I did not have the foresight to use [Devise](https://github.com/plataformatec/devise) that also use Omniauth. I thought it would be fun to go through and add Devise into an existing app, while migrating everything. 

Keep in mind I'm working with an **existing app**. If you're starting from scratch, check out the Devise wiki on [integrating Omniauth](https://github.com/plataformatec/devise/wiki/OmniAuth:-Overview).

In this post I'm going to go through and convert them to Devise, showing how you can integrate Omniauth with Devise. I'm writing this post literally as [I do these steps](https://github.com/irosenb/cleanist/tree/devise).

Let's get started. 

## Adding Devise

First step is to add Devise to your Gemfile, like so: `gem 'devise'`, and then to `bundle`. 

Now we want to install devise. So go ahead and run `rails generate devise:install`. This generates a `devise.rb` file. 

## Delete Omniauth File

We're going to temporarily break our application. The problem is that we need to add our provider to the `devise.rb` file, but that will conflict with the existing `config/initializers/omniauth.rb` file. Add the provider from the omniauth file to the `devise.rb` file, changing `provider` to `config.omniauth`. 

If we keep the `omniauth.rb` file, it will conflict with the `devise.rb` file, so go ahead and delete the `omniauth.rb` file. 

## Generate Devise User




