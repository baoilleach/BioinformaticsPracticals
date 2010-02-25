Practical 6 for 2009/2010 - Phylogenetic trees (2)
==================================================



Installing Clustal
------------------

In the previous practical (see Practical 5,
`http://www.ucc.ie/microbio/MB6301/practical5\_trees.html <http://www.ucc.ie/microbio/MB6301/practical5_trees.html>`_),
you learnt how to run Clustal to make multiple alignments at the
EBI website. However, if you are building an alignment of several
sequences, it is often faster to run Clustal on your own computer.
To do that, you first need to install the Clustal program on your
computer.

To install Clustal on your computer, you need to follow these
steps:


#. Go to the website
   `ftp://ftp.ebi.ac.uk/pub/software/clustalw2/2.0.12/ <ftp://ftp.ebi.ac.uk/pub/software/clustalw2/2.0.12/>`_.
#. Right-click on the link to file clustalx-2.0.12-win.msi and
   choose "Save link as..." and then save the file in your "My
   Documents" folder.
#. Once the file has downloaded, double-click on the icon for file
   clustalx-2.0.12-win.msi . You will be asked "Are you sure you want
   to run this software?" Press "Run".
#. You will then see "Welcome to the ClustalX2 setup wizard". Press
   "Next".
#. You will be asked where to install ClustalX2. Select your "My
   Documents" folder.
#. Keep pressing 'yes' or 'Next' until the screen says "Completing
   the ClustalX2 setup wizard". Then press "Finish".

Clustal should now be installed on your computer.

Using Clustal to make a multiple alignment
------------------------------------------

Once you have installed Clustal, you can now align your sequences
using Clustal by following these steps:


#. Go to the "Start" menu on the bottom left of your Windows
   screen. Select "All Programs" from the menu, then select
   "ClustalX2" from the menu that appears. This will start up Clustal.
#. The Clustal window should appear. To load the DNA sequences that
   you want to align into Clustal, go to the Clustal "File" menu, and
   choose "Load sequences". Select the FASTA-format file containing
   your sequences to load it into Clustal.
#. This should read the sequences into Clustal. They have not been
   aligned yet, but will be displayed in the Clustal window. You can
   use the scrollbar on the right to scroll down and look at all the
   sequences. You can use the scrollbar on the bottom to scroll from
   left to right, and look along the length of the sequences.
#. Before you align the sequences using Clustal, you need to tell
   Clustal to make the output alignment file in PHYLIP alignment
   format, so that you can read it into R. To do this, go to the
   "Alignment" menu in Clustal, choose "Output Format Options". A form
   will appear, and in this form you should select "PHYLIP format" and
   deselect "CLUSTAL format", and then press "OK".
#. To now align the sequences using Clustal, go to the Clustal
   "Alignment" menu, and choose "Do Complete Alignment". A menu box
   will pop up, asking you where to save the output guide-tree file
   (called "something.dnd") and the output alignment file (called
   "something.aln"). You should choose to save them in your "My
   Documents" folder (so that you can easily read them into R from "My
   Documents" at a later stage).
#. Clustal will now align the sequences. This will take a couple of
   minutes (eg. 2-5 minutes). You will see that at the bottom of the
   Clustal window, it tells you which pair of sequences it is aligning
   at a particular point in time. If the numbers keep changing, it
   means that Clustal is still working away, and the alignment is not
   finished yet. Be patient!

Displaying phylogenetic trees in R
----------------------------------

In the previous practical (Practical 5,
`http://www.ucc.ie/microbio/MB6301/practical5\_trees.html <http://www.ucc.ie/microbio/MB6301/practical5_trees.html>`_),
you learnt how to build phylogenetic trees in R.

As you learnt in the previous practical, once you have built a
phylogenetic tree in R, you can display it using the plot.phylo()
function. If you are plotting a rooted tree (a tree with an
outgrup), there are three different ways of plotting the tree using
plot.phylo(): the default option is to display the tree as a
*rectangular cladogram*, but you can also plot the tree as a
*triangular cladogram* or *radial tree*. You can specify these four
options by using the "type=" option for the plot.phylo() function:
"plot.phylo(type="c")" specifies a triangular cladogram, while
"plot.phylo(type="r")" specifies a radial tree.

As well as plotting a tree using different formats (eg. rectangular
cladogram or radial tree), it is also possible to rotate the
branches in a tree around the internal nodes of the tree. When a
tree that contains *n* sequences is stored in R, the external nodes
correspond to the sequences of the tree, and are numbered 1, 2, 3,
... *n*. The internal ndoes of the tree are numbered *n* + 1,
*n + 2*, *n + 3* and so on... If you want to rotate the clade under
node 15 (an internal node) node around, you can use the rotate()
function. For example, if your original tree is stored in variable
*mytree*, you can type:

::

    > mytree2 <- rotate(mytree, 15)

You can then use plot.phylo() to plot *mytree2* to see the result
of rotating around that node.

Summary
-------

In this practical, you have learnt how to install and run the
Clustal multiple alignment program.

Exercises
---------

Answer the following questions, using the R package. For each
question, please record your answer, and what you typed into R to
get this answer.

Q1. The file `www.ucc.ie/microbio/MB6301/primates.fasta <http://www.ucc.ie/microbio/MB6301/primates.fasta>`_ contains a FASTA-format file of homologous COX1 protein sequences from primates, including human, Neanderthal, chimpanzee, bonobo, macaque, gorilla, orangutan, gibbon, velvet monkey, and black lemur. Make a multiple alignment of these sequences using Clustal. 
    Scroll along the alignment from left to right. Which sequences look
    most similar to the human sequence?
Q2. Read the multiple alignment file (which you should have saved as "primates.phy") into R, and make a rooted phylogenetic tree with bootstrap values, using the black lemur sequence as the outgroup. 
    Which of the other sequences is the Neandertal sequence most
    closely related to? Based on the bootstrap values, how confident
    are you of this?
    What other living species is the most closely related to human?
    Based on the bootstrap values, how confident are you of this?
    Note: the black lemur sequence is an appropriate outgroup to use,
    as black lemur belongs to a different group of primates (the
    Strepsirrhini) than all the other primates in the tree (which
    belong to the Haplorrhini).
    Hint: you may like to look at Practical 5
    (`http://www.ucc.ie/microbio/MB6301/practical5\_trees.html <http://www.ucc.ie/microbio/MB6301/practical5_trees.html>`_)
    to help you remember how to build rooted trees of protein
    sequences, with bootstrap values.
Q3. Use the "type" option in the plot.phylo() function to display your tree from Q2 as a triangular cladogram, and then as a radial tree. 
    Can you see that these pictures all are showing the same tree?
    Is the amount of information the same in the default (rectangular
    cladogram) tree displayed by plot.phylo(), in the triangular
    cladogram, and in the radial tree?
Q4. In a rooted phylogenetic tree with *n* sequences, it can be shown that there are *n - 1* internal nodes. R numbers the external nodes (sequences) from 1 to *n*, and the internal nodes from (*n* + 1) to (2 \* *n*). Rotate your phylogenetic tree from Q2 around each of the internal nodes in turn, and plot the tree each time. 
    Are you convinced that all of the trees are equivalent?




