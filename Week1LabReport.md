# CSE 15L Lab Report Week 1

## Download Visual Studio Code:
If you have not already, please download VS Code here: https://code.visualstudio.com/
![Imgur](https://i.imgur.com/yuZtLMO.png)
Just leave all of the install steps as default, unless you want to change the install location. Follow all of the install instructions and open it up on your computer.

## Remotely Connecting on Visual Studio
To log into your account, you'll need to open your terminal. Open the terminal using the command Ctrl `. Make sure you open the git based terminal and not a different kind.

Type in $ ssh cs15lwi23ABC@ieng6.ucsd.edu, replacing ABC with whatever your course-specific account has
![Imgur](https://i.imgur.com/h8UAZIi.png)

It is fine if it says it can't verify the authenticity, assuming this is your first time logging in. Type yes. 
If Host Key Verification fails, try typing in your ssh [email] one more time and write yes again. This worked for me.
![Imgur](https://i.imgur.com/wpJWANh.png)

Next, enter your passwood. You should now see a notice if you entered it correctly:
![Imgur](https://i.imgur.com/HZfcObz.png)

This notice will be followed up by a bunch of other stats. You are now logged in!

## Accessing Files From Other Accounts

![image](https://user-images.githubusercontent.com/54158686/212519922-e126bf7f-18f7-4eb4-b16c-54e5773b1f64.png)

I think the most interesting command we tried during lab today was trying to access other people's files. Note that we can attempt to navigate directly to someone else's account, implying that all accounts are under a shared folder cs15lwi23. However, we still get denied access, most likely because we have not provided credentials yet for the specific account we tried to access. 
