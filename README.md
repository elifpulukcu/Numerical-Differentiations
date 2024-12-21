# Numerical Differentiations – Code

A small Java program that reads polynomial function definitions from text files (e.g., `functions1.txt`, `functions2.txt`, `functions3.txt`), plots them on a coordinate plane (using Princeton’s **StdDraw** library or any equivalent), and computes approximate derivatives numerically. If a file is missing or the polynomials cannot be parsed, the program gracefully handles these exceptions.

## Table of Contents
1. [About](#about)
2. [Features](#features)
3. [Dependencies](#dependencies)
4. [Usage](#usage)
5. [How It Works](#how-it-works)
6. [Contributing](#contributing)
7. [License](#license)

---

## About

This project demonstrates how to:

- **Read** polynomial coefficients (comma-separated) from text files like `functions1.txt`.
- **Instantiate** different polynomial objects (`Polynomial1D`, `Polynomial2D`, `Polynomial3D`) based on the number of coefficients.
- **Plot** these functions over a 2D canvas (with x, y axes from `-10` to `10`).
- **Compute** approximate derivatives numerically, highlighting points where the derivative is near zero.
- **Save** the resulting plot (optional) as an image.

These capabilities showcase object-oriented design in Java, basic numerical techniques, and rudimentary data visualization.

---

## Features

- **Polynomial Hierarchy**  
  - `Polynomial` (base class)  
  - `Polynomial1D`, `Polynomial2D`, `Polynomial3D` (subclasses)
- **Flexible File Input**  
  - Reads lines from text files (e.g., `functions1.txt`, `functions2.txt`) that define polynomials with different degrees.  
- **Canvas Drawing**  
  - Uses `StdDraw` methods to draw each polynomial in **light blue** with a resolution of 700×700 pixels.
- **Numerical Differentiation**  
  - Employs a finite-difference method \(\frac{f(x+h)-f(x)}{h}\) to approximate derivatives for each polynomial.
- **Zero-Derivative Points**  
  - Identifies where the derivative is close to zero and marks these points on the canvas in **black**.

---

## Dependencies

1. **Java 8+**  
   The project should compile and run under any modern Java version that supports your environment.

2. **Princeton’s StdDraw**  
   If you are using the provided `StdDraw` library, place `StdDraw.java` in the same directory or ensure it is on your classpath.  
   > *Alternatively, you may refactor the code to use a different plotting library.*

---

## Usage

1. **Prepare Your Input Files**  
   - By default, the code looks for files such as `functions1.txt`, `functions2.txt`, or `MyFunction.txt`.  
   - Each line in these files contains comma-separated numbers representing polynomial coefficients.  
     - **1D Example** (`a, b`): `1.0,2.5`  
     - **2D Example** (`a, b, c`): `2.0,-1.0,3.0`  
     - **3D Example** (`a, b, c, d`): `1.0,0.5,-2.0,4.0`

2. **Compile the Code**  
   ```bash
   cd Numerical-Differentiations/Code
   javac Main.java Polynomial.java Polynomial1D.java Polynomial2D.java Polynomial3D.java
   ```
   *(Include `StdDraw.java` if required.)*

3. **Run the Program**  
   ```bash
   java Main
   ```
   - Depending on how `Main.java` is set up, it may read one or more `.txt` files (such as `functions1.txt`).
   - It then **draws** the polynomials and computes approximate derivatives.

4. **Output**  
   - A 700×700 window (or a saved `.png` file) shows the plotted polynomials in **light blue**, plus zero-derivative points in **black**.
   - The console prints information about each polynomial, including approximate zero-derivative points.

---

## How It Works

1. **Reading Input**  
   - `Main.java` attempts to read lines from the specified `.txt` files in the `Code/` directory.  
   - Each line is split by commas, and the coefficients are parsed as `double`.

2. **Instantiating Polynomials**  
   - If two coefficients are detected, a `Polynomial1D` object is created. If three, `Polynomial2D`, and so on.  
   - These objects are stored in a list for further processing.

3. **Drawing and Derivatives**  
   - For each polynomial, the code samples points from `x = -10` to `x = 10` at small increments (e.g., 0.01).  
   - It evaluates the polynomial (`evaluate(x)`) and records `(x, y)` for plotting.  
   - A simple finite-difference method approximates the slope at each point:
     \[
       f'(x) \approx \frac{f(x+h) - f(x)}{h}
     \]
   - If `|f'(x)| < threshold`, we consider it a near-zero derivative, plotting a black circle at that \((x, f(x))\).

4. **Error Handling**  
   - If any file is missing or unreadable, the code prints an error to the console (e.g., *“File not found”*).  
   - If no zero-derivative points are found, a corresponding message is displayed.

---

## Contributing

1. **Fork** this repository and clone your fork locally.  
2. Create a **branch** for your feature/fix:  
   ```bash
   git checkout -b feature/my-new-feature
   ```
3. **Commit** changes to your branch, then push back to your fork.  
4. **Open a pull request** on GitHub, detailing your changes and why they should be merged.

---

## License

This project is offered under the [MIT License](../LICENSE) (or whichever license you choose to include).  
You are free to use, modify, and distribute this code in personal or commercial projects.

---

**Enjoy exploring polynomial functions and numerical differentiation!**  
If you have questions or encounter any issues, please open an [issue](../../issues) or reach out to the repository maintainer.
