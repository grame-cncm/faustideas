

# Google Summer of Code possible projects

## Discovering the Faust ecosystem

The application process for GSoC consists of the next steps:

- become acquainted with the [Faust language and ecosystem](https://faust.grame.fr). In particular looking at the [Powered By Faust](https://faust.grame.fr/community/made-with-faust/) page can help understanding the variety of projects that have been developed using Faust. 
- join to [Faust Slack channel](https://faustaudio.slack.com) and #gsoc channel where you can reach the mentors and ask questions about the GSoC program, or #faust channel on [The Audio Programmer](https://theaudioprogrammer.com/community) discord, or the [Faust Mailing Lists](https://faust.grame.fr/community/help/)
- read the [GSoC guide for students](https://developers.google.com/open-source/gsoc/resources/guide). Develop your understanding of the various stages of the program. Read this [blog post](https://sayak.dev/gsoc-faqs/)
- check the [GSoC contribution timeline](https://developers.google.com/open-source/gsoc/timeline)
- read our [Contributing guidelines](https://github.com/grame-cncm/faust/wiki/Contributing)
- get invite to chosen project in Faust github organization
- submit the application/proposal including all requirements at the Google Summer of Code Site

## Information Candidates Should Supply

The application process has several steps. Before contacting anybody verify that you are eligible, that is that you are enrolled as student, don't get a tuition fee, etc. The next step is to contact the mentor of the project you are interested in. You have to convince him that you are the right person to get the job done. The next step is to work out more details and to contact the mentoring organization by providing the following information by email to [research@grame.fr](mailto:research@grame.fr):

* Project:
  * Select a project in the list and provide your personal and detailed description. If you wish to work on another idea of your own, we are pretty open as long as this serves the goal of consolidating Faust and its ecosystem as a whole.
  * Provide a proposal of a technical solution with your envisioned methodology. The more detailed the better.
  * Provide a realistic schedule with objectives (one every two weeks for example) and deadlines. Focus on mid-term objectives as well as on the final evaluation.

* Personal data:
  * First name, last name, affiliation and geographical location.
  * A brief list of the main studies and programming courses attended, with ranking.
  * List of the most important software projects contributed and success.
  * Which are your best skills in terms of programming ?
  * In general what is your taste in terms of programming? language, methodology, team work, etc.
  * Is there anything that prevents you from working full time on the project during the program period?
  * How do you see your involvement after the program ends? Do you see yourself pushing the project further, or do you see yourself contributing to other Faust and its ecosystem projects?
  * Are you more interested in the Faust language and its ecosystem, or do you feel more like a hacker?
  * What are your long-term wishes in terms of job?


## Possible projects:

- [Support for CLAP format](#support-for-clap-format)
- [Integration in Surge](#integration-in-surge)
- [Integration in Bespoke](#integration-in-bespoke)
- [Integration in Godot](#integration-in-godot)
- [Integration in Cables.gl](#integration-in-cablesgl)
- [PluginGuiMagic architecture ](#pluginguimagic-architecture)
- [VST plugin embedding the dynamic compiler](#vst-plugin-embedding-the-dynamic-compiler)
- [Integration in Audiokinetic Wwise ](#integration-in-audiokinetic-wwise)
- [Integration in BELA](#integration-in-bela)
- [Integration in openFramework](#integration-in-openframework)
- [Packaging system for Faust libraries](#packaging-system-for-faust-libraries)
- [Faust programming by examples](#faust-programming-by-examples)
- [Languages built on top of the signal API](#languages-built-on-top-of-the-signal-api)

---

### Support for CLAP format

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

[CLAP](https://github.com/free-audio/clap#learn-about-clap) is an Audio Plugin format (as pure C api), liberally licensed (MIT), entirely developers in the open (GitHub), with support from commercial developers ([u-he](https://u-he.com), [Bitwig](https://www.bitwig.com/de/), more). 
CLAP has many design goals, but a primary one was to allow developers to build their base plugin layer using a properly open clean C standard, to replace the VST2 API which most folks base their plugin model on, and then project into other systems. An extensive discussion can be [accessed here](https://www.kvraudio.com/forum/viewtopic.php?t=574861).

The project is to develop a `faust2clap` tool (see [faust2xx Tools](https://faustdoc.grame.fr/manual/tools/) and [Developing a faust2xx Script](https://faustdoc.grame.fr/manual/architectures/#developing-a-faust2xx-script)) to *statically* compile Faust DSP code in a CLAP plugin. You'll have to develop or adapt [C++ architecture files](https://faustdoc.grame.fr/manual/architectures/). Look at additional [CLAP projects](https://github.com/free-audio).

**Expected outcomes:** the result will be a `faust2clap` script to compile a DSP program in a CLAP plugin.

**Skills required/preferred:** C++ programming, audio and Faust programming.

**An easy, medium or hard difficulty rating of each project:** medium

---

### Integration in Surge

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

The Surge Synth Team is a group of musicians, developers, testers, documenters, and general volunteer open source enthusiasts who randomly assembled to work on the [Surge Synthesizer](https://surge-synth-team.org). Use the [Discord channel](https://discord.gg/aFQDdMV) to connect to their community.

The project is to develop a `faust2surge` tool (see [faust2xx Tools](https://faustdoc.grame.fr/manual/tools/) and [Developing a faust2xx Script](https://faustdoc.grame.fr/manual/architectures/#developing-a-faust2xx-script)) to *statically* compile Faust DSP code in a Surge plugin. This is currently [discussed here](https://github.com/surge-synthesizer/surge/issues/3669#issuecomment-967062337). You'll probably have to develop or adapt [C++ architecture files](https://faustdoc.grame.fr/manual/architectures/).

**Expected outcomes:** the result will be a `faust2surge` script to compile a DSP program in a Surge plugin.

**Skills required/preferred:** C++ programming, audio and Faust programming, knowledge of the [JUCE framework](https://juce.com).

**An easy, medium or hard difficulty rating of each project:** medium

---

### Integration in Bespoke

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

**More detailed description of the project:** [Bespoke](https://www.bespokesynth.com) is a modular DAW for Mac, Windows, and Linux. It contains a bunch of modules, which you can connect together to create sounds. Use the [Discord channel](https://discord.gg/YdTMkvvpZZ) to connect to their community. The integration could follow the two steps:

- develop a `faust2bespoke` tool (see [faust2xx Tools](https://faustdoc.grame.fr/manual/tools/) and [Developing a faust2xx Script](https://faustdoc.grame.fr/manual/architectures/#developing-a-faust2xx-script)) to *statically* compile Faust DSP code in Bespoke modules

- a complementary approach is to directly embed the Faust compiler ([using libfaust + LLVM JIT](https://faustdoc.grame.fr/manual/embedding/)), allowing DSP programs to be edited, dynamically compiled, and run in the platform

This is currently [discussed here](https://github.com/BespokeSynth/BespokeSynth/issues/317). You'll probably have to develop or adapt [C++ architecture files](https://faustdoc.grame.fr/manual/architectures/). A recent [Faust integration in TouchDesigner](https://github.com/DBraun/TD-Faust/) can be studied as an example.

**Expected outcomes:** the result will be:

- a`faust2bespoke` tool to compile Faust DSP code in Bespoke modules

- a Bespoke plugin embedding the libfaust + LLVM library, and allowing DSP programs to be edited, dynamically compiled, and run in the platform

**Skills required/preferred:** C++ programming, graphical programming, audio and Faust programming.

**An easy, medium or hard difficulty rating of each project:** medium to hard

References: 

- [Bespoke Anywhere](https://nime.pubpub.org/pub/8jaqbl7m/release/1?readingCollection=bd12ca41)
---

### Integration in Godot

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

**More detailed description of the project:** [Godot Engine](https://godotengine.org) is a feature-packed, cross-platform game engine to create 2D and 3D games from a unified interface. It provides a comprehensive set of common tools, so that users can focus on making games without having to reinvent the wheel. The integration could follow the two steps:

- develop a `faust2godot` tool (see [faust2xx Tools](https://faustdoc.grame.fr/manual/tools/) and [Developing a faust2xx Script](https://faustdoc.grame.fr/manual/architectures/#developing-a-faust2xx-script)) to *statically* compile Faust DSP code in Godot modules

- a complementatry approach is to directly embed the Faust compiler ([using libfaust + LLVM JIT](https://faustdoc.grame.fr/manual/embedding/)), allowing DSP programs to be edited, dynamically compiled, and run in the platform

You'll probably have to develop or adapt [C++ architecture files](https://faustdoc.grame.fr/manual/architectures/). A recent [Faust integration in TouchDesigner](https://github.com/DBraun/TD-Faust/) can be studied as an example.

**Expected outcomes:** the result will be:

- a`faust2godot` tool to compile Faust DSP code in Godot modules

- a Godot plugin embedding the libfaust + LLVM library, and allowing DSP programs to be edited, dynamically compiled, and run in the platform

**Skills required/preferred:** C++ programming, audio and Faust programming.

**An easy, medium or hard difficulty rating of each project:** medium to hard

---

### Integration in Cables.gl

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

**More detailed description of the project:** [Cables.gl](https://cables.gl) is a tool for creating beautiful interactive content. With an easy to navigate interface and real time visuals, it allows for rapid prototyping and fast adjustments. You are provided with a set of operators, such as mathematical functions, shapes, materials and post processing effects. Connect these to each other with virtual cables to create the experience you have in mind. Easily export your piece of work at any time. Embed it into your website or use it for any kind of creative installation. Use the [Discord channel](https://discord.com/invite/AGTarWv) to connect to their community.

The project would be to integrate the [Faust Web Audio Library](https://www.npmjs.com/package/@grame/libfaust) to dynamically compile and run Faust DSP programs in Cables.gl. 

**Expected outcomes:** the result will be a Cable.gl plugin embedding the libfaust WASM library, and allowing DSP programs to be edited, dynamically compiled, and run in the platform.

**Skills required/preferred:** TypeScript/JavaScript programming, Web technologies, audio and Faust programming.

**An easy, medium or hard difficulty rating of each project:** medium

---

### PluginGuiMagic architecture 

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr) and [Daniel Walz](daniel@foleysfinest.com)

**Expected size of project:** 175 hours

**More detailed description of the project:** [PluginGuiMagic](https://foleysfinest.com/developer/pluginguimagic/) is a WYSWYG runtime design system for [JUCE](https://juce.com) plugins. The foleys_plugin_magic module allows to have a generated UI, that can be edited at runtime using advanced layout and styling options. It also adds visualisers to display signals, levels and spectra with no extra coding involved. The project is to develop new C++ [architecture files](https://faustdoc.grame.fr/manual/architectures/) to ease the use of PGM in the [faust2juce](https://github.com/grame-cncm/faust/tree/master-dev/architecture/juce) tool.

**Expected outcomes:** the result will be set of C++ architecture files and an improved `faust2juce` tool.

**Skills required/preferred:** C++ programming, knowledge of the JUCE framework, knowledge of the foleys_plugin_magic module, audio and Faust programming.

**An easy, medium or hard difficulty rating of each project:** medium

---

### VST plugin embedding the dynamic compiler

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

**More detailed description of the project:** A VST plugin using the [libfaust + LLVM JIT](https://faustdoc.grame.fr/manual/embedding/) to do DSP live coding in any VST aware host. FX and monophonic or polyphonic synthesizers can be written. The source code can be edited and recompiled on the fly. The GUI has to be automatically created. The [pMix](https://github.com/olilarkin/pMix2) and [Amati](https://github.com/glocq/Amati) projects can be used as starting points. An integration with the [PluginGuiMagic](https://foleysfinest.com/developer/pluginguimagic/) architecture could possibly be added. 

**Expected outcomes:** the result will be a VST plugin developed with the [JUCE framework](https://juce.com) .

**Skills required/preferred:** C++ programming, audio and Faust programming, knowledge of the JUCE framework.

**An easy, medium or hard difficulty rating of each project:** medium

---

### Integration in Audiokinetic Wwise 

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 350 hours

**More detailed description of the project:** [Audiokinetic](https://www.audiokinetic.com/en/) is the leading global provider of the most advanced and scalable cross platform interactive audio solutions. A trusted technology partner to the world’s largest developers, OEMs, and audio production companies, its flagship product Wwise is the gold standard interactive audio engine on the market. 
    [Wwise](https://www.audiokinetic.com/en/products/wwise) features a complete suite of design and development tools, making it easy to prototype and bring to life your creative vision for audio, no matter the scale of your project. The integration could follow the two steps:
    
- develop a `faust2wwise` tool (see [faust2xx Tools](https://faustdoc.grame.fr/manual/tools/) and [Developing a faust2xx Script](https://faustdoc.grame.fr/manual/architectures/#developing-a-faust2xx-script)) to *statically* compile Faust DSP code in Wwise modules

- a complementatry approach is to directly embed the Faust compiler ([using libfaust + LLVM JIT](https://faustdoc.grame.fr/manual/embedding/)), allowing DSP programs to be edited, dynamically compiled, and run in the platform

Look at the [faust2wwise](https://github.com/grame-cncm/faust2wwise) preliminary work. You'll probably have to develop or adapt [C++ architecture files](https://faustdoc.grame.fr/manual/architectures/).

**Expected outcomes:** the result will be: 

- a new `faust2wwise` tool with the associated C++ architecture files to compile a DSP project in a ready to use Wwise plugin

- a plugin embedding the libfaust + LLVM JIT dynamic compiler technology to allow Faust DSP live-coding

**Skills required/preferred:** C++ programming, audio and Faust programming, knowledge of the Audiokinetic Wwise architecture.

**An easy, medium or hard difficulty rating of each project:** hard

---

### Integration in BELA

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

**More detailed description of the project:** [BELA](https://bela.io) is a maker platform for creating beautiful interaction. Designed for artists, musicians, researchers and makers, Bela brings the power of ultra-low latency interactive audio and sensors to your digital projects. A Faust/BELA integration has already been done in a `faust2bela` tool.

**Expected outcomes:** the result will be: 

- an improved `faust2bela` tool

- a fully integrated Faust/BELA IDE that would allow to design and experiment Faust code in the Web plaform (using the dynamic WebAssembly based compilation chain), then compile it in C++ and deploy it on the BELA board. Monophonic DSP and MIDI controllable polyphonic instruments should be supported. 

---

### Integration in openFramework

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

**More detailed description of the project:** [openFrameworks](https://openframeworks.cc/about/) is an open source C++ toolkit designed to assist the creative process by providing a simple and intuitive framework for experimentation. It allows to access a lot of additional extensions and libraries in the form of [addons](https://ofxaddons.com). The project is to explore how Faust can be integated in the framework, either statically (using the C++ generated code from a DSP program), or possibly embedding the [libfaust](https://faustdoc.grame.fr/manual/embedding/) compiler. Adapted architecture files will be developed.   

**Expected outcomes:** the result will be a set of C++ architecture files and openFrameworks demo examples explaining how to use them.

---

### Packaging system for Faust libraries

**Mentors:** [Yann Orlarey](mailto:orlarey@grame.fr) and [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 350 hours

**More detailed description of the project:** The idea is to develop a packaging system to facilitate the integration of Faust libraries in a DSP project. The inspiration comes from the [Julia](https://www.julialang.org) language with the [JuliaHub](https://juliahub.com/) project and/or the [Rust](https://www.rust-lang.org/) language with the [Cargo](https://doc.rust-lang.org/cargo/) package manager. 

#### Requirements

- load packages containing Faust sources, either in .dsp or in .lib format
- be able to load sets of files (typically a library that is written as several .lib files)
- isolate packages in different environments, to avoid name conflicts
- notion of a centralized directory on GitHub, where contributions can be made in the form of Pull Requests. Publishing tool (with search by content) of this directory, general, like **fausthub** (inspired for example by Juliahub https://juliahub.com/lp/).
- at each PR, test of the syntax of the code with GitHub actions
- cache management: typically 1) the package is loaded the 1st time and kept in a cache, 2) then the compiler uses the version in the cache. Work on the question of new version management.
- automatic generation of the documentation from the lib files (stating from the existing tools and possibly adapting them), automatic deployment
- preservation semantic: we want to be able to keep a project as a DSP file with all its needed libraries with specific version numbers   

#### Syntax proposal

##### Simple version

`package("foo")` ⇒ syntactic sugar for `library("https://faustpackages.grame.fr, "path/to/actual/librarie.lib")`

##### Version with constraint on version number

`package("foo", "3.4")` ⇒ syntactic sugar for `library("https://faustpackages.grame.fr, "path/to/actual/3.4/librarie.lib")`

`package("foo").bar`

or else: 

`foo = package("foo")` and `foo.bar` in the DSP code

#### Tools to describe packages
	
- look at the package format of Rust or Julia: .toml file, src folders, tests

- look at the TOML format (https://toml.io/en/), used by Rust and Julia

**Expected outcomes:** 

- a working insfrastructure with a server hosting the published packages

- an extended Faust compiler able to access the server

**Skills required/preferred:** C++ programming, server/client technology.

**An easy, medium or hard difficulty rating of each project:** hard

---

### Faust programming by examples

**Mentors:** [Yann Orlarey](mailto:orlarey@grame.fr) and [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 350 hours

**More detailed description of the project:** The objective is to develop a new approach to Faust programming, not textual or graphical, but based on DAW-like examples. This programming principle is analogue to the one described in the article [Real time Composition in Elody](https://hal.archives-ouvertes.fr/hal-02158910/document). This approach is based on the idea of manipulating and editing virtual "audio files" which represent the real time audio inputs and outputs. 

To take a simple monophonic example, let's call these two virtual audio files `INPUT` and `OUTPUT`. Let's note `t:file` the fact of placing in the DAW a file `file`at time `t` in seconds and `t:file*0.75` the fact of placing in the DAW a file at time `t` but also controlling its sound level. So the DAW construction `{0:INPUT, 1:OUTPUT*0.75}` corresponds to a realtime echo whose Faust translation is `process = + ~ (@(ma.SR):*(0.75));`. 

**Expected outcomes:** the project consists in exploring this model and see how standard DAW editing actions can be translated in Faust DSP programs. A prototype coded in TypeScript, JavaScript or any other scripting languages will be developed.

**Skills required/preferred:** C++ programming, possibly TypeScript + JavaScript or other scripting languages.

**An easy, medium or hard difficulty rating of each project:** hard

---

### Languages built on top of the signal API

**Mentors:** [Yann Orlarey](mailto:orlarey@grame.fr) and [Stéphane Letz](mailto:letz@grame.fr)

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
- [Improve faust2vcvrack](#improve-faust2vcvrack)
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
