# ros-astrobee
#### A Docker Image and run scripts for NASA's Astrobee Robot Software
(Astrobee source code available at https://github.com/nasa/astrobee/tree/972b78b6651e87a634f7ae99a3b12aea860053f1)

## Instructions to get started with a prebuilt Astrobee sim:
 
Install docker for your OS and check with `docker version`
*(If running on a Windows 10 host, start your Docker desktop.)*

Clone this repo and `cd` into it:
```
git clone https://github.com/tammerb/ros-astrobee.git
cd ros-astrobee/
```

### Pull the Docker image
Pull the pre-built Docker image (*note: the compressed image is 1.7GB and 6GB once extracted*):
```
docker pull thbarkouki/astrobee:built
```

Check that the pull was successful with the `docker images` command.

### Run the Simulator (*testing* a script that runs on Windows 10, Linux, and Mac OS):
Run the simulator with:
```
./run.sh
```
*Depending on your OS, you may see some `... command not found` errors. You can ignore these.*

A browser tab should automatically open at http://localhost:8080/vnc_auto.html. If not, manually enter this address into your browser.
See below for **Flying Astrobee** instructions. Once you're done, close the browsers tab, exit the terminal you're controlling the Astrobee from with `exit`, and stop and remove both containers with `docker-compose down` in the original terminal you started in.

#### Running on a Linux host:
Run the simulator with
```
./rununix.sh
```
*Note: If you get a "Got permission denied while trying to connect to the Docker daemon socket..." error, execute the script with `sudo`*
```
sudo ./rununix.sh
```

#### Running on a Windows host (tested with git for Windows: https://gitforwindows.org/):
Same as above for linux but run the following script instead:
```
./runwin.sh
```

### Flying Astrobee: TELEOP
In a new terminal from the one you launched the sim from, enter (aka attach to) the docker container and source the ros commands with:
```
docker attach astrobee_sim_container
source /root/freeflyer_build/native/devel/setup.bash
```
Now you should be able to "tele-operate" the astrobee using the teleop instructions available from the original Astrobee repo here:
https://github.com/nasa/astrobee/blob/972b78b6651e87a634f7ae99a3b12aea860053f1/management/executive/teleop_tool.md

#### *For testing only:* To install the sim and start the containers, but not launch the sim (this will also do the `pull` step above if not already done):
Run `install.sh`. This will start both the astrobee and noVNC containers, but will not launch the sim. You can open a second terminal and attach to the sim container by running `docker attach astrobee_sim_container`. You can then edit and launch the sim from inside. Exit the container with `exit`, and stop and remove both containers with `docker-compose down`.

## Instructions to build an astrobee simulator:
*coming soon*
