# ece486_ece687_spring2026_course_notes
Collaborative repository for the **ECE 486 / ECE 687** student course notes. We use the **Tufte-LaTeX Handout Style**.

---

## Step-by-Step Contribution Guide

You do not need a complex local LaTeX setup. GitHub Actions will compile your document into a PDF every time you submit a Pull Request.

### Step 1: Claim your Lecture Slot
1. Navigate to the **Issues** tab of this repository.
2. Click **New Issue** and select the **Claim a Lecture Scribe Slot** template.
3. Check the existing issues to ensure no one else has claimed your target date, then submit.

### Step 2: Write Your Notes
1. Open this repository locally or directly in your browser using **GitHub Codespaces**.
2. Locate your assigned lecture file inside the `lectures/` directory (e.g., `lectures/week-2/lecture-3.tex`).
3. Open the file and type your notes directly between the `\begin{document}` and `\end{document}` tags.

> Do **NOT** add commands like `\documentclass`, `\usepackage`, or `\begin{document}` inside your lecture file. These are handled automatically by the master compiler and will cause the build to fail.

### Step 3: Link Your File to the Master Textbook
To ensure your notes appear in the main textbook, you must tell the master file to look for your work:
1. Open `master-handout.tex` in the root folder.
2. Scroll down to the `% COMPLETE LECTURE LINKS` section.
3. Find your lecture line and make sure it is uncommented (it should look like `\subfile{lectures/week-2/lecture-3.tex}\newpage`).

### Step 4: Submit a Pull Request (PR)
1. Commit your changes to a new branch and push them to GitHub.
2. Open a **Pull Request** back to the `main` branch.
3. Complete the automated PR checklist that appears on your screen.
4. Watch the **Actions** check at the bottom of your PR page. If it turns green, your notes compiled perfectly! If it turns red, click it to check your LaTeX syntax for errors.

---

## Tufte Layout Formatting Quick Sheet

The Tufte layout provides wide side margins. Make sure to leverage this space. See [this example of lecture notes](https://www.gnotomista.com/files/teaching/optimization_based_robot_control_course_notes.pdf) as well as the use cases below:

### 1. Marginal Sidenotes
Replace standard footnotes with `\sidenote{}` to add margin commentary, matrix notation hints, or reference frame explanations:
```latex
The matrix $R \in SO(3)$ is an orthogonal matrix.\sidenote{Remember: This implies $R^T R = I$ and $\det(R) = 1$.}
```

### 2. Side-Margin Figures
Place coordinate frame transforms or joint schemas cleanly in the margin without interrupting the text flow:
```latex
\begin{marginfigure}
  \centering
  \includegraphics[width=\linewidth]{robot-joint.png}
  \caption{Joint 1 reference frame configuration.}
end{marginfigure}
```

### 3. Full-Width Equations
For expansive mathematical expressions (such as complex manipulator inertia tensors), scale them across the entire page width:
```latex
\begin{fullwidth}
\begin{equation}
    M(q)\ddot{q} + C(q,\dot{q})\dot{q} + g(q) = \tau
\end{equation}
\end{fullwidth}
```

---

## Compiling Notes Locally (Optional)

If you prefer to preview your work locally before pushing to GitHub, you will need a LaTeX distribution installed on your machine:
* **Windows**: Install [MiKTeX](https://miktex.org).
* **macOS**: Install [MacTeX](https://tug.org).
* **Ubuntu/Debian**: Run `sudo apt install texlive-latex-extra texlive-science latexmk`.
* **ArchLinux**: Run `sudo pacman -Syu texlive-latexextra texlive-mathscience texlive-binextra`.

To compile, navigate to your file directory via terminal and run: `latexmk -pdf lecture-XX.tex`.
