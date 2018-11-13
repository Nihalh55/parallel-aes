# Parallel AES Cryptography
![Github Issues](https://img.shields.io/github/issues/gurupunskill/parallel-aes.svg) 
![GitHub pull requests](https://img.shields.io/github/issues-pr/gurupunskill/parallel-aes.svg)
![GitHub](https://img.shields.io/github/license/gurupunskill/parallel-aes.svg)

A CUDA and OpenMP implementation of _`Fei.et.al Practical parallel AES algorithms on cloud for massive users andtheir performance evaluation`_.

## Introduction

Advanced Encryption Standard (AES) is a symmetric-key algorithm and is one of the strongest standards for electronic encryption in the world. It is widely used in software, hardware as well as in cloud applications. However, AES takes quite some time to encrypt messages especially when the number of users as well as the length of the text is quite large, which is the case in cloud enviroments.  
This is primarily because AES is implemented in a serial fashion. In the paper titled _`Fei.et.al Practical parallel AES algorithms on cloud for massive users andtheir performance evaluation`_ , the authors have brought out a parallel implementation for AES on the GPU as well as the CPU, which can be easily virtualised on cloud enviroments.  
AES is parallelisable as it is a symmetric block ciper and the encryption of each block is independent of the other blocks and as a result this can be done in a parallel fashion. The paper uses the concepts of _coalescing_ and _slicing_.
1. Coalescing: Putting together all the users' data together from the buffer to a contingous memory location.
2. Slicing: Dividing the coalesced data into equal parts so workload amongst threads is distributed evenly.  
  
The paper talks about 6 algorithms, namely:  

 * GCS  : GPU Coalescing and Slicing
 * GCNS : GPU Coalescing and no Slicing
 * GNC  : GPU no Coalescing and no Slicing
 * CCS  : CPU Coalescing and Slicing
 * CCNS : CPU Coalescing and no Slicing
 * CNC  : CPU no Coalescing and no Slicing  
  
All these algorithms have been implemented in this project and the results have been recorded, visualised and verified.  

## Software Tools, Languages and Frameworks Used

1. `C++` : C++ was the primary programming language used for coding out the algorithms.
2. `python` : The Python programming language was used to visulaise the results by plotting graphs.
3. `CUDA` : CUDA platform was used to implement the three GPU algorithms as it provides architecture for parallel computing on the GPU.
4. `OpenMP` : OpenMP platform was used to implement the three CPU algorithms as it provides architecture for parallel computing on the CPU.
5. `VSCode` : VSCode was the primary text editor used.
6. `github` : Github was used for collaboration and as a version control system.

## Instructions for Use

1. Open terminal and exceute `git clone https://github.com/gurupunskill/parallel-aes.git` to clone the repository.
2. Change directory to `parallel-aes/` using `cd`.
3. Change directory to `src` to execute the algorithms so as to view and compare the speeds.
    1. Once in `parallel-aes/src/` change directory to `generator`.
    2. Run `g++ generate.cpp` and `./a.out`. This creates the normalised dataset which will be used by the algorithms.
    3. Run `cd ..` to go back to parent directory.
    4. Change directory to any one of the 7 folders having an AES implementation algorithm.
    5. Run `g++ <algo-name>.cpp` and `./a.out`. You will view the required speeds on the terminal.
    6. Change directory to `norm_dataset` to view the ciper texts in your text editor.
4. Change directory to `docs` to view documentation.

## File Structure

* `docs` : All the documentation for the project is present in this folder.
    * `img` : Images of graphs showing results of each algorithm are present here.
    * `AES-explanatory-paper.pdf` : The paper that was used to learn AES from.
    * `Fei_et_al-2016-Concurrency_and_Computation%3A_Practice_and_Experience.pdf` : The research paper being implemented.
    * `NIST FIPS AES.pdf` : The paper that was used to learn AES from.
* `src` : Source code for the project is present in this folder
    * `ccns` : Source code for the implementation of CCNS algorithm.
    * `ccs` : Source code for the implementation of CCS algorithm.
    * `cnc` : Source code for the implementation of CNC algorithm.
    * `gcns` : Source code for the implementation of GCNS algorithm.
    * `gcs` : Source code for the implementation of GCS algorithm.
    * `generator` : Source code for producing a normalised random dataset which is used for encryption tests and analysis.
    * `gnc` : Source code for the implementation of GNC algorithm.
    * `include` : Contains the source code for the header files defined by us.
        * `aeslib.hpp` : Source code for the header file containing AES code.
        * `genlib.hpp` : Source code for the header file containing general common functions.
        * `paralellcore.cuh` : Source code for the header file containing functions for CUDA implementation of AES.
        * `parallelcpu.hpp` : Source code for the header file containing unctions for OpenMP implementation of AES.
    * `norm_dataset` : The normalised dataset along with cipher texts (this file will be present once code is run on local repository)
    * `sequential` : Source code for the implementation of serial AES algorithm.
    * `tdata.csv` : CSV file where results are dumped into. Used for plotting graphs.
* `.gitignore` : Files to be ignored during commits by git.
* `License` : MIT license
* `README.md` : Document giving a brief overview of the project. 


## Results