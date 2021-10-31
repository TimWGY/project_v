## Intro

#### [Man-Computer Symbiosis](http://worrydream.com/refs/Licklider - Man-Computer Symbiosis.pdf) by JCR Licklider

Thoughts: Computers should help humans in **formulative thinking** (by guiding us in intuitive trial-and-error process) and **save time in routinized work** (calculating, plotting, searching, etc). The **difference in "language" and "speed"** between humans and computer pose challenges in the proposed "symbiosis". These observations are still relevant in today's HCI world.

Author also discusses how computer can **work with team of humans**. Author proposed to develop technologies such as writing interface, wall display, natural language understanding, which are becoming mature now after half a century. To what extent these technologies are applied and to what level has the symbiosis developed requires more examination.

#### [The Data Lifecycle](https://hdsr.mitpress.mit.edu/pub/577rq08d/release/3) by Jeannette M. Wing

> *Data science is the study of extracting value from data.* “Value” is subject to the interpretation by the end user and “extracting” represents the work done in all phases of the *data life cycle*.

Generation -> Collection  -> Processing  -> Storage  -> Management  -> Analysis  -> Visualization -> Interpretation

Thoughts: There are many stages before data reach data analysts' desktops. Paying attention to **data generation and collection** process not only helps greatly with cleaning and feature engineering, but also the interpretation of results and reflection of limitations. 

**Storage and management** is becoming increasingly important as we are creating larger and faster datasets, building longer and more complex analytical pipeline. How to store (and not to store) data, how to manage their structures and versions. These questions affect scale and efficiency bottleneck both in computing power and human collaboration.

What really inspired me is that Prof. Wing list **visualization and interpretation as two separate stages** in the lifecycle. This makes sense to me as I found many EDA tools that generate an array of graphs but no interpretation. Interpretation is inherently a human job. While graphs have their implicit message, especially when designed intentionally, the interpretation still needs to be mediated by person who is familiarized with the lifecycle. Alternatively, if we truly want to design automatic EDA tools, we need to consider how to **integrate critical interpretation and reflection** alongside the graphs generated.  

#### [Agency plus automation: Designing artificial intelligence into interactive systems](https://www.pnas.org/content/pnas/116/6/1844.full.pdf) by Jeffrey Heer

Summary: 

For humans and computers to collaborate, there is a trade-off to make: how automated should computer programs be, how much agency and control should human users retain?

Successful "Automation + Agency" integration can be achieved by automatic reasoning + user-centered interactive systems. 

The challenge to achieve such goal are:

1. Research community focus mostly on developing full automation.
2. Users want to feel in control and not interrupted in their workflow.
3. Too much automation/recommendation discourage thinking.

Some solutions/tools are proposed by the author: 

1. Domain Specific Language (DSL)
   1. Formalize specification and user action model
   2. "Shared representation" for humans and machines
2. Machine Learning Artificial Intelligence Searching Models 
   1. Models that search through space defined by/in DSL to predict possible next steps of the user
3. Graphic Interface that Maps DSL to Intuitive Visuals
   1. ... such that user can review and act upon machine output more effeciently

Author gives 3 case studies:

1. Data Wrangling
2. Exploratory Data Analysis
3. Machine Translation

Future Steps:

1. Build inference, learning, monitoring, model management services so as to reduce the prototyping/developing efforts
2. Construct shared representation of data in data-driven manner
3. * Help promote interpretability and skill acquisition of novices
4. * Use appropriate design to encourage critical engagement in face of automated decision support

Thoughts: 

One of the key takeways for me is that "users want to feel in control and not interrupted in their workflow". I used to think full automation is a plausible idea and machine should be more proactive in mixed intiative data exploration. But after trying many solutions and my own tools, I found myself easy to **drift away from my analytic goal**, distracted by computer-generated recommendations and went on to explore less pertinent aspects of the data. Some solution has an intention detection mechanism which may help user be more focused in their analysis, but I find most **intention detection mechanism** less accurate. Having computer second-guessing my intention by observing my actions is fine when I have a rough idea of what to explore, but it could be frustrating if I have a clear idea, but **could not get my AI counterpart to understand my idea precisely** and execute it. **Teaching the AI through examples** may take more time and thinking than writing out fully-specified codes.

In a purely exploratory settings, I tend to gravitate towards the graphs that are shown to me first, **only to realize there is a better way** to formulate the question / visualize the phenomenon at a much later stage, **when I think abstractly and independently**. This resonates with the observation author made about "automation discourages thinking". 

**Clicking and scrolling** is so "natural" and "intuitive" that we become lazy thinkers. Once we see a potential insight from one of the graphs, our confirmation bias will nudge us towards those graphs verify this "insight". The innoccent computer, with **no knowledge about the meaning and assumptions of underlying data**, picks up this intention and feeds users with more related graphs. This works just like how certain algorithms powering the social media could strengthen stereotypes. This is why designing interface that encourages critical engagement and training intelligent reasoning machine is so important. 

