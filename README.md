# carrion-baggage

An Eclipse project allowing us to edit our ontology in TopBraid Composer.

## Setup

*You should only need to perform these steps once. After that, goodbye GitHub for Mac!*

### Install Git

  * Help > Install New Software... 
  * Install dialog:
    * "Work with:" drop-down menu: Select latest Eclipse update site (currently Kepler)
    * May take a moment for available software to load
    * Expand "Collaboration" software group and check the box next to "Eclipse Git Team Provider"
  * Click [Next] and follow the instructions to complete installation.
  
  See also: <http://www.topquadrant.com/products/installing-git-in-topbraid-composer/>

### Import CV project from GitHub

  * File > Import... > Git > Projects from Git > [Next] > Clone URI > [Next]
  * "Source Git Repository" dialog box
    * In "URI:" textbox, enter: https://github.com/HiinEnkelte/carrion-baggage
    * Under "Authentication", enter your GitHub username and password
    * Click checkbox: "Store in Secure Store" and enter secure-store password when prompted (any password is OK; you can use your GitHub password, which isn't terribly secure but probably doesn't matter)
    * "Branch Selection": master is pre-selected; click [Next]
    * "Local Destination": default is $HOME/git/carrion-baggage; that's OK; click [Next]
    * [Finish]
    
* * *

## Working on the project

### Open the ontology

  * In "Navigator" pane (bottom left), expand CVProject
  * Click twice on cv.rdf
  
### Saving: takes a looong time!

  * File > Save
  * On my machine, this can take about 6 minutes! Screen goes blank, hard drive whirs.
  * Don't interrupt if at all possible.
  * Signs of an interrupted save:
    * Keep an eye on the numbers in the "Classes" pane (top left)
    * If these numbers suddenly change drastically, the file got truncated
    * As of now (5/6/15), Resource and Thing are at about 50K each
    
### Edit the ontology

*Hoping we'll flesh this section out over time.*

* * *

## Git operations

### Pull down changes

*Do this before every editing session!*

  * Right-click on CVProject in Navigator pane (bottom left)
  * Team > Pull

### Commit changes

*Do this after every editing session!*

#### First, create patch to capture your changes

*This is an extra step, but makes it way easier to fix conflicts.*

  * Right-click on CVProject in Navigator pane (bottom left)
  * Team > Create Patch...
     * Click "Workspace" radio button and "Browse"
     * In "File name:" text box, enter <yourinitials>-<YYYYMMDD>.patch, e.g. kk-20150506.patch
       * For subsequent edits in a single day, add a number: e.g. kk-20150506-1.patch
     * Click "Finish"

#### Commit and push

  * If you've made local changes, the project and changed files will have a ">" before them
  * Right-click on CVProject
  * Team > Commit...
  * "Commit Changes" dialog:
    * Enter commit message (short, but descriptive)
    * Modified files will be selected in bottom window; your .patch file will not
    * Click "Commit and Push" (left button)! *(not just "Commit", the right button)*

#### In case of conflicts, commit your .patch file instead

When I created a conflict, I got a message in a pop-up window called
"Push Results", saying my push had been "[rejected -
non-fast-forward]".

  * Right-click on CVProject
  * Team > Commit...
  * In the "Commit changes" dialog:
    * Enter "conflict" in the commit message
    * Select your .patch file in the bottom window
    * Click "Commit and Push"
    * Email me
    * **DON'T PULL** until changes are resolved!
    * If you want to keep editing, just create and commit more patch files

### Back out changes before commit

If the save fails (see below), or if you made changes and then changed your mind, here's how to back them out:

  * Right-click on CVProject in Navigator pane
  * Team > Reset...
  * "Reset" dialog: under "Reset type", select "Hard" radio button, click "Reset"
  * "Confirm" dialog appears about overwriting changes you've made to working directory; click "Yes"
  * If you've got the ontology open, close it (click the X next to the filename in the middle top pane)
  * File > Refresh (or F5)
  * Open (or re-open) the ontology
