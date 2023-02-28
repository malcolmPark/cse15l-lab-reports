# **Week 5 Lab Report** by Malcolm Park (Jooahn)

This weeks lab report will focus on commands that are used in bash scripts. In particular, I will be focusing on the `grep` command, variations I can use with `grep`, and examples of using it with the written_2 data.

## Variations of `grep` command I will use
These command extensions were all found with [geeksforgeeks.org](https://www.geeksforgeeks.org/grep-command-in-unixlinux/)
```
grep -c : This command will return the number of lines that match a string
grep -n : This command will display the line number in addition to the actual output of the matched line.
grep -i : This command acts as a case insenstive search
grep -l : This command will display the name of the files that match a string 
```

### `grep -c`
- <img width="300" alt="First use of grep -c" src="https://user-images.githubusercontent.com/122580137/221717237-a591b903-b924-4d95-a466-8cedaf4f8e38.jpeg">
- This first use of `grep -c` shows that the word "and" appears in 8 lines in the text file HandRLosAngeles. This is useful because it doesn't fill up your screen with all the texts that the string appears in, making it easier for programmers to notice.
- <img width="300" alt="Second use of grep -c" src="https://user-images.githubusercontent.com/122580137/218573392-0c4b77e9-80be-4074-bd0f-af3fce9cacb2.jpeg">
- This second use of `grep -c` is combined with the -r command that recursively searches the directory. Therefore, it shows all files in the travel_guides directory and shows the number of lines with the matching string of "asia". This is technically more useful than the original `grep -c` command since it is recursive and you can apply it over a general directory.

### `grep -n`
- <img width="300" alt="First use of grep -n" src="https://user-images.githubusercontent.com/122580137/218576073-7f9dadef-03f8-4363-9da3-61886f2322d2.jpeg">

- This first use of `grep -n` shows that the word "America" appears in lines 6, 10, 20, and 30 along with the actual lines the word appears in in the file Cuba-History.txt. This is useful because it allows the programmers to directly see where the matched strings appear in the text file.
- <img width="300" alt="Second use of grep -n" src="https://user-images.githubusercontent.com/122580137/218577107-ee99dc46-b7a5-496d-ba23-4f31cc2a3a1a.jpeg">
- This second use of `grep -n` is combined with the -H command, so that it displays the file name in addition to the line number and the line of text that contains the matching string. Here, it is looking for the string "The word zoot" in the Castro directory. This is useful because it offers more information than the previous one in that the programmer doesn't need to add an additional code to find what the file with the matching string is.

### `grep -i`
- <img width="300" alt="First use of grep -i" src="https://user-images.githubusercontent.com/122580137/218578432-94284f07-a7b8-419c-8a35-1ef8a33072fd.png">
- This first use of `grep -i` shows the case matches of the word "Democratic" while searching the Berlin-History.txt, regardless of the case of each letter. This is useful because as a programmer, we might want to find all uses of the string, but finding all of the case insensitive matches would be hard without this feature.
- <img width="300" alt="Second use of grep -i" src="https://user-images.githubusercontent.com/122580137/218579912-e521e5f9-66a2-4e95-8888-dcbc1db729c6.png">
- This second use of `grep -i` is combined with the -w command, so that it displays the lines that contain the matching string as a full word, regardless of whether it is in a different case or not. Again, this command is useful because we might want to know matching cases only when the matched word is a full string of its own and not a substring.

### `grep -l`
- <img width="300" alt="First use of grep -l" src="https://user-images.githubusercontent.com/122580137/218580667-ef3913d7-f1dc-4693-b599-a469220d1eb3.png">
- This first use of `grep -l` shows that the word "Indonesia" is used in files Amsterdam-History.txt, Amsterdam-WhereToGo.txt, Bali-History.txt, Bali-WhatToDo.txt, Bali-WhereToGo.txt, Berlin-WhereToGo.txt, and Canada-WhereToGo.txt within the berlitz2 directory. This command is useful because it doesnt crowd out the screen like many of the `grep` command extensions does before.
- <img width="300" alt="Second use of grep -l" src="https://user-images.githubusercontent.com/122580137/218581298-74fbb77a-c17d-4c91-b79f-d7513674f938.png">
- This second use of `grep -L` is a unique variation of `grep -l`; Instead of showing the files that do have the matching string, it will show all of the files that do NOT have the matching string. Therefore, the command shows all of the files in berlitz2 directory that do NOT have the string value "British" inside it. Say that we are programming an answer checking machine; This command is crucial because it can show whether the given answer is a plausible one or not.
