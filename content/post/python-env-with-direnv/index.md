---
title: Seamless virtual environments with direnv
description: Forget about initializing and maintaining your python environments,
    shell profile, environment variables, aliases and much more!
slug: virtualenvs-with-direnv
date: 22023-08-16 21:11:06
image: cover.png
categories:
    - Programming
    - Unix
tags:
    - python
    - shell
toc: true
---

I have been using Python for a while, from small pet projects to professional
sass services. I like writing Python but one thing that bugs me the most is
virtual environment. I get it you keep your packages separate between your
projects so that updating one thing here doesn't break something else somewhere
but initializing the environment every time i switch between projects is the
worst hassle. It's easy to forget to do so especially when you are trying to
do an urgent fix that the client is thinking for.

Looking for a solution to do this I wrote a small bash function to overwrite
the `cd` function which would change the directory and initialize a `.profile`
file in the directory if present. But then I thought if this is so easy to do,
then surely someone would've done it and would likely have added a ton more
features into the same. That's how I found `direnv`.

`direnv` allows you to have a `.envrc` script in your folder that gets run to
create a shell environment as per your requirements.

While on surface it sounds simple, the amount of overheads the devs have built
into it is amazing. You can use `direnv` specific commands to achieve complex
tasks.

Eg. Following is the requirement:
1. I want to initialize an environment of python3.8.6 in my directory.
2. I have a work folder on my drive that I keep all my work projects in,
lets say `/home/username/work`. I have few environment variables that are
common to all projects and I also have project specific ones.

Now with the script I wrote I would have to go through the hassle of setting up
a new python environment for every new project. Hardcode its path in my
`.envrc` and then I'll have to copy paste the common environment variables and
so on.

With direnv it becomes as simple as

```shell
source_up

layout pyenv 3.8.6

export PROJECT_SPECIFIC_FOO=project_specific_foo
```

where `source_up` would automatically source my parent directory which would
contain common env vars, `layout pyenv` will create me a `virtualenv` with the
given python version and export will allow me to set project specific env vars.

Installation instructions for `direnv` can be found [here](https://direnv.net/docs/installation.html)

Theres a lot more to do with `direnv` which you can read about [here](https://github.com/direnv/direnv/wiki)

Read more about direnv at [official webpage](https://direnv.net/)
