# Using the Cloudera QuickStart VM for the first time.

## Using the WordCount program + basic commands.

A quick tutorial for the installation [here](https://www.youtube.com/watch?v=EuCjP0JLxT8[).

### Getting the data

In the example, we'll use the Shakespeare works. The link is [here](https://ocw.mit.edu/ans7870/6/6.006/s08/lecturenotes/files/t8.shakespeare.txt).

Save the file as a txt file. 

### Enter the directory

In my case, the txt file is in *Downloads* 

```bash
cd Downloads
```

### Check if the file is in the folder you're in

```bash
ls
```

### Load the txt file to the Hadoop File System

*words.txt* is my txt file.*

```bash
hadoop fs -copyFromLocal words.txt
```

### Check if the file was indeed  uploaded to Hadoop File System

```bash
hadoop fs -ls 
```

----------------------------------------

**Note:** The following two steps are not mandatory, but I decided to leave it there since it can help to learn other basic commands. I marked such steps with (*)

### Copy the txt inside HDFS. *

This is not necessary, it was just part of the tutorial I followed. Anyway, I'll leave it here.

This line of code copies *words.txt* file to another, which I called *words2.txt*:

The `ls` is just to verify it was successfully uploaded

```bash
hadoop fs -cp words.txt words2.txt
hadoop fs -ls
```

### Copy the HDFS files to the local directory*

And use `ls` to verify it

```bash
hadoop fs -copyToLocal words2.txt
ls
```

### Deleting a file in HDFS

```bash
hadoop fs -rm words2.txt 
```

Now, use `ls` to see that *words2.txt* is no longer there

```bash
ls
```



--------------------------------

## The WordCount program of Hadoop

Hadoop comes with some preloaded programs, in this case we'll use the wordcount program

### Show all Hadoop programs

```bash
hadoop jar /usr/jars/hadoop/examples.jar 
```

You should be able to see a "menu" of programs. Keep scrolling down until you see the *Wordcount* program.

### See which arguments the program needs

```bash
hadoop jar /usr/jars/hadoop-examples.jar wordcount
```

### Use the program

This code uses wordcount on the *words.txt* file and stores the results in a file called *out*. Of course, you can change the name of your output file.

```bash
hadoop jar /usr/jars/hadoop-examples.jar wordcount words.txt out
```

**NOTE:** you'll see how the program works. It can take a while

Once the program finishes:

### Check if the output file *out* was created

```bash
hadoop fs -ls 
```

### Look inside the *out* file

```bash
hadoop fs -ls out 
```

### Store the results of the *out* file in a new txt file and copy it to a local txt file named [insert whatever name you want]. (In my case, such new file is called "local.txt")

```bash
hadoop fs -copyToLocal out/part-r-00000 local.txt  
```

### See the results!

```
more local.txt
```

If you want to quit, press `q` 

Press the space bar to scroll down in your results.

------------------------------



