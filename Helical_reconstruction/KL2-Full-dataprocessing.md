Data Processing on Tao Mac:

# Step01 - ssh to biowulf
## Open your terminal on Mac, and type:
- [ ] ssh -Y dout2@biowulf.nih.gov
- [ ] Password: Ty2020$$
# Step02 - Start a new interactive node
## When successfully login to biowulf, type:
- [ ] sinteractive --cpus-per-task=16 --mem-per-cpu=2g --gres=lscratch:200 --time=12:00:00
* This is to start an interactive node, so that you can see the GUI of RELION for picking particles
# Step03 - cd to your data file
## When succeeded to a new node, type
- [ ] cd /data/dout2/20200130Krios_KL2
# Step04 - Load and start RELION software
## Type:
- [ ] module load RELION
- [ ] relion& 

# Step05 - Start mannual picking particles
## When you see relion GUI, left click 019:MannualPick/job019, and click Continue on the right, start picking particles.

* To be noted, remember to right click and save STAR coordinates file when finished mannual picking. 
