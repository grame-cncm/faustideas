

# Google Summer of Code possible projects

The application process for GSoC consists of next steps:

- become acquainted with the [Faust language and ecosystem](https://faust.grame.fr)
- join to [Faust Slack channel](https://faustaudio.slack.com) and/or #faust channel on [The Audio Programmer](https://theaudioprogrammer.com/community) discord
- search mentor for chosen project in mailing list discuss
- get invite to chosen project in Faust github organization
- submit the application/proposal including all requirements at the Google Summer of Code Site

Possible projects:

- [Integration in Bespoke](#integration-in-bespoke)
- [Integration in Cables.jl](#integration-in-cablesjl)
- [Integration in HISE](#integration-in-hise)
- [Packaging system for Faust libraries](#packaging-system-for-faust-libraries)
- [Faust programming by examples](#faust-programming-by-examples)
- [Alternative languages built on top of the signal API](#alternative-languages-built-on-top-of-the-signal-api)
---

## Integration in Bespoke

**Mentor:** Stéphane Letz

**Expected size of project:** 175 hours

**More detailed description of the project:** [Bespoke](https://www.bespokesynth.com) is a modular DAW for Mac, Windows, and Linux. Bespoke is a software modular synthesizer. It contains a bunch of modules, which you can connect together to create sounds. 
[Benedict Gaster work](https://github.com/bgaster/BespokeSynth) uses WebAssembly as the compilation target language, and has already done the Bespoke Synth integration. So possibly this work could be directly merged.
A more ambitious approach would be to directly embed the Faust compiler (using the libfaust + LLVM JIT way) with would even produce faster code. This is currently [discussed here](https://github.com/BespokeSynth/BespokeSynth/issues/317). A recent [Faust integration in TouchDesigner](https://github.com/DBraun/TD-Faust/) can be studied as an example.  

**Expected outcomes:** the result will a Bespoke plugin embedding the libfaust library and allowing DSP programs to be edited, dynamically compiled, and run in the platform.

**Skills required/preferred:** C++ programming, graphical programming 

**An easy, medium or hard difficulty rating of each project:** medium

---

## Integration in Cables.jl

**Mentor:** Stéphane Letz

**Expected size of project:** 175 hours

**More detailed description of the project:** [Cables.gl](https://cables.gl) is a tool for creating beautiful interactive content. With an easy to navigate interface and real time visuals, it allows for rapid prototyping and fast adjustments. You are provided with a set of operators, such as mathematical functions, shapes, materials and post processing effects. Connect these to each other with virtual cables to create the experience you have in mind. Easily export your piece of work at any time. Embed it into your website or use it for any kind of creative installation.

The project would be to integrate the [Faust Web Audio Library](https://www.npmjs.com/package/@grame/libfaust) to dynamically compile and run Faust DSP programs in Cables.jl. A recent [Faust integration in TouchDesigner](https://github.com/DBraun/TD-Faust/) can be studied as an example.  

**Expected outcomes:** the result will a Cable.ji plugin embedding the libfaust WASM library, and allowing DSP programs to be edited, dynamically compiled, and run in the platform.

**Skills required/preferred:** C++ programming, Web technologies

**An easy, medium or hard difficulty rating of each project:** medium

---

## Integration in HISE

**Mentor:** Stéphane Letz

**Expected size of project:** 175 hours

**More detailed description of the project:** [HISE](http://hise.audio) is a cross-platform open source audio application for building virtual instruments. It emphasizes on sampling, but includes some basic synthesis features for making hybrid instruments as well as audio effects. You can export the instruments as VST/AU/AAX plugins or as standalone application for Windows / macOS or iOS.

The project would be to integrate the Faust compiler (using the libfaust + LLVM JIT way) into HISE for live editing and then used to generate C++ at compile time. This would allow for much more complex effects development without need to delve into C++ DSP.
This is currently [discussed here](https://github.com/christophhart/HISE/issues/224). A recent [Faust integration in TouchDesigner](https://github.com/DBraun/TD-Faust/) can be studied as an example.  

**Expected outcomes:** the result will be a HISE plugin embedding the libfaust WASM library, and allowing DSP programs to be edited, dynamically compiled, and run in the platform.

**Skills required/preferred:** C++ programming, knowledge of the JUCE framework

**An easy, medium or hard difficulty rating of each project:** medium


---

## Packaging system for Faust libraries

**Mentors:** Yann Orlarey and Stéphane Letz

**Expected size of project:** 350 hours

**More detailed description of the project:** The idea is to develop a packaging system to facilitate the integration of Faust libraries in a DSP project. The inspiration comes from the [Julia](https://www.julialang.org) language with the [JuliaHub](https://juliahub.com/) project and/or the [Rust](https://www.rust-lang.org/) language with the [Cargo](https://doc.rust-lang.org/cargo/) package manager. 

### Requirements

- load packages containing Faust sources, either in .dsp format or in .lib format
- be able to load sets of files (typically a library that is written with several .lib files)
- isolate packages in different environments to avoid name conflicts
- notion of a centralized directory on GitHub, where contributions can be made in the form of Pull Requests. Publishing tool (with search by content) of this directory, general, like **fausthub** (inspired for example by Juliahub https://juliahub.com/lp/).
- at each PR, test of the syntax of the code (with GitHub actions)
- cache management: typically 1) the package is loaded the 1st time and kept in a cache, 2) then the compiler uses the version in the cache. See the question of new version management?
- automatic generation of the documentation from the lib files (stating from the existing tools and possibly adapting them), automatic deployment
- preservation semantic: we want to be able to keep a project as a DSP file with all its dependend libraries with specific version numbers   

### Syntax proposal

#### Simple version

`package("foo")` ⇒ syntactic sugar for `library("https://faustpackages.grame.fr, "path/to/actual/librarie.lib")`

#### Version with constraint on version number

`package("foo", "3.4")` ⇒ syntactic sugar for `library("https://faustpackages.grame.fr, "path/to/actual/3.4/librarie.lib")`

`package("foo").bar`

or else: 

`foo = package("foo")` and `foo.bar` in the DSP code

### Tools to describe packages
	
- look at the package format of Rust or Julia: .toml file, src folders, tests
- look at the TOML format (https://toml.io/en/), used by Rust and Julia

**Expected outcomes:** 

- a working insfrastructure with a server hosting the published packages
- an extended Faust compiler able to access the server

**Skills required/preferred:** C++ programming

**An easy, medium or hard difficulty rating of each project:** hard

---

## Faust programming by examples

**Mentors:** Yann Orlarey and Stéphane Letz

**Expected size of project:** 350 hours

**More detailed description of the project:** The objective is to develop a new approach to Faust programming, not textual or graphical, but based on DAW-like examples. This programming principle is analogue to the one described in the article [Real time Composition in Elody](https://hal.archives-ouvertes.fr/hal-02158910/document). This approach is based on the idea of manipulating and editing virtual "audio files" which represent the real time audio inputs and outputs. 

To take a simple monophonic example, let's call these two virtual audio files `INPUT` and `OUTPUT`. Let's note `t:file` the fact of placing in the DAW a file `file`at time `t` in seconds and `t:file*0.75` the fact of placing in the DAW a file at time `t` but also controlling its sound level. So the DAW construction `{0:INPUT, 1:OUTPUT*0.75}` corresponds to a realtime echo whose Faust translation is `process = + ~ (@(ma.SR):*(0.75));`. 

**Expected outcomes:** the project consists in exploring this model and see how standard DAW editing actions can be translated in Faust DSP programs. A prototype coded in TypeScript, JavaScript or any other scripting languages will be developed.

**Skills required/preferred:** C++ programming, possibly TypeScript + JavaScript or other scripting languages.

**An easy, medium or hard difficulty rating of each project:** hard

---

## Languages built on top of the signal API

**Mentors:** Yann Orlarey and Stéphane Letz

**Expected size of project:** 350 hours

**More detailed description of the project:** The [signal API](https://faustdoc.grame.fr/tutorials/signal-api/) opens an intermediate access inside the Faust compilation chain. Generating complex expressions by directly using it can quickly become really tricky and unpracticable. So a language created on top of the signal API is usually needed. This is exactly what the Block Diagram Algebra is all about, and the entire Faust language itself.

But some other approaches can possibly be tested. The [Elementary audio language](https://www.elementary.audio) for instance is built over a [similar signal](https://docs.elementary.audio/guides/making_sound) language and uses JavaScript as the upper layer language to help create complex signal graphs programmatically. 

**Expected outcomes:** the project consits in exploring various approaches to build a language on top of the signal API. It could be a textual one (like JavaScript, Haskell or scripting languages...) or a purely graphical tool. 

**Skills required/preferred:** C++ programming, possibly TypeScript + JavaScript, Haskell or other functional languages.

**An easy, medium or hard difficulty rating of each project:** hard

---

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
- [TensorFlow Support](#tensorflow-support)
- [Improved Linear Algebra Support](#improved-linear-algebra-support)
- [Finish the DX7 Implementation](#finish-the-dx7-implementation)
- [Trigonometric simplifications](#trigonometric-simplifications)
- [WebAssembly specific optimisations](#webassembly-specific-optimisations)
- [Improve faust2audiokit](#improve-faust2audiokit)
- [Testing tools on the Web](#testing-tools-on-the-web)

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

## TensorFlow Support

* Currently addressed by: nil

Be able to generate TensorFlow code with Faust.

---

## Improved Linear Algebra Support

* Currently addressed by: nil

Linear algebra operations are currently poorly supported in Faust. Having a way to conveniently express matrices would improvement. As part of that, linear algebra/matrix operations (e.g., inversion, multiplication, determinant, etc.) primitives could be added to the language.

### Potential Implementation

Matrices could be expressed using the Faust-multirate `vectorize` primitives
by creating vectors of vectors.

It would be interesting to try to implement matrix operations from scratch in  Faust. Although it might be hard and not so optimized, thus a more pragmatic solution would be to implement them as primitives. That would be a fair amount of work as this would imply that the corresponding code for each language supported by Faust would have to be supported. 

---

## Finish the DX7 Implementation

* Currently addressed by: nil

Essentially, finish `dx7.lib`. It might be worth looking at these elements to
make this happen:

* <https://webaudiomodules.org/demos/wasm/dx7.html>
* <https://github.com/everythingwillbetakenaway/DX7-Supercollider>

---

## Trigonometric simplifications

* Currently addressed by: nil (suggested by [Pierre Leconte](https://github.com/grame-cncm/faust/issues/59))

For some applications, trigonometric functions (spherical harmonics) are used, and depending on the algorithm, the output formula could be very complicated. However, in a lot of cases, trigonometric identities could help to simplify drastically the expressions.

---

## WebAssembly specific optimisations

* Currently addressed by: Stéphane and Yann

To run as fast as possible and approch native code performances as much as possible, WebAssembly code requires some specific optimisations, like: memory access (index precomputation as much as possible...), delay lines handling, struct/stack variables access...etc. We have started an informal collaboration with Mozilla engineers (Benjamin Bouvier) to work on this subject.

---

## Improve faust2audiokit

* Currently addressed by: nil

The [faust2audiokit](https://github.com/grame-cncm/faust/tree/master-dev/architecture/audiokit) tool transforms a Faust DSP program into a fully working AudioKit node. The result can be a monophonic DSP or a MIDI controllable polyphonic one (when the DSP describes an instrument, following the freq, gain, gate parameter naming convention).

The project consist in improving and finishing the tool.

---

## Testing tools on the Web

* Currently addressed by: nil

Faust distribution already contains some testing tools, like `faust2plot` or `faust2octave`.etc. It would be great to have them running in a Web page (or some extension of the same idea). For signal generators/processors, several output formats (oscilloscope, spectrogramme...), and for processors several calibrated input signals (dirac impulse, ramp, sinusoide..) would be available.
