# **Week 7 Lab Report** by Malcolm Park (Jooahn)

This week's lab report will focus on detailing and reproducing the task from the lab competition on our own. The lab challenge was an activity where we needed to login to out ssh key, clone a fork of a repository, run tests, demonstrate they fail, fix the errors within the tests, and commit/push the change to the github account!

## Preparations for the lab challenge (github and login command-line setup). 
> This is not a part of the timed challenge, but preparations for that portion of the lab challenge.

1. Generating SSH Keys for ieng6
- First, we will open our terminal using visual studio code. Then, we will run <ssh-keygen>. After doing so, we will keep pressing <Enter> until we see a text called "randomart image".
  <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221719699-a389c77d-09ae-401c-9071-56547a1a3350.jpeg">
- Then, we will login to our remote course specific account on ieng6.
  <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221720291-dc954a32-6d0a-4900-85b7-a0f3d45f52b6.jpeg"> 
- After doing so, run <mkdir .ssh> and then logout of the remote account.
  <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221720807-bb28c85a-a2f5-4cf4-8cc1-f9af73f069a7.jpeg">
- Now we want to copy the public ssh key that we created on our personal computer to our remote account. We will do this by finding the path the ssh key that we made (which ends in .pub) and running <scp /Users/jooahn/.ssh/id_rsa.pub cs15lwi23awc@ieng6.ucsd.edu:~/.ssh/authorized_keys>. The path and the login key should be different for the user. This will save the ssh key into the .ssh directory inside a file called authorized_keys.
  <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221721874-eae24e77-f56c-4e2b-b3eb-79a8ea7de90c.jpeg">

2. Generating SSH Keys for Github
- We will be creating a new private SSH key in ieng6 for accessing Github from our remote access accounts.
- Firstly, login to ieng6 and run the command <ssh-keygen>, pressing <Enter> again till we get the "randomart image".
  <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221722652-a7040ed3-1f4b-4318-b62b-45ba6b22d7a0.jpeg">
  <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221722654-966534c8-ad0d-46c6-bba1-8a74a625b0dc.jpeg">
- Afterwards, we will add the public key to our Github account, by first displaying the SSH public key by using <cat> through typing <cat /home/linux/ieng6/cs15lwi23/cs15lwi23awc/.ssh/id_rsa.pub>. The public key should be different per user.
  <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221723007-0b619d2c-1197-430e-89e2-274a6cd6a0b4.jpeg">
- We will then open our Github account through a browser, go to the settings, and click SSH and GPG keys in the "Access" section. Then we will add in a new SSH key with the title "Malcolm's ieng6 machine" and the key type with "Authentication Key" and type in the output of the <cat> command into the key field.
  <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221723629-b20154e9-38a1-4094-8f8d-d90f63978331.jpeg">
- Then, we will return to our ieng6 terminal and run <ssh-keyscan -t rsa github.com >> ~/.ssh/known_hosts> to add github.com as a recognized host to prevent further yes/no questions. To confirm that this was successfully done, we can run <ssh -T git@github.com> to verify.
  <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221724106-1558678d-3fed-46c1-b957-157a61e890dc.jpeg">

  
  
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
