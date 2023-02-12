# The Grep Command
In this lab report, we shall explore the options **-r, -l, -L**, and **-c** for the grep command. I've included screenshots and codeblocks of output to highlight parts of the output and show the colors. I found all my commands at this link: https://man7.org/linux/man-pages/man1/grep.1.html

## Default Behavior
Grep highlights all the words that match our search, and only prints out lines in the file that contains our word. Here is some output for grep using no extra command-line options: ```grep Lucayans written_2/travel_guides/berlitz2/Bahamas-History.txt ```

```
grep Lucayans written_2/travel_guides/berlitz2/Bahamas-History.txt
Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the 
Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to 
replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
```

## The -r Option
This is useful if we already know what file we want to search, but what if we want to find files with the word "Lucayans"? In this case, we case use the -r command to recursively search through many directories.
```grep -r Lucayans```

```
[cs15lwi23aon@ieng6-202]:skill-demo1-data:261$ grep -r Lucayans                      
written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of 
Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared 
them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly 
called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the 
gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to 
settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water 
on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
```

![image](https://user-images.githubusercontent.com/54158686/218286338-c28f5c18-7480-4210-9a1e-ebb6fc22bb16.png)

Even though we are passing in a directory (our working directory in this case), grep still works! Notice how grep also searches through all the subdirectories within our current directory and spits out the file name, which it did not do before.

Here is another example. Let's say I forgot to submit my scholarship applications, and now I need a cheap place to vacation. I can use the command ```grep -r cheap``` to find all the places that will be cheap to vacation at!

![image](https://user-images.githubusercontent.com/54158686/218286247-f78f5ab7-af10-45a2-a6a0-9b00a24e4b64.png)


```
grep -r cheap
written_2/non-fiction/OUP/Abernathy/ch15.txt:The most effective weapon used by American capital in weakening the power of organized labor has been to hire immigrant workers....[I]mmigrants are cheap and controllable. The conditions they toil under make a mockery of the already low American labor standards—the most regressive among the advanced industrial nations.20 
written_2/non-fiction/OUP/Abernathy/ch2.txt:A full-blown textile industry therefore blossomed in New England, fostered by the region’s access to abundant water power, capital, mechanical skills, and a hardworking labor force. But the adoption of steam power in New England was delayed until the 1850s and 1860s, at which time most of the significant water-power sites 
were already in use. The efficiency of steam engines had by then been greatly improved through the use of better materials, and their operating costs reduced by cheaper transportation 
of coal.32 Southern manufacturers had already adopted steam engines for textile production, 
along with newer and more productive technology. As a result, after 1880 the industry began 
to expand south, particularly in North and South Carolina, Georgia, and Alabama. By 1920, over half of the spinning and weaving capacity was in the South, leading industrialization there. By 1980, little of this basic part of the textile industry remained in New England.     
```

## The -l Option
I have only included the first few outputs; this command prints out much more! If we only care about the file names, sifting through all this information is very cumbersome. We can add the -l command to help us with this! -l makes it so grep only returns the file names, without any of the matching text.

```grep -r -l Lucayans```


```
[cs15lwi23aon@ieng6-202]:skill-demo1-data:266$ grep -r -l Lucayans
written_2/travel_guides/berlitz2/Bahamas-History.txt
```

![image](https://user-images.githubusercontent.com/54158686/218286990-4ed84ac2-79f2-41f7-a54e-7d91302d7af8.png)

Much cleaner! Now I know the exact file name that contains the word "Lucayans". We can do something similar for our cheap vacation example too.

```
[cs15lwi23aon@ieng6-202]:skill-demo1-data:267$ grep -r -l cheap
written_2/non-fiction/OUP/Abernathy/ch15.txt
written_2/non-fiction/OUP/Abernathy/ch2.txt
written_2/non-fiction/OUP/Abernathy/ch3.txt
written_2/non-fiction/OUP/Rybczynski/ch2.txt
written_2/travel_guides/berlitz1/HistoryFWI.txt
written_2/travel_guides/berlitz1/HistoryHongKong.txt
written_2/travel_guides/berlitz1/HistoryIndia.txt
written_2/travel_guides/berlitz1/HistoryItaly.txt
written_2/travel_guides/berlitz1/HistoryLasVegas.txt
written_2/travel_guides/berlitz1/IntroItaly.txt
written_2/travel_guides/berlitz1/IntroMallorca.txt
written_2/travel_guides/berlitz1/WhatToEgypt.txt
written_2/travel_guides/berlitz1/WhatToGreek.txt
written_2/travel_guides/berlitz1/WhatToHongKong.txt
written_2/travel_guides/berlitz1/WhatToIbiza.txt
written_2/travel_guides/berlitz1/WhatToIndia.txt
written_2/travel_guides/berlitz1/WhatToIsrael.txt
written_2/travel_guides/berlitz1/WhatToIstanbul.txt
written_2/travel_guides/berlitz1/WhatToItaly.txt
written_2/travel_guides/berlitz1/WhatToJapan.txt
written_2/travel_guides/berlitz1/WhatToLasVegas.txt
written_2/travel_guides/berlitz1/WhatToMadeira.txt
written_2/travel_guides/berlitz1/WhatToMallorca.txt
written_2/travel_guides/berlitz1/WhereToEdinburgh.txt
written_2/travel_guides/berlitz1/WhereToFrance.txt
written_2/travel_guides/berlitz1/WhereToHongKong.txt
written_2/travel_guides/berlitz1/WhereToIbiza.txt
written_2/travel_guides/berlitz1/WhereToIndia.txt
written_2/travel_guides/berlitz1/WhereToIsrael.txt
written_2/travel_guides/berlitz1/WhereToItaly.txt
written_2/travel_guides/berlitz1/WhereToJapan.txt
written_2/travel_guides/berlitz1/WhereToMadeira.txt
written_2/travel_guides/berlitz1/WhereToMalaysia.txt
written_2/travel_guides/berlitz1/WhereToMallorca.txt
written_2/travel_guides/berlitz2/Algarve-WhatToDo.txt
written_2/travel_guides/berlitz2/Algarve-WhereToGo.txt
written_2/travel_guides/berlitz2/Amsterdam-WhatToDo.txt
written_2/travel_guides/berlitz2/Amsterdam-WhereToGo.txt
written_2/travel_guides/berlitz2/Bahamas-Intro.txt
written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2/travel_guides/berlitz2/Bali-WhatToDo.txt
written_2/travel_guides/berlitz2/Bali-WhereToGo.txt
written_2/travel_guides/berlitz2/Barcelona-WhatToDo.txt
written_2/travel_guides/berlitz2/Beijing-WhatToDo.txt
written_2/travel_guides/berlitz2/Bermuda-WhatToDo.txt
written_2/travel_guides/berlitz2/Budapest-WhatToDo.txt
written_2/travel_guides/berlitz2/California-WhatToDo.txt
written_2/travel_guides/berlitz2/California-WhereToGo.txt
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
written_2/travel_guides/berlitz2/CanaryIslands-History.txt
written_2/travel_guides/berlitz2/CanaryIslands-WhatToDo.txt
written_2/travel_guides/berlitz2/Cancun-WhatToDo.txt
written_2/travel_guides/berlitz2/Cancun-WhereToGo.txt
written_2/travel_guides/berlitz2/China-WhatToDo.txt
written_2/travel_guides/berlitz2/Costa-WhatToDo.txt
written_2/travel_guides/berlitz2/Costa-WhereToGo.txt
written_2/travel_guides/berlitz2/CostaBlanca-History.txt
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt
written_2/travel_guides/berlitz2/Nepal-WhatToDo.txt
written_2/travel_guides/berlitz2/Nepal-WhereToGo.txt
written_2/travel_guides/berlitz2/Paris-WhatToDo.txt
written_2/travel_guides/berlitz2/Poland-WhatToDo.txt
written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt
written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
written_2/travel_guides/berlitz2/PuertoRico-WhatToDo.txt
written_2/travel_guides/berlitz2/PuertoRico-WhereToGo.txt
written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt
```

![image](https://user-images.githubusercontent.com/54158686/218287838-fb753e6e-301f-46c5-9dbc-a52b4370d096.png)

A lot of locations with cheap options to chose from! Again, only file names are being printed, not the actual content of the files.

## The -L Option

Now, let's say I just came off a big project reporting on the Lucayans, and I don't want to think about it anymore. What if I want to find all the files that don't mention Lucayans? I can use the command ```grep -r -L Lucayans ```

```
written_2/travel_guides/berlitz2/Amsterdam-WhatToDo.txt
written_2/travel_guides/berlitz2/Amsterdam-WhereToGo.txt
written_2/travel_guides/berlitz2/Athens-History.txt
written_2/travel_guides/berlitz2/Athens-Intro.txt
written_2/travel_guides/berlitz2/Athens-WhatToDo.txt
written_2/travel_guides/berlitz2/Athens-WhereToGo.txt
written_2/travel_guides/berlitz2/Bahamas-Intro.txt
written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2/travel_guides/berlitz2/Bali-History.txt
written_2/travel_guides/berlitz2/Bali-WhatToDo.txt
written_2/travel_guides/berlitz2/Bali-WhereToGo.txt
written_2/travel_guides/berlitz2/Barcelona-History.txt
```

![image](https://user-images.githubusercontent.com/54158686/218286156-47532184-aa99-4118-9385-f2b387cfd9f4.png)

Notice how the file "Bahamas History" doesn't show up in the file results. Only the files without the words Lucayans shows up!

Let's do the same thing for our vacation example. It turns out, I actually submitted my scholarship applications in my sleep! I don't want to go somewhere cheap anymore. Let's see where I can go using the command ```grep -r -L cheap```

```
written_2/travel_guides/berlitz1/IntroMadrid.txt
written_2/travel_guides/berlitz1/IntroMalaysia.txt
written_2/travel_guides/berlitz1/JungleMalaysia.txt
written_2/travel_guides/berlitz1/WhatToDublin.txt
written_2/travel_guides/berlitz1/WhatToEdinburgh.txt
written_2/travel_guides/berlitz1/WhatToFWI.txt
written_2/travel_guides/berlitz1/WhatToFrance.txt
written_2/travel_guides/berlitz1/WhatToHawaii.txt
written_2/travel_guides/berlitz1/WhatToJamaica.txt
written_2/travel_guides/berlitz1/WhatToLakeDistrict.txt
written_2/travel_guides/berlitz1/WhatToLosAngeles.txt
```
![image](https://user-images.githubusercontent.com/54158686/218287492-f63125d5-5116-4d59-aa58-e25a41e14ef6.png)

A lot of options! Notice that none of the files that showed up in the **-l** command shows up in this list.


## The -c Option
What if I just want to know how many lines contain the word Lucayans? I can use the command ```grep -r -c Lucayans```.

![image](https://user-images.githubusercontent.com/54158686/218287560-b14ebc43-449a-4db9-bc6d-d42e45f26908.png)

```
written_2/travel_guides/berlitz2/Athens-Intro.txt:0
written_2/travel_guides/berlitz2/Athens-WhatToDo.txt:0
written_2/travel_guides/berlitz2/Athens-WhereToGo.txt:0
written_2/travel_guides/berlitz2/Bahamas-History.txt:2
written_2/travel_guides/berlitz2/Bahamas-Intro.txt:0
written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt:0
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt:0
```
Notice that _written_2/travel_guides/berlitz2/Bahamas-History.txt_ is the only file with a value greater than zero. This is why we only see the Bahamas-History file in our output for ```grep -r Lucayans```!

We can apply this same concept to our vacation example. I want to see which place has the most cheap options. Let's find out with the command:

```grep -r -c cheap```. 

![image](https://user-images.githubusercontent.com/54158686/218286311-34e7d7d9-831c-4541-abe0-9814a78b2ee6.png)

```
written_2/travel_guides/berlitz2/Nepal-WhereToGo.txt:3
written_2/travel_guides/berlitz2/NewOrleans-History.txt:0
written_2/travel_guides/berlitz2/Paris-WhatToDo.txt:1
written_2/travel_guides/berlitz2/Paris-WhereToGo.txt:0
written_2/travel_guides/berlitz2/Poland-History.txt:0
written_2/travel_guides/berlitz2/Poland-WhatToDo.txt:3
written_2/travel_guides/berlitz2/Portugal-History.txt:0
written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt:2
written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt:1
written_2/travel_guides/berlitz2/PuertoRico-History.txt:0
written_2/travel_guides/berlitz2/PuertoRico-WhatToDo.txt:1
written_2/travel_guides/berlitz2/PuertoRico-WhereToGo.txt:2
written_2/travel_guides/berlitz2/Vallarta-History.txt:0
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt:0
written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt:1
```

As you can see, written_2/travel_guides/berlitz2/Poland-WhatToDo.txt has three mentions of the word cheap! Maybe I'll plan my next vacation for there after all...

## Closing Thoughts
That is four different options for the grep command! We were able to search for all files in a directory with **-r**, only return file names with **-l**, only return non-matching files with **-L**, and return the number of times a word is mentioned with **-c**.
