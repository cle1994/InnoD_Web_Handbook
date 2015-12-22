# Setup and Basics

**Quick Jump**

* [Git](#git)
* [Node](#node)
* [Things you might find useful](#helpful-things)

## [Homebrew](http://brew.sh/)

**ONLY IF YOU'RE ON MAC**

In Terminal:

```bash
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

<a name="git"><a/>
## [Git](https://git-scm.com/)

**LEARN GIT, IT'S IMPORTANT**

Git is a free and open source distributed version control system. What does
that mean? Pretty much it lets you make edits to your code/files and put them
under versions so you can revert them if something goes bad.

I or your tier leader could teach you Git but honestly, this is more fun:
[Try Git](https://try.github.io/levels/1/challenges/1). More advanced functions
like pull requests and merge conflicts will be taught by your tier leader.

*If you're hardcore, here's the
[documentation for Git](https://git-scm.com/documentation)*

#### A Basic Rundown
These are the commands you'll probably be using most with simple explanations.

Start a git repository for version control.
```bash
$ git init
```

See current git status
```bash
$ git status
```

Add files to be tracked by git
```bash
$ git add [FILE]      # add just one file
$ git add [FOLDERS]   # add a folder
$ git add .           # add all in current folder
```

Commit files to version control (take a snapshot)
```bash
$ git commit -m '[MESSAGE]'   # where MESSAGE is your commit message
```

Push to remote repository, like GitHub
```bash
$ git push [REMOTE] [BRANCH]:[REMOTE_BRANCH]  # git push origin master:master
```

Add a remote
```bash
$ git remote add origin https://github.com/user/repo.git
```

<a name="github"><a/>
#### [Github](https://github.com)

I recommend using GitHub for your remote version control. If you're a student
you get 5 private repositories for free, plus bunch of other goodies
[here](https://education.github.com/).

<a name="git-installation"><a/>
#### Installation

**Mac**

In Terminal:

```bash
> brew install git
```

**Windows**

Follow instructions found [here](http://msysgit.github.io)

**Linux**

In Terminal:

*Fedora*

```bash
> yum install git
```

*Debian/Ubuntu*

```bash
> apt-get install git
```

<a name="node"><a/>
## [Node.js](https://nodejs.org/en/)

> Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.
> Node.js uses an event-driven, non-blocking I/O model that makes it
> lightweight and efficient. Node.js' package ecosystem, npm, is the largest
> ecosystem of open source libraries in the world.

I can talk about node all day but for the purposes of Web Tier, it's used
mostly for automation. If you're in Web Development, you might use it as a
server framework.

<a name="node-installation"><a/>
#### Installation

Install and use NVM for the love of...seriously don't manage Node by yourself

**Mac & Linux**

In Terminal:

```bash
> curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
```

**Windows**

Follow the instructions found
[here](https://github.com/coreybutler/nvm-windows)

#### Post Install Setup

In Terminal (Mac/Linux) or Command Prompt (Windows)

```bash
> nvm install stable
> nvm use stable
> node -v
```

You should see a node version, the latest stable found on the node
[homepage](https://nodejs.org/en/).

<a name="helpful-things"><a/>
## Things you might find useful

This stuff might make your life a lot easier as a web developer.

<a name="helpful-sublime"><a/>
#### If you use [Sublime](http://www.sublimetext.com/)

- [Sublime Package Manager](https://packagecontrol.io/)
    - Installation: https://packagecontrol.io/installation
    - Helps you manage and install packages for Sublime
- [Emmet](http://emmet.io/)
    - Installation: https://packagecontrol.io/packages/Emmet
    - Your HTML markup becomes so much easier
- [Babel](https://babeljs.io/)
    - Installation: https://packagecontrol.io/packages/Babel
    - For ES6/ES7 Javascript support
- [Sass](http://sass-lang.com/)
    - Installation: https://packagecontrol.io/packages/Sass
    - For way better CSS

<a name="helpful-atom"><a/>
#### If you use [Atom](https://atom.io/)

You can install these through your Atom `preferences > Install`

- [Emmet](http://emmet.io/)
    - Search `Emmet`
    - Install "emmet" by emmetio
- [Babel](https://babeljs.io/)
    - Search `language-babel`
    - Install "language-babel" by gandm
- [Sass](http://sass-lang.com/)
    - Search `language-sass`
    - Install "language-sass" by atom

<a name="helpful-vim"><a/>
#### If you use Vim

*Vim master race, jk I'm not like that*

Take a look at my [dotfiles](https://github.com/cle1994/dotfiles).
