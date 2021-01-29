# OneEuroBlueprint
One Euro Noise Filter in UE4.26 Blueprint for Vive Trackers. White paper (https://cristal.univ-lille.fr/~casiez/1euro/) By Géry Casiez

# Thank You:
Greg Corson for the Vive Puck model, Aiden Wilson on how to use LivelinkXR plugin 


# Prereqs
1. Enable LiveLinkXR Plugin
2. Add Preprocessor --> Transform Axis Switch --> set Orientation Axis Z --> X, X --> Z

# Check Demo Map, OR:

# Setup Unfiltered Tracker
1. add "Tracker_Unfiltered" to the scene. the coordinate will be your SteamVR Root
  a. Change "Tracker To Use" parameter to your Tracker/controller's Livelink ID
2. add "TrackerOffsetter_Unfiltered to the scene. 
  a. select your Tracker_Unfiltered Actor as "Parent"
  b. expand "Offset" and adjust offset as you wish. 
  c. uncheck "Guide Visible" to hide the offset guide
  d. select any Actor as "Child" ( Cine Camera, BP Camera, plane, lightsaber, mesh, etc).

# Setup Filtered Tracker
1. Add 3 "OneEurObj" to the scene. you need 3 objects for each Tracker_Filtered actor
2. add "Tracker_Filtered" to the scene.
  a. select EU X, EU Y , EU Z parameter as each of the OneEurObj actors
  b. you can play around with mincutoff, rate, and beta for stabilization ( i dont see much change, i might have bad default or global variable issue, but the default value works OK). 
  
  According to the paper:
  "Note that parameters fcmin and beta have clear conceptual relationships: if high speed lag is a problem, increase beta; if slow speed jitter is a problem, decrease fcmin."
  
3. add "TrackerOffsetter_Filtered"
  a. select your Tracker_filtered actor as Parent. 
  b. Offset, Child, and Guide Visible works like before
  
