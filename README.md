

# Mia Scott Assignment: GA2 #

1.  Add a header to your README file to indicate that this file (and dir) is for your assignment.

    done!

1. Initialize a Git repository inside your new directory.

    I used the following command:

    ```
    git init

    ```

    The output was:
    
    ```
    Initialized empty Git repository in /fs/ess/PAS2880/users/scott2291/GA2/.git/
    ```


1.    Add & stage and then commit the README file with an appropriate commit message.

        I used the following commands:

         ```
        git add README.md
        git commit -m "Adding README to Git Respository"
        ```

        The output was:
    
         ```
        1 file changed, 80 insertions(+)
        create mode 100644 README.md
        ```

1. Copy the genome annotation GTF file GCF_016801865.2.gtf.gz that is in your copy of the Garrigós et al. (2025) data to a file data/annot.gtf.gz (i.e., into the data dir you just created).

    I used the following commands:

    ```
    cp ../garrigos-data/ref/GCF_016801865.2.gtf.gz data/annot.gtf.gz
    ls data/
    ```

    The output was:
    
    ```
    annot.gtf.gz
    ```


1. Check the file size of annot.gtf.gz. Then, decompress the GTF file with the gunzip command below. Finally, check the size of the resulting annot.gtf file. How large is the size difference between the compressed and uncompressed files?

    I used the following commands:

    ```
    ls -lh data/
    gunzip data/annot.gtf.gz
    ls -lh data/
    ```

    The output was:
    
    ```
    -rw-rw----+ 1 scott2291 PAS2880 5.1M Sep 18 14:47 annot.gtf.gz
    -rw-rw----+ 1 scott2291 PAS2880 123M Sep 18 14:47 annot.gtf
    ```
    There is a 117.9M difference in size between the compressed and uncompressed files 

1. The total number of “genomic features” (genes, exons, etc.) listed in a GTF file is simply the number of lines in its main/table section.

   - Count the total number of lines in annot.gtf.
       
        I used the following command:

        ```
        wc -l data/annot.gtf
        ```

        The output was:
    
        ```
        408402 data/annot.gtf
        ```
   - Take a look at the contents of the file and count the number of header lines by eye.


     I see 4 header lines

   - Based on your knowledge of what the GTF header lines look like, combine grep -v and wc -l to count the number of genomic features in the file.

       
        I used the following command:

        ```
        grep -v "#" data/annot.gtf | wc -l 
        ```

        The output was:
    
        ```
        408397
        ```
1. Does the difference between the two line counts you just performed correspond to the number of header lines you counted visually? If not, can you figure out which other line(s) than the header lines contain the pattern you used with grep above?
        
    The difference between the two lines do not correspond to the header sections I counted because the command accounted a line that contained "###" at the end of the GTF that I missed. The `grep` command noticed this pattern where I missed it.

1. How many distinct “sequences” (chromosome/scaffolds/contigs) are represented in the annotation file? Store a list of these distinct sequences in a file results/scaffolds.txt.

  
    I used the following commands:

    ```
    grep -v "#" data/annot.gtf | cut -f 1 | sort | uniq | wc -l
    grep -V "#" | cut -f 1  data/annot.gtf | sort | uniq > results/scaffolds.txt
    ls results/
    ```

    The output was:
    
    ```
    167
    scaffolds.txt
    ```


1. Print a “count table” (like we did towards the end of this section) of feature types in the annotation: this should have a count of the number of times each feature type occurs. (Such a table will for example show how many genes have been annotated in this genome – quite useful!)

  
     I used the following command:

    ```
    grep -v "#" data/annot.gtf | cut -f 3 | sort | uniq -c
    ```

    The output was:
    
    ```
    141444 CDS
    166177 exon
    19673 gene
    25864 start_codon
    25892 stop_codon
    29347 transcript
    ```

1. Check the status of your Git repository. You should see that your README has changed but also that Git has detected the files in the data and results dirs. You don’t want to commit any files in the data and results dirs, so create a .gitignore file that makes Git ignore them. Check the status of your repository again – is your .gitignore file working as intended?

  
    I used the following commands:


     ```
    git status
    echo "data/" > .gitignore 
    echo "results/" >> .gitignore 
    cat .gitignore 
    git status
    ```

    The output was:
    
    ```
    On branch main
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

    Untracked files:
    (use "git add <file>..." to include in what will be committed)
        data/
        results/

    no changes added to commit (use "git add" and/or "git commit -a")

    ```
        data/
        results/
     

    ```
    On branch main
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

    Untracked files:
        (use "git add <file>..." to include in what will be committed)
           .gitignore

    no changes added to commit (use "git add" and/or "git commit -a")
    ```
    Yes, my .gitignore file has worked as intended

1. Stage and commit the .gitignore file.
  
    I used the following commands:

    ```
    git add .gitignore
    git commit -m "Add a gitignore file"
    ```

    The output was:
    
    ```
    [main 6c2ad08] Add a gitignore file
    1 file changed, 2 insertions(+)
    create mode 100644 .gitignore
    ```

