# Backup slides

-

# Lattice

-

$$\int \mathcal{D}[\Phi] \mathrm{e}^{-S[\Phi(x, t)]} O[\Phi(x, t)]$$

Notes:
Computational quantum field theorists only want one thing
and it's analytically incalculable.

-

<div style="float: left; width: 60%; height: 100%; vertical-align: middle;">

$$\int \mathcal{D}[\Phi] \mathrm{e}^{-S[\Phi(x, t)]} O[\Phi(x, t)] \\\\
= \lim_{N\rightarrow\infty} \frac{1}{N} \sum_{n=1}^{\infty} O[U]$$

</div>

<div style="float: right; width: 40%; height: 100%; vertical-align: middle;">

![A three-dimensional lattice of points](./images/lattice.svg) <!-- .element style="width: 100%;" -->

</div>

Notes:
So what do?
Computers hate integrals,
so let's discretise everything.
Firstly,
discretise the spacetime to a lattice of points.
Then,
discretise the integral,
so we instead sum over some finite number of samples,
distributed with probability weight $\mathrm{e}^{-S[\Phi]}$.
(Note we Wick rotate to Euclidean time so the action can be real.
If $S[\Phi]$ is complex,
e.g. has a chemical potential,
the problem is harder.)
And we can't put Grassman variables into a computer,
so we have to integrate out the fermion fields,
so the state of the system is just the gauge field,
which sits on the links between adjacent sites.

-

- Ensemble: $O(1000)$ configurations
- Typical volume: $96 \times 48^4$
- Space-time dimensions: 4
- $\mathrm{SU}(3)$: $3 \times 3 \times 2$ real numbers
- Double precision: 8 bytes per number

Total: 5.5TiB <!-- .element class="fragment" -->

$O(100\mathrm{k})$ GPUh <!-- .element class="fragment" -->

Notes:
So if the gauge field is the state of our system,
we need to store it so that we can compute observables on it.
Since many observables can be computed on it,
we don't want to throw it away,
but instead share it so that others can make use of it.
But since we typically want more than one point per observable,
we need multiple ensembles.
How do we share tens of terabytes of data?

-

![ILDG logo](./images/ildg.svg) <!-- .element height="100px" -->

![Map of the world showing ILDG regional grids](./images/ildg-map.svg) <!-- .element height="500px" -->

Notes:
The International Lattice Data Grid defines
specifications on how to exchange gauge configurations.
They also provide an identity management service,
and reference implementations for a standards-compatible
metadata catalogue and file catalogue.
The task of deploying these,
and providing storage elements to actually host the binary configurations,
is delegated to Regional Grids.
Currently,
communities are gradually trying to restart their Regional Grids,
after a period of unfunded inactivity.

-

<div style="float: left; width: 40%; height: 100%; vertical-align: middle;">

![Three-dimensional operator with a line connecting sites in the shape of a "+" outlined](./images/lattice_operator.svg)

</div>

<div style="float: left; width: 60%; height: 100%; vertical-align: middle;">

![Zenodo logo](./images/zenodo.svg) <!-- .element height="100px" class="fragment" -->

![Illustration of a piece of text showing citations to software as described in the notes](./images/name-software-with-modifications-editable.svg) <!-- .element height="300px" class="fragment" -->

</div>

Notes:
Once we have generated our ensemble of field configurations,
we then need to actually compute observables on them,
so we can perform the ensemble average that will approximate the integral.
The output of this will typically be much smaller than the configuration,
and the process will require access to the configurations and to HPC resources,
so we will want to share the output of this
so that others can reproduce our subsequent analysis.
Where can we do this?
[click]
Zenodo is one possible location:
it is hosted by CERN,
so is going to be around for a while,
and provides DOIs for records.
Its capacity is limited,
so we can't store configurations there,
but for up to 50GiB per paper it's a good choice.
What about if we want others to be able to reproduce these computations?
[click]
It's not sufficient to describe the algorithm used,
as implementations vary.
We must specify the name of the software used,
so that others may find it.
Even if that software isn't released publicly
(which it should be),
having a name lets readers know if different work used the same software
Specifying a version number lets others know what later changes
you won't have had incorporated when you ran the code.
And providing any changes you made to the software is crucial.

