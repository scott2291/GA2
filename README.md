

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
        git init
        ```

        The output was:
    
         ```
        Initialized empty Git repository in /fs/ess/PAS2880/users/scott2291/GA2/.git/
        ```

1. Copy the genome annotation GTF file GCF_016801865.2.gtf.gz that is in your copy of the Garrigós et al. (2025) data to a file data/annot.gtf.gz (i.e., into the data dir you just created).

1. Check the file size of annot.gtf.gz. Then, decompress the GTF file with the gunzip command below. Finally, check the size of the resulting annot.gtf file. How large is the size difference between the compressed and uncompressed files?

1. The total number of “genomic features” (genes, exons, etc.) listed in a GTF file is simply the number of lines in its main/table section.

   - Count the total number of lines in annot.gtf.
   - Take a look at the contents of the file and count the number of header lines by eye.
   - Based on your knowledge of what the GTF header lines look like, combine grep -v and wc -l to count the number of genomic features in the file.

1. Does the difference between the two line counts you just performed correspond to the number of header lines you counted visually? If not, can you figure out which other line(s) than the header lines contain the pattern you used with grep above?

1. How many distinct “sequences” (chromosome/scaffolds/contigs) are represented in the annotation file? Store a list of these distinct sequences in a file results/scaffolds.txt.

1. Print a “count table” (like we did towards the end of this section) of feature types in the annotation: this should have a count of the number of times each feature type occurs. (Such a table will for example show how many genes have been annotated in this genome – quite useful!)

1. Check the status of your Git repository. You should see that your README has changed but also that Git has detected the files in the data and results dirs. You don’t want to commit any files in the data and results dirs, so create a .gitignore file that makes Git ignore them. Check the status of your repository again – is your .gitignore file working as intended?

1. Stage and commit the .gitignore file.

1. Stage and commit the README.md file again.

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

