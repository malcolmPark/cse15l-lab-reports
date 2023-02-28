# **Week 7 Lab Report** by Malcolm Park (Jooahn)

This week's lab report will focus on detailing and reproducing the task from the lab competition on our own. The lab challenge was an activity where we needed to login to out ssh key, clone a fork of a repository, run tests, demonstrate they fail, fix the errors within the tests, and commit/push the change to the github account!

## Preparations for the lab challenge (github and login command-line setup). 
> This is not a part of the timed challenge, but preparations for that portion of the lab challenge.

1. Generating SSH Keys for ieng6
- First, we will open our terminal using visual studio code. Then, we will run <ssh-keygen>. After doing so, we will keep pressing <Enter> until we see a text called "randomart image".
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221719699-a389c77d-09ae-401c-9071-56547a1a3350.jpeg">
- Then, we will login to our remote course specific account on ieng6.
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221720291-dc954a32-6d0a-4900-85b7-a0f3d45f52b6.jpeg"> 
- After doing so, run <mkdir .ssh> and then logout of the remote account.
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221720807-bb28c85a-a2f5-4cf4-8cc1-f9af73f069a7.jpeg">
- Now we want to copy the public ssh key that we created on our personal computer to our remote account. We will do this by finding the path the ssh key that we made (which ends in .pub) and running <scp /Users/jooahn/.ssh/id_rsa.pub cs15lwi23awc@ieng6.ucsd.edu:~/.ssh/authorized_keys>. The path and the login key should be different for the user. This will save the ssh key into the .ssh directory inside a file called authorized_keys.
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221721874-eae24e77-f56c-4e2b-b3eb-79a8ea7de90c.jpeg">

2. Generating SSH Keys for Github
- We will be creating a new private SSH key in ieng6 for accessing Github from our remote access accounts.
- Firstly, login to ieng6 and run the command <ssh-keygen>, pressing <Enter> again till we get the "randomart image".
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221722652-a7040ed3-1f4b-4318-b62b-45ba6b22d7a0.jpeg">
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221722654-966534c8-ad0d-46c6-bba1-8a74a625b0dc.jpeg">
- Afterwards, we will add the public key to our Github account, by first displaying the SSH public key by using <cat> through typing <cat /home/linux/ieng6/cs15lwi23/cs15lwi23awc/.ssh/id_rsa.pub>. The public key should be different per user.
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221723007-0b619d2c-1197-430e-89e2-274a6cd6a0b4.jpeg">
- We will then open our Github account through a browser, go to the settings, and click SSH and GPG keys in the "Access" section. Then we will add in a new SSH key with the title "Malcolm's ieng6 machine" and the key type with "Authentication Key" and type in the output of the <cat> command into the key field.
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221723629-b20154e9-38a1-4094-8f8d-d90f63978331.jpeg">
- Then, we will return to our ieng6 terminal and run <ssh-keyscan -t rsa github.com >> ~/.ssh/known_hosts> to add github.com as a recognized host to prevent further yes/no questions. To confirm that this was successfully done, we can run <ssh -T git@github.com> to verify.
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221724106-1558678d-3fed-46c1-b957-157a61e890dc.jpeg">

  
  
  
  
  
  
  
  
  
  
  
  
  
  
## Actual Lab Challenge.
> This section will now cover the actual lab challenge.
> Time yourself!

### Setups
  Delete any existing fork of the repository. Fork the repository. Start timer!
### Process
  1. Login to ieng6.
  <br /> Open terminal and type <ssh cs15lwi23awc@ieng6.ucsd.edu>. The password will not be prompted if correctly prepared.
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221725284-75b7a9a8-9360-43f2-b283-c7ac6ad57ed8.jpeg">
  
  2. Clone your fork of the repository from your github account.
  <br /> Type <git clone https://github.com/malcolmPark/lab7>. The url is the link for the forked repository in your github account.
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221725774-b6553259-4e8f-4fea-9ab4-ad7b8aa66528.jpeg">
  
  3. Run tests and demonstrate failure.
  <br /> Type <javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java> and then <java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests> to run the tests to demonstrate that they fail.
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221726459-cc305526-d914-4c46-9339-339569efe7b4.jpeg">
  
  4. Change tests to fix failure.
  <br /> Now that we know that there is a failing text, we can type <nano ListExamples.java> to directly edit the java files from the bash script. 
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221727135-69a05cda-4dff-4cac-8f23-ac335b3c8cf7.jpeg">
  <br /> We can use the arrow key to move down where the error is, but scrolling down is much faster. After we get to the correct line, type <right> 12 times to get to the text we need to change. Replace the "1" to "2" so that it changes from "index1" to "index2".
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221727443-528c24c5-4d3e-4b17-b4a0-f2815b5cf0ab.jpeg">
  <br /> When we are done changing the test, type <^o> ctrl o to save the changes and type <^x> ctrl x to exit back to the terminal.
  
  5. Run the tests again to demonstrate success.
  <br /> Type <javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java> and then <java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests> to run the tests to demonstrate that they now succeed. Or, now that we have the command in the search history, we can use the up arrow <up> three times to compile and two times to run the tests.
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221728242-4d0c0b28-d3f9-45bf-ae88-8c9ec0331f04.jpeg">
  
  6. Commit and push
  <br /> Now that we have everything fixed, we are ready to commit and push the changes to our github account. We will do so by first typing <git add .> which adds all the java files we intend to commit and push. Then, we type <git commit -m "Changes"> and then <git push>.
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221729085-c57f7ffd-606e-4e05-bac1-dbc221c80a56.jpeg">
  <br /> <img width="300" alt="Screen Shot 2023-01-12 at 5 38 38 PM" src="https://user-images.githubusercontent.com/122580137/221729240-9741711a-0da4-4222-895f-f6538a21ebc8.jpeg">


  

