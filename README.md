# UPMC Pierre Voice Data

A French speech corpus designed for synthesis, recorded in 2013 at the Institut des Systèmes Intelligents et de Robotique (ISIR), Université Pierre et Marie Curie (UPMC) by Pierre Chauvin, a male native speaker of French.

## Data format

### Audio

The audio data is provided in the losslessly compressed [FLAC](https://xiph.org/flac/) format, which can be played by a [myriad of software](https://xiph.org/flac/links.html#software), including [Praat](http://praat.org/).
The speaker was recorded at a 48 kHz sampling rate (prompts 1 through 100 at 44.1 kHz), 16 bits per sample, in mono.
No filters of any sort have been applied to this raw data.

### Phonetic segmentation

Phonetic labels, automatically obtained using forced alignment using the eHMM tool from [Festvox](http://festvox.org/) 2.1, are provided as Xwaves `.lab` files;
each line (after the header) has the fields

    [ENDTIME] [NUMBER] [LABEL]

where `ENDTIME` is in seconds, `NUMBER` has no significance, and `LABEL` uses a variant of the [SAMPA](http://www.phon.ucl.ac.uk/home/sampa/) phonetic alphabet.
(These files can also be opened in Praat using the command `Read IntervalTier from Xwaves...`.)

## Downloading the corpus

### Git and git-annex

The best way of downloading the data is to use [**Git**](http://git-scm.com/).
To make the most of the features offered by GitHub, you should [**fork**](https://github.com/marytts/upmc-pierre-data/fork) this repository to your own GitHub account, then use your favorite Git client to **clone** that repo to your local machine.
Please refer to [GitHub Help](https://help.github.com/) and [the Web](http://google.com/) as required.

Because Git is not designed to efficiently handle large amounts of binary data, specifically the audio files in the corpus, we *manage* those files using [**git-annex**](http://git-annex.branchable.com/).
This means that the actual audio files are not stored in this repo, but we nevertheless leverage the benefits of distributed revision control by tracking which **Git remotes** *do* have copies of the audio files.
However, git-annex also performs poorly with large *numbers* of files, so the `.flac` files have been packaged into [tarballs](http://en.wikipedia.org/wiki/Tar_%28computing%29), one per speaking style.
(Use `tar` or your favorite file archive utility to unpack.)

**You will need git-annex** to handle this elegantly.

Once you've cloned the repository, you can use the command `git annex get audio.tar` to get `audio.tar`, i.e. the `tar` file containing the audio recordings.

### Alternative: Git-less download

If all of that stuff about Git and version control is just too technical, you can still download the corpus in a few simple steps.

1. Download the most recent version (the *master branch*) of this repository as a `.zip` file by clicking on the "Download ZIP" button, or the following URL:

    <https://github.com/marytts/upmc-pierre-data/archive/master.zip>

2. Download the audio data directly from one of the web remotes, such as

    <http://mary.dfki.de/download/upmc-pierre-data/audio.tar>

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/">
  <img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/3.0/88x31.png" />
</a>
<br />
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/">Creative Commons Attribution-ShareAlike 3.0 Unported License</a>.
See the `LICENSE` file for details.
