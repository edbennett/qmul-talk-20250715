# History

-

[![Photograph of statues of Newton and Leibniz](./images/newton_leibniz.jpg) <!-- .element: width="1000px" -->](https://commons.wikimedia.org/wiki/File:Statues_of_Isaac_Newton_and_Gottfried_Leibniz.jpg)

Notes:
Two of the finest scientists of the 17th century.
Both claimed to have invented calculus.
Likely that they both did, independently.
But neither claim could be proven
because the culture was to be secretive about your work
so you could make money by teaching it to those who wanted to learn.

-

![Photograph of the Royal Society's premises in Crane Court](./images/rs.jpg) <!-- .element: width="700px" -->

Notes:
Around the same time,
the Royal Society gets going.
Motto: "Nullius in Verba" - don't take anyone's word for it.
Starts the first scientific journal,
and promotes the philosophy that for your work to be recognised,
you must publish it,
in such a way that anyone can reproduce and understand it.

-

Process $\rightarrow$ Data $\rightarrow$ Analysis $\rightarrow$ Results

Notes:
The form of a paper was supposed to be this:
you explain what you did,
show what data that gave you,
show what you did to the data,
and then present the results of that process.
Simple,
logical,
and in principle anyone skilled in the art could follow it to reproduce you work.

-

![Photograph of a supercomputer](./images/supercomputer.jpg) <!-- .element: width="1200px" -->

Notes:
This was pretty successful for a few hundred years,
creating science as we know it.
Then in the twentieth century,
we taught sand how to think and gave it anxiety.
Great:
we now have (in principle) fully deterministic machines,
so we can share the exact set of steps,
and they can be reproduced precisely,
without the possibility of human error.

-

![Screen shot of a lot of code in very small font, filling the screen](./images/lots_of_code.png) <!-- .element: width="1800px" -->

Notes:
Unfortunately,
the length of instructions is longer than a typical paper,
even before you include the code of others that you're building on top of.

-

Process $\rightarrow$ ⬛ $\rightarrow$ 🪄 $\rightarrow$ ✨Results✨

Notes:
This,
and some early missteps like
"treating the computer like a piece of lab equipment",
meant that adopting computers actually reduce reproducibility
rather than improved it.

-

_An article about computational science in a scientific publication is **not** the scholarship itself, it is merely **advertising** of the scholarship. The actual scholarship is the complete software development environment and the complete set of instructions which generated the figures._

&mdash;[attributed to Jon Claerbout, around 1995](https://statweb.stanford.edu/~wavelab/Wavelab_850/wavelab.pdf)

Notes:
"Claerbout" rhymes with "share shout".
Returning to where we would like to be:
many people view papers as the ultimate goal.
But if they don't enable reproducibility,
then it is the supporting work
that forms the actual research.

---

# Definitions

-

## Reproducibility

<span class="fragment fade-in" data-fragment-index="1">Same data</span>
<span class="fragment fade-in" data-fragment-index="2">$+$ same analysis</span>
<span class="fragment fade-in" data-fragment-index="3">$\rightarrow$ Same results</span>

<span class="fragment fade-in" data-fragment-index="4">(from [The Turing Way project](https://the-turing-way.netlify.app/reproducible-research/overview/overview-definitions.html))</span>

Notes:
Reproducibility is when you can take the same data,
run the same analysis on it,
and get the same results out at the end.
This sounds trivial&mdash;if
we can't satisfy this requirement,
are we doing science?
All of science is built on the idea
that we can stand on the shoulders of giants;
if those giants change shape depending on who looks at them,
then we are building on quicksand.

-

## Replicability

New data $+$ same analysis $\rightarrow$ Same results

<br>

## Robustness

Same data $+$ new analysis $\rightarrow$ Same results

Notes:
If we don't have reproducibility,
then these are right out.

-

## Open Science

The movement to make all research accessible to all levels of society.

![Papers](images/paper.jpg) <!-- .element width="200px" -->&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[![Experimental Samples](images/test_tube.jpg) <!-- .element width="200px" -->](https://www.publicdomainpictures.net/en/view-image.php?image=302908&picture=filling-up-the-test-tube)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
![Code](images/photo_of_code.jpg) <!-- .element width="200px" --> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![Data](images/photo_of_data.jpg) <!-- .element width="200px" -->

Notes:
In some sense,
this will always be an unachievable ideal to be strived towards.
The more of society we make our data accessible to,
the more overhead costs pile up.
Try making a petabyte of data downloadable to anyone on the internet
without a business model to pay for the bandwidth and long-term fast storage.

-

## [FAIR](https://www.go-fair.org/fair-principles/)

Data and software should be:

- **F**indable
- **A**ccessible
- **I**nteroperable
- **R**eusable

Notes:
Each of these terms has more detailed definitions;
see the [FAIR Principles](https://www.go-fair.org/fair-principles/).

-

## Persistent identifier

- A long-lasting reference to an object.
- Does not change even if the original moves.
- Ideally, resolves in a web browser.

![DOI](./images/doi.svg) <!-- .element class="fragment" -->

Notes:
You're probably familiar with DOIs as journals give them out for articles
(since journals love to reorganise their websites).

---

# Modest proposals

-

## Croucher’s law

*“I am an idiot and I will make mistakes”*

&mdash;[Mike Croucher](https://mikecroucher.github.io/MLPM_talk/)

Notes:
Human error is inevitable.
We should plan for it,
rather than hope it doesn't affect us.

-

![Comic exhorting us to "automate ALL the things"](./images/automate.png)

(with apologies to [Hyperbole and a Half](https://hyperboleandahalf.blogspot.com))

Notes:
This doesn't bypass human error,
but does make it more detectable and auditable.
We fix an error once,
then it doesn't happen again
(at least for that workflow).
We miss an error,
someone else can spot later exactly where we went wrong.

-

[![Software Carpentry](./images/swc.svg) <!-- .element width="500px" -->](https://software-carpentry.org) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [![Data Carpentry](./images/dc.svg) <!-- .element width="300px" -->](https://datacarpentry.org)

Notes:
This requires some programming.
Fortunately,
there are organisations that can help with learning to do so.

-

[![Logo of the Data Stewards Network](./images/data-stewards.svg) <!-- .element width="400px" -->](https://datastewards.net/)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [![Logo of the Society of Research Software Engineering](./images/socrse-knockout.png) <!-- .element width="400px" -->](https://society-rse.org)

Notes:
There is also professionalisation in those who look after data and software,
and train researchers in how to do so.

-

![Papers](./images/paper.jpg) <!-- .element width="100px"  vertical-align="middle" --> ![right arrow](./images/arrow.svg) ![DOI](./images/doi.svg) <!-- .element width="100px"  vertical-align="text-middle" --> 

![Code](./images/photo_of_code.jpg) <!-- .element width="100px"  vertical-align="text-middle" --> <span class="fragment fade-in" data-fragment-index="1"> ![right arrow](./images/arrow.svg) ![DOI](./images/doi.svg) <!-- .element width="100px" vertical-align="text-middle" --></span>

![Data](./images/photo_of_data.jpg) <!-- .element width="100px"  vertical-align="text-middle" --> <span class="fragment fade-in" data-fragment-index="1"> ![right arrow](./images/arrow.svg) ![DOI](./images/doi.svg) <!-- .element width="100px"  vertical-align="text-middle" --></span>

Notes:
You already get DOIs for your papers,
both from the arXiv and from the journal.
You can do the same thing for your data and the software workflows that process them.

-

[![Screen shot of the article "the war over supercooled water"](./images/supercooled-water.png) <!-- .element width="1000px" -->](https://physicstoday.scitation.org/do/10.1063/pt.6.1.20180822a/full/)

Notes:
In 2011, a discrepancy was found between the results of two groups regarding computing the predited properties of an unexplored part of the phase diagram of water. One group wanted to understand the difference, the other ignored them and kept publishing anyway. In 2013, the former asked the latter for their code to try and understand the source of the discrepancy. They got no response. In 2016, the latter group published in Nature, with the phrase "scripts available on request". The former group asked again, and got nothing, until they approached the editors of Nature to ask the authors to keep their word. Once they had the code, within a week they had narrowed the differences in approach to a handful, and after a couple of months of testing they identified the issue. The more reticent group had made an unusual choice in their initial conditions for their Monte Carlo, and when this was done in the other setup, it gave a similar result. This was published in 2017, shortly after the PI of the latter group had passed away. Had both groups been fully open with their methodology, six years of arguments and bitterness would have been avoided, and everyone could have spent their time on more productive things.

-

[![Title block of a document entitled "The TELOS Collaboration Approach to Reproducibility and
Open Science"](./images/guidance.png) <!-- .element height="500px" -->](https://arxiv.org/abs/2504.01876)

[![GitHub logo](./images/github.svg) <!-- .element height="48px" style="vertical-align: -24px; margin-right: 12px;" --> telos-collaboration/strategy](https://github.com/telos-collaboration/strategy) • [arXiv:2504.01876](https://arxiv.org/abs/2504.01876)

Notes:
It's good to refer to what other groups are doing,
and to discipline-specific guidance where it's available.
For those working in lattice,
our collaboration has documented its approach
and made the guide available online.
The working document is on GitHub;
suggestions for improvement are welcome.

-

![Mathematica logo](./images/mathematica.png) <!-- .element height="200px" -->

Notes:
Like any other programming language,
Mathematica code can be automated.
It may require a change in the way you use it:
if currently you are editing files by hand to change input parameters,
you might look into defining functions and calling them from a wrapper file.
Either way,
your Mathematica notebooks and Wolfram Language scripts
are valuable for others to understand your work,
and should be published.

-

![Plot of M/M0 against Delta, showing blue and black points starting evenlt spaced, but merging pairwise at high Delta, leaving a single black ground state at 1.0.](./images/gg-plot.png) <!-- .element width="600px" -->

Notes:
Similarly,
if you're putting numbers into a plot,
then likely someone may at some point be interested in the values of those numbers.
Publishing them as data allows others to make use of them
without needing to hold a ruler up to your PDF.

-

$$
\begin{align}
a(x) &= a_0 + a_1 x + \dots + a_{100} x^{100} \\\\
b(x) &= b_0 + b_1 x + \dots + b_{100} x^{100} \\\\
&\qquad\qquad\vdots \\\\
z(x) &= z_0 + z_1 x + \dots + z_{100} x^{100}
\end{align}
$$

Notes:
Even if your work is purely analytical,
it's worth thinking about
whether a TeX or PDF file is the best way to share the results.
If you're sharing equations with many terms,
or numbers with decimal places that result from evaluating them,
consider whether you could share these as data,
either as supplementary material to a paper,
or citable separately.

-

![Four-panel comic, of two caped figures with swords facing off. The first, with "GOOD" on their chest, says "We could have been friends, you know." The second, says "No. We couldn't have.", opening their cape to reveal "PERFECT" on their chest.](./images/perfect-good.jpg) <!-- .element height="500px" -->

([Shen Comix](https://bsky.app/profile/shenanigansen.bsky.social/post/3ltwv2ueffc26))

Notes:
The most important thing is to not let the perfect be the enemy of the good. Everyone is embarrassed about the quality of their code, but even imperfect code is better than a completely black box. You can work incrementally&mdash;perhaps in your next paper, you just dump all of the scripts you used on Zenodo and link them in the paper. Then in the next one, you could work to write more documentation to help others be able to run the full analysis without needing to ask you for details. Then you might work to automate it end to end. And then as you start new projects perhaps you take a little extra time to focus on the design of tools so they can be more reusable by others.

---

# Poll

---

## Conclusions

Sharing workflows and data

- brings us closer to the ideals forming the basis of the scientific method
- is increasingly required by funders
- helps others to understand and build on your work
- is not free, but has high benefit:cost
- is easier when making use of guidance
