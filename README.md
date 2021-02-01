# metisChan

A 4chan clone made with Flask. Built to be super-lightweight and easy to use!

Made by @khodges42, updated by @saintly1337

# Installation Guide

Since many of you don't know how to install and run it locally, I (saintly1337) will tell you.
Here is a little Index of what is awaiting you:
- <a href="#0-Requirements">0. Requirements</a>
- <a href="#1-Installing-git-and-docker-compose-docker">1. Installing git and docker-compose docker</a>
- <a href="#2-Cloning-the-Repo-on-your-Machine">2. Cloning the Repo on your Machine</a>
- <a href="#3-Editing-everything-to-your-comfort">3. Editing everything to your comfort</a>
- <a href="#4-Creating-the-Database">4. Creating the Database</a>
- <a href="#5-Running-the-Flask-App">5. Running the Flask-App</a>
- <a href="#6-Being-done">6. Being done</a>

# 0. Requirements
First of all: you need Linux. Or at least a Linux emulator. If you don't got one, I recomend using <a href="https://www.virtualbox.org">VirtualBox</a>. And <a href="https://ubuntu.com/download/desktop">here</a> you can download Ubuntu ISO.

Then if you got this, you can continue.

# 1. Installing git and docker-compose docker
> sudo apt-get update

checking if sudo needs an update

> sudo apt-get install git

installing git on your machine to clone the repo

> sudo apt-get install docker-compose docker

installig the docker

# 2. Cloning the Repo on your Machine
> sudo git clone https://github.com/khodges42/metischan.git

self explaining

# 3. Editing everything to your comfort
Well, now here is a little bit text, deal with it.

In the "templates" folder are all the sites which will be used on the final-site:
- board.html - this is gonna be the main page which you will load on, like an index
- front.html - i actually don't know myself, but ok
- reply.html - self-explaining, but if you don't get it, this is the page that will appear 

What are you going to do with that?
You're gonna change the "title" tag so your site doesn't appear as "metischan". For this, simply just open the html file in the editor of your choice (I recomend using emacs, just search it up).
For example, I will be guiding you through editing board.html
If you want to change the page title which will appear on the tab-name, simply just search the "title"-tag which is located at the very top of the page, right under the "doctype" tag (you won't change this). The exact tag looks like this:
> <title>metisChan</title>

So you wanna change the "metisChan" to the name of your choice. In my case it's gonna be "oneChan" (whyevery, idk how I came up with this name).
When you open the html file now in your browser (I recomend using FireFox) you will notice that the tab-title says: "oneChan". What a surprise! Now you wanna change this on every html file located in the "templates" folder so you don't have randomly the "metisChan" title when you are responding to a post or so.
Furthermore I've already done some adjustments so you don't have to take care of this. Also, I've provided a .css file into the folder, just ignore this. We will come to this later.
Ok, now you got your pages ready to go. Of course you still can change things like the text like when you post the field where you have to put your name says "Username" instead of simplay "Name", but you don't have to do it.

# 4. Creating the Database
Now we come to the more trickier part. For this you need SQLite 3, of course I will tell you how to install it.
Just type in this:
> sudo apt-get install sqlite3

Of course there are other ways to do it, but this is the comfiest way.
After this you can check if it is installed with the comand
> sqlite3

If it says this:
> SQLite version 3.22.0 2018-01-22 18:45:57

> Enter ".help" for usage hints.

> Connected to a transient in-memory database.

> Use ".open FILENAME" to reopen on a persistent database.

> sqlite>

you made everything right! Of course, the SQLite version may change when this tutorial is outdated, but the installation will be the same (at least I hope).
Then make a right click on the metischan-master folder and open a terminal in it. You can check if everything is fine when you execute this comand:
> ls

With this you can see everything in this folder. If you are using lubuntu you will be seeing, that the foldernames are written in blue.

(Optional) You can check the schema.sql file with:
> cat schema.sql

After you done everything like I told you, you have to put everything in a Database. You can do it like this:
> cat schema.sql | sqlite3 chan.db

So now you put it all together in the chan.db Database. Then you just press simply enter when it shows you this afterwards:
> >

When you check it with "ls" you can see, that there is a new file called "chan.db". This is where the fun begins.
Now you can view this Database in SQLite3 with:
> sqlite3 chan.db

Then you should get in the menu where the input line says:
> sqlite>

Then you can leave this with the following comand:
> .quit

(Optional) You can view the created tables with:
> .tables

Then should "boards", "posts" and "replies" displayed. If not, you have done something wrong.

# 5. Running the Flask-App
After all the previous steps, you're several steps closer to your goal (lmao what is this sentence??).
Now just run these comands:
> export FLASK_APP=server.py

> flask run

Then it should spit you out some text and the url which the whole shit is running on and can be found. Most always it is "http://127.0.0.1:5000" but it can change. Then you can run this in the browser and see your half-way finished imageboard. Yay!!
Now to create your first actual board, run these comands, I will explain them.
> insert into boards(board_short_name, board_description) values ('a', 'Anime');

So you are instering a board. the values are "a" and "Anime". In this case, "a" is the short name. the link will be "127.0.0.1:5000/a/", so simply the category, and "Anime" is the board title which you will see on the board, once you opened it. Of course you can add more boards, so for now let's add two more:
> insert into boards(board_short_name, board_description) values ('h', 'Hentai');

> insert into boards(board_short_name, board_description) values ('m', 'Music');

So now we got these, let's test it by refreshing the browser page where you have the site opened. As you can see, under the title of the page are links. Well done.

# 6. Being done
Well, great job! You are done. If you had any problems, feel free to start a discussion or comit an issue. Hope you got easily through it and if you have any improvements here, feel free, to change this file and make them (:
greetings, saintly1337!