-

![Image showing a diagram of a 3D lattice of points with an arrow pointing to the ILDG logo](./images/lattices-to-ildg.svg) <!-- .element width="400px" -->

![Diagram showing icon representing large blocks of data with an arrow pointing to the HDF5 logo](./images/hdf5-for-more.svg) <!-- .element width="600px" -->

![Diagram showing icons illustrating columned data and plots on the left, with arrows pointing to a CSV file icon on the right](./images/csv-for-columns.svg) <!-- .element width="300px" -->

Notes:
Your data release wants to have raw data,
final data,
metadata and analysis parameters,
and potentially also input files for the HPC computations that led to the raw data.
In terms of data formats,
we already discussed that for configurations we use the ILDG standard formats.
In terms of what we include in our data release,
large data should ideally be packed into a standardised binary format like HDF5.
If your HPC code doesn't produce data such a format,
you can package it,
but it's good to also include the original raw data
in case anything was lost or corrupted in the translation.
Smaller data,
in particular those that non-computational specialists may want access to,
should be a plaintext tabular format like CSV,
that is widely supported by spreadsheet software
in addition to more programmatic data analysis tools.

-

Data $\rightarrow$ ⬛🪄 $\rightarrow$ ✨Results✨

Notes:
Now we have our data in order,
we need to open the black box and look at the analysis more closely.

-

![Plot with default matplotlib style](./images/matplotlib-plot-default.svg) <!-- .element height="300px" -->

![Plot styled to look like in a paper](./images/matplotlib-plot-paper.svg) <!-- .element height="300px" class="fragment" -->
![Plot styled to have a dark background](./images/matplotlib-plot-dark.svg) <!-- .element height="300px" class="fragment" -->

Notes:
Here's a plot in the default Matplotlib plot style.
What if we want it to be more consistent with our paper
[click]
or look good on a presentation with a dark background?
[click]

-

<div style="float: left; width: 700px">

```python
$ head plot_script.py
import matplotlib.pyplot as plt

plt.rcParams["figure.figsize"] = (7, 4)
plt.rcParams["font.size"] = 16
plt.rcParams["axes.labelsize"] = 16
plt.rcParams["legend.fontsize"] = 16
plt.rcParams["lines.markersize"] = 2.0
plt.rcParams["lines.linewidth"] = 0.8
plt.rcParams["lines.markeredgewidth"] = 0.8
plt.rcParams["font.family"] = "lmodern"
plt.rcParams["text.usetex"] = True
plt.rcParams["errorbar.capsize"] = 2
```

</div>

<div style="float: right; width: 500px;" class="fragment">

```python
$ head paper.mplstyle
figure.figsize: 7, 4
font.size: 16
axes.labelsize: 16
legend.fontsize: 16
lines.markersize: 2.0
lines.linewidth: 0.8
lines.markeredgewidth: 0.8
font.family: lmodern
text.usetex: True
errorbar.capsize: 2

$ head plot_script.py
import matplotlib.pyplot as plt
plt.style.use("./paper.mplstyle")
```

</div>

Notes:
One way to achieve this would be 
to manually specify the sequence of formatting options
in each Python script,
or write a helper function to do this.
[click]
But a function to do this is already built into Matplotlib:
you can define a style file containing all your preferences,
and load it in one line each time you plot.
You don't have to use Matplotlib of course;
similar functionality is built into most plotting tools.
The important thing is that you are not manually massaging data.

-

<pre>
Ensemble M1:
mass: 3.1415 ± 0.0926
decay constant: 5.35897 ± 0.00932
Ensemble M2:
mass: 3.84626 ± 0.04338
decay constant: 3.27950 ± 0.00288
Ensemble M3:
mass: 4.1971 ± 0.6939
decay constant: 9.3751 ± 0.0582
Ensemble M4:
mass: 0.97494 ± 0.04592
decay constant: 3.078 ± 0.164
</pre>

</div>

$\downarrow$

<div>

