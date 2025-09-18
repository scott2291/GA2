

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

        I used the following command:

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

    I used the following command:

    ```
    cp ../garrigos-data/ref/GCF_016801865.2.gtf.gz data/annot.gtf.gz
    ls data/
    ```

    The output was:
    
    ```
    annot.gtf.gz
    ```


1. Check the file size of annot.gtf.gz. Then, decompress the GTF file with the gunzip command below. Finally, check the size of the resulting annot.gtf file. How large is the size difference between the compressed and uncompressed files?

    I used the following command:

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

    data/
    results/

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

    ```
    git add .gitignore
    git commit -m "Add a gitignore file
    ```

    The output was:
    
    ```
    [main 6c2ad08] Add a gitignore file
    1 file changed, 2 insertions(+)
    create mode 100644 .gitignore
    ```

1. Stage and commit the README.md file again.

    ```
    git add .gitignore
    git commit -m "Add a gitignore file
    ```

    The output was:
    
    ```
    [main 6c2ad08] Add a gitignore file
    1 file changed, 2 insertions(+)
    create mode 100644 .gitignore
    ```

1. Copy the FASTQ file ERR10802863_R1.fastq.gz of the Garrigós et al. (2025) data to a file of the same name inside the same data dir you copied the GTF file into.

1. Check the status of your Git repository. Does the FASTQ file show up? Why/why not?

1. How many reads does the FASTQ file contain?

1. How many reads in the FASTQ file contain the sequence ACGT? (You can assume this string does not occur outside of the lines with sequences.)

1. How many reads contain at least 10 consecutive Ns (uncalled bases)? (You can assume that stretches of N’s do not occur in the sequence quality lines.)

1. Using the read length information in the FASTQ read header lines, print a count table of read lengths.

1. Compare the number you got in the previous question with the number of 35-bp reads from the question before that. What does this seem to tell you? To confirm, can you check what a sample of 35-bp reads look like?

    1. Stage and commit the README.md file again.

Bonus

    1. Name at least two concepts or commands that we have gone over in the course so far, but which you feel you do not (fully) understand. It helps to be specific about what you struggle with.

