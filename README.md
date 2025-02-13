

# Google Summer of Code possible projects

This page contains a list of possible GSoC projects, with a preliminary section explaining the prerequisites to follow before working on a real project.

## Discovering the Faust ecosystem

The application process for GSoC consists of the next steps:

- become acquainted with the [Faust language and ecosystem](https://faust.grame.fr). In particular looking at the [Powered By Faust](https://faust.grame.fr/community/powered-by-faust/) page can help understanding the variety of projects that have been developed using Faust. Read also the [technical documentation](https://faustdoc.grame.fr).
- join the [Faust discord server](https://discord.gg/RzuFg6B8zA) and #gsoc channel.
- read the [GSoC guide for students](https://developers.google.com/open-source/gsoc/resources/guide). Develop your understanding of the various stages of the program. Read this [blog post](https://sayak.dev/gsoc-faqs/).
- check the [GSoC contribution timeline](https://developers.google.com/open-source/gsoc/timeline).
- read our [Contributing guidelines](https://github.com/grame-cncm/faust/wiki/Contributing).
- get invite to chosen project in Faust github organization.
- submit the application/proposal including all requirements at the Google Summer of Code Site.

## Information Candidates Should Supply

The application process has several steps. First, verify that you meet the GSoC contributor [eligibility requirements](https://summerofcode.withgoogle.com/get-started), i.e. you are at least 18 years old, eligible to work in your country of residence, etc. As of 2023, GSoC eligibility has been expanded to include "open source beginners" in addition to students. The next step is to contact the mentor(s) of the project you are interested in; the best place to do so is in the `#gsoc` channel of the [Faust Discord server](https://discord.gg/vzh7CggBtj), where you can ask questions related to the project you're interested in working on, and submit draft proposals for feedback. Your goal is to convince prospective mentors that you are the right person to get the job done; you can do this by sharing your previous work, demonstrating relevant experience/intuition, asking pertinent questions, etc. Finally, submit a project proposal via your GSoC contributor dashboard. Your submission must include a PDF that should contain the following information:

* Project:
  * A detailed description of the project that you wish to tackle. Either select a topic from the list [below](#possible-projects), or, if you wish to work on an idea of your own, **we are pretty open as long as this serves the goal of consolidating Faust and its ecosystem as a whole**.
  * A proposal of a technical solution with your envisioned methodology. The more detailed the better.
  * A realistic schedule with objectives (one every two weeks for example) and deadlines. Focus on mid-term objectives as well as on the final evaluation.

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

- [Integrated Faust Language Server and Formatting Extension for VS Code](#tntegrated-faust-language-server-and-formatting-extension-for-vs-code)
- [Extending the Faust DSP Testbench](#extending-the-faust-dsp-testbench)
- [Backend for MOJO](#backend-for-mojo)
- [Support for CLAP format](#support-for-clap-format)
- [Integration in Surge](#integration-in-surge)
- [Integration in Bespoke](#integration-in-bespoke)
- [Integration in Godot](#integration-in-godot)
- [PluginGuiMagic architecture ](#pluginguimagic-architecture)
- [Integration in Audiokinetic Wwise ](#integration-in-audiokinetic-wwise)
- [Integration in BELA](#integration-in-bela)
- [Integration in openFramework](#integration-in-openframework)
- [Faust programming by examples](#faust-programming-by-examples)
- [Languages built on top of the signal API](#languages-built-on-top-of-the-signal-api)
- [Developing modular synthesis using widget modulation](#developing-modular-synthesis-using-widget-modulation)

Some [more ideas](#faust-ideas) could possibly be turned as GSoC projects.

### Integrated Faust Language Server and Formatting Extension for VS Code

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr) 

**Expected size of project:** 175 hours

**Description:** A [language server](https://en.wikipedia.org/wiki/Language_Server_Protocol), sometimes called an LSP, is a code analysis tool that allows programming environments to get information about projects. This lets them display information like code completions, inline errors, locations of function definitions, reference official documentation, and more. Many programming languages have their own language server (see https://langserver.org/ for a list), but it seems that Faust doesn't. If there was a Faust language server, it would make it easier to write Faust code using any IDE that supports LSP. This would make it easier for beginners to get started writing Faust using programming tools they're already familiar with, and it would make it easier for experts to navigate large codebases. The [tree-sitter-faust](https://github.com/khiner/tree-sitter-faust) project could be helpful in doing any parsing required for a language server.
We propose to create a Visual Studio Code extension that integrates the Faust Language Server with a dedicated Faust code formatter. Leveraging the `vscode-languageclient` package, the extension will launch the Faust Language Server to provide robust features (code completion, diagnostics, navigation) while also offering context-aware formatting tailored to Faust DSP syntax.

- **Integrate the Faust Language Server:**  
  Use `vscode-languageclient` to launch and manage the server, ensuring features like auto-completion and error checking are available for `.dsp` files.

- **Develop a Faust Code Formatter:**  
  Implement a formatter that understands Faust’s constructs, providing commands and auto-format-on-save functionality to improve readability and enforce best practices.

**Expected outcomes:**

- A fully functional VS Code extension that combines the Faust Language Server with a dedicated code formatter.
- Enhanced developer productivity through improved code intelligence and formatting.
- Comprehensive documentation and user-friendly configuration options, making it easier for the Faust community to adopt best practices.

**Skills required:** Faust programming, TypeScriitp and Web programmin.

**An easy, medium or hard difficulty rating of each project:** medium

---
### Extending the Faust DSP Testbench

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr) 

**Expected size of project:** 175 hours

**Description:** The [Faust DSP Testbench](https://github.com/grame-cncm/Faust-DSP-Testbench), a fork of the DSP-Testbench project, is designed to help developers using the JUCE framework to analyse their Faust DSP. This project will focus on extending the Testbench’s functionality to make it a more comprehensive and user-friendly tool for developers and researchers working with Faust.

The proposed extensions aim to:
- Extend and improve the visualisation tools.
- Enable better visualization of DSP performance and behavior.

**Expected outcomes:**
- A robust, user-friendly Faust DSP Testbench with automated testing, benchmarking, and visualization capabilities.
- Comprehensive documentation and tutorials for using the Testbench effectively.

**Skills required:** Faust programming, DSP theory, C++, knowledge of the [JUCE framework](https://juce.com).

**An easy, medium or hard difficulty rating of each project:** medium

---
### Backend for MOJO 

**Mentors:** [Stéphane Letz](mailto:letz@grame.fr) and [Yann Orlarey](mailto:orlarey@gmail.com)  

**Expected size of project:** 175 hours

[Mojo](https://www.modular.com/max/mojo) is a new programming language that bridges the gap between research and production by combining the best of Python syntax with systems programming and metaprogramming. Mojo combines the usability of Python with the performance of C, unlocking unparalleled programmability of AI hardware and extensibility of AI models. With Mojo, you can write portable code that’s faster than C and seamlessly inter-op with the Python ecosystem. Having [autodifferentiation](https://en.wikipedia.org/wiki/Automatic_differentiation) inside the language is not yet ready but is regularly discussed on [Mojo Discord](https://docs.modular.com/mojo/community). 

The primary objective of the project is to [develop a backend](https://github.com/grame-cncm/faust/tree/master-dev/compiler/generator/template) for this new language, add architecture files, and measure how the generated code behaves doing various benchmarks. 

**Expected outcomes:**

- a new backend to generate MOJO code 
- development of MOJO architecture files to create benchmarks and measure the speed of the generated code 

**Skills required/preferred:** C++ and basic Python programming, Faust programming

**An easy, medium or hard difficulty rating of each project:** medium

---
### Differentiable DSP in Faust [Taken in 2024]

**Mentors:** [Thomas Rushton](mailto:thomas.rushton@inria.fr), [David Braun](mailto:db1224@princeton.edu), [Stéphane Letz](mailto:letz@grame.fr), and [Yann Orlarey](mailto:orlarey@gmail.com)  

**Expected size of project:** 175 hours

Differentiable programming is a technique whereby a program can be differentiated with respect to its inputs, permitting the computation of the sensitivity of the program's outputs to changes in its inputs.

Partial derivatives of a program can be found analytically via [automatic differentiation](https://en.wikipedia.org/wiki/Automatic_differentiation) and, coupled with an appropriate loss function, used to perform gradient descent.
Differentiable programming has consequently become a key tool in solving machine learning problems.

Differentiable digital signal processing ([DDSP](https://intro2ddsp.github.io/background/what-is-ddsp.html)) is the specific application of differentiable programming to audio tasks. DDSP has emerged as a key component in machine learning approaches to problems such as source separation, timbre transfer, parameter estimation, etc. DDSP is reliant on a programming language with a supporting framework for automatic differentiation. In Python, this is provided by libraries such as TensorFlow and JAX; other languages, [Swift](https://github.com/apple/swift/blob/main/docs/DifferentiableProgramming.md) for example, may feature native support.

We would like to explore the possibility of implementing automatic differentiation in Faust; the successful implementation of a Faust library for differentiable programming would permit the application of Faust to DDSP 
problems. Exploratory [work](https://github.com/hatchjaw/faust-ddsp) on such a library has begun; one aim is to turn this into a comprehensive package of support for differentiable Faust programs.

Related work, concerned with adding automatic differentiation capabilities to the Faust compiler, was conducted for a [previous edition](https://github.com/grame-cncm/faust/pull/939) of GSoC. Also consult David Braun's [DawDreamer](https://github.com/DBraun/DawDreamer) project, which uses Faust's [JAX](https://jax.readthedocs.io/en/latest/notebooks/quickstart.html) backend.

**Expected outcomes:**

- creation of an automatic differentiation library describing derivatives for 
  all of Faust's operators, helper functions for generalising the creation of 
  differentiable Faust programs, a variety of time- and frequency-domain loss 
  functions, etc.;
- development of a series of practical applications of the new library;
- a new autodiff (or machine learning) architecture file, to support the 
  training of machine learning models and the generation of parameter weights;
- a means to use the generated weights for real-time inference.

**Skills required/preferred:** Faust programming, machine learning

**An easy, medium or hard difficulty rating of each project:** medium

---

### Support for CLAP format

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

[CLAP](https://github.com/free-audio/clap#learn-about-clap) is an Audio Plugin format (as pure C api), liberally licensed (MIT), entirely developers in the open (GitHub), with support from commercial developers ([u-he](https://u-he.com), [Bitwig](https://www.bitwig.com/de/), more). 
CLAP has many design goals, but a primary one was to allow developers to build their base plugin layer using a properly open clean C standard, to replace the VST2 API which most folks base their plugin model on, and then project into other systems. An extensive discussion can be [accessed here](https://www.kvraudio.com/forum/viewtopic.php?t=574861).

The project is to develop: 
- a `faust2clap` tool (see [faust2xx Tools](https://faustdoc.grame.fr/manual/tools/) and [Developing a faust2xx Script](https://faustdoc.grame.fr/manual/architectures/#developing-a-faust2xx-script)) to *statically* compile Faust DSP code in a CLAP plugin.
- and a CLAP pluging embedding the [libfaust](https://faustdoc.grame.fr/manual/embedding/) based dynamic compilation chain, so that DSP programs can be *written and recompiled* on the fly
- new [C++ architecture files](https://faustdoc.grame.fr/manual/architectures/) will have to be developed.

Look at additional [CLAP projects](https://github.com/free-audio).

**Expected outcomes:** The result will be a `faust2clap` script to compile a DSP program in a CLAP plugin, and a CLAP pluging embedding libfaust.

**Skills required/preferred:** C++ programming, audio and Faust programming.

**An easy, medium or hard difficulty rating of each project:** medium

---

### Integration in Surge

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

The Surge Synth Team is a group of musicians, developers, testers, documenters, and general volunteer open source enthusiasts who randomly assembled to work on the [Surge Synthesizer](https://surge-synth-team.org). Use the [Discord channel](https://discord.gg/aFQDdMV) to connect to their community.

The project is to develop a `faust2surge` tool (see [faust2xx Tools](https://faustdoc.grame.fr/manual/tools/) and [Developing a faust2xx Script](https://faustdoc.grame.fr/manual/architectures/#developing-a-faust2xx-script)) to *statically* compile Faust DSP code in a Surge plugin. This is currently [discussed here](https://github.com/surge-synthesizer/surge/issues/3669#issuecomment-967062337). You'll probably have to develop or adapt [C++ architecture files](https://faustdoc.grame.fr/manual/architectures/).

**Expected outcomes:** The result will be a `faust2surge` script to compile a DSP program in a Surge plugin.

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

**Expected outcomes:** The result will be:

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

**Expected outcomes:** The result will be:

- a`faust2godot` tool to compile Faust DSP code in Godot modules

- a Godot plugin embedding the libfaust + LLVM library, and allowing DSP programs to be edited, dynamically compiled, and run in the platform

**Skills required/preferred:** C++ programming, audio and Faust programming.

**An easy, medium or hard difficulty rating of each project:** medium to hard

---

### Integration in Cables.gl [Taken in 2024]

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

**More detailed description of the project:** [Cables.gl](https://cables.gl) is a tool for creating beautiful interactive content. With an easy to navigate interface and real time visuals, it allows for rapid prototyping and fast adjustments. You are provided with a set of operators, such as mathematical functions, shapes, materials and post processing effects. Connect these to each other with virtual cables to create the experience you have in mind. Easily export your piece of work at any time. Embed it into your website or use it for any kind of creative installation. Use the [Discord channel](https://discord.com/invite/AGTarWv) to connect to their community.

The project would be to integrate the [Faust Web Audio Library](https://github.com/grame-cncm/faust2webaudio) to dynamically compile and run Faust DSP programs in Cables.gl. 

**Expected outcomes:** The result will be a Cable.gl plugin embedding the libfaust WASM library, and allowing DSP programs to be edited, dynamically compiled, and controlled with an adapted Graphical User Interface. 

**Skills required/preferred:** TypeScript/JavaScript programming, Web technologies, audio and Faust programming.

**An easy, medium or hard difficulty rating of each project:** medium

---

### PluginGuiMagic architecture 

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr) and [Daniel Walz](daniel@foleysfinest.com)

**Expected size of project:** 175 hours

**More detailed description of the project:** [PluginGuiMagic](https://foleysfinest.com/developer/pluginguimagic/) is a WYSWYG runtime design system for [JUCE](https://juce.com) plugins. The foleys_plugin_magic module allows to have a generated UI, that can be edited at runtime using advanced layout and styling options. It also adds visualisers to display signals, levels and spectral with no extra coding involved. The project is to develop new C++ [architecture files](https://faustdoc.grame.fr/manual/architectures/) to ease the use of PGM in the [faust2juce](https://github.com/grame-cncm/faust/tree/master-dev/architecture/juce) tool.
Another [faust_juce_pgm_skeleton](https://github.com/unicornsasfuel/faust_juce_pgm_skeleton) project to look at.

**Expected outcomes:** The result will be set of C++ architecture files and an improved `faust2juce` tool.

**Skills required/preferred:** C++ programming, knowledge of the JUCE framework, knowledge of the foleys_plugin_magic module, audio and Faust programming.

**An easy, medium or hard difficulty rating of each project:** medium

---

### VST plugin embedding the dynamic compiler [Taken in 2024]

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

**More detailed description of the project:** A VST plugin using the [libfaust + LLVM JIT](https://faustdoc.grame.fr/manual/embedding/) to do DSP live coding in any VST aware host. FX and monophonic or polyphonic synthesizers can be written. The source code can be edited and recompiled on the fly. The GUI has to be automatically created. The [pMix](https://github.com/olilarkin/pMix2) and [Amati](https://github.com/glocq/Amati) projects can be used as starting points. An integration with the [PluginGuiMagic](https://foleysfinest.com/developer/pluginguimagic/) architecture could possibly be added. 

**Expected outcomes:** The result will be a VST plugin developed with the [JUCE framework](https://juce.com) .

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

**Expected outcomes:** The result will be: 

- a new `faust2wwise` tool with the associated C++ architecture files to compile a DSP project in a ready to use Wwise plugin

- a plugin embedding the libfaust + LLVM JIT dynamic compiler technology to allow Faust DSP live-coding

**Skills required/preferred:** C++ programming, audio and Faust programming, knowledge of the Audiokinetic Wwise architecture.

**An easy, medium or hard difficulty rating of each project:** hard

---

### Integration in BELA

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

**More detailed description of the project:** [BELA](https://bela.io) is a maker platform for creating beautiful interaction. Designed for artists, musicians, researchers and makers, Bela brings the power of ultra-low latency interactive audio and sensors to your digital projects. A Faust/BELA integration has already been done in a `faust2bela` tool and some preliminary work on the [dynamic compilation chain](https://faustdoc.grame.fr/manual/embedding/) have [been done](https://github.com/giuliomoro/bela-faust-jit).  

**Expected outcomes:** The result will be: 

- an improved `faust2bela` tool

- a fully integrated Faust/BELA IDE that would allow to design and experiment Faust code in the Web plaform (using the dynamic WebAssembly based compilation chain), then compile it in C++ and deploy it on the BELA board. Monophonic DSP and MIDI controllable polyphonic instruments should be supported. 

- a finished dynamic compilation chain integration.

---

### Integration in openFramework

**Mentor:** [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 175 hours

**More detailed description of the project:** [openFrameworks](https://openframeworks.cc/about/) is an open source C++ toolkit designed to assist the creative process by providing a simple and intuitive framework for experimentation. It allows to access a lot of additional extensions and libraries in the form of [addons](https://ofxaddons.com). The project is to explore how Faust can be integated in the framework as an [ofxFaust](https://forum.openframeworks.cc/t/developing-a-faust-addon) addon, either statically (using the C++ generated code from a DSP program), or possibly embedding the [libfaust](https://faustdoc.grame.fr/manual/embedding/) compiler. Adapted architecture files will have to be developed.   

**Expected outcomes:** The result will be a new **ofxFaust** and openFrameworks demo examples explaining how to use it.

---

### Packaging system for Faust libraries [Taken in 2024]

**Mentors:** [Yann Orlarey](mailto:orlarey@gmail.fr) and [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 350 hours

**More detailed description of the project:** The idea is to develop a packaging system to facilitate the integration of Faust libraries in a DSP project. The inspiration comes from the [Julia](https://www.julialang.org) language with the [JuliaHub](https://juliahub.com/) project and/or the [Rust](https://www.rust-lang.org/) language with the [Cargo](https://doc.rust-lang.org/cargo/) package manager. 

#### Requirements

- load packages containing Faust sources, either in .dsp or in .lib format
- be able to load sets of files (typically a library that is written as several .lib files)
- isolate packages in different environments, to avoid name conflicts
- notion of a centralized directory on GitHub, where contributions can be made in the form of Pull Requests. Publishing tool (with search by content) of this directory, general, like **fausthub** (inspired for example by Juliahub https://juliahub.com/lp/).
- at each PR, test of the syntax of the code with GitHub actions
- cache management: typically 1) the package is loaded the 1st time and kept in a cache, 2) then the compiler uses the version in the cache. Work on the question of new version management.
- automatic generation of the documentation from the lib files (starting from the existing tools and possibly adapting them), automatic deployment
- preservation semantic: we want to be able to keep a project as a DSP file with all its needed libraries with specific version numbers   

#### Syntax proposal

##### Simple version

`package("foo")` ⇒ syntactic sugar for `library("https://faustpackages.grame.fr, "path/to/actual/library.lib")`

##### Version with constraint on version number

`package("foo", "3.4")` ⇒ syntactic sugar for `library("https://faustpackages.grame.fr, "path/to/actual/3.4/library.lib")`

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

**Mentors:** [Yann Orlarey](mailto:orlarey@gmail.fr) and [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 350 hours

**More detailed description of the project:** The objective is to develop a new approach to Faust programming, not textual or graphical, but based on DAW-like examples. This programming principle is analogue to the one described in the article [Real time Composition in Elody](https://hal.archives-ouvertes.fr/hal-02158910/document). This approach is based on the idea of manipulating and editing virtual "audio files" which represent the real time audio inputs and outputs. 

To take a simple monophonic example, let's call these two virtual audio files `INPUT` and `OUTPUT`. Let's note `t:file` the fact of placing in the DAW a file `file`at time `t` in seconds and `t:file*0.75` the fact of placing in the DAW a file at time `t` but also controlling its sound level. So the DAW construction `{0:INPUT, 1:OUTPUT*0.75}` corresponds to a realtime echo whose Faust translation is `process = + ~ (@(ma.SR):*(0.75));`. 

**Expected outcomes:** The project consists in exploring this model and see how standard DAW editing actions can be translated in Faust DSP programs. A prototype coded in TypeScript, JavaScript or any other scripting languages will be developed.

**Skills required/preferred:** C++ programming, possibly TypeScript + JavaScript or other scripting languages.

**An easy, medium or hard difficulty rating of each project:** hard

---

### Languages built on top of the signal API

**Mentors:** [Yann Orlarey](mailto:orlarey@gmail.fr) and [Stéphane Letz](mailto:letz@grame.fr)

**Expected size of project:** 350 hours

**More detailed description of the project:** The [signal API](https://faustdoc.grame.fr/tutorials/signal-api/) opens an intermediate access inside the Faust compilation chain. Generating complex expressions by directly using it can quickly become really tricky and unpracticable. So a language created on top of the signal API is usually needed. This is exactly what the Block Diagram Algebra is all about, and the entire Faust language itself.

But some other approaches can possibly be tested. The [Elementary audio language](https://www.elementary.audio) for instance is built over a [similar signal](https://docs.elementary.audio/guides/making_sound) language and uses JavaScript as the upper layer language to help create complex signal graphs programmatically. 

**Expected outcomes:** The project consits in exploring various approaches to build a language on top of the signal API. It could be a textual one (like JavaScript, Haskell or scripting languages...) or a purely graphical tool. 

**Skills required/preferred:** C++ programming, possibly TypeScript + JavaScript, Haskell or other functional languages.

**An easy, medium or hard difficulty rating of each project:** hard

---

### Developing modular synthesis using widget modulation  

**Mentors:** [Yann Orlarey](mailto:orlarey@gmail.fr) and [Stéphane Letz](mailto:letz@grame.fr)

[Widget modulation](https://faustdoc.grame.fr/manual/syntax/#widget-modulation) acts on the widgets of an existing Faust expression, but without requiring any manual modifications of the expression's code. This operation is done directly by the compiler, according to a list of target widgets and associated modulators. Target widgets are specified by their label, as used in the graphical user interface. Modulators are Faust expressions that describe how to transform the signal produced by widgets. 

The project would be to develop a set of [modular synthesizers](https://en.wikipedia.org/wiki/Modular_synthesizer), typically by choosing and adapting existing functions in the [Faust Libraries](https://faustlibraries.grame.fr), each of them with a pretty GUI, to be combined in a patch like model. The widget modulation syntax will be used to prepare the widgets to be modulable. The implementation will be done using web technologies, and in particular [FaustWasm](https://github.com/grame-cncm/faustwasm), a high-level API that wraps around Faust compiler. Here is a list of possible steps:  

- choose and adapt existing functions in the Faust Libraries and add a pretty GUI with [User Interface Primitives](https://faustdoc.grame.fr/manual/syntax/#user-interface-primitives-and-configuration) to create modules including oscillators (which generate sound), filters (which modify sound by frequency), amplifiers (which control the volume), and modulators (like LFOs and envelopes, which affect other parameters over time)

- create sequencing modules, vital for composition in modular synthesis. It allows users to create a series of notes (a sequence) that can be sent to an oscillator to produce rhythmic patterns or melodies

- define a library of modulation circuits, using the [lowest/highest](#TODO) primitives of the language, and define adapted signal mappings

- create a global GUI to rack all used modules as in [VCV Rack](https://vcvrack.com), using Web technologies, and develop the connection logic needed between all considered modules, compiled and connected as separated Faust [Web Audio](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API) nodes

**Expected size of project:** 350 hours

**Expected outcomes:** The project aims in developing new libraries for modular synthesis and a prototype Web application. 

**Skills required/preferred:** Faust programming, Web programming

**An easy, medium or hard difficulty rating of each project:** medium

---

## Past GSoC editions

### 2024: FaustNet - DDSP, Faust in Cables.gl, Amati++, a VST/CLAP Plugin embedding the dynamic compiler and Faust Package Manager

- **FaustNet - DDSP** aimed to continue the work done on adding automatic differentiation in Faust (started in a GSOC 2023 project), to leverage machine learning for audio processing tasks directly within the familiar Faust environment. It was worked on by [Advik Raj Basani](https://github.com/FloofCat) and contributed as a [Pull Request](https://github.com/hatchjaw/faust-ddsp/pull/1) on Thomas Rushton [faust-ddsp](https://github.com/hatchjaw/faust-ddsp) library. 

- **Faust in Cables.gl** aimed to develop a Cables.gl plugin that compiles Faust DSP code into a WASM AudioWorklet in real-time. It was worked on by [Fay Carsons](https://github.com/FayCarsons) and contributed as a separated [Faust Cables plugin](https://github.com/FayCarsons/Cables-Faust-Plugin) project.

 - **Amati++, a VST/CLAP Plugin embedding the dynamic compiler**, inspired by the pMix and Amati projects, this plugin has been built using the JUCE framework for the interface and libfaust with LLVM and interpreter backend API to compile Faust code. It was  worked on by [Tyler Li](https://github.com/Orisu179) and is still a [work-in-progress](https://github.com/Orisu179/AmatiPP).

- **Faust Package Manager** aimed to add a packaging system to facilitate the integration of Faust libraries in a DSP project. It was worked on by [Shehab Khaled Roshdy](https://github.com/shehab299) and a was contributed as a [Pull Request](https://github.com/grame-cncm/faust/pull/1049) that is still in test in a [master-dev-pacman](https://github.com/grame-cncm/faust/tree/master-dev-pacman) branch.

### 2023: Automatic Differentiation in the Faust Compiler and Better Faust on the Web

- **Automatic Differentiation in the Faust Compiler** aimed at adding Automatic differentiation directly in the compiler, so that gradient calculation can be carried out natively in Faust, with applications in Machine Learning algorithms. The project was worked  by [Thomas Rushton](https://github.com/hatchjaw) and completed with this [Pull Request](https://github.com/grame-cncm/faust/pull/939), and finally integrated in the Faust [master-branch](https://github.com/grame-cncm/faust/commit/681a303b8ddc9ef2e67c2cc5d5df83f27323b865). 

- **Better Faust on the Web** aimed at enhancing Faust’s support for the web platform, and was worked on by [Ian Clester](https://ijc8.me/). Transitioning the Faust web tools to a rewritten TypeScript version has been completed and deployed in updated versions of the [Faust editor](https://fausteditor.grame.fr) and [Faust playground](https://faustplayground.grame.fr) and soon in the [Faust Web IDE](https://faustide.grame.fr) with this [Pull Request](https://github.com/grame-cncm/faustide/pull/72). A Faust web component embedding the libfaust JS/WebAssembly compiler has been [developed](https://github.com/ijc8/faust-web-component) and will be used soon in the [Faust documentation](https://faustdoc.grame.fr). The development is fully detailed in this [blog post](https://ijc8.me/2023/08/27/gsoc-faust/). 

### 2022: Integration in HISE
    
Faust Integration in HISE aimed at integrating support for the Faust audio programming language into HISE, an extensive framework for the creation of sample-based virtual musical instruments. The project has been [completed](https://resonant-bytes.de/blog/gsoc-final-submission/) by [Roman Sommer](https://resonant-bytes.de/about/) with the help of [Christoph Hart](https://github.com/christophhart) as mentor, and announced [here](https://forum.hise.audio/topic/6505/faust-is-here).


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
- [Improved Linear Algebra Support](#improved-linear-algebra-support)
- [Finish the DX7 Implementation](#finish-the-dx7-implementation)
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

## Progressive Web applications for iOS and Android

Faust code can easily be distributed as self-contained Web pages containing the Faust DSP code as a statically compiled Web Audio node. The project is to improve the current model to deploy the pages as [Progressive Web applications](https://en.wikipedia.org/wiki/Progressive_web_app). The [faustwasm](https://github.com/grame-cncm/faustwasm) package will be improved to allow this new kind of deployment model. The use of [movement sensors](https://developer.mozilla.org/en-US/docs/Web/API/Sensor_APIs) will be added in the architecture to keep the same capability currently found in the native applications. Deployment on iOS and Android machines will be tested.

Done, see [faustpwa](https://faustpwa.grame.fr).

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
