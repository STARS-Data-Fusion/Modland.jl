# Modland.jl

MODIS/VIIRS Sinusoidal Land Tile Utilities for Julia
<!-- 
Gregory H. Halverson (they/them)<br>
[gregory.h.halverson@jpl.nasa.gov](mailto:gregory.h.halverson@jpl.nasa.gov)<br>
Lead developer and designer<br>
NASA Jet Propulsion Laboratory
-->
## Overview

This Julia module provides functions for converting geographic latitude and longitude coordinates to sinusoidal projection coordinates and mapping those to MODIS land tile indices.

## Installation

Ensure that you have the required dependencies installed before using this module. You may need to install libraries such as `ArchGDAL.jl` for coordinate transformations.

## Usage

### `latlon_to_sinusoidal`

Converts latitude and longitude coordinates to sinusoidal projection coordinates.

```julia
latlon_to_sinusoidal(lat::Float64, lon::Float64)::Tuple{Float64, Float64}
```

#### **Arguments**

- `lat::Float64`: Latitude in degrees (-90 to 90).
- `lon::Float64`: Longitude in degrees (-180 to 180).

#### **Returns**

- `Tuple{Float64, Float64}`: Sinusoidal projection coordinates `(x, y)`.

#### **Example**

```julia
x, y = latlon_to_sinusoidal(34.0, -118.0)
println("Sinusoidal Coordinates: ($x, $y)")
```

#### **Error Handling**

- Raises an error if latitude is out of range (-90 to 90).
- Raises an error if longitude is out of range (-180 to 180).

---

### `sinusoidal_to_modland`

Converts sinusoidal projection coordinates to MODIS land tile indices.

```julia
sinusoidal_to_modland(x::Float64, y::Float64)::String
```

#### **Arguments**

- `x::Float64`: Sinusoidal x coordinate.
- `y::Float64`: Sinusoidal y coordinate.

#### **Returns**

- `String`: MODIS land tile index formatted as `hXXvYY`.

#### **Example**

```julia
tile_index = sinusoidal_to_modland(x, y)
println("MODIS Tile Index: $tile_index")
```

#### **Error Handling**

- Raises an error if `x` is outside the valid bounds.
- Raises an error if `y` is outside the valid bounds.
