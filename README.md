# neuriteTracer
MaSIV neurite tracer plugin

## What is it?
This is a plugin that provides manual neurite tracing capabilities to MaSIV, the MATLAB-based large image viewer.  


## How to install?
Ensure you ``external_plugins`` preference in ``masivPrefs.yml`` contains a valid directory into which you will install plugins. This directory should be *outside* of the MaSIV install directory. This way you can more easily upgrade MaSIV in the future. For example, you preferences file might contain:

``
externalPluginsDirs: {~/.masiv_plugins}
``

Then run:

``masiv_plugin.update('~/.masiv_plugins/neuriteTracer')``


## FAQ
Q: After installing I get an error indicating that a neuriteTracer preference can not be found. 
<br >
A: Close the tracer GUI. Remove the neuriteTracer section from the preferences YML. Restart the tracer plugin. 