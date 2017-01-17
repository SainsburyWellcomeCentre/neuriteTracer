
# MaSIV neuriteTracer
This is a plugin that provides manual neurite tracing capabilities to [MaSIV](https://github.com/alexanderbrown/masiv), the MATLAB-based large image viewer.  


### How to install?
It is best to use the MaSIV plugin installer since in future MaSIV will check plugins installed this way for updates.
You an also use Git and manually search for updates if you wish. 
In both cases you will first need to ensure that MaSIV has an external plugins directory defined:

* The ``external_plugins`` preference in ``masivPrefs.yml`` should contain a valid directory into which you will install plugins. 
* This directory should be *outside* of the MaSIV install directory. e.g. in your home directory. 
* Edit the preferences file and create the directory if necessary. 

If using the plugin manager, in MATLAB run:

```
masiv.pluginManager.install('https://github.com/raacampbell/neuriteTracer')
```

Note that it's the web url (*not the Git URL*) you are entering. 
Follow the on-screen instructions. 
Now you can update the plugin separately from MaSIV. 
To update the plugin, you feed its directory into the update function:

```
masiv.pluginManager.update('~/.masiv_plugins/neuriteTracer')
```

If you are using Git, simply clone neuriteTracer into your external plugins directory as normal. 



### Usage instructions
Start the plugin and left-click on the image to place the first point (node). 
This point is the "root" node. 
Each traced tree has only one root node.
Root nodes may have one or more "child" nodes, which are connected descendant nodes. 
By definition, a root node can not be a child of another node so root nodes have no "parent" nodes. 
Nodes with no children are known as "leaves".

The root node will be highlighted in red. 
The next point that you click will be connected to the root node and red highlight marker will move from the root node to the most recently placed node. 
Thus, the red highlight indicates which node will be the parent of the next node that is laid down. 
The red-highlighted growth marker can be moved to a different node by holding down `alt` and mousing over other nodes in the current image depth. 
Nodes in the current images depth are highlighted by white dots. 
You may also label the current node using the GUI panel (e.g. see the "neurite type" and "termination" panels).

Navigation through the image is by the standard MaSIV WASD and arrow key system. 
You may also use the mouse wheel to change layers and ctrl+wheel will zoom.


### Removing nodes and branches
* Switch to `delete` mode in the GUI (or press `ctrl-d`).
* Clicking will remove the node nearest to the mouse cursor.
* To remove all nodes downstream of particular node, press `shift` + `ctrl` and click.
* The tree is auto-saved before this operation is performed and the location of the auto-save printed to screen. 


### Changing the parent of a node
You can change the parent of a node in the event of a mistake during tacing
* Switch to `add` mode in the GUI (or press `ctrl-a`).
* Select the node you wish to reassign by holding down `alt` and moving the red marker to that node.
* Now `shift` + `ctrl` + click on the node you want to be the new parent of this selected node.
* The operation is automatically aborted if performing it will destroy the integrity of the tree 
   (e.g. you can't turn a node's child into its parent).
* The tree is auto-saved before the parent change this operation is performed and the location of the auto-save printed to screen. 
* Currently this procedure only works for nodes within the same trace (the same tree)


### Keyboard shortcuts:
* `ctrl+a` - switch to add mode
* `ctrl+d` - switch to delete mode
* `r`      - go to layer that contains the root node
* `l`      - go to next leaf
* `k`      - go to previous leaf
* `n`      - move highlight to parent node and centre
* `m`      - move highlight to first child node and centre
* `j`      - searches forward along the tree to the nearest branch point and centres on this
* `h`      - searches backwards (towards soma) to the nearest branch point and centres on this


### Dependencies
neuriteTracer requires [matlab-tree](https://github.com/raacampbell/matlab-tree.git). 

### FAQ
Q: After installing I get an error indicating that a neuriteTracer preference can not be found. 
<br >
A: Close the tracer GUI. Remove the neuriteTracer section from the preferences YML. Restart the tracer plugin. 
