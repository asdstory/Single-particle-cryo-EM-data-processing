# Example - Processing PnuC_3NR data_20190429, totally 102 images

# Step01 - Import images (motion corrected by MotionCorr2)

Input files: *_sum_DW.mrc

Node type: 2D micrographs/tomograms(*.mrc)

# Step02 - CTF estimation

#I/O

Spherical aberration (mm): 2.7
Voltage (kV): 300 # Because this dataset was collected on Titan Krios, Building 13, under low mag (13kx)
Amplitude contrast: 0.1
Magnified pixel size (Angstrom): 1.08
Amount of astigmastism (A): 100

#Searches

Use as default

#CTFFIND-4.1

Use CTFFIND-4.1? Yes

#Step03 - Particle Picking using GAutomatch

[user@biowulf]$ sinteractive --gres=gpu:k80:1 --mem=20g -c14
[user@biowulf]$ module load gautomatch
[user@cn3144 ~]$ gautomatch --apixM 1.06 --diameter 80 *_sum_DW.mrc 

# Step04 - Import particle files generated by GAutomatch

Input files: *_automatch.star
Node type: 2D/3D particle coordinates (*.box, *_pick.star)

# Step05 - Extract Particles

#Extract

Particle box size (pix): 200


# Step06 - 2D classificaiton

# CTF

Do CTF-correction? Yes
Ignore CTFs until first peak? Yes

# Optimization

Number of classes: 100
Mask diameter (A): 180

#2D classification results showed good alignment, but still, the class distribution of each 2D projection was very low, ~5%. However, by combining all the good particles, there were still ~50% among all the particles picked.

# Further optimization - 1 Optimize the box size and Mask diameter
#I changed the box size to 180, Mask diameter to 160, redo the Particle extraction and 2D classification, see if this will make 2D alignment results much better.

#Try 1: 
Particle box size (pix): 180
Mask diameter (A): 160

#Results: 
1. Particles aligned much better than before, best class has 6% distribution.

#Try 2: 
Particle box size (pix): 170
Mask diameter (A): 150


# Further optimization - 2 Select some templates from last 2D classification, and do template-based particle picking again, using RELION-Autopick.