1. Stage and commit the README.md file again.

  
    I used the following commands:

    ```
    git add README.md
    git commit -m "Part A complete"
    ```

    The output was:
    
    ```
    [main 0005e62] Part A complete
    1 file changed, 162 insertions(+), 2 deletions(-)
    ```

1. Copy the FASTQ file ERR10802863_R1.fastq.gz of the Garrigós et al. (2025) data to a file of the same name inside the same data dir you copied the GTF file into.

  
    I used the following commands:


    ```
    cp ../garrigos-data/fastq/ERR10802863_R1.fastq.gz data/
    ls data
    ```

    The output was:
    
    ```
    annot.gtf  ERR10802863_R1.fastq.gz
    ```

1. Check the status of your Git repository. Does the FASTQ file show up? Why/why not?
    
  
    I used the following command:


     ```
    git status
    ```

    The output was:
    
    ```
    On branch main
    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
     (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

    no changes added to commit (use "git add" and/or "git commit -a")
    ```

    The copied FASTQ file does not show up in my Git repository because of the gitignore file that is designed to ignore any file that are in `/data`.

1. How many reads does the FASTQ file contain?
  
   I used the following command:

    ```
   zgrep -c  "@" data/ERR10802863_R1.fastq.gz
    ```

    The output was:
    
    ```
    500000
    ```

1. How many reads in the FASTQ file contain the sequence ACGT? (You can assume this string does not occur outside of the lines with sequences.)
  
    I used the following command:

    ```
   zgrep -c "ACGT" data/ERR10802863_R1.fastq.gz
    ```

    The output was:
    
    ```
    100465
    ```

1. How many reads contain at least 10 consecutive Ns (uncalled bases)? (You can assume that stretches of N’s do not occur in the sequence quality lines.)
  
    I used the following command:

    ```
   zgrep -c "NNNNNNNNNN" data/ERR10802863_R1.fastq.gz
    ```

    The output was:
    
    ```
    32612
    ```

1. Using the read length information in the FASTQ read header lines, print a count table of read lengths.

  
    I used the following command:

    ```
   zgrep "@" data/ERR10802863_R1.fastq.gz | cut -d ' ' -f 3 | sort | uniq -c
    ```

    The output was:
    
    ```
    32678 length=35
      4 length=36
      7 length=37
      2 length=38
      3 length=39
      4 length=40
      4 length=41
      3 length=42
      6 length=43
      6 length=44
      4 length=45
      8 length=46
      6 length=47
      3 length=48
      2 length=49
     11 length=50
     14 length=51
     14 length=52
     12 length=53
     11 length=54
     18 length=55
     13 length=56
     13 length=57
     17 length=58
     21 length=59
     27 length=60
     28 length=61
     28 length=62
     47 length=63
     90 length=64
     61 length=65
     49 length=66
     78 length=67
    276 length=68
    620 length=69
   1962 length=70
    8483 length=71
    28617 length=72
    123453 length=73
    303297 length=74
    ```

1. Compare the number you got in the previous question with the number of 35-bp reads from the question before that. What does this seem to tell you? To confirm, can you check what a sample of 35-bp reads look like?


    My `zgrep` command found 32612 reads that had 10 N's in a row compared to the 32678 35-bp length reads. This indicated to me that there are some 35-bp reads that do not contain a sequence with 10 N's in a row. 
  
    To test this theory, I used the following command:

    ```
   zgrep -A 3 "length=35"  data/ERR10802863_R1.fastq.gz | less 
    ```
    One of the reads I found had an output of
    
    ```
    @ERR10802863.640571 640571 length=35
    ACATTTAGATACCGTGGTTAGTATCTAAATGTNNN
    +
    AAAAAEEE/EE/AEEEEEEAEEEE/EEEEEEE###
    --
    ```
    This shows me that there are some reads that include sequence information and have a length of 35 bp.


1. Stage and commit the README.md file again.

    I used the following commands:

    ```
    git add README.md
    git commit -m "Part B complete"
    ```

    The output was:
    
    ```
    [main 5a5a968] Part B completed
    1 file changed, 173 insertions(+), 13 deletions(-)
    ```

Bonus

1. Name at least two concepts or commands that we have gone over in the course so far, but which you feel you do not (fully) understand. It helps to be specific about what you struggle with.

 - I struggled the most with wildcard expansion. I am particularly confused in regards to using it in the middle of a file to match any file in the working dir.  I think it makes the commands feel less readable to me, and in general I could only see myself using this command for very specfic purposes. 

 - I also confused about the commands head and tail.  I understand how they work, but I don't see them as particularly useful. My question around these commands centers more on when they would be used rather than how they would be used. 

 - I am still working on understanding creating count tables and gathering information from sequence files using `grep`, `cut`, `sort`, and `uniq`. I see the ability to use these commands in a pipe as incredibly useful, but it took me a while to figure out how to get the commands to display how I wanted. This assignment helped me understand how to use them in succession much better, but I would appreaciate going through more example of using these function in a pipe.


 - Git repo was created on 9/26, updated 9/29
