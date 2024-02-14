---
layout: page
title: Teaching
comments: false
carbonads: false
---

## Syllabi

### Introduction to Astronomy
* **Overview: Historical Importance and Present-day Relevance**
* **Thought Experiment: Using Astronomy Knowledge to Survive on a Deserted Island**
  - Celestial Navigation
  - Timekeeping
  - Harvesting Resources in Sync with Cycles and Seasons
* **Electromagnetic Spectrum**
* **Interaction of Light and Matter**
  - Light as a Wave and Particle
  - Key Concepts: Reflection, Refraction, and Diffraction
  - Absorption and Emission
  - Scattering, Interference, and Polarization
* **Mapping the Sky**
* **The Sun**
  - Structure
  - SOHO (Solar and Heliospheric Observatory)
* **Stars**
  - Color of Stars
  - Spectral Types
  - Failed Stars: Brown Dwarfs
  - Formation and Evolution Models
  - Stellar Atmosphere Models
* **Solar System: In-situ Observations**
  - Mars Curiosity and Perseverance Rovers
  - Juno Mission to Jupiter
  - Cassini Mission to Saturn
  - New Horizon Mission to Pluto
  - Voyager Space Probe Missions to Interstellar Space
* **Earth: Looking Up and Looking Down**
  - Earth Observation: Copernicus Program
  - Living, Breathing World: Multiyear Timelapse
* **Planets**
  - Structure: Core, Atmosphere
  - Formation: N-body using REBOUND
  - Evolution: Radius, Atmosphere, Orbit
* **Exoplanets**
  - Detection
  - Statistics
  - Surprising Discoveries
* **Black Holes, Neutron Stars, and Gravitational Waves**
* **Milky Way**
* **Galaxy: Structure, Formation, and Evolution using galpy**
* **Cosmology**
  - Structure: Flat, Curved, Open, or Closed?
  - Composition: Matter, Dark Matter, Dark Energy
  - Formation: Cosmic Microwave Radiation and the Big Bang
  - Evolution: Hubble's Experiment and the Expanding Universe

### Astronomical Observation and Data Analysis
* **Atmospheric Windows: In which wavelengths best to observe what target?**
  - Blackbody Radiation
  - Earth's Atmosphere
* **Science Goals: What and Why to Observe**
* **Planning: How to Observe the Target**
  - Ground-based and Space-based Observations
  - Observing Constraints
    - Where is it? Coordinates
    - Is it observable tonight? Rising and Setting Times
    - North and South Hemisphere
    - Weather: Cloud, Humidity, Turbulence
    - Moon
    - Satellites Trails
  - Signal-to-Noise
    - Exposure Time
    - Filters
* **Engineering: Science vs Cost**
  - Telescope Design and Operation
    - Tracking and Auto-guiding
  - Instrumentation
    - From Analog to Digital: Photographic Plates and CCD
    - Pixel Sensitivity
    - Pixel Scale
    - Field-of-View
    - Total Telescope-Instrument Throughput
* **Data Reduction with Astropy**
  - Dark Current: Dark Frame Subtraction
  - Flat Field: Flat Frame Division
  - Background Subtraction
  - Bad/Hot Pixels
* **Plate-solving with Astrometry.net**
* **World Coordinate System (WCS)**
* **Photometry with Photutils**
  - Aperture Photometry
    - Optimizing Aperture Size and Shape
  - PSF Photometry
  - Treatment of Outliers
    - Weather: Cloud, Humidity, Turbulence
    - Everything Else Unaccounted for (Systematics)
    - Saturation
    - Cosmic Rays
* **Barycentric Time Correction (MJD to BJD Conversion)**
  - Light Travel Time Delay
* **Transit Modeling**
  - Basic Model
    - Pytransit
    - Starry
  - Parameterization
    - Transforms
    - Quadratic Limb Darkening: u1, u2 -> q1, q2 (Kipping+2016)
    - Impact Parameter and Rp/Rs (Espinosa+2018)
    - Stellar Density
    - Cosi, a/Rs
* **Period Search, Periodogram**
  - BLS
  - TLS
  - (Generalized) Lomb-Scargle
* **Spectroscopy**
  - Cross-correlation
  - RV Modeling
    - Basic Model
    - Parameterization
  - Joint RV+Transit Modeling

### Algorithms: Fast, Numerically Stable, Closed-form Solutions
* **Python Basics**
* **Version Control with Git and GitHub**
* **Re-usable Code**
* **Numba, JIT**
* **List Comprehension vs For-loops**

### Statistics
* **AstroML**
  - Probability Distributions
* **Sympy: Analytic**
* **Bayesian vs Frequentist**
* **Fitting Models to Data**
  - Linear Algebra
  - Maximum Likelihood
* **Optimization**
  - Gradient-free, scipy.optimize.solve
  - Autodiff, jax
* **Monte Carlo**
  - Propagation of Uncertainties
* **Sampling**
  - MCMC
  - Nested Sampling
  - Convergence Tests
* **Reporting Results**
  - Posteriors vs Point Estimates
  - Percentiles
* **Visualization**
  - Corner Plot
  - Posteriors
* **Mixture Models**
* **Gaussian Process Regression**
* **Hierarchical Modeling**
* **Machine Learning**

### Miscellaneous
* **Personal Website**
* **CV**
* **Reproducible Work Using Show-Your-Work**

## References
* [Mitch Richmond's lectures](http://spiff.rit.edu/classes/)

