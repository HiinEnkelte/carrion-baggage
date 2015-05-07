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

*Hope we'll flesh this section out over time.*

* * *

## Git operations

### Pull down changes

*Do this before every editing session!*

  * Right-click on CVProject in Navigator pane (bottom left)
  * Team > Pull

### Commit changes

*Do this after every editing session!*

  * If you've made local changes, the project and changed files will have a ">" before them
  * Right-click on CVProject in Navigator pane (bottom left)
  * Team > Commit...
  * "Commit Changes" dialog:
    * Enter commit message (short, but descriptive)
    * Click "Commit and Push" (left button)! *(not just "Commit", the right button)*

### Back out changes before commit

If the save fails (see below), or if you made changes and then changed your mind, here's how to back them out:

  * Right-click on CVProject in Navigator pane
  * Team > Reset...
  * "Reset" dialog: under "Reset type", select "Hard" radio button, click "Reset"
  * "Confirm" dialog appears about overwriting changes you've made to working directory; click "Yes"
  * If you've got the ontology open, close it (click the X next to the filename in the middle top pane)
  * File > Refresh (or F5)
  * Open (or re-open) the ontology
  
### Conflicts

OK, when I tried to create a conflict, the message I got, in a pop-up window called "Push Results", said my push had been "[rejected - non-fast-forward]".

Anyway, if a push fails, email me and we'll work it out. My changes are (or should be) programmatic, so I can re-do them without much effort.

Email me and we'll work it out. My changes are (or should be) programmatic, so I can re-do them without much effort.