<table>
<tr><th>Ensemble</th><th>$m$</th><th>$f$</th></tr>
<tr><td>M1</td><td><span class="fragment">0.3142(93)</span></td><td><span class="fragment">5.3590(93)</span></td></tr>
<tr><td>M2</td><td><span class="fragment">3.846(43)</span></td><td><span class="fragment">3.2795(29)</span></td></tr>
<tr><td>M3</td><td><span class="fragment">4.20(69)</span></td><td><span class="fragment">9.375(58)</span></td></tr>
<tr><td>M4</td><td><span class="fragment">0.975(46)</span></td><td><span class="fragment">3.08(16)</span></td></tr>
</table>

</div>

Notes:
What about tables?
In a manual workflow,
you might consider transcribing number by hand into your LaTeX documents
from a log file like the one at the top,
or you might drag a CSV file into a table generator,
and copy and paste the result into your paper.
But there's a more automated, reproducible way to do this too.

-

```python
df.to_latex("assets/tables/table1.tex")
```

$\downarrow$

```tex
\begin{table}
    \caption{A spectrum.}
    \input{assets/tables/table1.tex}
\end{table}
```

Notes:
Your code can output a LaTeX file directly,
and the resulting file can be read in from your paper.

-

<div class="r-stack" style="float: left;">

![A paper extract with the text "We find that $g_\mu = 0.0314(15)."](./images/implausible-result.svg) <!-- .element class="fragment fade-out" data-fragment-index="3" width="450px" -->

![A paper extract with the text "We find that $g_\mu = 0.0271(82)."](./images/different-implausible-result.svg) <!-- .element class="fragment current-visible" data-fragment-index="3" width="450px" -->

</div>

<div style="float: right;">

<div class="r-stack" style="width: 600px;">

```tex
\newcommand \gmuResultFinal 0.0314(15)
```
<!-- .element class="fragment current-visible" data-fragment-index="2" -->

```tex
\newcommand \gmuResultFinal 0.0271(82)
```
<!-- .element class="fragment current-visible" data-fragment-index="3" -->

</div>

$\downarrow$ <!-- .element class="fragment" data-fragment-index="2" -->

```tex
\input{definitions.tex}

\begin{document}
We find that $g_\mu = \gmuResultFinal$.
```
<!-- .element class="fragment" data-fragment-index="2" -->


Notes:
We can take this a step further.
Frequently we want to quote numbers in the text of our documents.
Since these numbers will usually be the result of our analysis workflow,
we'd prefer if they could be generated automatically.
In particular,
if you quote many numbers in the text,
or quote one number in many places,
it can be challenging to keep them all consistent by hand
as the analysis is updated.
Similarly to tables,
we output a `.tex` file,
[click]
but in this case we use `\newcommand` to define a macro
that we can use wherever we want to quote a particular number.
When the workflow is re-run,
[click]
updating the `.tex` file will update the numbers everywhere they are used.

-

![Flowchart of the steps in a typical lattice computation](./images/workflow-diagram.svg)

Notes:
Here's a representative, relatively simple lattice analysis workflow.
Each input file might be used to compute multiple observables,
but all classes of file might not be present for all ensembles.
Each output plot may depend on a different subset of ensembles,
or a different set of intermediary parameters.
How might we approach analysing this?

-

![Hands at a keyboard](./images/finger-pressing-computer-keyboard.jpg) <!-- .element height="600px" -->

Notes:
The most naive approach would be to manually invoke each computation by hand.
This would be quite laborious,
and as we discussed earlier,
is prone to errors.
If the data or one of our tools changed,
we'd need to work out what to re-run,
and make sure all the old data were purged.

-

~~~ bash
#!/bin/bash

for ensemble in $(cat ensembles)
do
    for channel in $(cat channels)
        do
        python -m analysis.compute_mass ${ensemble} ${channel} \
            > results/${ensemble}/${channel}.dat
        # ...
    done
    # ...
done

# ...
~~~

Notes:
A shell script is a step up from doing everything by hand,
and is much more auditable later.
Equally,
we could write a Python program that imports our various tools as libraries,
and encode the entire analysis as a Python program that way.
This does however mean that if even if most of our data and code haven't changed,
we still need to re-run everything.
And even if we have steps that don't depend on each other,
we can't easily utilise parallelism and run them at the same time.
We could try and implement such functionality,
checking modification dates,
caching last run times,
and spinning out parallel processes at various points,
but that's a lot of functionality that isn't our specialism&mdash;surely
someone else has encountered this problem before?

