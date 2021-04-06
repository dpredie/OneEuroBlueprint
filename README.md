# New to V2.1: 1EF
1EF noise filter now works as a Blueprint Component, no need for complicated object filtering. 

see demo "1EF" map for setup. 

# Prerequisite for Vive Tracker
- Enable LiveLinkXR Plugin
- Add Preprocessor --> Transform Axis Switch --> set Orientation Axis Z --> X, X --> Z

# Prerequisite for Realsense T265 Tracker
- kougaku's RealSense OSC sender .exe ( https://github.com/kougaku/RealSenseOSC )
- for 4.25 - Epic's OSC Plugin
- for 4.26 - monsieurgustaf's OSC plugin ( Epic's 4.26 OSC do not work with this sender, you have to recompile this plugin https://github.com/monsieurgustav/UE4-OSC )


# Options
- separate cutoff and beta for Location and Rotation
- Button to Reinitialize after you update the parameters ( calls constructor )
- disable and enable filter checkbox

# 1EF BP Component 
You can use this Component in your own blueprint to get 1EF filtering, check ViveTracker_1EF or T265_OSC_1EF as sample implementation

# Thank You:
Greg Corson for the Vive Puck model, help in analyzing stabilization. Aiden Wilson on how to use LivelinkXR plugin 


# DEPRECATED: OneEuroBlueprint V1.0
One Euro Noise Filter in UE4.26 Blueprint for Vive Trackers. White paper (https://cristal.univ-lille.fr/~casiez/1euro/) By Géry Casiez

# Setup Unfiltered Tracker
1. add "Tracker_Unfiltered" to the scene. the coordinate will be your SteamVR Root
  a. Change "Tracker To Use" parameter to your Tracker/controller's Livelink ID
2. add "TrackerOffsetter_Unfiltered to the scene. 
  a. select your Tracker_Unfiltered Actor as "Parent"
  b. expand "Offset" and adjust offset as you wish. 
  c. uncheck "Guide Visible" to hide the offset guide
  d. select any Actor as "Child" ( Cine Camera, BP Camera, plane, lightsaber, mesh, etc).

# Setup Filtered Tracker
1. Add 6 "OneEurObj" to the scene. you need 6 objects for each Tracker_Filtered actor
2. add "Tracker_Filtered" to the scene.
  a. select EU X, EU Y , EU Z, EU XRoll, EU YPitch, EU ZYaw parameter as each of the OneEurObj actors
  b. you can play around with mincutoff, rate, and beta for stabilization ( i dont see much change, i might have bad default or global variable issue, but the default value works OK). 
  
  According to the paper:
  "Note that parameters fcmin and beta have clear conceptual relationships: if high speed lag is a problem, increase beta; if slow speed jitter is a problem, decrease fcmin."
  
3. add "TrackerOffsetter_Filtered"
  a. select your Tracker_filtered actor as Parent. 
  b. Offset, Child, and Guide Visible works like before
  

