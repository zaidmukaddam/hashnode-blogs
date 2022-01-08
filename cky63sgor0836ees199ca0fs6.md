## MoodWiser - Fun habit tracker to keep everyone accountable

# What is MoodWiser?

MoodWiser is a simple, minimalistic, useful and fun habit tracker that keeps you and your friends accountable for each other by giving praises y'all deserve to reach your goal!

[Live Demo](https://moodwiser.co)  /  [GitHub Repository](https://github.com/zaidmukaddam/moodwiser)

# The Story Behind MoodWiser

I've always wanted to build a super simple mood tracker so I came up with the name during mid December, last year. Then I left the project there to hang until I realized I wouldn't be able to complete it in time because I wasn't working on it. 😂 So now it is time to bring the project back from Hibernation!🦾

I believe a lot of people are like me:


1. Start a new habit
2. Execute it for a few days
3. Forget about it
4. Back to step 1

Let's call this the deadly "start a new habit" loop.

In order to escape the loop, MoodWiser became a habit tracker with me being the first user. Here I am, participating in a hackathon with a project to make sure I complete the hackathon. How hilarious! 😂

To make things more fun, a praise feature was implemented so that we can receive praises from friends and families to keep ourselves going. Also, it's a good chance to get them to signup and get themselves out of the loop!

That's the story of how MoodWiser turned into a habit tracker to keep everyone out of the deadly "start a new habit" loop!

# Tech Stack

- HarperDB - The Database known for simplicity without sacrifice!
- Auth0 - User authentication that's super easy to integrate
- Next.JS - The React framework for production
- Chakra UI - UI development that's just deadly simple
- Vercel - Deployment for the app, where the app lives

# Features and Usage
## 🌓 Supports dark and light modes

![okidokie.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1641660388295/8zjBMq55C.gif)

## 📱 Responsive on all devices

![moodpromotedis.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1641660823990/n8iUGEMUZ.png)

## ✏ Track your habits and moods

![recordedmood.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1641662096783/KNavWPbQF.gif)

**Track your mood and habits**
Yay the mood part is still alive, tied together with the habit tracking!

![recordedmood2.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1641662633316/P_m4gjVQM.gif)

## 🥰 Earn praises by sharing the praiser link

Step 1: Copy the praiser link

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1641662806671/Yomimtxgr.png)

Step 2: Share it with your friends

Step 3: Praise your friends back


## How I built it
### Choosing the stack
- Database - Easy choice and you know why! HarperDB to the rescue!
- Authentication - I didn't feel comfortable going through sensitive information, so I chose a trustworthy Auth0 which also supports login with third-party services such as Google.
- Front End & Back End - I wanted to use TypeScript for everything and manage APIs easily. Loved using React and also heard about the Next.JS for quite some time. Next.JS fulfills all my wishes so I definitely should try it out.
- Deployment - Since I chose Next.JS, Vercel as the main contributor behind it supports deployment for it like no one else. Only a few clicks away from deploying the app's front end and back end automatically. Super easy to setup!

### Database
HarperDB exposes a REST API along with example code and a Postman collection to start out, it was super easy to follow. I didn't find the need to use a wrapper library. CRUD operations can be called easily without much hassle.

Below is the how I structured the database to save all the data I needed for MoodWiser to work.
![Database Design](https://raw.githubusercontent.com/zaidmukaddam/moodwiser/main/ERD.png)

## Challenges I ran into
After having the project idea in mind with some basic features, it's time for implementation! **It's my first time releasing a side project to the public with the front end and back end all built on my own.**

# FAQ
**Who is suitable for MoodWiser?**  
Anyone and everyone! You can use it by yourself and praise yourself, or let your friends join in the fun as well!

**Where is my data saved?**  
Application data such as user profiles, habits and praises are saved in HarperDB. Passwords goes through Google if you choose Google login and Auth0 if you register an account with them. MoodWiser don't have access to all passwords.

Shameless plug:  [MoodWiser](https://moodwiser.co) 
