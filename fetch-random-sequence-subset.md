### How to extract a random subset of sequences from a sequence file.

Starting with a sequence file `<seqfile1>`, follow these steps to create a new sequence file `<seqfile2>` that contains a random subset of 100 of the sequences from `<seqfile1>`. 

#### Step 1. Get a list of the sequences

```
> esl-seqstat -a <seqfile1> | grep ^\# | awk '{ print $2 }' > <listfile1>
```

#### Step 2. Select a random subset of the sequence names

```
> esl-sfetch 100 <listfile1> > <listfile2>
```

#### Step 3. Index the original file and fetch the 100 sequences

```
> esl-sfetch --index <seqfile11>
> esl-sfetch -f <seqfile1> <listfile2> > <seqfile2>
```

#### Step 4. Confirm the new sequence file has 100 sequences in it:

```
> esl-seqstat <seqfile2>
```

The output should include:
```
Number of sequences: 100
```



