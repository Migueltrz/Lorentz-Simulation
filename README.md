# Simulation of Lorentz Transformations using Pygame

![Python](https://img.shields.io/badge/python-3.8%2B-blue?logo=python&logoColor=white)
![Pygame](https://img.shields.io/badge/pygame-2.0%2B-green?logo=pygame)
![License](https://img.shields.io/badge/license-MIT-yellow)
![Status](https://img.shields.io/badge/status-active-success)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux-lightgrey)

---

![Lorentz Simulation Banner](./images/banner_lorentz.png "Lorentz Simulation — Python & Pygame")

## General Description

**Project:** *Development of a simulation of Lorentz transformations in special relativity using the Pygame library in Python.*

This project visually demonstrates **Lorentz transformations**, showing **length contraction** and **time dilation** as an object approaches the speed of light.  
It was developed to enhance understanding of *Special Relativity* through interactive visualizations built with Python.

---

## Table of Contents

<details>
  <summary>Click to expand</summary>

1. [Problem Statement](#problem-statement)
2. [Objectives](#objectives)
3. [Theoretical Framework](#theoretical-framework)
4. [Methodology](#methodology)
5. [Results](#results)
6. [Conclusions](#conclusions)
7. [Installation](#installation)
8. [Execution](#execution)
9. [References](#references)

</details>

---

## Problem Statement

Despite their significance in modern physics, relativistic concepts are often abstract and challenging to grasp.  
This project aims to make them accessible and visual, enabling learners to understand them more intuitively.

![Conceptual representation of special relativity.](./images/problematic.png "Example of visual motivation")

---

## Objectives

**General Objective:**  
Develop animations illustrating the effects of *length contraction* and *time dilation* under Lorentz transformations.

**Specific Objectives:**
1. Implement a simulation in `Python` using the `Pygame` library.  
2. Visualize the relationship between rocket velocity and the Lorentz factor (γ).  
3. Provide an interactive and educational tool for teaching special relativity.

---

## Theoretical Framework

| Concept | Description |
|----------|-------------|
| **Galilean Transformations** | Preserve Newton’s equations between inertial reference frames. |
| **Lorentz Transformations** | Keep the speed of light constant for all inertial observers. |
| **Length Contraction** | A moving object appears shorter from an inertial frame. |
| **Time Dilation** | A moving clock runs slower compared to one at rest. |

![Lorentz Transformation Diagram.](./images/lorentz_diagram.png "Visualization of Lorentz transformations")

---

## Methodology

**Development Stages**

1. **Class design:** Creation of main classes (`Rocket`, `Watch`, `Button`).  
2. **Integration:** Incorporation of all classes into the main executable file.  
3. **Interactivity:** Definition of events and user interactions in Pygame.  
4. **Visualization:** Real-time simulation of motion and relativistic effects.

The simulation follows an object-oriented approach and uses Pygame for event-driven rendering.

---



### File Overview

#### `rocket.py`
Defines the **Rocket** class: attributes, size, position, and drawing functions.
```python
class Rocket:
    def __init__(self, position, scale):
        self.position = position
        self.scale = scale
    def draw(self, screen):
        # Draw the rocket
        pass
```
####  `watch.py`

Implements the Watch class: simulates clock movement and rotation.

``` python

class Watch:
    def update(self, speed):
        self.angle += speed
```
#### `button.py`

Contains classes for Start, Pause, and Stop buttons, managing user clicks.

``` python
if start_button.clicked():
    simulation_running = True
```

#### `main.py`

Imports all modules, initializes Pygame, sets up the screen, and applies the Lorentz factor:

$$\gamma = \frac{1}{\sqrt{1 - \left(\frac{v^2}{c^2}\right)}}$$


Optional: Add a diagram here showing relationships between files and classes.

## Results

The program simulates two reference frames:

* Frame 1: The stationary observer sees the rocket moving close to light speed.

* Frame 2: The observer inside the rocket perceives spatial contraction.

Frame	Visualized Effect	Description
*	Time Dilation	The rocket’s clock runs slower.
*	Length Contraction	External objects appear shorter.

## Conclusions

This simulation enables a visual and dynamic understanding of Lorentz transformations.
It serves as an effective educational tool for learning special relativity and can be expanded with additional physical effects.

## Installation
Requirements

* Python ≥ 3.8
* Pygame
* Numpy (optional)

Installation Command
```
pip install pygame numpy
```
## Execution

Run the program from your terminal:
```
python main.py
```

Ensure that all images are located inside the /images folder and the modules (rocket.py, watch.py, button.py) are in the same directory.

## References

Beiser, A. (2003). Concepts of Modern Physics.

Acosta, V., Cowan, C. L., & Graham, B. J. (1975). Curso de Física Moderna.

McGugan, W. (2007). Beginning Game Development with Python and Pygame: From Novice to Professional. Apress.

Kelly, S., & Kelly, S. (2016). Basic Introduction to Pygame. In Python, PyGame and Raspberry Pi Game Development, 59–65.

## Contributing

Contributions, feedback, and suggestions are welcome.
Feel free to open a Pull Request or report issues in the Issues section.

## License

This project is licensed under the MIT License
