## MIPS Assembly: Solving Linear Equations with Cramer’s Rule  

### 1. Overview  
This project implements a **system of linear equations solver** using **Cramer’s Rule** in **MIPS assembly**. The program reads equations from a text file, processes them into matrix form, solves for variables, and outputs the results either to a file or the screen.  

---  

### 2. Key Components  

#### **2.1 Reading the Input File**  
- The program prompts the user for an **input file name**.  
- It opens the file and reads **multiple systems of equations** separated by empty lines.  
- Each equation is stored in memory for processing.  

---  

#### **2.2 Parsing the Equations**  
- Extract coefficients of variables (`x`, `y`, `z`) from the equations.  
- Convert each system into **matrix representation**.  
- Example input:

  ```  
  2x + 3y = 5  
  4x - y = 1  
  ```  
  is stored as:  

  ```  
  |  2   3  | | x |   |  5 |  
  |  4  -1  | | y | = |  1 |  
  ```  

---  

#### **2.3 Applying Cramer’s Rule**  
- Compute the determinant (**D**) of the coefficient matrix.  
- Compute **Dx, Dy, Dz** by replacing columns in `D` with the result column.  
- Compute the solutions:  
  
$$
X = \frac{D_x}{D}
$$

$$
Y = \frac{D_y}{D}
$$

$$
Z = \frac{D_z}{D}
$$





- Determinants are calculated using:  
  - **2×2 matrices:** Simple cross-multiplication.  
  - **3×3 matrices:** Laplace Expansion method.  

---  

#### **2.4 Displaying or Saving the Output**  
- The program prompts the user to choose an output format:  
  - **Screen (`s/S`)**  
  - **File (`f/F`)**  
- Results are formatted clearly for readability.  

---  

#### **2.5 Error Handling**  
- The program includes checks for:  
  - **Invalid file structure** or missing coefficients.  
  - **Singular matrices** (determinant = 0, no unique solution).  
  - **Invalid user inputs** (incorrect commands or filenames).  
  - If an error occurs, the user is notified and given the option to retry.  

---  

#### **2.6 Looping Until Exit**  
- After solving a system, the program prompts the user for another input.  
- The program continues running until the user enters `'e'` or `'E'` to exit.  

---  
**Contents of `test.txt`:**  
-x + y + z = 0  
x + y = 9  
z = 8  

3x + 2y + z = 0  
x + y = 9  
z = 8  

5x - 2y + z = 0  
x - y = 9  
z = 3  

-6x + y = 12  
x + 2y = 9  

-12x + y = 24  
4y = 9  

-x + y = 0  
x + y = 9  

x - y = 0  
x + y = 9  

x + y = 1  
y = 9  

x + y = 9  

12x - 10y = 46  
3x + 20y = -11  

3x - 4y + 8z = 34  
4x + y - 2z = 1  
-6x - 13y + 20z = 61  

### Program Output Example

```
Enter the file name or e/E to exit: test.txt

-x + y + z = 0
x + y = 9
z = 8

the number of variables: 3
the number of equations: 3
the system is valid

Coefficient Matrix:
-1  1  1  
 1  1  0  
 0  0  1  

Output Matrix:
0  
9  
8  
```

```
3x + 2y + z = 0
x + y = 9
z = 8

the number of variables: 3
the number of equations: 3
the system is valid

Coefficient Matrix:
3  2  1  
1  1  0  
0  0  1  

Output Matrix:
0  
9  
8  
```

```
5x - 2y + z = 0
x - y = 9
z = 3

the number of variables: 3
the number of equations: 3
the system is valid

Coefficient Matrix:
5  -2  1  
1  -1  0  
0   0  1  

Output Matrix:
0  
9  
3  
```

```
-6x + y = 12
x + 2y = 9

the number of variables: 2
the number of equations: 2
the system is valid

Coefficient Matrix:
-6  1  
1   2  

Output Matrix:
12  
9   
```

```
-12x + y = 24
4y = 9

the number of variables: 2
the number of equations: 2
the system is valid

Coefficient Matrix:
-12  1  
0   4  

Output Matrix:
24  
9   
```

```
-x + y = 0
x + y = 9

the number of variables: 2
the number of equations: 2
the system is valid

Coefficient Matrix:
-1  1  
1   1  

Output Matrix:
0  
9  
```

```
x - y = 0
x + y = 9

the number of variables: 2
the number of equations: 2
the system is valid

Coefficient Matrix:
1  -1  
1   1  

Output Matrix:
0  
9  
```

```
x + y = 1
y = 9

the number of variables: 2
the number of equations: 2
the system is valid

Coefficient Matrix:
1  1  
0  1  

Output Matrix:
1  
9  
```

```
x + y = 9

the number of variables: 2
the number of equations: 1
the system is not valid
```

```
12x - 10y = 46
3x + 20y = -11

the number of variables: 2
the number of equations: 2
the system is valid

Coefficient Matrix:
12  -10  
3   20  

Output Matrix:
46  
-11  
```

```
3x - 4y + 8z = 34
4x + y - 2z = 1
-6x - 13y + 20z = 61

the number of variables: 3
the number of equations: 3
the system is valid

Coefficient Matrix:
3  -4   8  
4   1  -2  
-6  -13  20  

Output Matrix:
34  
1   
61  
```

---

### Options:
- **S/s**: Print results on screen
- **F/f**: Save results to file
- **E/e**: Exit

#### Example Output:
- **Solutions for each system of equations are displayed in fractional format:**
  ```
  X = -17/-2
  Y = -1/-2
  Z = -16/-2
  
  X = -26/1
  Y = 35/1
  Z = 8/1
  
  X = 21/-3
  Y = 48/-3
  Z = -9/-3
  
  X = 15/-13
  Y = -66/-13
  
  X = 87/-48
  Y = -108/-48
  
  X = -9/-2
  Y = -9/-2
  
  X = 9/2
  Y = 9/2
  
  X = -8/1
  Y = 9/1
  
  X = 810/270
  Y = -270/270
  
  X = -228/-114
  Y = 114/-114
  Z = -342/-114
  ```

---

- **User chooses to save results to a file:**
  ```
  Options:
  S/s: Print results on screen
  F/f: Save results to file
  E/e: Exit
  Enter your choice: f
  ```

- **User chooses to exit the program:**
  ```
  Options:
  S/s: Print results on screen
  F/f: Save results to file
  E/e: Exit
  Enter your choice: e
  ```

- **Program ends:**
  ```
  -- program is finished running --
  ```


