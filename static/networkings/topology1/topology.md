![Topology](./topology.jpg)

**Language:** latex

.tex
---
```latex
\documentclass{article}
\usepackage{network}
\usepackage{pgfplots}

\usetikzlibrary{positioning, patterns}

\begin{figure}
\centering\resizebox{\textwidth}{!}{
	\begin{tikzpicture}[node distance=4cm]
		\node (S1){\server{Sender}};
		\node[right of=S1] (R1){\router{Router1}};
		\node[right of=S1] (R1){\router{Router1}[true]};
		\node[right of=R1] (R2){\router{Router2}};
		\node[right of=R2] (S2){\server{Receiver}};
		\node[yshift=3.5cm] at ($ (R1) !.5! (R2) $)  (R3) {\router{Router 3}};
		\draw[thick] (S1) -- node[ethernet, at start]{eth0} node[ethernet, at end] {eth0} (R1) node[speed, midway] {100 Mbps};
		\draw[thick] (R1) -- node[ethernet, at start]{eth1} node[ethernet, at end] {eth1} (R2) node[speed, midway] {100 Mbps};
		\draw[thick] (R1) -- node[ethernet, at start]{eth2} node[ethernet, at end] {eth0} (R3) node[speed, midway] {100 Mbps};
		\draw[thick] (R2) -- node[ethernet, at start]{eth2} node[ethernet, at end] {eth1} (R3) node[speed, midway] {100 Mbps};
		\draw[thick] (R2) -- node[ethernet, at start]{eth0} node[ethernet, at end] {eth0} (S2) node[speed, midway] {100 Mbps};
	\end{tikzpicture}
}
\caption{Complicated Topology}
\end{figure}

\end{document}
```

[network.sty](https://github.com/snowzjx/network.sty)

**Acknowledgement:** [@Junxue Zhang](https://github.com/snowzjx)