In this lab report, we shall explore the options -r, -l, -L, and -c.
grep -r cheap
![image](https://user-images.githubusercontent.com/54158686/218286247-f78f5ab7-af10-45a2-a6a0-9b00a24e4b64.png)

grep -r Lucayans



grep -r -l Lucayans



grep -r -L Lucayans 

![image](https://user-images.githubusercontent.com/54158686/218286156-47532184-aa99-4118-9385-f2b387cfd9f4.png)
Notice how the file "Bahamas History" doesn't show up in the file results. Only the files without the words Lucayans shows up!


grep -c cheap
![image](https://user-images.githubusercontent.com/54158686/218286311-34e7d7d9-831c-4541-abe0-9814a78b2ee6.png)

As you can see, written_2/travel_guides/berlitz2/Poland-WhatToDo.txt has three mentions of the word cheap! Maybe I'll plan my next vacation for there...
