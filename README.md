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
  * Click the person icon on the top right to see human-readable labels
  
### Saving: takes a looong time!

  * File > Save
  * On my machine, this can take about 6 minutes! Screen goes blank, hard drive whirs.
  * Don't interrupt if at all possible.
  * Signs of an interrupted save:
    * Keep an eye on the numbers in the "Classes" pane (top left)
    * If these numbers suddenly change drastically, the file got truncated
    * As of now (5/6/15), Resource and Thing are at about 50K each
    
### Edit the ontology

*Hope we'll **flush** this section out over time.*

#### Find a single entity

  * "Text Search" tab, rightmost on bottom middle pane
  * "Search string (regex):" text pane

#### Stored queries with arguments

##### Find composer/work combo

  * Model > Run SPARQL Query from SPIN Template...
  * Select "owl:FilterComposerWorks" from list
  * Enter text (or regexes) to match composer / work name, e.g. Haydn / Divertimento
    * Be sure to hit Enter in each text box; it will remind you if you don't
  * Results show up on "SPIN Template Results" tab, bottom right - can be maximized

##### Order composer's works

  * Model > Run SPARQL Query from SPIN Template ...
  * Select "owl:SortComposerWorksByID"
  * Enter text (or regexes) to match composer's name
    * Be sure to hit Enter in text box
  * Results show up on "SPIN Template Results" tab, bottom right - can be maximized

#### Stored queries without arguments

##### Query Library

*If you know SQL, this will give you post-traumatic flashbacks.*

  * SPARQL tab: bottom middle, left of "Text Search" tab
  * I stored a couple of cruft-detecting queries
    * works not in MusicBrainz
    * composers without works
  * How to see saved queries:
    * double-click on spin:query in "Properties" tab, middle right, main window
    * saved queries appear at bottom of Property form in the middle
  * How to run saved queries:
     * In "Query Library" tab, click checkbox next to query and hit green arrow icon above it
  * How to save queries:
    * complete query in Query Editor
    * click twice on spin:query property in Properties pane
    * select push-pin icon above Query Editor to attach query to spin:query property

##### Query Editor

  * Nifty features (esp. as compared to Protege):
    * Knows ontology-defined prefixes
    * Syntax highlighting
    * Error correction
    * Auto-completion: ctrl-space

* * *

## Git operations

### Pull down changes

*Do this before every editing session!*

  * Right-click on CVProject in Navigator pane (bottom left)
  * Team > Pull

### Back out changes without committing

If a save fails (see above), or if you made changes and then changed your mind, here's how to back them out:

  * Right-click on CVProject in Navigator pane
  * Team > Reset...
  * "Reset" dialog: under "Reset type", select "Hard" radio button, click "Reset"
  * "Confirm" dialog appears about overwriting changes you've made to working directory; click "Yes"
  * If you've got the ontology open, close it (click the X next to the filename in the middle top pane)
  * File > Refresh (or F5)
  * Open (or re-open) the ontology

### Commit changes

*Do this after every editing session!*

#### 1. Create patch file

*This is an extra step, but makes it easier to fix conflicts.*

  * Right-click on CVProject in Navigator pane (bottom left)
  * Team > Create Patch...
     * Click "Workspace" radio button and "Browse"
     * In "File name:" text box, enter `yourinitials-YYYYMMDD.patch`, e.g. kk-20150506.patch
       * For subsequent edits on the same day, add a number: e.g. kk-20150506-1.patch
     * Click "Finish"

#### 2. Commit and push modified files

  * If you've made local changes, the project and changed files will have a ">" before them
  * Right-click on CVProject
  * Team > Commit...
  * "Commit Changes" dialog:
    * Enter commit message (short, but descriptive)
    * Modified files will be selected in bottom window; your .patch file will not
    * Click "Commit and Push" (left button)! *(not just "Commit", the right button)*

#### 3. If there's a conflict, commit patch file(s) instead

When I created a conflict, I got a message in a pop-up window called
"Push Results", saying my push had been "[rejected - non-fast-forward]".
If this happens:

  * Right-click on CVProject
  * Team > Commit...
  * In the "Commit changes" dialog:
    * Enter "conflict" in the commit message
    * Select your .patch file in the bottom window
    * Click "Commit and Push"
    * Email me
    * If you want to keep editing, create and commit more patch files
    * **DON'T PULL** until I tell you the conflicts have been resolved!

*Jean, ignore this part:*

  * COMMAND-LINE FU
    * `git reset --hard HEAD^`   (undo last commit)
    * `git reset --hard HEAD~2` (last two commits)
    * without the --hard argument, undoes commits but not changes
    * This and other gems at: <http://sethrobertson.github.io/GitFixUm/fixup.html#remove_last>

#### 4. If no conflict, you can delete your patch file(s)

*You don't have to delete them, but they'll clutter up your workspace.*

 * Right-click on patch file in Navigator pane
 * Delete
 * OK
