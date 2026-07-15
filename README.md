# 🚦 City Traffic Scene Simulation

A 2D animated city scene built with **OpenGL** and **FreeGLUT** in **C++**. The scene shows buildings, trees, clouds, birds, a sun, and two buses driving in opposite directions on a two-lane road — just like real city traffic.

## ✨ Features

- 🌇 Animated sky with a sun that grows smoothly when the program starts
- ☁️ Clouds and flapping birds in the background
- 🏢 Three different buildings (gray, brownish-red, and pink) with windows, doors, and rooftops
- 🌳 Trees placed between the buildings
- 🛣️ Two roads with white dashed lane markings and a yellow center divider
- 🚌 A red bus moving left → right on the top road
- 🚌 A blue bus moving right → left on the bottom road
- 🔁 Buses loop back automatically when they leave the screen
- 🎞️ Smooth animation running at about 60 frames per second

---

## 🛠️ Built With

- **C++**
- **OpenGL**
- **FreeGLUT**
- Basic computer graphics concepts: Midpoint Circle Algorithm, Bresenham Line concept, and 2D Translation

---

## 📋 Requirements

Before running the project, make sure you have:

1. A C++ compiler (like **g++** on Linux/Mac or **MinGW** on Windows)
2. **FreeGLUT** installed (this provides `GL/glut.h`)
3. An IDE like **Code::Blocks** or **Visual Studio** (optional, but easier for beginners)

### Installing FreeGLUT

**Windows (using MinGW):**
- Download FreeGLUT from the official site or via a package manager like MSYS2:
  ```
  pacman -S mingw-w64-x86_64-freeglut
  ```

**Linux (Ubuntu/Debian):**
```bash
sudo apt update
sudo apt install freeglut3-dev
```

**macOS:**
```bash
brew install freeglut
```

---

## ▶️ How to Run

### Option 1: Using the terminal (Linux/Mac)

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/city-traffic-simulator.git
   cd city-traffic-simulator
   ```

2. Compile the program:
   ```bash
   g++ main.cpp -o traffic_sim -lGL -lGLU -lglut
   ```

3. Run it:
   ```bash
   ./traffic_sim
   ```

### Option 2: Using the terminal (Windows with MinGW)

1. Compile:
   ```bash
   g++ main.cpp -o traffic_sim.exe -lfreeglut -lopengl32 -lglu32
   ```

2. Run:
   ```bash
   traffic_sim.exe
   ```

### Option 3: Using Code::Blocks / Visual Studio

1. Create a new empty C++ project.
2. Add `main.cpp` (the source file) to the project.
3. Link the **OpenGL**, **GLU**, and **FreeGLUT** libraries in your project/build settings.
4. Build and run the project.

A window titled **"City Traffic Scene Simulation"** will open, showing the animated city scene.

---

## 📁 Project Structure

```
city-traffic-simulator/
├── main.cpp        # All the source code (shapes, objects, animation)
├── README.md        # This file
└── screenshot.png   # (optional) A picture of the running program
```

---

## 🧠 How It Works (Simple Explanation)

- The screen is treated like a graph from **(0,0)** at the bottom-left to **(1000,1000)** at the top-right.
- Simple shapes like rectangles and circles are drawn using basic functions (`drawRect`, `drawCircle`), and these are combined to build bigger objects like buses, buildings, and trees.
- A **timer function** runs every 16 milliseconds (about 60 times per second) to update positions and redraw the screen, creating smooth animation.
- The buses move using **2D translation** — their x-position simply increases or decreases each frame. When a bus goes off-screen, its position resets to the other side, making it loop forever.
- The sun starts small and grows bigger over time (an "ease-out" effect), and the birds flap their wings by moving up and down slightly each frame.

---

## 🚧 Known Limitations

- Bus speed is fixed and can't be changed while running
- No traffic lights, pedestrians, or user controls yet
- The scene is fully 2D (no depth or 3D perspective)
- No textures or images — all colors are flat/solid

---

## 🔮 Future Improvements

- [ ] Add traffic signals that stop and start the buses
- [ ] Add pedestrians and crosswalks
- [ ] Add keyboard/mouse controls to change bus speed or add vehicles
- [ ] Add day/night sky transitions with street lights
- [ ] Add more vehicle types (cars, trucks, bicycles)
- [ ] Rebuild transformations using `glTranslatef()` and `glPushMatrix()` / `glPopMatrix()`

---

## 👥 Authors

This project was created as a lab project for **CSE412: Computer Graphics Lab**, Department of Computer Science and Engineering, Daffodil International University.

- Fahim Montasir
- Md. Ibna Labid
- Mahidul Hasan

---

## 📄 License

This project is open for learning purposes. Feel free to fork it, modify it, and build on top of it.
