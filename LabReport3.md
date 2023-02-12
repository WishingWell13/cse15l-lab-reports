In this lab report, we shall explore the options -r, -l, -L, and -c. I've included screenshots and codeblocks of output to highlight parts of the output and show the colors.

Grep highlights all the words that match our search, and only prints out lines in the file that contains our word. Here is some output for grep using no extra command-line options: ```grep Lucayans written_2/travel_guides/berlitz2/Bahamas-History.txt ```

```
grep Lucayans written_2/travel_guides/berlitz2/Bahamas-History.txt
Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the 
Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to 
replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
```

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

```grep -r cheap
written_2/non-fiction/OUP/Abernathy/ch15.txt:The most effective weapon used by American capital in weakening the power of organized labor has been to hire immigrant workers....[I]mmigrants are cheap and controllable. The conditions they toil under make a mockery of the already low American labor standards—the most regressive among the advanced industrial nations.20 
written_2/non-fiction/OUP/Abernathy/ch2.txt:A full-blown textile industry therefore blossomed in New England, fostered by the region’s access to abundant water power, capital, mechanical skills, and a hardworking labor force. But the adoption of steam power in New England was delayed until the 1850s and 1860s, at which time most of the significant water-power sites 
were already in use. The efficiency of steam engines had by then been greatly improved through the use of better materials, and their operating costs reduced by cheaper transportation 
of coal.32 Southern manufacturers had already adopted steam engines for textile production, 
along with newer and more productive technology. As a result, after 1880 the industry began 
to expand south, particularly in North and South Carolina, Georgia, and Alabama. By 1920, over half of the spinning and weaving capacity was in the South, leading industrialization there. By 1980, little of this basic part of the textile industry remained in New England.     
```

I have only included the first few outputs; this command prints out much more! If we only care about the file names, sifting through all this information is very cumbersome. We can add the -l command to help us with this! -l makes it so grep only returns the file names, without any of the matching text.

```grep -r -l Lucayans```

```
[cs15lwi23aon@ieng6-202]:skill-demo1-data:266$ grep -r -l Lucayans
written_2/travel_guides/berlitz2/Bahamas-History.txt
```

![image](https://user-images.githubusercontent.com/54158686/218286990-4ed84ac2-79f2-41f7-a54e-7d91302d7af8.png)

Much cleaner! Now I know the exact file name that contains the word "Lucayans". We can do something similar for our cheap vacation example too.

```grep -r -L Lucayans ```

![image](https://user-images.githubusercontent.com/54158686/218286156-47532184-aa99-4118-9385-f2b387cfd9f4.png)
Notice how the file "Bahamas History" doesn't show up in the file results. Only the files without the words Lucayans shows up!


```grep -c cheap```

![image](https://user-images.githubusercontent.com/54158686/218286311-34e7d7d9-831c-4541-abe0-9814a78b2ee6.png)

As you can see, written_2/travel_guides/berlitz2/Poland-WhatToDo.txt has three mentions of the word cheap! Maybe I'll plan my next vacation for there...
