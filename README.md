# datarecommend

## Preparation

### Data Download

- CoAuthor Network(.hdt), Scientific Item Title RDF(.hdt), and Abstract RDF(.hdt):[download link](https://surfdrive.surf.nl/files/index.php/s/ibrwDJNem6fLUdk)
- Embedding based on citation network: [download link](https://zenodo.org/record/6324341)
- Benchmark Corpus (Gold Standard for evaluation): [download link](https://zenodo.org/record/6386897)

### Needed Data List
All the following files are from this github or the links above. And make sure uncompress all the download compressed file (.tar or .tar.bz2). Also, make sure put all files together in one folder (--data Path_to_folder, default is the folder of [python file](./Recommendation.py) )
- seeds.txt (List of seeds, one seed per line)
- cands.txt (List of candidates, one candidate per line)
- StandardSchLink.hdt (Standard links for evaluation, stored as RDF/HDT format)
- StandardSchLink.hdt.index.v1-1 (index file for standard links)
- mag_authors_2020_ComplEx_entity.npy (numpy file for pretrained MAKG author entity embeddings)
- authors_entities.dict (index file for pretrained MAKG author engtity embeddings)
- Citation_vectors.txt (pretrained dataset/paper entity embeddings on MAKG citation network)
- Paper.hdt (triples of papers' titles)
- Paper.hdt.index.v1-1
- PaperAbs.hdt (triples of papers' abstracts)
- PaperAbs.hdt.index.v1-1
- PaperAuthorAffiliations.hdt (triples of MAKG paper-author or dataset-author authorships)
- PaperAuthorAffiliations.hdt.index.v1-1

### Python Library

- [pybind11](https://pybind11.readthedocs.io/en/stable/index.html#)
- [pyHDT](https://callidon.github.io/pyHDT/)
- [numpy](https://numpy.org/)
- [gensim](https://radimrehurek.com/gensim/)
- [tqdm](https://tqdm.github.io/)
- [rank_bm25](https://github.com/dorianbrown/rank_bm25)
- [networkx](https://networkx.org/)
- [SentenceTransformers](https://www.sbert.net/)

## Usage

```
usage: Recommendation.py [-h] [-th THRESHOLD] [-bm25t BM25_THRESHOLD] [-hop HOP] -data DATA [-out OUT] [-random RANDOM] [-all ALL] [-top TOP]
optional arguments:
  -h, --help            show this help message and exit
  -th THRESHOLD, --threshold THRESHOLD
                        Threshold for similarity between author embedding
  -bm25t BM25_THRESHOLD, --bm25_threshold BM25_THRESHOLD
                        Threshold for BM25 ranking                    
  -hop HOP, --hop HOP   Hop number for graph walk  
  -data DATA, --data DATA
                        Path to directory contains all needed data                        
  -out OUT, --out OUT   Directory to store all result files. Default is directory of this python file  
  -random RANDOM, --random RANDOM
                        Random select seeds from seed file. Recommended argument for large-scale seed file                        
  -all ALL, --all ALL   Run with all hops and thresholds for author embedding similarity  
  -top TOP, --top TOP   Threshold for Bert and citation embedding similarity approaches
```
