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

## Extracting the corpus

### Prerequisites

Java 8 (or later) and [SoX] must be installed.

### Assembling the data

The data processing is delegated to [Gradle] and the [FLAML plugin].

Run `./gradlew unpackData extractTextFiles extractLabFiles extractWavFiles` to download and extract all data. See the [FLAML plugin] documentation for details.

Run `./gradlew assemble` to prepare the data for distribution.

## License

[![Creative Commons License](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/by-sa.svg)](http://creativecommons.org/licenses/by-sa/4.0/)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License].
See the `LICENSE.md` file for details.

[Creative Commons Attribution-ShareAlike 4.0 International License]: http://creativecommons.org/licenses/by-sa/4.0/
[FestVox]: http://festvox.org/
[FLAC]: https://xiph.org/flac/
[FLAML plugin]: https://github.com/m2ci-msp/gradle-flaml-plugin
[Gradle]: https://gradle.org/
[Praat]: http://praat.org/
[SAMPA]: http://www.phon.ucl.ac.uk/home/sampa/
[SoX]: http://sox.sourceforge.net/
[YAML]: http://yaml.org/
