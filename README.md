# piffle
Python library for generating and parsing [IIIF Image API](http://iiif.io/api/image/2.1/) URLs in an
object-oriented, pythonic fashion.

[![Build Status](https://travis-ci.org/emory-lits-labs/piffle.svg?branch=develop)](https://travis-ci.org/emory-lits-labs/piffle)
[![Coverage Status](https://coveralls.io/repos/github/emory-lits-labs/piffle/badge.svg?branch=develop)](https://coveralls.io/github/emory-lits-labs/piffle?branch=develop)
[![Code Health](https://landscape.io/github/emory-lits-labs/piffle/develop/landscape.svg?style=flat)](https://landscape.io/github/emory-lits-labs/piffle/develop)

## Installation and example use:

`pip install piffle`

Example use for generating an IIIF image url:

```
>>> from piffle.iiif import IIIFImageClient
>>> myimg = IIIFImageClient('http://image.server/path/', 'myimgid')
>>> print myimg
http://image.server/path/myimgid/full/full/0/default.jpg
>>> print myimg.info()
http://image.server/path/myimgid/info.json"
>>> print myimg.size(width=120).format('png')
http://image.server/path/myimgid/full/120,/0/default.png
```

Example use for parsing an IIIF image url:

```
>>> from piffle.iiif import IIIFImageClient
>>> myimg = IIIFImageClient.init_from_url('http://www.example.org/image-service/abcd1234/full/full/0/default.jpg')
>>> print myimg
http://www.example.org/image-service/abcd1234/full/full/0/default.jpg
>>> print myimg.info()
http://www.example.org/image-service/abcd1234/info.json
>>> myimg.as_dict()['size']['full']
True
>>> myimg.as_dict()['size']['exact']
False
>>> myimg.as_dict()['rotation']['degrees']
0.0
```

## Development and Testing

This project uses [git-flow](https://github.com/nvie/gitflow) branching conventions.

Install locally for development (the use of virtualenv is recommended):

`pip install -e .`

Install test dependencies:

`pip install -e ".[test]"`

Run unit tests: `py.test` or `python setup.py test`

## Publishing

To upload a tagged release to [PyPI](https://pypi.python.org/pypi) with
a [wheel](http://pythonwheels.com/) package:

  `python setup.py sdist bdist_wheel upload`
