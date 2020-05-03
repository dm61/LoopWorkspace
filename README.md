# Loop Simulator Running on an iPhone Simulator

This Loop workspace points to Loop and LoopKit branches customized to allow non-real-time simulation of Loop on an iPhone simulator. *The simulator Loop does not work on real iPhones and installation on a real device should never be attempted.* The simulator runs real Loop code but the simulation is significantly faster, and is based on code-customizable settings and code-customizable model-based glucose responses.

The simulation time step is set to 0.2 seconds representing 1 min of real time. The sample time for glucose data coming from a mock CGM and for dosing through a mock pump is 5 * (simulation time step) = 1 second. This corresponds to 60/0.2 = 300x faster simulation compared to standard real-time Loop operation. 

The user settings are code-customizable in `Loop/Loop/Models/SimulationSettings.swift`

The glucose-response model is code-customizable in `Loop/Loop/Models/MockHumanModel.swift`

The Loop simulator may be used to quickly gain insights into how Loop operates or responds in certain scenarios, and to peform basic checks of correctness and effectiveness of various existing or in-development features, especially Loop models and algorithms. 

**The simulator currently has significant limitations:**  
* There is no user interface for the simulator: all settings or model changes require code customization
* There is no way to pause or restart simulation
* There is no resetting mechanism: any settings or model changes require recompiling and reinstalling Loop on a *fresh* iPhone simulator (in the Simulator Hardware menu, Erase All Content and Settings brings the iPhone simulator to a fresh state)
* The `MockHumanModel` is currently just a quick hack; the model could be substantially improved in many ways
* There are no assesment tools to evaluate or compare different Loop settings, models or algorithm features
* Having an option to *not* update the Loop screens during simulation would potentially allow substantially faster simulations
* Overall code implementation could be significantly improved in many ways

# Workspace directions are the same as for the standard LoopWorkspace 

## Clone sim-test branch from dm61 LoopWorkspace repository

This repository uses git submodules to pull in the various workspace dependencies.

To clone this repo:

```
git clone --branch=sim-test --recurse-submodules https://github.com/dm61/LoopWorkspace
```

## Open

Change to the cloned directory and open the workspace in Xcode:

```
cd LoopWorkspace
xed .
```

## Build

Select the "Loop (Workspace)" scheme (not the "Loop" scheme) and Build, Run, or Test.

<a href="/docs/scheme-selection.png"><img src="/docs/scheme-selection.png?raw=true" alt="Image showing how to select the Loop (Workspace) scheme in Xcode" width="400"></a>

