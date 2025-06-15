# Problem 1  \documentclass{article}
\usepackage{amsmath, amssymb}
\usepackage{graphicx}
\usepackage{hyperref}
\usepackage{enumitem}

\title{Problem 1: Equivalent Resistance Using Graph Theory}
\author{}
\date{}

\begin{document}

\maketitle

\section*{🧠 Motivation}
Calculating equivalent resistance is a foundational problem in physics and electrical engineering. While simple series and parallel resistor combinations are easy to analyze by hand, more complex circuits can quickly become unmanageable.

By applying graph theory, we can treat an electrical circuit as a mathematical graph:
\begin{itemize}
    \item Nodes (vertices) represent junctions where wires or components meet.
    \item Edges represent resistors, and each edge is labeled with a weight equal to the resistor’s resistance value.
\end{itemize}

Graph theory allows for a systematic, repeatable process for reducing complex resistor networks to a single equivalent resistance between two points (terminals). This is especially useful in automation, simulation tools, and optimization tasks in circuit design.

\section*{🔢 Key Concepts}

\subsection*{1. Series Connection}
Two resistors are in series if:
\begin{itemize}
    \item They are connected end-to-end.
    \item No branching exists between them.
    \item The same current flows through both.
\end{itemize}

\textbf{Rule:}
\[
R_{\text{eq}} = R_1 + R_2 + \dots + R_n
\]

\subsection*{2. Parallel Connection}
Two or more resistors are in parallel if:
\begin{itemize}
    \item They are connected between the same two nodes.
    \item The voltage across each is the same.
    \item The current divides among the resistors.
\end{itemize}

\textbf{Rule:}
\[
\frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2} + \dots + \frac{1}{R_n}
\]

\section*{📉 Graph Theory Approach}

\subsection*{A. Representing the Circuit as a Graph}
\begin{itemize}
    \item \textbf{Vertices:} Electrical junctions or nodes
    \item \textbf{Edges:} Resistors (with weights equal to resistance values)
\end{itemize}

\subsection*{B. Algorithm Steps}
\begin{itemize}
    \item \textbf{Input:} A graph representing a resistor network, and two terminals (start and end nodes)
    \item Identify Series Connections:
        \begin{itemize}
            \item Look for a node connected to exactly two other nodes (and is not a terminal).
            \item Collapse this node and add the two resistances.
        \end{itemize}
    \item Identify Parallel Connections:
        \begin{itemize}
            \item Check for multiple edges (resistors) between the same two nodes.
            \item Combine them using the parallel rule.
        \end{itemize}
    \item \textbf{Reduce the Graph:} 
        \begin{itemize}
            \item Continue identifying and simplifying series and parallel structures.
            \item Iteratively simplify until only one edge remains between the start and end nodes.
        \end{itemize}
    \item \textbf{Output:} The weight of the final edge is the equivalent resistance between the terminals.
\end{itemize}

\section*{🔍 Examples of Application}

\subsection*{🔹 Example 1: Simple Series}

\textbf{Circuit:}
\[
\text{A} \xrightarrow{5\,\Omega} \text{B} \xrightarrow{10\,\Omega} \text{C}
\]

Start Node (S): A \\
End Node (T): C

Node B has 2 connections $\Rightarrow$ series.

\[
R_{\text{eq}} = 5 + 10 = 15\,\Omega
\]

\subsection*{🔹 Example 2: Simple Parallel}

\textbf{Circuit:}

Two resistors between A and B:

\[
\text{A} \xrightarrow{10\,\Omega} \text{B}, \quad \text{A} \xrightarrow{20\,\Omega} \text{B}
\]

\[
\frac{1}{R_{\text{eq}}} = \frac{1}{10} + \frac{1}{20} = \frac{3}{20} \Rightarrow R_{\text{eq}} = \frac{20}{3} \approx 6.67\,\Omega
\]

\subsection*{🔹 Example 3: Mixed/Nested Circuit}

\begin{itemize}
    \item A connects to B with $4\,\Omega$
    \item B connects to D with $6\,\Omega$
    \item A connects to C with $12\,\Omega$
    \item C connects to E with $12\,\Omega$
    \item D and E connect to each other with $6\,\Omega$
\end{itemize}

Goal: Find equivalent resistance between A and E.

\textbf{Steps:}
\begin{itemize}
    \item Series: $R_{BD} = 4 + 6 = 10\,\Omega$
    \item Series: $R_{CE} = 12 + 12 = 24\,\Omega$
    \item D–E link: $6\,\Omega$ connects two paths
    \item Path 1: A–B–D–E = $10 + 6 = 16\,\Omega$
    \item Path 2: A–C–E = $24\,\Omega$
\end{itemize}

\[
\frac{1}{R_{\text{eq}}} = \frac{1}{16} + \frac{1}{24} = \frac{5}{48} \Rightarrow R_{\text{eq}} = \frac{48}{5} = 9.6\,\Omega
\]

\section*{🧮 Advantages of the Graph-Based Method}

\begin{itemize}
    \item \textbf{Scalable:} Works for any complexity.
    \item \textbf{Systematic:} Reduces manual trial and error.
    \item \textbf{Automatable:} Forms the basis for circuit simulation software.
    \item \textbf{Visualizable:} Helps to draw circuit as a network.
\end{itemize}

\section*{⏱️ Efficiency Considerations}
\begin{itemize}
    \item For small circuits, the approach is fast and intuitive.
    \item Detecting series: Can be done using node degree checks.
    \item Detecting parallel: Check for multiple edges between two nodes.
    \item Iteratively applying both rules eventually simplifies any reducible network.
\end{itemize}

\section*{📘 Applications}
\begin{itemize}
    \item Designing electrical circuits
    \item Simulation tools (like SPICE)
    \item Network reliability modeling
    \item PCB (printed circuit board) optimization
    \item Energy distribution systems
\end{itemize}

\section*{🧩 Conclusion}
Using graph theory to compute equivalent resistance offers a powerful, systematic alternative to manual analysis. It is especially useful for complex and nested resistor networks, providing both educational insight and practical utility in electrical engineering and computer science.

\end{document}


