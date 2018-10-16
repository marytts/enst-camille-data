# ENST Camille Voice Data

A French speech corpus designed for synthesis, recorded in 2013 at Télécom ParisTech (ENST) by Camille Dianoux, a female native speaker of French.

## Data format

### Audio

The audio data is provided in the losslessly compressed [FLAC] format, which can be played by a [myriad of software](https://xiph.org/flac/links.html#software), including [Praat].
The speaker was recorded at a 44.1 kHz sampling rate, 16 bits per sample, in mono.
No filters of any sort have been applied to this raw data.

### Phonetic segmentation

Annotations are provided as a single [YAML] file. It contains a list of utterances, each of which consists of
- a prompt code (file basename),
- the utterance text,
- the recording date,
- utterance start and end times (in seconds) in the FLAC file,
- the phonetic segments (obtained using the eHMM tool from [FestVox] 2.1), each of which has
  - a label (based on [SAMPA], `_` denotes silence), and
  - its end time (in seconds), relative to that utterance's start time

For example,
```yaml
- prompt: text_0366
  text: les alpinistes installent un bivouac au pied de la montagne .
  date: 2013-06-17T15:34:58Z
  start: 3185.5455782309
  end: 3191.814965986
  segments:
  - { lab: _, dur: 0.614969 }
  - { lab: l, dur: 0.08 }
  - { lab: e, dur: 0.135 }
  - { lab: a, dur: 0.09 }
  - { lab: l, dur: 0.045 }
  - { lab: p, dur: 0.085 }
  - { lab: i, dur: 0.075 }
  - { lab: n, dur: 0.06 }
  - { lab: i, dur: 0.105 }
  - { lab: s, dur: 0.095 }
  - { lab: t, dur: 0.065 }
  - { lab: '@', dur: 0.115 }
```

## Downloading the corpus

### Git and git-annex

The best way of downloading the data is to use [**Git**](http://git-scm.com/).
To make the most of the features offered by GitHub, you should [**fork**](https://github.com/marytts/enst-camille-data/fork) this repository to your own GitHub account, then use your favorite Git client to **clone** that repo to your local machine.
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

    <https://github.com/marytts/enst-camille-data/archive/master.zip>

2. Download the audio data directly from one of the web remotes, such as

    <http://mary.dfki.de/download/enst-camille-data/audio.tar>

## License

[![Creative Commons License](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/by-sa.svg)](http://creativecommons.org/licenses/by-sa/4.0/)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License].
See the `LICENSE.md` file for details.

[Creative Commons Attribution-ShareAlike 4.0 International License]: http://creativecommons.org/licenses/by-sa/4.0/
[FestVox]: http://festvox.org/
[FLAC]: https://xiph.org/flac/
[Praat]: http://praat.org/
[SAMPA]: http://www.phon.ucl.ac.uk/home/sampa/
[YAML]: http://yaml.org/
