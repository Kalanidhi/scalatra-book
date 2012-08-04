Installation
============

Getting started with a new web framework can be a bit scary. Luckily, Scalatra 
is actually quite easy to install, as it has relatively few dependencies.

### 1. Install a JVM
 
Scalatra is web microframework written in Scala, so you'll need to have a 
Java Virtual Machine (JVM) installed. Many systems will already include 
a JVM (do `java -version` in a terminal to find if yours does). If you don't 
yet have Java installed, you can find out how to install it for your system
[here](http://docs.oracle.com/javase/7/docs/webnotes/install/index.html).

### 2. Install SBT 

The next thing you'll need is `sbt`, the Simple Build Tool. This is a Scala 
program which will automatically download everything your Scalatra project 
needs, and build it. 

You can download `sbt` at the [SBT website](http://www.scala-sbt.org/download.html).

### 3. Install conscript and giterate

[Conscript](https://github.com/n8han/conscript) is a tool for installing and
updating Scala code. [Giter8](https://github.com/n8han/giter8/), which depends 
on conscript, allows you to check out project templates directly from Github. 
It's the recommended way of getting started with Scalatra. 

To install conscript, issue this command in your terminal:

{pygmentize:: }
curl https://raw.github.com/n8han/conscript/master/setup.sh | sh
{pygmentize}

This will create a _bin_ folder in your home directory.  Put that on your 
path, by adding the following to your shell's profile (e.g. ~/.bash_profile):

{pygmentize:: }
PATH=$PATH:~/bin
export path
{pygmentize}

Make sure you reload your shell:

{pygmentize:: }
source ~/.bash_profile
{pygmentize}

Now you can use conscript to install Giter8: 
{pygmentize:: }
cs n8han/giter8
{pygmentize}

That's it! You've now got everything you need. 

### Generating a Scalatra project

Now that all of the dependencies are out of the way, you can generate a project. 

Run:

{pygmentize:: }
g8 scalatra/scalatra-sbt
{pygmentize}

This will check out a pre-built application skeleton for you (from Github), 
and ask you some questions about your application:

{pygmentize::}
$ g8 scalatra/scalatra-sbt
> organization [com.example]:
> package [com.example.app]:
> name [scalatra-sbt-prototype]:
> servlet_name [MyScalatraServlet]:
> scala_version [2.9.1]:
> version [0.1.0-SNAPSHOT]:
{pygmentize}

`organization`: Used for publishing.  Should be the reverse of a domain
name you control.  If you don't own a domain, `com.github.username` is a
popular choice.

`package`: All Scala code belongs in a package.  The [Scala Style
Guide](http://docs.scala-lang.org/style/naming-conventions.html#packages)
recommends that your packages start with your organization.  This convention is
used across multiple JVM languages and gives your project a globally unique
namespace.

`name`: The name of your project.  g8 will generate a project into a
folder of this name, and the artifacts you publish will be based on this name.

`servlet_name`: the name of your servlet. This might be something like 
*BlogServlet* or just *Blog*.

`scala_version`: The version of Scala your project is built with.  When in
doubt, use the default.

`version`: The version number of your project.  This is entirely up to you,
but we like [Semantic Versioning](http://semver.org/).


### Building

Scala is a compiled language, so you need to build your Scalatra project. 

Enter your application's top-level directory and type `sbt`, and the 
application will build.

Running in Development
======================

### Automatic Code Reloading

Restarting an application manually after every code change is both slow and
painful. It can easily be avoided by using a tool for automatic code reloading.

SBT will allow you to [signal a restart of the application when it detects
code changes](https://github.com/harrah/xsbt/wiki/Triggered-Execution). The
syntax for restarting includes adding `~` in front of the command you want to
re-execute.  To recompile and reload your application automatically with
xsbt-web-plugin 0.2.10, run the following:

{pygmentize::}
$ sbt
> container:start
> ~ ;copy-resources;aux-compile
{pygmentize}
