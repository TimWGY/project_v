### Intro

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



