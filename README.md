# PurpleNight

![PurpleNightDesktop](https://user-images.githubusercontent.com/88662373/133921749-6410c698-f3fd-4d3e-b084-9250c7cedebb.png)

Dock : Plank

### **Prerequisites**

* Git set up in you computer
* Basic know-how of linux(prevents confusion)

## **Set Up**

### **Preperation**

1. Clone repo into a directory of your choice 
    * If you're new to all this then create a directory for you cloned repositories(or put in the downloads folder)
    * The directory you are in before cloning the repo(in the terminal) is the directory where the repository clones 
    * so for the sake of this tutorial move into the downloads folder `cd /Downloads/`
    * Then use `git clone <link>` the link to this repo is under 'code'(It's a green button next to about)

1. Install conky-all (available in system repositories)
   * **BONUS TIP**(for apt package manager)
   * To check whether a package is available in the official repo use `apt search <keywords>`

1. Install all the fonts included, I recomend using a font manager for faster installs in the future

1. Create a new directory called **.conky** at `$HOME or ~/` (aliases for /home/username/)

1. Create a new folder in ~/.conky (say purplenight) and copy the conkyrc files(both) and the conkystart.sh into it

If you have been following along, you should now have the following
* **PurpleNight** that you cloned in a directory of your choice
* The included **fonts** (EarthOrbiter, UnitedKingdom and Library3am) installed 
* A **~/.conky/purplenight** directory with .conkyrc21, .conkyrc22, .conkyrc23 and conkystart.sh  

### **Configuration**

#### **conkyrc files**

Now we edit the conkyrc files
   1. Change the **minimum_size**, **maximum_width**, **maximum_height** values to match you screen size
   1. Change the **<network_name>** in the code to match your network name.
      
      You can find you network name by using `ip link show`
   
   1. You will find pieces of code resembling `${font <font_name>:size=8}` with no variables or text after them.
      - When I was messing around I found that the size you put in said code can change the size of the spaces between lines in the conky. 
      - So if you need things from different conkys to align when they are already as close as possible, just change the size of the spaces on one of the conkyrc files
   1. Save files(obviously)

Now that you have modified the conkyrc files, we need a script do the work of starting conkys for us
 
#### **Startup script**
  
The conkystart.sh will play the role of the start up script. It should look like so
  
```
#!/usr/bin/bash 
sleep 1 
conky -q -c /home/username/.conky/purplenight/.conkyrc21 & 
conky -q -c /home/username/.conky/purplenight/.conkyrc22 & 
conky -q -c /home/username/.conky/purplenight/.conkyrc23 & exit
```
* line 1 is the shebang, it tells the computer where to look for the shell
    * To find yours use `which shell` if it's not the same then replace `/usr/bin/bash` with it 

* line 2 defines the delay before executing the following code  
    * `sleep 1` as in delay for 1 second 
* lines 3, 4 and 5 have the commands that will start the conky
    * `conky -q -c` (conky start it, -q and -c are flags telling it to run in quiet mode and to get config file from the given location)
    * Change path to the configuration files based on where you put them
    * `&` tells it to move to the next command and `exit` tells it to close itself

Now run the startup script like so `bash <path to startup.sh>` and make changes in the conkyrc's as you see fit

Now search for program that manages your startup applications and add a new program, and in the write `bash <location to conkystart.sh>` in the place for command.

You should be done by now.

## Thank you for visiting
