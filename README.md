# openmc-plasma-source

This python-based package offers a collection of pre-built [OpenMC](https://github.com/openmc-dev/openmc) neutron sources for fusion applications.

## Installation

OpenMC is required to use this package.

To install openmc-plasma-source, simply run:
```
pip install openmc-plasma-source
```

## Usage

### Tokamak Source

Create a source with a spatial and temperature distribution of a tokamak plasma.
The OpenMC sources are ring sources which reduces the computational cost and the settings.xml file size.

The equations implemented here are taken from [this paper](https://doi.org/10.1016/j.fusengdes.2012.02.025).

```python
from openmc_plasma_source import TokamakSource

my_source = TokamakSource(
    elongation=1.557,
    ion_density_centre=1.09e20,
    ion_density_peaking_factor=1,
    ion_density_pedestal=1.09e20,
    ion_density_separatrix=3e19,
    ion_temperature_centre=45.9,
    ion_temperature_peaking_factor=8.06,
    ion_temperature_pedestal=6.09,
    ion_temperature_separatrix=0.1,
    major_radius=9.06,
    minor_radius=2.92258,
    pedestal_radius=0.8 * 2.92258,
    mode="H",
    shafranov_factor=0.44789,
    triangularity=0.270,
    ion_temperature_beta=6
  )
```

For a more complete example check out the [example script](https://github.com/fusion-energy/openmc-plasma-source/blob/better_readme/examples/tokamak_source_example.py).

![out](https://user-images.githubusercontent.com/40028739/135100022-330aa51c-e2a2-401c-9738-90f3e99c84d4.png)
 ![out](https://user-images.githubusercontent.com/40028739/135098576-a94709ef-96b4-4b8d-8fa0-76a201b6c5d2.png)

### Ring Source


Create a ring source with temperature distribution of a 2000eV plasma.

```python
my_plasma = FusionRingSource(
    start_angle = 0.,
    stop_angle = 6.28318530718,  # input is in radians
    temperature = 20000.,  # ion temperature in eV
    fuel='DT'
)
```
### Point Source

Create a point source with temperature distribution of a 2000eV plasma.


```python
my_plasma = FusionPointSource(
    coordinate = (0, 0, 0),
    temperature = 20000.,  # ion temperature in eV
    fuel = 'DT'
)
```