-

![Snakemake](./images/snakemake.svg) <!-- .element height="300px" -->

Notes:
Indeed they have;
the problem is "workflow management",
and there is entire zoology of "workflow managers"
that solve some or all of the issues described,
as well as a host of other difficulties.
One popular example,
and one that maps reasonably well to lattice problems,
is Snakemake.

-

~~~ snakemake
plot_styles = "styles/paper.mplstyle"

rule mpcac:
    input:
        data="raw_data/correlators.h5",
        script="src/fit_mpcac.py",
    output:
        data="intermediary_data/{ensemble}/mpcac.json",
        eff_mass_plot="intermediary_data/{ensemble}/mpcac_effmass.pdf",
    conda:
        "envs/fitting.yml"
    shell:
        (
            "python {input.script} {input.data} --output_data {output.data} "
            "--plot_file {output.eff_mass_plot} --plot_styles {plot_styles}"
        )
~~~
<!-- .element style="height: 420px;" -->

~~~ shellsession
snakemake --cores 1 --use-conda intermediary_data/Nf2DB4M2/mpcac.json
~~~

Notes:
In Snakemake,
for each piece of functionality in your workflow,
like "fit a correlator"
or "plot a graph",
you define a rule explaining what inputs it takes,
what outputs it gives back,
and how to run it.
When you ask for a file,
Snakemake works out what rule to run, and runs it.

-

~~~ snakemake
rule all:
    input:
        "assets/plots/mpcac_scan.pdf",


rule mpcac_scan_plot:
    input:
        data=expand("intermediary_data/{ensemble}/mpcac.json", ensemble=ensembles),
        script="src/plot_mpcac.py",
    output:
        plot="assets/plots/mpcac_scan.pdf",
    conda:
        "envs/plotting.yml"
    shell:
        (
            "python {input.script} {input.data} "
            "--plot_file {output.plot} --plot_styles {plot_styles}"
        )
~~~
<!-- .element style="height: 480px;" -->

~~~ shellsession
snakemake --cores 6 --use-conda
~~~

Notes:
If you don't specify a file to build,
Snakemake looks at the first rule in the file
(similarly to `make`),
which is conventionally called `all`.
When you ask for a file that depends on many other files,
Snakemake builds a directed acyclic graph
(DAG)
of the steps needed to achieve it,
and then runs all of the needed steps.
It can use multiple CPU cores to achieve this;
it can also farm work out to clusters.

-

```shellsession
$ cp ensemble1/effective_mass_g5.pdf ../paper/effective_mass_g5_ensemble1.pdf
$ cp ensemble2/effective_mass_gk.pdf ../paper/effective_mass_gk_ensemble2.pdf
$ cp code/analysis/spectrum_summary.pdf ../paper/
$ cp code/analysis/spectrum_summary.tex ../paper/
$ cp code/analysis/metafit.pdf ../paper/
$ cp code/analysis/spectrum_definitions.tex ../paper/
...
```

Notes:
Now,
we've taken steps to generate all of our results automatically,
but there are still some things we're having to do manually&mdash;namely,
keeping all of the TeX and image files we're generating in sync.
If each file is manually copied in when it is changed,
then it is all too easy for some to be forgotten,
meaning that our paper is in an inconsistent state,
where different figures reflect different underlying data.

-

```
$ tree assets
assets
├── definitions
│   └── spectrum.tex
├── plots
│   ├── effective_mass_g5_ensemble1.pdf
│   ├── effective_mass_gk_ensemble2.pdf
│   └── spectrum_summary.pdf
└── tables
    └── spectrum_summary_table.tex

4 directories, 5 files
```

```tex
\includegraphics{assets/plots/spectrum_summary.pdf}
```

Notes:
To avoid this,
it can be a good idea to generate all outputs to be included in a publication
in a single `assets` directory.
This can then be deleted from your LaTeX project and replaced afresh
each time you run your workflow.
When you're ready to publish,
you can also delete the `assets` directory generated by the workflow
and regenerate it completely from scratch,
to make sure that no leftover files from previous runs are present.
There are a couple of things to be careful of:
firstly,
make sure your filenames are all different,
even if they are in different directories.
Otherwise the arXiv will refuse to render your file.
Secondly,
if you publish in Physical Review,
the upload tool completely ignores directory structure,
so the preview PDF will fail to generate.
This doesn't matter&mdash;you can proceed without this,
as the editorial office will do the compilation,
but it's annoying and I've complained at APS repeatedly about this.

