# pysolorie

[![Quality Checks](https://github.com/aaghamohammadi/pysolorie/actions/workflows/quality_checks.yml/badge.svg?branch=main)](https://github.com/aaghamohammadi/pysolorie/actions/workflows/quality_checks.yml)
[![Publish](https://github.com/aaghamohammadi/pysolorie/actions/workflows/publish.yml/badge.svg?branch=main)](https://github.com/aaghamohammadi/pysolorie/actions/workflows/publish.yml)
[![CodeQL](https://github.com/aaghamohammadi/pysolorie/actions/workflows/github-code-scanning/codeql/badge.svg?branch=main)](https://github.com/aaghamohammadi/pysolorie/actions/workflows/github-code-scanning/codeql)
![GitHub License](https://img.shields.io/github/license/aaghamohammadi/pysolorie)
![PyPI - Downloads](https://img.shields.io/pypi/dm/pysolorie)
[![Documentation Status](https://readthedocs.org/projects/pysolorie/badge/?version=latest)](https://pysolorie.readthedocs.io/en/latest/?badge=latest)
![PyPI - Version](https://img.shields.io/pypi/v/pysolorie)
![PyPI - Format](https://img.shields.io/pypi/format/pysolorie)
![PyPI - Status](https://img.shields.io/pypi/status/pysolorie)
[![codecov](https://codecov.io/gh/aaghamohammadi/pysolorie/graph/badge.svg?token=TF9E8Y3Q67)](https://codecov.io/gh/aaghamohammadi/pysolorie)
![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)
![code style: black](https://img.shields.io/badge/code%20style-black-black)

[![SonarCloud](https://sonarcloud.io/images/project_badges/sonarcloud-white.svg)](https://sonarcloud.io/summary/new_code?id=aaghamohammadi_pysolorie)



**pysolorie** stands for **Py**thon **Sol**ar **Orie**ntation Analysis of Solar Panel. It is a Python library designed to help you analyze the orientation of solar panels.

<img src="docs/_static/images/solar_panel.svg" width="600">

How can one maximize the solar irradiation energy received by a solar panel?


## Features

``pysolorie`` is a library designed to help you find this optimal orientation. Its features include, but are not limited to:

- Finding the optimal tilt angle for a fixed solar panel, assuming a clear-sky condition.
- Plotting the optimal tilt angle over a range of days.
- Plotting the daily direct irradiation energy over a range of days.
- Generating a CSV, JSON, or XML report detailing the optimal tilt angle over a range of days.
- Calculating the sunrise and sunset hour angles for a specific day.
- Utilizing Hottel's model to quantify clear-sky conditions and estimate the atmospheric transmission of clear-sky beam radiation.
- Calculating the solar zenith angle.
- Calculating the solar time.
- Calculating solar declination and hour angle.

# How to Install pysolorie

``pysolorie`` requires Python 3.9 or higher.

The easiest way to install ``pysolorie`` is from PyPI.

```bash
python3 -m pip install pysolorie
```


## Example Usage
With the pysolorie package, you can plot the optimal orientation of a solar panel given the climate type, altitude, and latitude of the location. For instance, the following code plots the optimal orientation for each day of the year for the city of Tehran. For more examples, please refer to the [Getting started](https://pysolorie.readthedocs.io/en/latest/getting_started.html) section of our documentation. The full [API Reference](https://pysolorie.readthedocs.io/en/latest/reference/modules.html) is also available on our website.

```python
from pathlib import Path
from pysolorie import IrradiationCalculator, Plotter

# Instantiate a Plotter object from the pysolorie library
plotter = Plotter()

# Instantiate an IrradiationCalculator object for the city of Tehran
irradiation_calculator = IrradiationCalculator(
    climate_type="MIDLATITUDE SUMMER",
    observer_altitude=1200,
    observer_latitude=35.6892
)


# Use the plotter to plot the optimal orientation of a solar panel for each day of the year
plotter.plot_optimal_orientation(
    irradiation_calculator,
    from_day=1,
    to_day=365,
    path=Path("results.svg"),
    plot_kwargs={
        "xlabel": "Day",
        "ylabel": "Beta (degrees)",
        "title": "Optimal Solar Panel Orientation",
    },
    savefig_kwargs={"dpi": 300},
)
```

This figure, generated by the example code, illustrates the optimal orientation of a solar panel for each day of the year in Tehran. The x-axis represents the day of the year, while the y-axis represents the optimal angle (Beta) in degrees. As can be seen, the optimal angle varies throughout the year, highlighting the importance of adjusting the orientation of the solar panel to maximize the energy received.

<img src="docs/_static/images/example_usage.svg" width="600">

## Documentation

You can find the complete documentation for pysolorie at our [Read the Docs page](https://pysolorie.readthedocs.io/).

## Contributing

We welcome contributions to pysolorie! If you're interested in contributing, please take a look at our [contribution guidelines](https://pysolorie.readthedocs.io/en/latest/contributing.html) for detailed information on how you can help.

Thank you for considering contributing to pysolorie!
