# pynative: Simple CLI for native-land.ca API

![](https://tokei.rs/b1/github/samapriya/pynative?category=code)
![](https://tokei.rs/b1/github/samapriya/pynative?category=files)
![PyPI - License](https://img.shields.io/pypi/l/pynative)
![PyPI - Downloads](https://img.shields.io/pypi/dm/pynative)
![PyPI](https://img.shields.io/pypi/v/pynative)
[![CI pynative](https://github.com/samapriya/pynative/actions/workflows/main.yml/badge.svg)](https://github.com/samapriya/pynative/actions/workflows/main.yml)



## Table of contents
* [Installation](#installation)
* [Getting started](#getting-started)
* [pynative Simple CLI for Native Land API](#pynative-simple-cli-for-native-land-api)
    * [pynative fetch](#pynative-fetch)
    * [pynative location](#pynative-location)
    * [pynative place](#pynative-place)

## Installation
This assumes that you have native python & pip installed in your system, you can test this by going to the terminal (or windows command prompt) and trying

```python``` and then ```pip list```

**pynative only support Python v3.4 or higher**

To install **pynative: Simple CLI for Native Land API** you can install using two methods.

```pip install pynative```

or you can also try

```
git clone https://github.com/samapriya/pynative.git
cd pynative
python setup.py install
```
For Linux use sudo or try ```pip install pynative --user```.

I recommend installation within a virtual environment. Find more information on [creating virtual environments here](https://docs.python.org/3/library/venv.html).

## Getting started

As usual, to print help:

```
pynative -h
usage: pynative [-h] {fetch,location,place} ...

Simple CLI for Native Land API

positional arguments:
  {fetch,location,place}
    fetch               Download most updated map and type as GeoJSON file
    location            Search using lat long pair location for data and
                        download as GeoJSON file
    place               Search using a place name or address and download as
                        GeoJSON file

optional arguments:
  -h, --help            show this help message and exit
```

To obtain help for specific functionality, simply call it with _help_ switch, e.g.: `pynative location -h`. If you didn't install pynative, then you can run it just by going to *pynative* directory and running `python pynative.py [arguments go here]`

## pynative Simple CLI for Native Land API
The tool is designed to interact with the [Native-Land](https://native-land.ca/) API. All of these APIs are open and function without authentication.

## Native Land Disclaimer
This map does not represent or intend to represent official or legal boundaries of any Indigenous nations. To learn about definitive boundaries, contact the nations in question. Also, this map is not perfect -- it is a work in progress with tons of contributions from the community. Please send us fixes if you find errors. If you would like to read more about the ideas behind Native Land or where we are going, check out the blog. You can also see the roadmap. Also something to keep in mind

* Native Land is not meant to be vetted at the level of an academic resource
* Native Land is aimed at settlers to engage them with Indigenous history in a fun, interactive, and subtle way
The datasets are always in flux and the latest datasets can be downloaded using their API

#### Suggested Citation

```
(dataset) Native Land Territories map. (2021). Native Land CA. https://native-land.ca/. Accessed 2021-09-24.
```

### pynative fetch
This allows you to fetch the latest version of territories, language and treaties layers. It tries to fetch this from the dynamic data link and if that fails uses the maps endpoints to fetch this. It requires the map type and the full path to a GeoJSON file where the output will be exported

```
usage: pynative fetch [-h] --mtype MTYPE --path PATH

optional arguments:
  -h, --help     show this help message and exit

Required named arguments.:
  --mtype MTYPE  Map type territories|languages|treaties
  --path PATH    Full path to map.geojson
```

Example usage:

```
pynative fetch --mtype territories --path "full path to file.geojson"
```


### pynative location
This is a more custom fetch for the dataset which allows you to fetch a subset of the overall maps based on the lat long location. The tool requires a comma seperate latitude,longitude and full path to a GeoJSON file.

```
pynative location -h
usage: pynative location [-h] --ll ... --mtype MTYPE --path PATH

optional arguments:
  -h, --help     show this help message and exit

Required named arguments.:
  --ll ...       Comma seperated latitude,longitude
  --mtype MTYPE  Map type territories|languages|treaties
  --path PATH    Full path to map.geojson
```

Example usage:

```
pynative location --mtype languages --path "full path to map.geojson" --ll 40.6938609,-89.5891008
```

### pynative place
This is an extension of the location tool , it can convert an address into a lat long pair and thallows you to fetch a subset of the overall maps based on the lat long location based on whether or not datasets are available for that location. The tool requires an address and makes use of the Open Street map API to get the lat long pair and full path to a GeoJSON file.

```
pynative place -h
usage: pynative place [-h] --addr ADDR --mtype MTYPE --path PATH

optional arguments:
  -h, --help     show this help message and exit

Required named arguments.:
  --addr ADDR    Comma seperate place name or address
  --mtype MTYPE  Map type territories|languages|treaties
  --path PATH    Full path to map.geojson
```

Example usage

```
pynative place --addr "Raleigh,NC" --mtype territories --path "Full path to file.geojson"
```

## changelog

#### v0.0.3
- added disclaimer for Native Land and citation recommendation
- general improvements

#### v0.0.2
- added improvements overall to all tools
- added place tool search for location using address
- extended functionality to fetch and convert to GeoJSON object
- general improvements