#### [Support the Data Enthusiast: Challenges for Next-generation Data-analysis Systems](http://www.vldb.org/pvldb/vol7/p453-morton.pdf) by Kristi Morton et al.

Takeaways:  Goals for the next-generation systems proposed: "1) support visual and interactive data exploration 2) **recommend relevant data to enrich visualizations** 3) facilitate the **integration and cleaning** of datasets." Authors emphasize the importance of combining these features in an **"uninterrupted data analysis cycle"**, which coincide with the point made in "Automation + Agency" paper. 

Today's challenge / motivation for proposed goals: visual analytics services have high "churn rate", many used once and never return. Reasons include: 1) current services lack adequate data cleaning capabilities (mostly because preset data are cleaned already) 2) no recommendation for datasets to integrate with the current data 3) even if a user find new dataset, joining capabilities are primitive. Personally, I believe another reason is that visualization interfaces are not playful enough, some **elements of gamification** and goal-setting mechasim will make users want to **explore more and have ownership over the work** they have done.

The **complex transformations to get data ready for plotting cause disruptions** to the analysis cycle. Preemptive computation to automate some transformations is wasteful and relatively slow in a real-time interactive environment. Once transformations are defined by one user, should we share the same cleaning procedure to other users of the same data? **Version management and quality validation** are key considerations.

Recommendation of new datasets may draw from "schemas, axis labels, annotations, domain of values being visualized, primary keys, or aggregation/filters/projections used" but also "**collaborative filtering**" based on actions of **similar users** or **users in similar situations**.

Author argues for the necessity of **a formalism that unifies** the above fuctionalities, while acknowledging that these funtionalities are usually conducted "using different interfaces and yield very different actions". **VizQL**, the formalism underlying Tableau, is quoted as a partial example. Another interesting observation is that different functionalities may have **different time-scales**. Dataset recommendations based on entity resolution may take much longer to train and run compared to other analytical tasks. 

<br><br><br>

## Tasks

#### [A Multi-Level Typology of Abstract Visualization Tasks](https://www.cs.ubc.ca/labs/imager/tr/2013/MultiLevelTaskTypology/brehmer_infovis13.pdf) by Matthew Brehmer, Tamara Munzner

Visualization process decomposed as chains of actions, made of three types of elements (why, how, what) at different levels of abstraction. This new topology is argued to inform better design workflow and evaluation strategy, to "describe", "generate", "evaluate" as the authors summarized.

**Simplied model:**

... -> Input -> ( Why -> How ) -> Output/Input -> ( Why -> How ) -> Output -> ...

What = Input/Output, Why and How correspond to the ends and means of a task.

**Why:**

High level: Consume (present, discover, enjoy) + Produce 

Mid level: Search (lookup, browse, locate, explore) ** Interesting definition, using 2D matrix of whether target and location is known or not.*

Low level: Query (identify, compare, summarize)

**How:**

Manipulate: select, navigate, arrange, change, filter, aggregate

Introduce: annotate, import, derive, record

Encode: encoding (visual encoding etc.)

**Limitations** of extant visualization taxonomy system:

Gap between high and low level of abstraction tasks. * This paper propose to mark High-Mid-Low level "why" tasks at every stage, which is very innovative. 

Lack of expression for sequences and dependencies. * This paper suggests that the use of "what" solve the sequence problem naturally. It's interesting to think that this input/output typology can support not only chain of actions, but also trees of actions, with branching representing diverging thoughts analyst may have during exploratory analysis.

**Theoretical foundations:**

*\*Distributed Cognition*, Stages of action, Sensemaking, *\*Play theory*

The idea of distributed cognition really excites me. I especially like how authors refer epistemic actions to "the process of coordination between internal mental models and external representations". A definition from Wikipedia describes distributed congition as when "cognition is off-loaded into the environment through social and technological means". I have been intrigued by this idea of facilitating mental and phyiscal cognitive representation for a while. In the refereneces, I identified a list of related literature in this direction, which will be covered in this doc. 

- J. Hollan, E. Hutchins, and D. Kirsh. Distributed cognition: toward a new foundation for human-computer interaction research. *ACM Trans. Computer-Human Interaction (TOCHI)*, 7(2):174–196, 2000.

- J. J. Thomas and K. A. Cook. *Illuminating the Path: The Research and*

  *Development Agenda for Visual Analytics*. IEEE, 2005.

- G.Klein,B.Moon,andR.R.Hoffman.Makingsenseofsensemaking2: A macrocognitive model. *IEEE Intelligent Systems*, 21(5):88–92, 2006.

