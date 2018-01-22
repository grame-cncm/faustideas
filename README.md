# Faust ideas

This repository hosts the "TODO/ideas list" for the [Faust programming 
language](http://faust.grame.fr).

## Conventions

* Items are placed at the bottom of the file and separated by `---`. 
* Items can have a person associated to them by declaring `* Currently 
addressed by: xxx`. If no-one is currently working on the item, replace 
`xxx` by `nill`. 
* Items are ordered by priority and are also listed in the [List](#list) 
section below. 
* Items can be commented by adding subsections, pictures, etc. 

## List

* [Improve the Faust Website](#improve-the-faust-website)
* [Move Library Documentation to the Libraries Repo and Try to Automate Doc Generation on the GH-pages Branch](#move-library-documentation)
* [Rewrite the Faust Documentation in Markdown ](#rewrite-the-faust-documentation-in-markdown)
* [Implement Jonathan Abel's Modal Reverb](implement-jonathan-abels-modal-reverb)
* [Improved UI Declarations](#improved-ui-declarations)
* [TensorFlow Support](#tensorflow-support)
* [Improved Linear Algebra Support](#improved-linear-algebra-support)
* [Finish the DX7 Implementation](#finish-the-dx7-implementation)
* [Trigonometric simplifications](#trigonometric-simplifications)
* [WebAssembly specific optimisations](#webassembly-optimisations)
* [Testing tools on the Web]](#testing-tools)

---

## Improve the Faust Website

* Currently addressed by: Romain

There's lots of work to do here, in particular:

* Improve the doc (see [corresponding item](#rewrite-the-faust-documentation-in-markdown))
* Add tutorials structured in a clear way (not as news posts)
* Make things more obvious
* Improve the overall design/theme, the new Faust logo should be more visible
* Highlight the web editor: make it a central component of the website

---

## Move Library Documentation to the Libraries Repo and Try to Automate Doc Generation on the GH-pages Branch

* Currently addressed by: nill

Just do it...

---

## Rewrite the Faust Documentation in Markdown 

* Currently addressed by: Romain

The main reason for doing this is to be able to have a portable html version
of the documentation. This is very important as having a doc in this format
will allow for a better listing by web search engines. Obviously, this will
imply some compromises and be a fair amount of work but it is really worth it.

---

## Implement Jonathan Abel's Modal Reverb

* Currently addressed by: Romain and Yann

This should be done as part of the Longyou grottoes project. The "final goal"
would be to create an interactive website where users can process the sound of
their microphone to apply the acoustics of this ancient space. Modal reverb
would allow to interpolate between IRs and change some of the parameters of
the space in real-time. It'd be nice if this could be reproducible so we need
to think about a way to nicely generate these reverbs from an impulse response.
This tool could be similar to `mesh2faust` or could come as part of a toolkit
in matlab/octave/pyhton, etc.  

---

## Improved UI Declarations

* Currently addressed by: Romain and Yann

Essentially allow for specific UI elements to have metadatas associated to them
outside of their declaration. As part of that, we want to implement a system
to further customize UI elements. 

### Potential Implementation

Several approaches are being considered to further customize UI elements. The 
first one would consist of being able to declare a "CSS" allowing for the use
of CSS code. Another approach (more generic and not limited to the web) would
allow for the declaration of UI-specific metadata inspired by CSS. 

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

Of course, it would still be possible to declare metadatas within the UI
declaration (this system would be fully backward compatible). Internally,
we'd have to parse the metadata and create a corpus of supported CSS metadatas
knowing that interfaces would be based on a specific kind of layout (e.g.,
grid layout). Once again, another option would be to allow to specify "pure
CSS" giving access to all the CSS features without having to do some 
reformatting. 

---

## TensorFlow Support

* Currently addressed by: Tim O'Brien

Be able to generate TensorFlow code with Faust.

---

## Improved Linear Algebra Support

* Currently addressed by: nill

Linear algebra operations are currently poorly supported in Faust. Having a
way to conveniently express matrices would improvement. As part of that,
linear algebra/matrix operations (e.g., inversion, multiplication, determinant,
etc.) primitives could be added to the language.

### Potential Implementation

Matrices could be expressed using the Faust-multirate `vectorize` primitives
by creating vectors of vectors.

It would be interesting to try to implement matrix operations from scratch in 
Faust. Although it might be hard and not so optimized, thus a more pragmatic
solution would be to implement them as primitives. That would be a fair amount
of work as this would imply that the corresponding code for each language
supported by Faust would have to be supported. 

---

## Finish the DX7 Implementation

Essentially, finish `dx7.lib`. It might be worth looking at these elements to
make this happen:

* <https://webaudiomodules.org/demos/wasm/dx7.html>
* <https://github.com/everythingwillbetakenaway/DX7-Supercollider>

---

## Trigonometric simplifications

* Currently addressed by: nill (suggested by [Pierre Leconte](https://github.com/grame-cncm/faust/issues/59))

For some applications, trigonometric functions (spherical harmonics) are used, and depending on the algorithm, the output formula could be very complicated. However, in a lot of cases, trigonometric identities could help to simplify drastically the expressions.

---

## WebAssembly specific optimisations

* Currently addressed by: Stéphane and Yann

To run as fast as possible and approch native code performances as much as possible, WebAssembly code requires some specific optimisations, like: memory access (index precomputation as much as possible...), delay lines handling, struck/stack variable access...etc. We have started an informal collaboration with Mozilla engineers (Benjamin Bouvier) to work on this subject.

---

## Testing tools on the Web

* Currently addressed by: nill

Faust distribution already contains some testing tools, like `faust2plot` or `faust2octave`. It would be great to have them running in a Web page (or some extension of the same idea). For signal generators/processors, several output formats (oscilloscope, spectrogramme...), and for processors several calibrated input signals (dirac impulse, ramp, sinusoides..) would be available.



