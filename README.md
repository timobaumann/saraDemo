# Sara Demonstrations over Time

This repository contains submodules and setup instructions for replicating 
previous demos of SARA. The main idea is not to collect the code here, but to 
collect information on how to re-run SARA demos that used particular (moving) 
modules (such as NLG-output evolving over times or by domain).

## The SARA@InMind-Retreat Demo
* date and purpose: 2017-04-28, GHC 6501, demonstration to Yahoo and to CMU-InMind colleagues
* short description: the demo does movie recommendation and combines three 
InMind projects (social reasoning, NLU&dialog management, movie recommendation)

### Modules involved:

#### JeroMQAndroid
The Android client that we used. 

#### MUF
The multi user framework (MUF) is the "main part" of the server, 
the IP of the computer running this must be given in the UI of JeroMQAndroid. 
This module performs: 
* orchestration of the system backend
* passing incoming data to NLU/DM and conversational classifier
* passing the conversational classification to the rapport estimator
* social reasoner modifies the DM system intent according to estimated rapport.
* pass on the NLG result to BEAT for annotation (and from there to display).
This likes to run on (Florian's) Windows PC.

#### NLU-DM
Yulun's dialog management component. This can live on an AWS instance -- 
of course the MUF server must know the IP where this lives.

#### MISSING: movie recommendation (still missing)
Rose's movie recommendation component, usually also lives on AWS. 
The DM module must know where this lives.

#### MISSING: Conversational Classifier

#### MISSING: Rapport Estimator
we have a working executable on a Macbook running Windows. 
We need to ask Michael about the source and how it's to be built.
The rapport estimator is running under the virtual human toolkit (VHT).
The module must be informed about the address of the computer running MUF 
to connect (because that also runs the VHT server).

#### BEAT
Beat is the generation component and turns text into visual behaviors. 
This likes to run on (Yoichi's) Macbook.

#### Unity
The unity module displays the character on the screen. 
This module runs on MacOS (preferably or mandatorily?).
This includes lip-synching which is done within this module (no external TTS required).
This likes to run on (Yoichi's) Macbook.

#### MISSING: Visualization "Under the Hood"
Or maybe that is contained in the Unity project?

### Modules indirectly involved:

#### OpenFace (not used)
We dropped OpenFace from the demo. This repository has small adaptations 
as compared to the original version (rotation of video by 90° and optimization 
for online processing).

#### OpenFaceQualifier (not used directly)
Likewise dropped from the demo. This is the main repository for the 
OpenFaceQualifier from which some classes were copied and extended 
into the MUF (but aren't used there in the demo setup).

### What else is needed?
The Virtual Human Toolkit must be installed (or we need the library, or something to that effect).

### MISSING: 
* Rose's movie recommendation (code + data) in one or two repositories
* Rose said she'd document her data interchange formats (beyond "it's json")

