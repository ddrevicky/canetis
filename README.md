# Canetis

Canetis is a recursive forced aligner built on Gentle. It gives, for each word in the
transcript of an audio file, the timestamp at which it was said in the audio.

There are many other excellent forced aligners out there, including Gentle, which Canetis is built on. However, on particularly long and/or noisy audio files, 
small errors can accumulate within standard forced aligners, leading to lower alignment rates. In order to
resolve this issue, our aligner implements the recursive algorithm described by Moreno et al. in the paper [“A Recursive Algorithm for the Forced Alignment of Very Long Audio Segments”](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.649.6346&rep=rep1&type=pdf).
We have found Canetis's performance to be noticeably improved compared to standard aligners such as Gentle,
and we hope you find it useful!

## Installation Process

**Dependencies**

1. Python 2.7 (Canetis will not work with Python 3)
2. Pip (which is linked to the Python 2.7 installation)
3. Git

**Install**

Clone the source onto your machine. `cd` into the `canetis` directory and run the following:
```bash
./install.sh
source ~/.bashrc
```

This will require sudo access. This will install all required dependencies, install Canetis, and perform required configuration.

**Verify Your Installation**

Run the following command: 

```bash
python2 test/test.py
```

Shortly, it should output test alignment results for both Gentle and Canetis.

## Usage

```bash
python2 align.py audio.wav transcript.txt output.txt
```

Puts a JSONified dictionary into the output.txt file, containing the following keys:
1. "start" - the start audio time
2. "end" - the end audio time
3. "word" - the word
4. "success" - whether the word was successfully aligned or not

## Results

We tested Canetis on a set of forensic interview audio/transcripts collected by the USC
Gould School of Law. On average, Canetis aligned 11.7% more words than Gentle, which we
would consider to be a significant improvement.

## Questions?
If you have questions or something doesn't work the way you expect, please let us know!
We are always looking to make this better. The best way to reach out is by creating a GitHub issue --
we'll be able to see it and respond promptly.

## Contributors

This project was created by [Nihar Sheth](http://github.com/nsheth12) and [Kian Ghodoussi](http://github.com/ghodouss).
