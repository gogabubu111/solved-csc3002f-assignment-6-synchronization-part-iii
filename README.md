Download Link: https://assignmentchef.com/product/solved-csc3002f-assignment-6-synchronization-part-iii
<br>
This assignment aims to give you experience in thread (and, by extension, process) synchronization using <strong>semaphores</strong>. In this project, you will write multithreaded programs in Java to solve <strong>three classic synchronization problems</strong>, using only semaphores.  A secondary aim is to give you experience in reading, understanding and correcting existing code.  The assignment is in three parts, increasing in difficulty.  The third part is described below.

<h1>Part III: Making methane with semaphores</h1>

Methane is a molecule with four hydrogens attached to a single carbon (CH<sub>4</sub>). For this project, you will run a simulation of the combination of carbon and hydrogen atoms into methane molecules.

There are two kinds of atoms (threads), <em>carbon</em> and <em>hydrogen</em>, in your simulations. In order to assemble these atoms into methane molecules, each atom must wait until the right number (and type) of atoms are available to bond (by calling the bond() method) into a complete methane molecule.

There are a number of synchronization constraints on this simulation, as follows.

Ø <strong>Only one methane molecule forms at a time.  </strong>You must guarantee that all the atoms from one molecule invoke bond() before any of the atoms from the next molecule.<strong>  </strong>In other words:

<ul>

 <li>If a carbon thread arrives at the barrier when no <em>hydrogen</em> threads are present, it has to wait for four <em>hydrogen</em></li>

 <li>If a <em>hydrogen</em> thread arrives at the barrier when no other threads are present, it has to wait for a <em>carbon</em> thread and a further three hydrogen threads.</li>

</ul>

You do not have to matching the atoms (threads) up explicitly; that is, the atoms (threads) do not necessarily know which other atoms (threads) they are paired up with. The key is just that atoms pass the barrier in complete sets; thus, if we examine the sequence of atoms that invoke bond()and divide them into groups of five, each group should contain one <em>carbon</em> and four <em>hydrogen</em> threads.

Assignment: Write synchronization code in Java for <em>carbon</em> and <em>hydrogen</em> molecules that enforces these constraints, using <strong>only </strong>the <strong>semaphore construct</strong>. We will  provide a reusable barrier class (an extension of Part I) for the barrier you will need.

1.1 Code skeleton: molecule

You <strong>must use</strong> and extend the molecule <strong>package provided</strong>, correctly

implementing the classes Hydrogen and Oxygen (and all the methods), so that the        RunSimulation class will execute correctly, <strong>always</strong>.   You may <strong>not add any methods to these classes</strong>. The semaphores you will need are defined already in the Methane class.  <strong>However, do not alter</strong> this class or <strong>any anther class at all </strong>(although you must submit them).  You will need to inspect the various classes to see how they work – this is part of the assignment and <strong>no explanation other than the code will be given</strong>.

An <strong>example</strong> of a correct execution of            molecule     is:

Ø java       molecule.RunSimulation       12        3

Starting simulation with 12 H and 3 C

—Group ready for bonding—

…Bonding….H4

…Bonding….H3

…Bonding….H1

…Bonding….H2

…Bonding….C2

—Group ready for bonding—

…Bonding….H7

…Bonding….H6

…Bonding….H5

…Bonding….H10

…Bonding….C1

—Group ready for bonding—

…Bonding….H12

…Bonding….H11

…Bonding….C3

…Bonding….H9

…Bonding….H8




<h1>1         Code requirements</h1>

You will code your solutions in Java, adding to the skeleton code provided.

You may only use the <strong>Semaphore</strong> class in the java.util.concurrent library: <strong>no other Java synchronization constructs at all</strong>.

All code must be <strong>deadlock free. </strong>

The output must comply with the stated synchronization constraints and with the examples shown.