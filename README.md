# Optical_Fiber_Simulation
# Optical Fiber Light Propagation Simulation

A Python-based visualization project that simulates light ray propagation through an optical fiber cable using **Matplotlib and NumPy**. The simulation demonstrates guided, misguided, and grazing rays, along with optical fiber parameters such as acceptance angle, critical angle, numerical aperture, V-number, and approximate number of propagation modes.

## Overview

Optical fibers transmit light through a core surrounded by cladding. The difference in their refractive indices allows light to propagate through the fiber under suitable conditions.

This project provides an animated visualization of ray propagation inside an optical fiber. Users can select the fiber type and launch angle to observe different ray behaviors and understand the underlying optical principles.

## Features

- **Interactive Inputs:** Select step-index or graded-index fiber and specify the launch angle.
- **Ray Propagation Visualization:** Observe multiple light rays traveling through the fiber.
- **Ray Classification:** Distinguishes guided, misguided, and grazing rays using different colors.
- **Optical Parameter Calculations:** Calculates acceptance angle, critical angle, V-number, and approximate guided mode count.
- **Reflection Tracking:** Counts reflections at the core boundary for guided rays in step-index mode.
- **Intensity Attenuation:** Models reflection losses and scattering losses as light propagates.
- **Animated Simulation:** Displays ray movement and changes in intensity over time.
- **Fiber Structure Visualization:** Shows the core and cladding regions with clearly marked boundaries.

## Technologies Used

- **Python** — Core programming language
- **NumPy** — Numerical calculations, vector operations, and array handling
- **Matplotlib** — Animated visualization and plotting

## Physics Concepts

### 1. Acceptance Angle

The maximum launch angle, measured relative to the fiber axis, for light entering the fiber from an external medium to be guided.

For a fiber surrounded by air:

\[
\theta_a=\sin^{-1}\left(\sqrt{n_1^2-n_2^2}\right)
\]

### 2. Critical Angle

The minimum angle of incidence, measured from the normal at the core-cladding interface, required for total internal reflection.

\[
\theta_c=\sin^{-1}\left(\frac{n_2}{n_1}\right)
\]

Here, \(n_1\) is the core refractive index and \(n_2\) is the cladding refractive index.

### 3. V-Number

The normalized frequency parameter used to characterize an optical fiber and estimate its mode capacity.

\[
V=\frac{2\pi a}{\lambda}\sqrt{n_1^2-n_2^2}
\]

Where:
- \(a\) = Core radius
- \(\lambda\) = Operating wavelength
- \(n_1\) = Core refractive index
- \(n_2\) = Cladding refractive index

### 4. Approximate Number of Modes

The code estimates the number of guided modes using:

- **Step-index fiber:** \(M\approx V^2/2\)
- **Graded-index fiber:** \(M\approx V^2/4\)

These are approximate formulas for highly multimode fibers under standard assumptions.

### 5. Optical Losses

The simulation applies attenuation factors to represent losses caused by reflection and scattering as the rays propagate.

## Default Parameters

| Parameter | Value |
|---|---:|
| Core refractive index | 1.50 |
| Cladding refractive index | 1.45 |
| Core radius | 1.0 units |
| Cladding radius | 2.0 units |
| Wavelength | 0.5 units |
| Reflection factor | 0.97 |
| Scattering factor per step | 0.999 |
| Number of rays | 7 regular rays + 1 grazing ray |

## Installation

### Prerequisites

Install Python 3 and the required libraries.

```bash
pip install numpy matplotlib
```

### Run the Project

1. Save the Python script as `optical_fiber_simulation.py`.
2. Open a terminal in the project directory.
3. Run:

```bash
python optical_fiber_simulation.py
```

4. Enter the fiber type when prompted:

```text
Enter fiber type (step / graded): step
```

5. Enter a launch angle in degrees:

```text
Enter launch angle: 20
```

The simulation window will display the animated light propagation through the fiber.

## Color Legend

| Color | Ray Type | Meaning |
|---|---|---|
| Green | Guided | Intended to represent rays confined within the core |
| Red | Misguided | Rays classified as outside the acceptance-angle condition |
| Blue | Grazing | A special ray used to demonstrate boundary-parallel propagation |

## Implementation Details

The program follows these main steps:

1. Calculates the acceptance angle, critical angle, V-number, and estimated mode count.
2. Accepts user input for fiber type and launch angle.
3. Initializes multiple rays with different launch angles and starting positions.
4. Advances each ray in small time-like simulation steps.
5. Applies reflection behavior for guided rays in step-index mode.
6. Applies a simplified trajectory adjustment for graded-index mode.
7. Updates ray intensity and reflection count.
8. Animates the fiber, rays, and calculated parameters using Matplotlib.

## Limitations

This project is an **educational ray-tracing approximation**, not a full electromagnetic simulation.

- The guided/misguided classification uses a simplified launch-angle condition.
- The graded-index model uses a simplified direction adjustment rather than solving a complete graded refractive-index profile.
- The grazing ray uses special-case behavior to demonstrate propagation parallel to the core boundary.
- Reflection and scattering losses are simplified and are not calibrated against a specific physical fiber.
- The displayed reflection count applies to the regular guided rays in the step-index branch; the special grazing ray does not increment this counter.
- The mode count formulas assume suitable multimode-fiber approximations and should not be treated as exact for every fiber.

## Future Improvements

- Implement a physically consistent ray-launch condition based on numerical aperture.
- Model refraction at the fiber entrance and total internal reflection using Snell's law.
- Implement a parabolic refractive-index profile for graded-index fibers.
- Add adjustable refractive indices, core radius, wavelength, and attenuation parameters.
- Display ray power and total transmitted intensity over distance.
- Add pause, resume, and reset controls to the animation.
- Compare simulated results with analytical optical-fiber calculations.

## Learning Outcomes

This project demonstrates the practical application of Python programming, numerical computation, visualization, and fundamental optical-fiber concepts. It provides an interactive starting point for understanding how launch conditions and fiber parameters affect light propagation.

## License

This project is available for educational and learning purposes. Add an appropriate open-source license if you intend to distribute or reuse it publicly.
