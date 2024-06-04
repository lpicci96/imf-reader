[![PyPI](https://img.shields.io/pypi/v/imf-reader.svg)](https://pypi.org/project/imf-reader/)
[![Documentation Status](https://readthedocs.org/projects/imf-reader/badge/?version=latest)](https://imf-reader.readthedocs.io/en/latest/?badge=latest)


# imf-reader

A package to access IMF data. For the moment this package only supports access to the World Economic Outlook (WEO) database.
Support for other IMF data and databases may be added in the future.

## Installation

```bash
$ pip install imf-reader
```

## Usage

This package has very basic functionality only to retrieve WEO data as a pandas DataFrame. 
To use it, import the `weo` module and call the `fetch_data` function.

```python
from imf_reader import weo

df = weo.fetch_data()
print(df)

```

By default, the function will return the WEO data for the latest year available.
You can specify a version by passing the month and year of the version you want to retrieve.
NOTE: The WEO reports are released in April and October of each year. The month of the version must 
be either "April" or "October".

```python
df = weo.fetch_data(version=("April", 2020))
```

Caching is used to avoid multiple requests to the IMF website for the same data and to enhance performance. 
Caching using the LRU (Least Recently Used) algorithm approach and stores data in RAM. The cache is cleared when the program is terminated.
To clear the cache manually, use the `clear_cache` function.

```python
weo.clear_cache()
```


For more advanced usage and tools for WEO data please use the [weo-reader package](https://github.com/epogrebnyak/weo-reader).


## Contributing

Interested in contributing? Check out the contributing guidelines. Please note that this project is released with a Code of Conduct. By contributing to this project, you agree to abide by its terms.

## License

`imf-reader` was created by Luca Picci. It is licensed under the terms of the MIT license.

## Credits

`imf-reader` was created with [`cookiecutter`](https://cookiecutter.readthedocs.io/en/latest/) and the `py-pkgs-cookiecutter` [template](https://github.com/py-pkgs/py-pkgs-cookiecutter).
