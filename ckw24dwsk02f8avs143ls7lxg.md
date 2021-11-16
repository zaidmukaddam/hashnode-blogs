## Linux for Hackers EP02 | Start Using Terminal

Hello beautiful people! After a long time, here I bring the 2nd Episode of the Linux for Hackers Series.

When it comes to Terminal, It’s the truly wheeled power of Linux. So please don’t use GUI in Linux. You should use Terminal instead of it.

![temrima1.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637066644798/2AbNnvgKV.jpeg)

So this is the where Terminal is in Kali Linux. Go ahead and click it…

![temrima2.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637066678393/wBONFhNtJ.jpeg)

So you can see here, Terminal opened up!

So this is the Linux Terminal, and this is how you are supposed to use Linux. Now if you’re coming from the GUI-only world Where all you use is a graphical user interface… Right!!!

![guiQ.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637066704814/OAstFbeHb.jpeg)

So true, this might seem a little scary. I totally get it!!!  
BUT DON’T WORRY!!!

We are going to walk through this, We are going to teach you a few commands here…

I’m going to slowly wing you off the Graphical User Interface.

I’ll put it up side by side…

Actually, watch here. I’m gonna teach your first few Linux commands…

So come on follow along with me…

![cli.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637066731635/Yts99WxVJ.jpeg)

So go ahead and have your Linux terminal open and also at the same time double click and open up your Home Directory.

![homedir.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637066753992/fvuRLtOd7.jpeg)

I’ll teach you the first few commands by doing something here in the GUI and then doing that same thing in the Linux Terminal.

Now here’s the first thing, what I love about the GUI is that you are always kind of know where you are right! because you can see it!

![teach1.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637066776611/XELckayjd.jpeg)

So here I’m in my user directory (Home directory). And you can see there is my stuff. Now, let’s look at the CLI which is Linux Terminal.

![visual.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637066947690/u5cT-1PRp.jpeg)

I don’t see anything here… How do I know I am, We are gonna solve that…  
This is our first command! type with me folks!!!

**01. pwd (Print Working Directory)**

It basically does what we see in the GUI address bar (/home/kali/).  
Simply, It tells us where we’re at…  
Hey, where am I? Oh! I’m right here!!!  
Let’s try it out! type pwd and go ahead and hit enter!  

```
pwd
/home/kali/
``` 

![view.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637067005165/nnJ-vhHUu.jpeg)

Bam!!! It shows us the full path of where we are right now!!!… you can see it exactly to same as the GUI address bar does.

But one thing, I can actually see my Desktop, Document folder, Download folder, Music folder, Pictures folder, Public folder, Template folder and Videos folder in GUI.

I don’t see those in CLI/ Terminal!!!

How do I see those in Terminal…???

Next command!  
type with me, It’s ls command!  

**02. ls (list)**

This is pretty simple what it does. It’ll simply list the contents of your current working directory!  
It’s gonna list what we see in GUI… Desktop, Document folder…etc.  
You wanna see it?  
Let’s do it!  

```
ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
``` 

![view1.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637067097263/acUDWBynB3.jpeg)

Boom!!!  
It did everything!  
We can see Desktop Documents… all kinds of stuff in Terminal also.  

SEE SEE!!! YOU CAN DO ANYTHING IN THE TERMINAL!!!  
and it’s faster!!!

![joketerm.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637067127329/0sqJP0ehz.jpeg)

I’ll convince you, don’t worry! let’s keep going!!!

let’s say we want to take a peek inside our desktop folder. I’ll show it first in GUI. I go inside the Desktop folder.  
I know you all know how to do that in GUI.

![gui.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1637067215534/KE200teoK.gif)

I just double-clicked the desktop folder, and I jumped in there…

So, how to do it in the terminal!

Our Next Command! here we go!

**03. cd (Change Directory)**

It’s going to do exactly what we just did in GUI.  
watch let’s do it right now!!!

Just after cd,  
I’ll hit space and tell it  
what directory do I want to go to…

```
cd Desktop
``` 

![cd.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1637067286622/K0FyR0mDj.gif)

Hey! Did it work???  
I don’t know! Let’s see…  
Let’s print our working directory!  

![res1.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1637067356127/Uo19nYe7o.gif)

We did!!!  
Here you can see the current working directory is changed!!!

We did indeed drill down right into the desktop folder and then to see what’s on our desktop as we can see in the GUI. But currently, my Desktop is empty! Let’s see what happens!!!

we can simply type ls command to list the contents!!!

![res2.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637067403516/2jKwNEgof.jpeg)

There’s not anything!!! in both GUI and CLI!!! It’s fine.  
Because actually, my desktop has nothing!!! cool!!!  

Now!!! We’re gonna learn one more command today!  
Hang with me!!!  

But so far we’ve done a lot,  
the pwd command → to see where we are  
the ls command → see what’s around us, what’s in our directory  
the cd command → to change where we are 

But now,  
How do we go back!!!???

Because we can do it in GUI easily using the back icon in the left top corner!

![back.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637067427946/sEBvAvhZ7.jpeg)

How do we do it in Terminal?!  
It’s actually super easy!!!  

so again we gonna type **cd**

**because Back means we gonna change our directory again!!!**

type cd and I’ll hit space and type double dot and hit Enter!

```
cd ..
``` 

![backres.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1637067492450/0Hb4iErMm.gif)

Boom! it works!!!  
Again we were in our home directory!  

Now just for fun!  
I wonder what will happen if we keep going backward???  
if we type in cd .. again and again??? what will happen??  

Okay, let’s do it and check!

![backback.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1637067536518/AMaokswoR.gif)

Oh, you can see, instead of home I’m simply at /  
And what this is?   
It is actually the **Root of the file system.**

It’s the end.  
We reached the end!

And we’ll talk more about that later! In upcoming episodes!

But, just for fun again… just that’s all for fun right!  
let’s enter the ls command now!!! at root… (/)

![iamroot.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1637068026148/FhYUT75oe.gif)

Boom! you can see now the content list of the root directory…

Huh! A lot of interesting files here…  
We’ll talk about all these files later!

Now real quick Quiz for you,

![quizzzz.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1637067799549/qMYOebhzv.jpeg)

Let’s see you got the idea right!

**Q. Assume you’re in the root directory in Linux Terminal. What command or commands would you enter to /home/kali/ directory?**

There are 02 options really…  
You can do it with one command or you can do it with 02 commands…  
**Please comment below your answer!!!**

I’ll discuss the answer in the comments of this article!

Now here we just scratched the surface.  
We are going deeper into Linux.  
We are gonna prepped and ready to become a hacker.  
But don’t that diminish the fact that you did a lot today with this article!  

We are moving from GUI to CLI… Specially Hackers like CLI! We love it right!
And we did, pwd, cd, ls… more to come!!!  

So if you wanna hack the Hashnode platform algorithm, just hit the follow button and hit the reaction buttons, also put your comment! It hacks the algorithm of the Hashnode :D.  
Ethically??!!! Yess Ethically!!!

# Summary

- pwd command → to see where we are
- ls command → see what’s around us, what’s in our directory
- cd command → to change where we are
- cd .. command → to go backward