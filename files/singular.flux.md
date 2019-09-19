# singular.flux - knowledge-based podcast generation

We are seeing the rise in both art production and accessibility. This translates into massive amounts of readily available data to create generative approaches to art that actually create representative art examples. While these methods are increasingly becoming better with image, audio has not seen huge rises in the development and applicability of actually interesting models for art generation (SampleRNN and the potential use of WaveNet are the two most obvious examples to come to mind). 

Here, an approach with a similar rationale to SampleRNN is used - taking a large enough database of short audio samples and segments, derived from several podcasts of broadcasters in Rádio Universidade de Coimbra, short podcasts are generated. These are not, in any way, meant to sound as actual radio programs. Instead, they are what could be considered an experimental radio show. 

While SampleRNN uses deep neural networks to achieve its objective of generating new audio, several methods are applied here, including completely stochastic approaches, hidden Markov models (HMMs) and deep learning (DL) methodologies, all of which are based on a multi-dimensional embedding of each sample based on audio descriptors.

Below I try to go into as much detail as possible to describe the different podcasts I have produced so far with these techniques and their respective embedded audio. It airs live every two weeks on [the music makers](https://www.facebook.com/themusicmakersruc/?ref=br_rs) at [Rádio Universidade de Coimbra](https://www.ruc.pt).

I
---

<iframe width="100%" height="60" src="https://www.mixcloud.com/widget/iframe/?hide_cover=1&mini=1&feed=%2Fviraodiscoetocaomesmo%2Fsingularflux-i%2F" frameborder="0" ></iframe>

The first edition of **singular.flux** features only three [the music makers](https://www.facebook.com/themusicmakersruc/?ref=br_rs), the radio program hosting this podcast. The first attempt at making something is fairly simple and not complex at all - all files where cut down into 1 second pieces (44,100 samples *per* piece) and a few were randomly assembled and concatenated with varying lengths.

II
---

<iframe width="100%" height="60" src="https://www.mixcloud.com/widget/iframe/?hide_cover=1&mini=1&feed=%2Fviraodiscoetocaomesmo%2Fsingularflux-ii%2F" frameborder="0" ></iframe>

The second edition features some improvement in the "concatenating" process (a crossfade was used to make the transitions sound smoother), a larger database (this time featuring much more programs than before) and the averaging of two randomly generated programs to create a kind of more "chaotic" atmosphere. 

III
---

<iframe width="100%" height="60" src="https://www.mixcloud.com/widget/iframe/?hide_cover=1&mini=1&feed=%2Fviraodiscoetocaomesmo%2Fsingularflux-iii%2F" frameborder="0" ></iframe>

The third edition features a new way of assembling the sounds - instead of using a random selection of programs, we started of with fewer samples and extracted Mel-frequency cepstral coefficients (MFCCs) for each 1 second piece. From this, I used something akin to affinity propagation (i.e. the next piece would be the nearest piece (determined through euclidean distance - the shortest "straight line" distance between two points) with no repitition). 

### Mel-frequency cepstrum

The Mel-frequency cepstrum (MFC) is a fairly standard technique of feature extraction for sound. An audio spectrum is usually obtained after performing a Fourier Transform (FT) to an audio sample (which converts amplitude as a function of time to frequency as a function of time) and audio models (i.e. for speech recognition) can be derived from this using HMMs. Now, the best way to characterize spectra is to look at its peaks (formants) which carry the identity of the sound. After identifying formants, we can fit a curve to this and extract the spectral envelope (the fitted curve) and the spectral details (spectrum values deviating from the fitted curve). If we then perform an inverse FT (IFT) on the spectral envelope (low frequency) and on the spectral details (high frequency), we get a cepstrum by combining both. 

This is pretty simple and straight forward as far as computation goes. 

To get an MFC, however, we have to go through a few additional steps, inspired in the human hearing - humans tend to identify sounds by focusing a great deal more on lower frequencies than on higher frequencies and, as such, we are more interested in extracting more information from lower frequencies than from higher frequencies. To do this, Mel-frequency filters are used, into which I will not be going into detail ([these slides](http://www.speech.cs.cmu.edu/15-492/slides/03_mfcc.pdf) from a CMU lecture are pretty easy to follow if you are interested in understanding this better).

The most amazing part about this is that using something as simple as euclidean distance you can start to actually hear how similar consecutive pieces sound.