# pyproclus

A Python implementation of the **PROCLUS** algorithm: **PRO**jected **CLUS**tering for high-dimensional data.

## Overview

PROCLUS is a subspace clustering algorithm that finds clusters in different subspaces of high-dimensional data. It automatically identifies relevant dimensions for each cluster, making it particularly effective for datasets where different clusters exist in different feature subspaces.

## Requirements

- [NumPy](http://www.numpy.org/)
- [SciPy](http://www.scipy.org/)
- [Matplotlib](http://matplotlib.org/) (for running the examples)
- [Cython](http://cython.org/) (optional, for building the Adjusted Rand Index evaluator)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Alessi0X/pyproclus-fork.git
   cd pyproclus-fork
   ```

2. (Optional) Build the Cython extension for faster evaluation of the Adjusted Rand Index:
   ```bash
   python setup.py build_ext --inplace
   ```
   or 
    ```bash
    make
    ```

## Usage

Check the example files (`example01.py`, `example02.py`, `example03.py`) for usage demonstrations.

Basic usage:
```python
import proclus as prc
import arffreader as ar

# Load data
X, supervision = ar.readarff("data/simple.arff")

# Run PROCLUS
medoids, dimensions, assignments = prc.proclus(X, k=3, l=2, seed=902884)

# Evaluate clustering
accuracy = prc.computeBasicAccuracy(assignments, supervision)
```

## Examples

- `example01.py` - Simple 2D clustering demonstration
- `example02.py` - High-dimensional data clustering
- `example03.py` - Subspace stream clustering with custom parameters
- `correlation.py` - Analysis of correlation between objective function and Adjusted Rand Index

## Implementation Notes

The [Adjusted Rand Index](http://en.wikipedia.org/wiki/Rand_index#Adjusted_Rand_index) evaluation measure is implemented in Cython for efficiency. Pre-generated C code is included in the distribution. This component is optional and only required for computing clustering quality metrics.

## Reference

Charu C. Aggarwal, Joel L. Wolf, Philip S. Yu, Cecilia Procopiuc, and Jong Soo Park. 1999. **Fast algorithms for projected clustering.** In Proceedings of the 1999 ACM SIGMOD international conference on Management of data (SIGMOD '99). ACM, New York, NY, USA, 61-72. DOI=[10.1145/304182.304188](http://dl.acm.org/citation.cfm?id=304188)

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

This is a fork with Python 3 compatibility updates. Original implementation by [Cassio M. M. Pereira](https://github.com/cmmp). 

Original repository: [https://github.com/cmmp/pyproclus](https://github.com/cmmp/pyproclus)