---

# Example

-

## [arXiv:2410.19484](https://arxiv.org/abs/2410.19484)

![Screenshot of the cover of the above linked paper](./images/2410.19484.png) <!-- .element width="500" -->

![Screenshot of a section of the above linked paper reading "Research Data Access Statement The data generated for this manuscript can be downloaded from Ref. [14], and the workflow used to analyse it from Ref. [15]. The analysis workflow used to analyse the open data at Ref. [12] is available from Ref. [16]."](./images/2410.19484_data.png) <!-- .element width="1000" -->

Data: [doi:10.5281/zenodo.13128505](https://doi.org/10.5281/zenodo.13128505)

Workflow: [doi:10.5281/zenodo.13128384](https://doi.org/10.5281/zenodo.13128384)

-

## Other examples from TELOS

- [Phys.Rev.D 110 (2024) 074504](https://doi.org/10.1103/PhysRevD.110.074504): [Data](https://doi.org/10.5281/zenodo.13349269), [Workflow](https://doi.org/10.5281/zenodo.13349298)
- [Phys.Rev.D 110 (2024) 074509](https://doi.org/10.1103/PhysRevD.110.074509): [Data](https://doi.org/10.5281/zenodo.11048346), [Workflow](https://doi.org/10.5281/zenodo.11048300)
- [Phys.Rev.D 109 (2024) 094517](https://doi.org/10.1103/PhysRevD.109.094517): [Data](https://doi.org/10.5281/zenodo.10932404), [Workflow](https://doi.org/10.5281/zenodo.10932408)
- [Phys.Rev.D 109 (2024) 094512](https://doi.org/10.1103/PhysRevD.109.094512): [Data](https://doi.org/10.5281/zenodo.10819721), [Workflow](https://doi.org/10.5281/zenodo.10929539)
- [Phys.Rev.D 108 (2023) 094508](https://doi.org/10.1103/PhysRevD.108.094508): [Data](https://doi.org/10.5281/zenodo.8136452), [Workflow](https://doi.org/10.5281/zenodo.8136514)
- [Phys.Lett.B 835 (2022) 137504](https://doi.org/10.1016/j.physletb.2022.137504) and [Phys.Rev.D 106 (2022) 094503](https://doi.org/10.1103/PhysRevD.106.094503): [Data](https://doi.org/10.5281/zenodo.6678411), [Workflow](https://doi.org/10.5281/zenodo.6685967)
- [Phys.Rev.D 106 (2022) 014501](https://doi.org/10.1103/PhysRevD.106.014501): [Data](https://doi.org/10.5281/zenodo.6637515), [Workflow](https://doi.org/10.5281/zenodo.6637743)

-

![Plot of M/M0 against Delta, showing blue and black points starting evenlt spaced, but merging pairwise at high Delta, leaving a single black ground state at 1.0.](./images/gg-plot.png)

---

# Summary

-

## Data

- Sharing data is good
  - Put a data release on Zenodo
  - Include your raw, unmodified data
  - Include final results, anything that's plotted or tabulated
  - Include metadata and other inputs to your analysis workflow
  - Cite the DOI in your paper

-

## Workflows

- Automate your workflows
  - Use plot styles
  - Output tables and definitions to `.tex`
  - Keep outputs in a single directory, linked into your LaTeX project
  - Snakemake is your friend
  - Use small components
  - Translate manual steps to data
- Share them once they're done
  - Use Zenodo
  - Cite the DOI in your paper
- Working reproducibly takes work but this pays off

-

## Further reading

- Lattice Virtual Academy lecture slides
  on Reproducibility and Open Science:
  https://edbennett.github.io/lava-ros-lectures/
- The TELOS Collaboration Approach
  to Reproducibility and Open Science
  [arXiv:2504.01876](https://arxiv.org/abs/2504.01876)

Notes:
I've only scratched the surface,
there's a lot more discussed in the notes above,
and likely plenty more things that aren't even on my radar.
