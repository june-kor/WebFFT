# WebFFT

The Fastest Fourier Transform on the Web!

## Existing web FFT libs

### Javascript-Based

- fft.js aka indutny
  - https://github.com/indutny/fft.js/ (last changed 2021)
  - What IQEngine used before WebFFT
- fft-js aka vail
  - https://www.npmjs.com/package/fft-js
  - https://github.com/vail-systems/node-fft (last changed 2019)
- jsfft aka dntj
  - https://github.com/dntj/jsfft (last changed 2019)
- fourier-transform
  - https://github.com/scijs/fourier-transform (last changed 2018)
  - author compared it to several others https://github.com/scijs/fourier-transform/blob/master/benchmark.md
- ndarray-fft
  - https://github.com/scijs/ndarray-fft (last changed 2016)
- DSP.js
  - https://github.com/corbanbrook/dsp.js (no longer maintained but last changed 2022)
- digitalsignals (fork of DSP.js)
  - https://github.com/zewemli/dsp.js (last changed 2014)
- fourier
  - https://github.com/drom/fourier (last changed 2021)
- ml-fft
  - https://github.com/mljs/fft (last changed 2020)

### WebAssembly-based

- PulseFFT
  - https://github.com/AWSM-WASM/PulseFFT (last change in 2018)
  - KissFFT based
- Mozilla's implementation used in webkit audio
  - appears to be a copy of kissFFT
  - https://github.com/mozilla/gecko-dev/tree/6dd16cb77552c7cec8ab7e4e3b74ca7d5e320339/media/kiss_fft
- fftw-js
  - FFTW (extremely popular for desktop) ported with webasm
  - https://github.com/j-funk/fftw-js
  - GPL licensed!!!
- pffft.wasm
  - https://github.com/JorenSix/pffft.wasm (last change June 2022)
  - SIMD support

### Other people's benchmarks and comparisons

- https://github.com/j-funk/js-dsp-test
- https://github.com/scijs/fourier-transform/blob/HEAD/benchmark.md
- https://thebreakfastpost.com/2015/10/18/ffts-in-javascript/
- https://toughengineer.github.io/demo/dsp/fft-perf/
