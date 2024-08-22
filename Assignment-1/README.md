# Assignment 1
---
### Task 1
1. File is created using `touch firstname`
2. For adding lines into the file without using the text editor we can use echo, `echo "a new line" > firstname`
3. In that same file if we want to append we will use `echo "some more lines" >> firstname`
4. To rename a file we can move it to the same location with a different name `mv firstname lastname`
5. The first 5 lines is given by `head -n 5 lastname`
6. Similarly the last 5 lines are given by `tail -n 5 lastname`
7. To print some section a combination of head and tail will be used `head -n 6 lastname | tail -n 4`

### Task 2
1. To open the file using a text editor use `vim firstname`.
2. Similarly another file can be opened in a different terminal using `vim lastname`
3. Processes are listed out using `ps -aux`
4. In this case we want to find vim, we will use `ps -aux | grep vim`
5. Note that id of the process that we want to kill. Now use `kill pid` to kill that process. This will terminate the vim process of that file
