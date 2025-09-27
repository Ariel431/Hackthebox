# HTB Linux Commands Exercise - Writeup

## New Commands Discovered in This Scene: 

- *which*
- *find*
- *locate*


## Questions and Solutions

### 1.  What is the name of the config file that has been created after 2020-03-03 and is smaller than 28k but larger than 25k?

Command to use :
```bash
    find / -type f   -name *.conf  -newermt 2020-03-03 -size +25k -size -28k 2>/dev/null 
```    

---

### 2. How many files exist on the system that have the ".bak" extension?

Command to use : 
```bash
    locate ".bak" | wc -l 
```    
                                OR

```bash
    find / -type f -name "*.bak" 2>/dev/null | wc -l
```                    
---


### 3. Submit the full path of the "xxd" binary.

Command to use : 
```bash
    which xxd
```    

--- 

## Command Reference

### Commands Used in This Exercise :
- `which` - This tool returns the path to the file or link that should be executed
  
- `locate` - The command locate offers us a The command locate offers us a quicker way to search through the system. In contrast to the find command, locate works with a local database that contains all information about existing files and folders .
The locate command relies on a database that needs to be updated with updatedb. For real-time results, use find instead.

- `find` - Besides the function to find files and folders, this tool also contains the function to filter the results. We can use filter parameters like the size of the file or the date. We can also specify if we only search for files or folders.

### Parameters of find : 
- `type f` - Hereby, we define the type of the searched object. In this case, 'f' stands for 'file'.

- `-name "*.conf"` -With '-name', we indicate the name of the file we are looking for. The asterisk (*) stands for 'all' files with the '.conf' extension. 

- `-size +25k` -We can then filter all the located files and specify that we only want to see the files that are larger than 25 KiB.

-  `-size -28k` -strictly less than 28 kilobytes

- `-newermt 2020-03-03` -With this option, we set the date. Only files newer than the specified date will be presented.

- `2>/dev/null` -This is a STDERR redirection to the 'null device', which we will come back to in the next section. This redirection ensures that no errors are displayed in the terminal. This redirection must not be an option of the 'find' command.

- `wc -l`  -To count the number of files found.



