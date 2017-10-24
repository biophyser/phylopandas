# PhyloPandas

Bringing [Pandas](https://github.com/pandas-dev/pandas)'s `DataFrame`s to phylogenetics. 

Read many formats directly to a Pandas `DataFrame` for easy manipulation of phylogenetic data.

Finally, phylogenetics for humans!

# How does it work?

Don't worry, we didn't reinvent the wheel here. PhyloPandas simply bridges [BioPython](https://github.com/biopython/biopython) (great for parsing/writing sequence data) and [Pandas](https://github.com/pandas-dev/pandas) 
(great for human-accessible data storage).   

# things you can do

Read any format:

```python
import phylopandas as phypd

df1 = phypd.read_fasta('sequences.fasta')
df2 = phypd.read_phylip('sequences.phy')
```

Convert formats:

```python
df = phypd.read_fasta('sequences.fasta')
df.to_phylip('sequences.phy')
```

Merge two *ordered* sequence files (such as a normal sequence file and its alignment).

```python
# Read sequence file into dataframe
df = phypd.read_fasta('sequences.fasta')

# Read alignment into dataframe
align = phypd.read_fasta('alignment.fasta')

# Add alignment using standard pandas functions
# NOTE: this assumes the alignment and sequence
#       file are ordered.
df = df.assign(alignment=align['sequence'])
```

# Install

Install from PyPi:

```
pip install phylopandas
```

Install from source:

```
git clone https://github.com/Zsailer/phylopandas
cd phylopandas
pip install -e .
```

# Dependencies

* BioPython
* Pandas
