
# MaSIV neuriteTracer
This is a plugin that provides manual neurite tracing capabilities to [MaSIV](https://github.com/alexanderbrown/masiv), the MATLAB-based large image viewer.  


### How to install?
Ensure your ``external_plugins`` preference in ``masivPrefs.yml`` contains a valid directory into which you will install plugins. This directory should be *outside* of the MaSIV install directory. For example, your preferences file might contain:

```
externalPluginsDirs: {~/.masiv_plugins}
```

Which means external plugins will be housed in in a hidden directory (hence the `.`) called `.masiv_plugins` that is located in your home directory (hence the `~`). Create the external plugins directory if does not already exist. 

To install the neurite tracer plugin run:

```
masiv_plugin.install('https://github.com/raacampbell/neuriteTracer')
```

Note that it's the web url (*not the Git URL*) you are entering. 
Follow the instructions. 
Now you can update the plugin separately from MaSIV. 
To update the plugin, you feed its directory into the update function:

``masiv_plugin.update('~/.masiv_plugins/neuriteTracer')``


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
