# **Week 7 Lab Report** by Malcolm Park (Jooahn)

This week's lab report will focus on detailing and reproducing the task from the lab competition on our own. The lab challenge was an activity where we needed to login to out ssh key, clone a fork of a repository, run tests, demonstrate they fail, fix the errors within the tests, and commit/push the change to the github account!

## Preparations for the lab challenge (github and login command-line setup). 
> This is not a part of the timed challenge, but preparations for that portion of the lab challenge.

1. First, we will open our terminal using visual studio code. Then, we will run <ssh-keygen>. After doing so, we will keep pressing <Enter> until we see a text called "randomart image".
- <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221719699-a389c77d-09ae-401c-9071-56547a1a3350.jpeg">

2. Then, follow the instructions listed on the website to download the appropriate file for your operating system.
3. In the end, you should have downloaded the correct file. Once you open it, it should look like this. 
01-12 at 5 32 30 PM" src="https://user-images.githubusercontent.com/122580137/212216551-25578a50-e01c-4fe4-985f-a0c794c9ef70.png">

## CSE Account Lookup and Remote Connection.
> Most of the CSE courses available in UCSD have accounts for each student to access 
> the linux labs remotely from their own computers. You will need to find it first.

### Finding CSE 15L Account
1. Go to this [Link](https://sdacs.ucsd.edu/~icc/index.php) and use the Account Lookup tool using your Username and Student ID
2. The website should show you your CSE course-specific account as it shows below. Click the grey button with your CSE account and use the password changing option to set a new password.

### Remotely Connecting to UCSD Linux Labs
If you are using a Windows operating system, you need to download git beforehand.
1. To remotely connect to the labs, first open a terminal in VSC. (You can do this by pressing Ctrl + ` or you can just find the terminal tab and make a new one.
2. Once you have the terminal open, type in ssh and then put your uscd CSE lab username.ucsd.edu and that will show a message of "The authenticity of host...".
- <img width="625" alt="Screen Shot 2023-01-16 at 9 38 47 PM" src="https://user-images.githubusercontent.com/122580137/212818561-1353d3ec-38f6-4cd4-ab4d-54cbc0bd6f2a.png">
3. Once you get this notification from VSC, type in yes and it will give you need to set a password. Then, it will show you that you are now on the remote server, which means that you are not connected to one of the computers in the CSE basement.

### Running a few commands
Now, we will run some commands such as cd, ls, pwd, mkdir, and cp with different ways.
Type in a few commands for the terminal line that you have learned during class for both your own computer's VSC and for your remote lab VSC to see how they differ. In the image, you can see on the left the commands run on the linux remote labs. On the right, you can see the same commands run on my macbook computer. - Here you can see that I ran the ls -lat command, which shows a list of all files by date.
<img width="617" alt="Screen Shot 2023-01-16 at 9 40 22 PM" src="https://user-images.githubusercontent.com/122580137/212818765-926fb9d3-ffca-4f7f-b653-a29991382eb0.png">

## Setting up your own Github page
1. Github (www.github.com) is an online website that is primarily used for sharing, storing, and collaborating on code. We can use Github to create our website, which we will use to create our first lab report.
2. We will first create an account, after which we will create a repository, whihc is a folder for your code. We will name this cse15l-lab-reports.
<img width="370" alt="Screen Shot 2023-01-16 at 9 42 53 PM" src="https://user-images.githubusercontent.com/122580137/212819437-4d755e7c-e37a-4688-9051-e44f2f6a2e82.png">

3. Then we will create a website using Markdown code, which we will do by clicking on the Settings option and then Pages option. Then We will choose main as the source for the Github page.
4. The .md extension is used for Markdown files, and we can use the cheatcode that is available to write out our first page!
