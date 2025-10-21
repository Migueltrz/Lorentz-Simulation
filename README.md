# Simulation of Lorentz Transformations using Pygame

![Python](https://img.shields.io/badge/python-3.8%2B-blue?logo=python&logoColor=white)
![Pygame](https://img.shields.io/badge/pygame-2.0%2B-green?logo=pygame)
![License](https://img.shields.io/badge/license-MIT-yellow)
![Status](https://img.shields.io/badge/status-active-success)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux-lightgrey)

---


<!-- ![Lorentz Simulation Banner](./images/banner_lorentz.png "Lorentz Simulation — Python & Pygame") -->

## General Description

**Project:** *Development of a simulation of Lorentz transformations in special relativity using the Pygame library in Python.*

This project visually demonstrates **Lorentz transformations**, showing **time dilation** and slightly **length contraction** as an object approaches the speed of light.  
It was developed to enhance understanding of *Special Relativity* through interactive visualizations built with Python.

---

## Table of Contents

<details>
  <summary>Click to expand</summary>

1. [Theoretical Framework](#theoretical-framework)
2. [Methodology](#methodology)
3. [Results](#results)
4. [Conclusions](#conclusions)
5. [Installation](#installation)
6. [Execution](#execution)
7. [References](#references)

</details>

---



## Theoretical Framework

| Concept | Description |
|----------|-------------|
| **Galilean Transformations** | Preserve Newton’s equations between inertial reference frames. |
| **Lorentz Transformations** | Keep the speed of light constant for all inertial observers. $$\gamma = \frac{1}{\sqrt{1 - \left(\frac{v^2}{c^2}\right)}}$$|
| **Length Contraction** | A moving object appears shorter from an inertial frame. |
| **Time Dilation** | A moving clock runs slower compared to one at rest. |


---


##  Methodology and Code Structure

The simulation is built using the **Pygame library** to create a visual and interactive environment. It demonstrates relativistic effects (or classical effects, depending on the chosen transformation) by simulating a rocket's motion relative to two observers: one stationary on a platform (frame S) and one moving with the rocket (frame S'). The core files and their functionalities are:

### `Main.py` (The Game Loop and Core Logic)

This is the main entry point of the simulation. It handles initialization, constant definition, event handling, and the core physics calculations.

* **Initialization and Setup**: Sets up the Pygame window, screen dimensions (`WIDTH`, `HEIGHT`), and loads all assets (images, fonts). Screen size dynamically adjusts based on the monitor's resolution.
* **Constants**: Defines fundamental parameters like the reference length of the rocket in its rest frame (`GLOBAL_L`), the speed of light in the simulation's units (`GLOBAL_C = 400`), and the normalized relative velocity $\alpha$ ($v/c$).
* **Event Handling**: Manages user input, including mouse clicks for buttons (Start, Stop, Pause, Galileo/Lorentz toggle) and key presses (e.g., `ESC` to quit, left/right arrows to scroll time).
* **Physics Core**: The main game loop uses `frame_rate` to calculate the global time (`global_time`). The **Lorentz factor** $\beta$ is calculated as $\beta = \sqrt{1 - \alpha^2}$ in the relativity mode.
* **Transformation Logic**:
    * **Lorentz (Relativity) Mode (`GALILEO = False`)**: The time for the moving observer (`frame1_rocket_time2`) is calculated using the time dilation formula:
        ```python
        frame1_rocket_time2 = global_time * beta
        ```
    * **Galilean (Classical) Mode (`GALILEO = True`)**: Time is absolute:
        ```python
        watch2.update(global_time) # The moving observer's watch also shows global_time
        ```
* **Button and Object Management**: Calls the `update()` and `blitme()` methods for all objects (`Rocket`, `Watch`, `Button` classes) to update their state and redraw them on the screen.

### `Rocket.py` (The Moving Object)

This class manages the visual representation, position, and physical properties of the rocket in the simulation.

* **Relativistic Length Contraction (`Lx_scale`)**: When Lorentz transformations are active, this method adjusts the rocket's drawn width based on the Lorentz factor $k = \sqrt{1-\alpha^2}$.
    ```python
    self.k = math.sqrt(1-alpha*alpha)
    self.scale = 1/self.k
    # Scale the image based on the calculated scale factor
    self.img_rocket = pygame.transform.scale(self.img_rocket, (int(global_l/self.scale), int(global_l*0.411)))
    ```
* **Position Update (`update`)**: Calculates the rocket's new position based on the elapsed time and relative velocity, ensuring it scrolls correctly across the background defined by the pillars.

### `Watch.py` (The Time Display)

The `Watch` class is responsible for displaying time on the clocks (both on the panel and on the moving objects) using an animated clock face.

* **Time Visualization (`update`)**: This method converts the calculated time (`t`) into angular positions for the clock's hand. It uses trigonometric functions to determine the $(x, y)$ coordinates of the hand's tip, simulating an analog clock where time $t$ corresponds to the angle.
    ```python
    # Calculates x and y position for the clock hand based on time t
    self.x = 30 * math.cos(math.pi/2 - math.pi/30 * t)
    self.y = 30 * math.sin(math.pi/2 - math.pi/30 * t)
    ```

### `Button.py` (Interactive Elements)

This file defines various button classes that manage user interaction, including visual feedback on hover/click.

* **Base Class (`Button`)**: Provides standard methods for loading, scaling, positioning, and drawing button images (`blitme`, `blitmeclick`).
* **Specialized Classes**:
    * `Start`, `Stop`, `Pause`, `Scroll`: Standard control buttons.
    * `Galileo`: A toggle button with a `click()` method to switch the `self.flag` between `True` (Galilean) and `False` (Lorentz), controlling the simulation's mode.
    * `Change_velocity`: Handles the visual slider for setting the relative velocity $\alpha$. The `bt1_x` attribute tracks the horizontal position of the slider's knob.




---

## Results

The program simulates two reference frames:

![Diagrama Referencia](imagenes/Imagen1.png)

* Frame 1: The stationary observer sees the rocket moving close to light speed.

* Frame 2: The observer inside the rocket perceives spatial contraction.

Frame	Visualized Effect	Description
*	Time Dilation	The rocket’s clock runs slower.
*	Length Contraction	External objects appear shorter.
  
---

## Conclusions

This simulation enables a visual and dynamic understanding of Lorentz transformations.
It serves as an effective educational tool for learning special relativity and can be expanded with additional physical effects.

---

## Installation
Requirements

* Python ≥ 3.8
* Pygame
* Numpy (optional)

Installation Command
```
pip install pygame numpy
```
---
## Execution

Run the program from your terminal:
```
python main.py
```

Ensure that all images are located inside the /images folder and the modules (rocket.py, watch.py, button.py) are in the same directory.
---
## References

Beiser, A. (2003). Concepts of Modern Physics.

Acosta, V., Cowan, C. L., & Graham, B. J. (1975). Curso de Física Moderna.

McGugan, W. (2007). Beginning Game Development with Python and Pygame: From Novice to Professional. Apress.

Kelly, S., & Kelly, S. (2016). Basic Introduction to Pygame. In Python, PyGame and Raspberry Pi Game Development, 59–65.

---

## Contributing

Contributions, feedback, and suggestions are welcome.
Feel free to open a Pull Request or report issues in the Issues section.

---

## License

This project is licensed under the MIT License
