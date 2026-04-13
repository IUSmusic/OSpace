# OSpace


![preview](/01.png)
![preview](/02.png)
![preview](/03.png)



**Spatial interaction system with OBoard as the typing module**

OSpace is a deployable spatial interaction system designed for calibrated physical environments. The system combines spatial anchoring, visible keyboard guidance, hand-tracked interaction, optional mirror support, and multimodal feedback.

OSpace is the system layer.

**OBoard** is the typing module inside OSpace.  
**Holo** is the keyboard interaction implementation that currently demonstrates and validates the input behavior.

- OBoard repository: https://github.com/IUSmusic/OBOARD
- Holo repository: https://github.com/IUSmusic/Holo

## Status

OSpace is currently focused on the **2D deployment of OBoard in physical space**.

At this stage, the keyboard is intentionally kept flat. The goal is to help users become comfortable with the OBoard layout, key arrangement, and interaction behavior before introducing more complex curved or volumetric geometry.

A curved or spherical keyboard may still be relevant for future AR or physical hardware paths, but it is not the primary objective of this phase.

## Purpose

The purpose of OSpace is to define and validate a complete spatial typing system that can be installed in any suitable calibrated environment, including:

- desks
- rooms
- studios
- offices
- shared installations
- dedicated interaction zones

This repository is not limited to a single room deployment. It describes a system architecture that can operate across multiple physical contexts as long as the environment can be calibrated and tracked.

## System Intent

OSpace exists to solve five system-level problems:

1. **Spatial persistence**  
   The keyboard should have a stable, remembered position in the environment.

2. **Visible placement**  
   The user should be able to see the keyboard when needed instead of relying only on memory.

3. **Reliable hand interaction**  
   Hand tracking should resolve hover, press, release, and other input states against the same keyboard model.

4. **Typing clarity**  
   The system should make it obvious which key is active, when a key is about to trigger, and when a key has committed.

5. **Progressive complexity**  
   The system should support future extensions such as curved geometry, richer spatial feedback, and hardware-assisted deployment without changing the core conceptual model.

## Relationship to OBoard

OBoard is the keyboard subsystem within OSpace.

Within this system, OBoard is responsible for:

- keyboard layout
- key geometry
- layer behavior
- typing logic
- symbol access
- spatial key organization
- visual key identity

For the current phase, OBoard is used as a **2D spatial keyboard surface**.

That means:

- the layout is spatially placed in the environment
- the user sees a flat keyboard surface
- interaction is resolved against a flat keyboard model
- mirror support reflects the same flat model
- feedback is aligned to that same model

This decision is intentional. The current challenge is not maximum spatial complexity. The current challenge is **layout adoption, typing comfort, and interaction familiarity**.

## Relationship to Holo

Holo is the current keyboard interaction reference for OSpace.

Holo contributes the following implementation direction:

- browser-based hand tracking
- gesture interpretation
- mirror-assisted feedback
- calibration and interaction tuning
- suggestion and input behavior
- mobile and desktop validation path

OSpace uses Holo as the current interaction foundation while broadening the system context beyond a single web keyboard experience.

In practical terms:

- **OBoard** defines the keyboard
- **Holo** validates interaction behavior
- **OSpace** defines the deployable system that places, shows, and operates the keyboard in physical space

## Why OBoard Is 2D in OSpace

A 2D OBoard is the correct choice for the current system phase.

Reasons:

- it is easier to learn
- it is easier to visually scan
- it reduces adaptation cost for a new layout
- it keeps targeting and confirmation more predictable
- it simplifies calibration and debugging
- it makes mirror support clearer
- it avoids introducing geometric complexity before users are comfortable with the keyboard itself

A 3D spherical or bowl-shaped version can be explored later as an optional mode. It should not be the default starting point while users are still learning the design.

## Deployment Model

OSpace is designed as a **spatially anchored visible input system**.

A deployment may include:

- a tracked physical environment
- one or more cameras for hand tracking
- an optional visual reveal layer, such as projection
- a stable keyboard anchor in physical space
- optional mirror presentation for confirmation
- sound and color-based feedback

The projection layer, when present, is only a **visual presentation layer**. It is not required to perform interaction sensing.

Interaction sensing is handled separately through tracking and input resolution.

## Core Architecture

OSpace is organized into five cooperating layers.

### 1. Spatial Layer

The spatial layer is responsible for where the keyboard exists in the environment.

Responsibilities:

- define keyboard pose
- persist placement
- restore stable location
- maintain shared coordinate consistency
- support environment-specific calibration

Key question:

**Where does the keyboard live?**

### 2. Visual Layer

The visual layer is responsible for showing the keyboard and related cues.

Responsibilities:

- render the OBoard surface
- maintain readable scale and orientation
- reveal the keyboard when needed
- support mirror mode
- display hover, pre-press, active, and committed states

Key question:

**What does the user see?**

### 3. Input Layer

The input layer is responsible for interpreting the user’s hand behavior relative to the keyboard.

Responsibilities:

- track hand and finger motion
- resolve hover candidates
- detect press intent
- handle release behavior
- suppress accidental commits from jitter
- map interaction to OBoard key zones

Key question:

**What is the user doing relative to the keyboard?**

### 4. Feedback Layer

The feedback layer is responsible for confirming system state and committed actions.

Responsibilities:

- visual confirmation
- key state change
- optional mirror reinforcement
- audio confirmation
- mode-specific feedback

Key question:

**Did the system understand the action?**

### 5. Configuration Layer

The configuration layer is responsible for deployment and tuning.

Responsibilities:

- environment calibration
- keyboard placement adjustment
- feedback preferences
- mirror visibility
- interaction thresholds
- layout-specific tuning

Key question:

**How is the system adapted to this environment and this user?**

## Interaction Model

