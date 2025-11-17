

# Faust ideas

This repository hosts the "TODO/ideas list" for the [Faust programming 
language](http://faust.grame.fr).

## Conventions

* Items are placed at the bottom of the file and separated by `---`. 
* Items can have a person associated to them by declaring `* Currently 
addressed by: xxx`. If no-one is currently working on the item, replace 
`xxx` by `nil`. 
* Items are ordered by priority and are also listed in the [List](#list) 
section below. 
* Items can be commented by adding subsections, pictures, etc. 

## List

- [Implement Jonathan Abel's Modal Reverb](#implement*jonathan-abels*modal-reverb)
- [Improved UI Declarations](#improved-ui-declarations)
- [Trigonometric simplifications](#trigonometric-simplifications)
- [WebAssembly specific optimisations](#webassembly-specific-optimisations)
- [Improve faust2audiokit](#improve-faust2audiokit)
- [Improve faust2vcvrack](#improve-faust2vcvrack)
- [Testing tools on the Web](#testing-tools-on-the-web)
- [Progressive Web applications for iOS and Android](#progressive-web-applications-for-ios-and-android)
- [A tool to generate Faust web components as NPM packages](#a-tool-to-generate-faust-web-components-as-npm-packages)
- [PFFT like wrapper for Faust DSP code](#pfft-like-wrapper-for-faust-dsp-code)
- [Hot reloadable soundfiles](#hot-reloadable-soundfiles)
- [WebGPU audio architecture](#webgpu-audio-architecture)
- [Invertible functions](#invertible-functions)
- [faust2nih tool](#faust2nihplug-tool)
- [Faust IDE MCP](#faust-ide-mcp)

## Implement Jonathan Abel's Modal Reverb

* Currently addressed by: Romain and Yann

This should be done as part of the Longyou grottoes project. The "final goal" would be to create an interactive website where users can process the sound of
their microphone to apply the acoustics of this ancient space. Modal reverb would allow to interpolate between IRs and change some of the parameters of
the space in real-time. It'd be nice if this could be reproducible so we need to think about a way to nicely generate these reverbs from an impulse response.
This tool could be similar to `mesh2faust` or could come as part of a toolkit in matlab/octave/pyhton, etc.  


## Improved UI Declarations

* Currently addressed by: Romain and Yann

Essentially allow for specific UI elements to have metadatas associated to them outside of their declaration. As part of that, we want to implement a system to further customize UI elements. 

### Potential Implementation

Several approaches are being considered to further customize UI elements. The first one would consist of being able to declare a "CSS" allowing for the use
of CSS code. Another approach (more generic and not limited to the web) would allow for the declaration of UI-specific metadata inspired by CSS. 

```
declare UI "
  synth{
    background-color: blue;
  }
  synth/freq{
    tooltip: Frequency parameter of the synth;
    width: 70%;
  }
  synth/gain{
    style: knob;
    tooltip: Gain parameter of the synth;
    width: 70%;
  }
";

f = hslider("freq",400,50,1000,0.1);
g = hslider("gain",0.5,0,1,0.01);
process = hgroup("synth",os.sawtooth(f)*g);

```

Of course, it would still be possible to declare metadatas within the UI declaration (this system would be fully backward compatible). Internally, we'd have to parse the metadata and create a corpus of supported CSS metadatas knowing that interfaces would be based on a specific kind of layout (e.g., grid layout). Once again, another option would be to allow to specify "pure CSS" giving access to all the CSS features without having to do some reformatting. 

---

## Trigonometric simplifications

* Currently addressed by: nil (suggested by [Pierre Lecomte](https://github.com/grame-cncm/faust/issues/59))

For some applications, trigonometric functions (spherical harmonics) are used, and depending on the algorithm, the output formula could be very complicated. However, in a lot of cases, trigonometric identities could help to drastically simplify the expressions.

---

## WebAssembly specific optimisations

* Currently addressed by: Stéphane and Yann

To run as fast as possible and approch native code performances as much as possible, WebAssembly code requires some specific optimisations, like: memory access (index precomputation as much as possible...), delay lines handling, struct/stack variables access...etc. We have started an informal collaboration with Mozilla engineers (Benjamin Bouvier) to work on this subject.

---

## Improve faust2audiokit

* Currently addressed by: nil

The [faust2audiokit](https://github.com/grame-cncm/faust/tree/master-dev/architecture/audiokit) tool transforms a Faust DSP program into a fully working AudioKit node. The result can be a monophonic DSP or a MIDI controllable polyphonic one (when the DSP describes an instrument, following the freq, gain, gate parameter naming convention).

The project consists in improving and finishing the tool.

---

## Improve faust2vcvrack

* Currently addressed by: nil

The [faust2vcvrack](https://github.com/grame-cncm/faust/tree/master-dev/architecture/vcvrack) The faust2vcvrack tool compiles a Faust DSP program in a folder containing the VCV Rack plugin C++ source code and a Makefile to compile it. By default the resulting C++ code is compiled and installed in the VCV Rack application:

The project consists in improving the tool, particulary the automatically created graphical user interface which is ugly for now. 

---

## Testing tools on the Web

* Currently addressed by: nil

Faust distribution already contains some testing tools, like `faust2plot` or `faust2octave`.etc. It would be great to have them running in a Web page (or some extension of the same idea). For signal generators/processors, several output formats (oscilloscope, spectrogramme...), and for processors several calibrated input signals (dirac impulse, ramp, sinusoide..) would be available.

---

## Progressive Web applications for iOS and Android [Done, see [faustpwa](https://faustpwa.grame.fr)]

Faust code can easily be distributed as self-contained Web pages containing the Faust DSP code as a statically compiled Web Audio node. The project is to improve the current model to deploy the pages as [Progressive Web applications](https://en.wikipedia.org/wiki/Progressive_web_app). The [faustwasm](https://github.com/grame-cncm/faustwasm) package will be improved to allow this new kind of deployment model. The use of [movement sensors](https://developer.mozilla.org/en-US/docs/Web/API/Sensor_APIs) will be added in the architecture to keep the same capability currently found in the native applications. Deployment on iOS and Android machines will be tested.

---

## A tool to generate Faust web components as NPM packages 

Faust code can easily be distributed as self-contained Web pages containing the Faust DSP code as a statically compiled Web Audio node. The project is to improve the current model to deploy the pages as ready-to-use NPM packages. The [faustwasm](https://github.com/grame-cncm/faustwasm) package will be improved to allow this new kind of deployment model. A `faust2webnpm` tool to compile a Faust DSP program will be developed, with [polyphonic](https://faustdoc.grame.fr/manual/midi/#configuring-and-activating-polyphony) and [polyphonic with global effect](https://faustdoc.grame.fr/manual/midi/#audio-effects-and-polyphonic-synthesizer) support.

---

## PFFT like wrapper for Faust DSP code

The [Max/MSP pfft~](https://docs.cycling74.com/max8/refpages/pfft~) object is designed to simplify spectral audio processing using the Fast Fourier Transform (FFT). In addition to performing the FFT and the Inverse Fast Fourier Transform (IFFT), pfft~ (with the help of its companion fftin~ and fftout~ objects) manages the necessary signal windowing, overlapping and adding needed to create a real-time Short Term Fourier Transform (STFT) analysis/resynthesis system.

This model has been tested and implemented by [Shihong Ren](https://github.com/Fr0stbyteR) for Faust and can be tested on a [customized version of the Faust IDE](https://faustide.shren.site/). The FFT input part process the temporal signal, delivers a tripplet of signals (real, imaginary, and current bin index), uses regular Faust DSP code working on this tripplet of signals, and finally do the iFFT process to produce temporal signals. 

Here is a noise reduction algorithm using this model written by Shihong.

It is actually a simplified version of the commonly used spectral denoise (10.1109/TASSP.1979.1163209). When the user hits the button, the algorithm learns the current spectrum as a reference of the background noise. Then, subtract from every input spectrum, the power of this background noise spectrum (for each FFT bin).

The Faust FFT DSP has 3 inputs: real part/imaginary part/current bin (as in pfft~ in Max). Each input gets sequentially a complex number as information about each FFT bin. The first part of the code gets the current FFT setup and defines necessary functions for calculating FFT info:

```
import("stdfaust.lib");

fftSize = hslider("fftSize", 1024, 2, 16384, 1);       // global variable set by the processor itself
fftHopSize = hslider("fftHopSize", 1024, 2, 16384, 1); // global variable set by the processor itself
bufferSize = fftSize / 2 + 1; // Bins from 0Hz to Nyquist freq
freqPerBin = ma.SR / fftSize;
binToFreq = *(freqPerBin);
freqToBin = /(freqPerBin);

cartopol(x, y) = x * x + y * y : sqrt, atan2(y, x);  // cartesian to polar
poltocar(r, theta) = r * cos(theta), r * sin(theta); // polar to cartesian
```

then UI components:

```
freezeBtn = checkbox("Capture");
reduceSld = hslider("Reduce", 0, 0, 2, 0.01);
```

Here is a function to freeze the last spectrum, when the checkbox is on, instead of bypassing the input, it puts the last received full spectrum buffer into a feedback loop:

```
freeze(rIn, iIn, bin) = out with { // 3 inputs for each audio channel: real, imaginary, current bin
    freezeSignal(sig, frz) = orig + freezed with {
        orig = sig * (1 - frz);
        freezed = orig : @(bufferSize) : + ~ (*(frz) : @(bufferSize - 1)) * frz;
    };
    out = freezeSignal(rIn, freezeBtn), freezeSignal(iIn, freezeBtn);
};
```

Finally the main processor, getting the current magnitude value and subtract the freezed spectrum's corresponding magnitude, then output the resulting spectrum for IFFT.

```
fftproc(rIn, iIn, bin) = out, out with { // 3 inputs for each audio channel: real, imaginary, current bin
    pol = cartopol(rIn, iIn);
    mag = pol : _, !;
    phase = pol : !, _;
    pol_freezed = freeze(rIn, iIn, bin) : cartopol;
    mag_freezed = pol_freezed : _, !;
    phase_freezed = pol_freezed : !, _;

    out = poltocar(mag * (1 - freezeBtn) + (mag - mag_freezed * reduceSld) * freezeBtn : max(0), phase);
};
process = fftproc;
```

The goal of the project is to use the same model for Faust code by writing a C++ wrapper that would add FFT and iFFT processing around the Faust DSP code. This can possibly be done by extending the [ffunction](https://faustdoc.grame.fr/manual/syntax/#foreign-function-declaration) primitive to a mode general version that would deliver a list of output values (instead of a single one), or if not possible, develop a dsp wrapper architecture file that would add the FFT/iFFT process around the Faust DSP code.

---

## Hot reloadable soundfiles

The [soundfile](https://faustdoc.grame.fr/manual/syntax/#soundfile-primitive) primitive currently provides access to a predefined list of external sound resources. These soundfiles are loaded once during the application's initialization and cannot be modified dynamically during runtime.

The primary objective of the project is to enable hot reloadability for soundfiles, allowing users to change them on the fly while the DSP code is actively running. To achieve this, two key aspects need enhancement:

- **code generation improvement**: the code generation process should be refined to facilitate an *atomic switch to the new soundfile* while the DSP code is in execution. This ensures a seamless transition between different sound resources without interrupting the ongoing processing.

- **soundfile loader architecture enhancement**: the architecture of the soundfile loader, detailed in [SoundUI.h](https://github.com/grame-cncm/faust/blob/master-dev/architecture/faust/gui/SoundUI.h), needs to be upgraded. This upgrade should introduce the capability for users to interactively change the loaded soundfile, potentially through a graphical user interface (GUI) element.

For instance, integrating a GUI item within the application can empower users to select and switch soundfiles effortlessly during runtime.

Additionally, a possible solution involves implementing a purely memory-based loader. This loader would *emulate soundfiles as audio buffers in memory*, allowing for dynamic changes to the loaded soundfiles without requiring a complete reload of resources. This approach enhances flexibility and responsiveness by enabling real-time alterations to the sound resource being processed.

By addressing these aspects, the project aims to elevate the functionality of the soundfile primitive, providing users with the ability to seamlessly modify soundfiles while the DSP application is actively running.

---

## WebGPU audio architecture

The [WebGPU audio](https://www.webgpuaudio.com/docs/intro) architecture represents an innovative model to use the WebGL language to compute and render audio on the Web platform: audio Synthesis uses rough streaming architecture to get chunks out of WebGPU and send control buffers to control a WebGPU compute shader.

The primary objective of the project is to develop a [WebGSL](https://www.w3.org/TR/WGSL/) backend for Faust, and an customized architecture file to render the computed audio using the [Web Audio API](https://www.w3.org/TR/webaudio/), as demonstrated in [the current demonstration](https://gist.github.com/JolifantoBambla/0a4e9c2a0a8bc475f081bc6f9d1aa1a8). To validate the efficacy of this model, benchmarks are planned. These will assess the performance of the WebGPU audio architecture, comparing it against the existing standards of [AudioWorklet and WebAssembly](https://faustdoc.grame.fr/manual/deploying/) solutions.

---

## Invertible functions

* Currently addressed by: nil

There could be a new primitive to automatically compute the inverse of a function. If the function can't be inverted at compile-time, then an error should be raised. Having access to the inverse would be useful when a user writes a custom scale function and wants to know its inverse. For example, the user might have an hslider whose visible range is [0-1], but the effective value is scaled:
```faust
scale = pow(_,5)*32*1000; // take [0-1] (unitless) and remap into [0-32000] milliseconds
scaleInverse = inverse(scale);
h = hslider("attack", scaleInverse(50), 0, 1, .01);
process = h : scale;
```

In the code above, we achieve three things:
* The `attack` parameter is "normalized" between 0 and 1, which is useful for modular synthesis.
* We have a custom `scale` function that remaps from [0-1] to a meaningful milliseconds unit.
* We set 50 milliseconds as the default `attack`.

Note that `scaleInverse` will effectively be `scaleInverse = _/(32*1000) : pow(_,1./5);` However, some functions are not invertible, or require assumptions. For example, the inverse of `pow(_,2)` is **plus or minus** `sqrt(_)`.

Other use cases could involve automatically inverting custom scales that use `ba.midikey2hz`.

In a more advanced example, it might be possible to invert a function that takes multiple arguments, while only inverting over the last argument.

Example:

```faust
func(a, b, c, x) = a+2*b+3*c+x;
funcInverse = inverse(func);
// funcInverse(a, b, c, y) now solves for x in y=func(a, b, c, x)
process = _ : funcInverse(1, 1, 1) : _;
```

This would be useful for numerical integration methods (see [en.adsr_bias](https://github.com/grame-cncm/faustlibraries/blob/e06f27dd86e110b9f8dcd0b355ee4fb3173c045d/envelopes.lib#L223)).

---

## faust2nihplug tool 

[NIH-plug](https://github.com/robbert-vdh/nih-plug) is an API-agnostic audio plugin framework written in Rust. The primary objective of the project is to develop a `faust2nihplug` tool to convert a Faust DSP program in a ready-to-compile NIH-plug project. Those [lowpass-lr4-faust-nih-plug](https://codeberg.org/obsoleszenz/lowpass-lr4-faust-nih-plug) and [lamb-rs](https://github.com/magnetophon/lamb-rs) projects can be used as starting points. Monophonic DSP and MIDI controllable polyphonic instruments should be supported.  

---

## Faust IDE MCP 

A Faust based project [Model Context Protocol](https://modelcontextprotocol.io/introduction) to interact with LLMs. See [WebChucK MCP](https://github.com/a-nom-ali/webchuck-mcp) as an example. 
