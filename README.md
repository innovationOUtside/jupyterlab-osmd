# jupyterlab_osmd

First attempt at JupyterLab mime renderer for MusicXML (`.muscixml` / mime type `application/vnd.recordare.musicxml` ) using [OpenSheetMusicDisplay](https://github.com/opensheetmusicdisplay/opensheetmusicdisplay/)

*Works a bit...*

![](images/screenshot.png)

`pip install jupyterlab-osmd`

Double click on a `.musicxml` file in the JupyterLab file browser and it should render using OSMD.

Python API:

```python
# Minimally
def OSMD(data=''):
    bundle = {}
    bundle['application/vnd.recordare.musicxml'] = data
    display(bundle, raw=True)

# A far more elaborate version available as:
#from jupyterlab_osmd import OSMD
# This supports:
# - MusicXML string
# - path to .musicxml or compressed .mxl file
# - URL to musicxml file

with open("Downloads/xmlsamples/Telemann.musicxml", 'r') as f:
    d = f.read()

OSMD(d)
```

## Requirements

- JupyterLab >= 4.0.0

## Install

To install the extension, execute:

```bash
pip install jupyterlab_osmd
```

## Uninstall

To remove the extension, execute:

```bash
pip uninstall jupyterlab_osmd
```

## Contributing

### Development install

Note: You will need NodeJS to build the extension package.

The `jlpm` command is JupyterLab's pinned version of
[yarn](https://yarnpkg.com/) that is installed with JupyterLab. You may use
`yarn` or `npm` in lieu of `jlpm` below.

```bash
# Clone the repo to your local environment
# Change directory to the jupyterlab_osmd directory
# Install package in development mode
pip install -e "."
# Install required node packages
npm install --save opensheetmusicdisplay uuid
# Install package requirements
jlpm install 
# Rebuild extension Typescript source after making changes
jlpm build
```

Build package:

`python -m build .`

### Packaging the extension

Push to PyPi: e.g. `twine upload dist/*0.1.2*`