OSpace treats typing as a staged spatial interaction sequence.

### Hover
A fingertip or pointer candidate is aligned with a key zone.

### Pre-press
The system detects likely activation intent but does not yet commit the key.

### Press
The system confirms a key event and emits the associated typing action.

### Release
The system exits the active state and prepares for the next action.

### Mirror assist
When enabled, the mirror presents a confirmation-oriented view of the current keyboard state to reduce ambiguity and improve confidence.

This staged model improves clarity, reduces accidental triggers, and makes non-contact input more understandable.

## Feedback Model

OSpace does not depend on direct physical haptics in the current phase.

Primary feedback channels:

- **visual feedback**
  - hover indication
  - active key state
  - committed key confirmation
  - mode and layer state

- **audio feedback**
  - key click confirmation
  - special key differentiation
  - warnings or invalid actions
  - mode transitions

- **mirror feedback**
  - optional assistive confirmation layer
  - especially useful when direct viewing angle is less ideal

This keeps the system lightweight while preserving interaction confidence.

## Technical Scope of the Current Phase

Current scope:

- deployable spatial system framing
- visible 2D OBoard presentation
- hand-tracked keyboard interaction
- optional mirror support
- layout familiarity and learnability
- interaction stability and clarity
- environment calibration concepts
- integration path with Holo interaction logic

Out of scope for the current phase:

- default curved keyboard geometry
- volumetric or spherical key surfaces
- hardware thermal feedback
- pressure-based tactile hardware
- production-grade AR immersion
- full physical appliance implementation

## Design Principles

OSpace follows these principles.

### System first
OSpace is the system. OBoard is one subsystem within it.

### Learnability before complexity
Users should first become comfortable with the keyboard layout before more advanced geometry is introduced.

### Shared model consistency
Spatial placement, visible rendering, and input resolution should all reference the same keyboard model.

### Visibility reduces cognitive load
The system should show the keyboard when needed so the user does not have to rely entirely on memory.

### Feedback must be immediate and legible
Non-contact typing depends on crisp feedback to feel trustworthy.

### Extensibility matters
The architecture should support future hardware or AR paths without requiring the keyboard concept to be redefined.

## Example System Configuration

A practical OSpace deployment can be described as:

- a calibrated physical environment
- a persistent keyboard anchor
- camera-based hand tracking
- visible 2D OBoard presentation
- optional mirror view
- sound and color feedback
- Holo-derived interaction logic

This configuration is sufficient to validate comfort with the OBoard layout before moving toward more complex spatial forms.

## Related Repositories

### OBoard
OBoard is the keyboard design and layout module used by OSpace.

Repository: https://github.com/IUSmusic/OBOARD

### Holo
Holo is the interaction-oriented keyboard project that currently validates hand tracking, gesture handling, mirror feedback, calibration, and typing flow.

Repository: https://github.com/IUSmusic/Holo

## Roadmap

Planned and possible next steps include:

- stronger environment calibration
- optional multi-camera tracking setups
- richer mirror presentation modes
- deployment profiles for different physical spaces
- deeper onboarding for new users
- optional curved OBoard mode
- comparison testing between flat and curved OBoard variants
- tighter integration between OBoard design changes and Holo interaction logic

## Summary

OSpace is a **spatial interaction system**.

It uses **OBoard** as the typing module and **Holo** as the current interaction foundation.

For the current phase, OSpace intentionally keeps OBoard **2D**. This allows the system to focus on the most important immediate goals:

- keyboard familiarity
- layout comfort
- interaction stability
- visible guidance
- deployment clarity

The long-term system may support more advanced spatial geometry. The current system is designed to make the keyboard understandable, usable, and learnable first.

# NOTICE

## OSpace

OSpace is a spatial interaction system.

Within OSpace:

- **OBoard** is the typing module
- **Holo** is the current interaction reference for keyboard behavior, calibration, mirror support, and hand-tracked input validation

## Related Repositories

- **OBoard**  
  https://github.com/IUSmusic/OBOARD

- **Holo**  
  https://github.com/IUSmusic/Holo

## Repository Relationship

This repository defines the **system layer**.

It may reference, integrate with, or conceptually build upon:

- the OBoard keyboard design and layout system
- the Holo interaction implementation and validation path

These repositories remain distinct projects.

## Rights and Licensing Relationship

Unless expressly stated otherwise in a specific file, the contents of this repository are governed by the license provided with this repository.

References to OBoard or Holo do **not** transfer ownership of those repositories or broaden the rights granted under their own license terms.

If any material originating from OBoard, Holo, or another repository is incorporated, copied, embedded, adapted, or redistributed in this repository, that material remains subject to its own applicable copyright notices, license terms, and restrictions in addition to any terms that apply here.

## Third-Party Materials

This project may depend on, interoperate with, or describe third-party technologies, runtimes, APIs, tools, trademarks, platforms, or services.

Examples may include:

- browser APIs
- hand-tracking runtimes
- projection technologies
- calibration and sensing pipelines
- platform-specific frameworks
- vendor names and product names used for descriptive reference

All third-party names, marks, technologies, and materials remain the property of their respective owners.

Use of third-party components, if any, remains subject to their own license terms, attribution requirements, and usage policies.

## Attribution Guidance

When referencing OSpace in technical discussion, evaluation, demonstrations, or research contexts, attribution should distinguish between:

- **OSpace** as the spatial interaction system
- **OBoard** as the keyboard module
- **Holo** as the current interaction implementation reference

This distinction should be preserved in documentation, presentations, public discussion, and derivative analysis.

## No Additional Grant

This NOTICE file is provided for attribution, repository relationship clarity, and rights consistency.

It does not grant any right, license, patent permission, trademark permission, or commercialization right beyond what is explicitly granted in the repository license.

