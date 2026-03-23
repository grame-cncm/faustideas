# GSoC 2026 Proposal: Web-Based UI System for Faust

## Project Description

Faust currently generates automatic UI backends but lacks a modern, fully web-based patch UI system comparable to Cmajor's patch GUI model. This project will create a standardized Web UI layer for Faust DSP modules, enabling rich, interactive graphical interfaces directly in browsers using HTML, CSS, JavaScript/TypeScript, WebAudio API, and WebAssembly.

The solution builds on Faust's existing JSON format (which describes DSP inputs/outputs, metadata, and UI elements like sliders/bargraphs) and extends it with web-specific layout and interaction metadata inspired by Cmajor's .cmajorpatch format. This will allow Faust-compiled DSP modules to expose real-time controllable parameters through a reference Web UI implementation compatible with Progressive Web Apps (PWAs) and online demos.

**Key Features:**
- Dynamic UI generation from enhanced Faust JSON
- Real-time parameter control via WebAudio AudioWorklet
- Resizable, responsive web interfaces with standard web components
- Cross-browser compatibility (Chrome, Firefox, Safari)

## Technical Solution and Methodology

### Phase 1: Faust Web UI Specification (Weeks 1-2)
- Extend Faust JSON with web UI properties: layout groups, scale factors, component types (sliders, buttons, XY pads), CSS classes
- Define bidirectional messaging protocol (JSON over postMessage) between UI and AudioWorklet
- Create JSON schema and validation tools

### Phase 2: UI Generator Backend (Weeks 3-4)
- Faust architecture file to export enhanced JSON + WASM DSP module
- TypeScript library to parse JSON and generate HTML/CSS/JS using web components (lit-html or similar)
- Template system for common Faust UI elements (horizontal sliders, vertical meters, toggles)

### Phase 3: Real-Time DSP/UI Integration (Weeks 5-7)
- Compile Faust DSP to WebAssembly via Emscripten
- AudioWorklet implementation for low-latency processing (<5ms)
- Parameter binding: UI controls ↔ AudioParam automation for glitch-free updates
- Touch/mouse/keyboard input handling with debouncing

### Phase 4: Demos and Integration (Weeks 8-10)
- 3-5 demo PWAs: synthesizer, guitar effects, drum machine
- PWA manifest generation, service worker caching
- Documentation and Faust example integration

### Phase 5: Polish and Testing (Weeks 11-12)
- Cross-browser testing, performance optimization
- Upstream PRs to Faust repo
- Comprehensive documentation and tutorial

**Deliverables:**
- Faust Web UI specification document
- TypeScript reference implementation library
- 5 demo applications
- Integration tests and documentation

## Schedule

| Period | Objectives | Milestones |
|--------|------------|------------|
| **Community Bonding (April)** | Finalize spec with mentors, prototype JSON parsing | Spec PR submitted |
| **Weeks 1-2 (May)** | Specification + basic JSON parser | JSON → static HTML demo |
| **Weeks 3-4** | UI generator + basic AudioWorklet | One working slider control |
| **Weeks 5-6** | Full bidirectional controls | **Midterm: 2 interactive demos** |
| **Weeks 7-8** | Advanced UI (groups, XY pads, bargraphs) | 3 complete demos |
| **Weeks 9-10** | PWA integration, service workers | 5 demos + docs |
| **Weeks 11-12 (Aug)** | Testing, optimization, PRs | **Final submission** |

**Total: 175 hours** (30-35 hrs/week during coding period May-August 2026)

## Personal Data

**Name:** Rahul Bhati  
**Affiliation:** Freelance Full-Stack Developer  
**Location:** Jaipur, Rajasthan, India  
**Contact:** rb083380@gmail.com | linkedin.com/in/rahul-bhati-25482a1a0 | github.com/Rahul-Bhati  

### Education
- **B.Tech Computer Science** - Bikaner Technical University (2019-2023)
- **WEB3 Cohort** - Harkirat Singh (Aug 2024-Present): Blockchain, DApps, DeFi, DevOps
- LeetCode: 210+ problems solved
- TechGig Global Semi-Finalist (Rank 2493/300k coders)

### Key Open Source Contributions
- [Starknet Documentation Fix](https://github.com/lfglabs-dev/docs.starknet.id/pull/120) - Improved developer guides
- [Q4 Builder Pre-Course](https://github.com/Rahul-Bhati/Q4-Builder-Pre-Course/pull/1) - UI bug fixes
- [TeamShiksha Join Process](https://github.com/TeamShiksha/join/pull/79) - Enhanced onboarding
- [Code100x CMS](https://github.com/code100x/cms/pull/1485) - Feature improvements

**Full GitHub:** [github.com/Rahul-Bhati](https://github.com/Rahul-Bhati)

### Technical Skills
**Languages:** JavaScript/TypeScript (expert), HTML/CSS, React, Node.js  
**Frameworks:** React/Next.js/React Native, Express.js, Tailwind CSS  
**Tools:** WebSockets, Zustand/Redux, Expo, Vercel/Netlify, Git/GitHub  
**Relevant Experience:** Real-time apps (WhatsApp-like chat), animations (Framer Motion), PWAs, WebAssembly (Solana/Rust exposure)

### Programming Preferences
- **Paradigm:** Functional-reactive (React hooks, state management)
- **Stack:** TypeScript + Next.js + Tailwind + Vercel (rapid prototyping)
- **Workflow:** Modular monorepos, Git collaboration, test-driven development
- **Experience:** Full-stack solo projects + open source + hackathon teams

**Availability:** Fully available full-time during GSoC (no conflicts)

### Post-Program Commitment
- Maintain Web UI library and demos
- Contribute additional Faust web examples
- Explore Tone.js integration and Web MIDI support
- Mentor future GSoC applicants

### Interests and Goals
**Faust Focus:** Hacker mindset with strong web development skills; excited about DSP + WebAudio + WASM convergence  
**Long-term:** Lead web3 audio projects or join audio tech organizations like GRAME  

**LLM Usage:** Used only for spellcheck and grammar polish. All technical content, project understanding, and personal experience written in my own words.

***

**Signature:** Rahul Bhati  
**Date:** March 23, 2026  
**GitHub:** Rahul-Bhati

