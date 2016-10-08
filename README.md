# neuriteTracer
MaSIV neurite tracer plugin

## What is it?
This is a plugin that provides manual neurite tracing capabilities to MaSIV, the MATLAB-based large image viewer.  


## How to install?
Ensure your ``external_plugins`` preference in ``masivPrefs.yml`` contains a valid directory into which you will install plugins. This directory should be *outside* of the MaSIV install directory. For example, your preferences file might contain:

``
externalPluginsDirs: {~/.masiv_plugins}
``

To install the neurite tracer plugin run:

```
masiv_plugin.install('https://github.com/raacampbell/neuriteTracer')
```

Note that it's the web url (not the Git URL) you are entering. Follow the instructions. Now you can update the plugin separately from MaSIV. To update the plugin, you feed its directory into the update function:

``masiv_plugin.update('~/.masiv_plugins/neuriteTracer')``


## FAQ
Q: After installing I get an error indicating that a neuriteTracer preference can not be found. 
<br >
A: Close the tracer GUI. Remove the neuriteTracer section from the preferences YML. Restart the tracer plugin. 