- A. Perer and B. Shneiderman. Integrating statistics and visualization for exploratory power: From long-term case studies to design guidelines. *IEEE Trans. Computer Graphics and Applications (CG&A)*, 29(3):39– 51, 2009.

- Z. Liu and J. T. Stasko. Mental models, visual reasoning and interac- tion in information visualization: a top-down perspective. *IEEE Trans. Visualization and Computer Graphics (TVCG)*, 16(6):999–1008, 2010.

- M. Pohl, M. Smuc, and E. Mayr. The user puzzle: Explaining the in- teraction with visual analytics systems. *IEEE Trans. Visualization and Computer Graphics (TVCG)*, 18(12):2908–2916, 2012.

Another theoretical foundation that is innovative from my perspective is the play theory. The authors talk about the casual readers of visualization, which I believe will become increasingly mainstream as the data generation (IoT, social media), display technology (ubiquitous computing surface, VRAR), and visualization techniques develop in today's world. I am interested in how insights from game design and gamification may bring values to visualization design.



#### [The Eyes Have It](https://www.cs.umd.edu/~ben/papers/Shneiderman1996eyes.pdf) by Ben Shneiderman

Published in 1996, this is quite a foresighted paper. 

The author proposes his famous *Visual lnformation-Seeking Mantra: overview first, zoom and filter, then details on demand", and add Relate, History, Extract to the tasks. Then, he discusses how the tasks apply to seven types of data (1-, 2-, 3-dimensional data, temporal and multi-dimensional data, and tree and network data). Together, the tasks and types form the *type by task taxonomy (TTT)*. 

Many of the ideas have been implemented and taken for granted for today's visualization tools. But there are some new lessons learned for me. 

1. Author commented on two challenges of creating good 3-dimensional scattergrams:  "disorientation (especially if the users point of view is inside the cluster of points)" and "occlusion (especially if close points are represented as being larger)". Last week, I have worked on a [3D scatter plot](https://github.com/TimWGY/r_world) myself, and I always felt the plot is good enough for sensemaking. The author has articulated the problems better than I do, and now I will look into literature on these two problems to see how I can improve.
2. The section on tree data ties together concept of plots that I used to think separately. Animated hyperbolic trees, cone tree, treemaps may look very different visually, but they all serve the purpose of visualizating hierarchy structure. I recently visualized the Google folder of long-term team projects, with the goal of understanding its structure, storage usage, update pattern, so that we can design better data management protocol. The visualization of such wide & deep directory is very challenging, especially the trade-off between keeping a sensible structure and providng enough detail. After reading this paper and searching the term "animated hyperbolic tree", I found [this paper](http://www.ramanarao.com/papers/startree-chi95.pdf) and [this interactive example](https://glouwa.github.io/d3-hypertree-examples/feature-slides/rslidy.html#10), which demonstrates a focus strategy that could really helps with my struggle with large directory visualization.
3. I also like the quote "Smooth zooming helps users preserve their sense of position and context." I think this corroborates my dislike of the plotly zoom via selection feature. I can see my selection highlighted right before triggering zooming, but the zooming happens in a flash as soon as I release my mouse, and now I am looking at a corner of the canvas without knowing the context. Something like how you do a smooth zoom in datashader is more natural to me. Another project that I came across at Columbia C4SR [In Plain Sight](https://dsrny.com/project/in-plain-sight) also use smooth zoom to put visualizations of very local areas in the larger context of the globe, which show the power behind this technique.
4. The author proposes that we should "allow extraction of sub-collections and of the query parameters". This is quite foresighted because one trend in visualization community right now is to use declarative languages and create specifications of visualizations such that they can be rendered efficiently client-side and server-side, cross-platforms, and support interactive and automatic transformations. Managing the specifications and share and re-apply them may be the next challenge. 
5. Finally, when discussing advanced filtering and dynamic queries, author describes a filter-flow model that aims at making complex boolean expressions more intuitive. I believe this is a terrific idea because its makes the abstract operations tangible. If we make the rendering of this filter-flow model real-time as user compose the filter expression, user can see how the query will change the sub-population size and potentially some other relevant features, which expedite their exploration and decision-making process. Interestingly, I found very limited follow-up literature on this model after [author's paper](http://www.cs.umd.edu/hcil/trs/92-07/92-07-published.pdf). There is an [evaluation study](https://dl.acm.org/doi/pdf/10.5555/2532129.2532136) in 2013 but I believe it missed the point of filter-flow model by simplifying it to a graphical programming interface model. I plan to experiment with visual filter-flow model in my [nl4ds project](https://github.com/TimWGY/nl4ds) to build more intuitive complex filtering. 

I realized that I need to pick up the pace with reading, so I plan to write more brief reflections for the papers to come, except when I really have something to express.

