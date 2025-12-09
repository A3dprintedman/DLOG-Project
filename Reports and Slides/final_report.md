Final Report (Due on 12/11/2025)

Introduction, including a summary of the project, related work/methods, and the results of this project.

Problem description, including a detailed description of the problem you address in this project.

Methodology, including a detailed description on the methods you developed or used.

Experiments, including, experiment setting, results, and your observations.

Conclusion and future work, including a summary of the main contributions of this project and potential future directions.




<style>
body {
	font-family: "Times New Roman", serif;
	font-size: 12pt;
}
</style>


<h1 style="text-align:center;">Graph Coloring for Efficient Code Compilation</h1>
<h3 style="text-align:center;">Andrew Erickson, Ethan Rapa, Haven Cook </h3>
<h4 style="text-align:center;">December 11, 2025</h3>


### Introduction

Register allocation is a core component in modern compiler backends, determining how program variables are mapped onto a limited number of machine registers. This mapping problem can be represented as a graph coloring task on a variable interference graph, where each vertex corresponds to a virtual register and edges denote liveness conflicts. Because graph coloring is NP-hard, compilers rely on heuristics such as greedy coloring, Chaitin’s algorithm, or linear-scan allocation.

Recent research explores whether Graph Neural Networks (GNNs) or Graph Transformers can outperform classical heuristics by learning structure present in real interference graphs. Our project originally aimed to conduct a meta-study of classical and deep learning–based graph coloring methods for register allocation. Over time, this evolved into a more fundamental problem: existing datasets were not suitable for studying real register interference, either because they were not interference graphs at all (e.g., DIMACS COLOR dataset) or because they contained unrealistic linear-scan approximations of live ranges (IEEE Dataset).

Therefore, the practical contribution of this project shifted toward designing and implementing a pipeline to generate high-quality interference graphs from LLVM IR, producing a dataset that could support machine learning research on register allocation. We additionally implemented coloring algorithms to generate baseline results on this dataset.

Our results demonstrate that real program interference graphs have structural properties absent from synthetic datasets, and that constructing them correctly requires nontrivial handling of SSA, Phi-nodes, per-block liveness, and function call semantics. While we did not complete training of a neural model, we created a working pipeline capable of generating high-fidelity interference graphs suitable for future ML research.


