# Practice Session 01: Cytoscape Basics

## Contents

0. About Cytoscape
1. Importing a network
2. Editing nodes and edge styles
3. Performing basic network analysis
4. Using a Cytoscape app (ClusterMaker2)

### Datasets for this session

* File [karate.gml](data/karate.gml)
* File [starwars.graphml](data/starwars.graphml)
* File [us_companies_ownership.csv](data/us_companies_ownership.csv)

# 0. About Cytoscape

[Cytoscape](http://www.cytoscape.org/) is an open source software platform for visualizing complex networks and integrating these with any type of attribute data.

You can look up the user manual at https://manual.cytoscape.org/en/stable.

First time you put your hands on cytoscape? This document can help [Cytoscape_fast_guide](https://github.com/jarlandi/sna-upv/blob/main/laboratory/session-1/cytoscape_fast_guide.md).

:warning: It is recomended to save your work in a session file (*.cys).

# 1. Importing a network

Before importing, we will have a fast look at the dataset file contents (just clik on the links above to open in the web browser). You will find three different data formats.

### Import Zachary's karate club network

Let's start with a simple case: [Zachary's Karate Club](https://en.wikipedia.org/wiki/Zachary%27s_karate_club). This was a Karate Club with a sensei (#1) and a club president (#34) that split into two: some people remained with the sensei, and the others created a new club with the club president.

It will be treated as an undirected newtwork.

* `File > Import > Network from File ...`.
* Select `karate.gml`.
* `Layout > Compound Spring Embedder`.
* Look at the graph and try to figure out if there is anything special about nodes 1 and 34 (you can pick and drag nodes to get a better view).
* [**REPORT**] Include this graph in your report plus a brief paragraph indicating whether nodes 1 and 34 have visually anything special.
* [**REPORT**] The Compound Spring Embedder is an algorithm derived from force-directed graph layout algorithms. Read the Wikipedia page on [force-directed graph drawing](https://en.wikipedia.org/wiki/Force-directed_graph_drawing) and explain in one paragraph, in your own words, how this works.

:warning: Do not use screenshots to catch images for the report; use `File > Export as image` instead (only the visible area of the graph is exported).

:warning: Be brief in all your commentars.

### Import the Star Wars characters network

This is a compilation of characters that appear in a Star Wars movie. The *scene* attribute (column in Table View) means the number of scenes the characters share or in which they are mentioned.

It will be treated as an undirected newtwork.

* `File > Import > Network from File ...`.
* Select `starwars.graphml`.
* If asked, select *shared name* for the node identifier column. This will transform node identifiers into a column named "shared name" internally.
* `Layout > Prefuse Force Directed Layout > All nodes > scenes`. The view should have been slightly improved.
* Find nodes with degree larger than *D=30*. Use the `Filter Panel` (in `Control Panel`). Apply and check the effect of the `select/show` selection (at bottom) on the graph view.
* Create an annotation indicating a character having a degree larger than *D*: on the graph, right click on blank space -> add text; modify the text in `Annotation Panel` (in `Control Panel`); then right click on the text -> add arrow.
* [**REPORT**] Include this graph in your report. 
* [**REPORT**] Include a list of the characters represented by nodes with degree larger than *D* (shared name, name, and number of scenes) and a brief commentary of what kind of characters they are.

### Import US companies ownership network

This network represents	 company co-ownership in the US.

It can be treated either as a directed or undirected newtwork.

* `File > Import > Network from File ...`.
* Select `us_companies_ownership.csv`.
* Click `OK` and accept default import (it should take less than a minute).
* [**REPORT**] Do you see more than one connected component (groups of interconnected nodes)? What do connected components represent in this graph?
* [**REPORT**] Include a brief commentary on large-degree nodes in this graph, which are they or where are they located in the graph? What do those nodes represent?
* `Layout > Edge Weighted Spring Embedder` :warning: This might take up to 20 minutes in a 8-core CPU, so better if you do this out of the laboratory hours (Cancel button works well).
* [**REPORT**] Include the resulting graph in your report.

# 2. Editing node and edge styles

In `Control Panel`, <ins>select Karate Club network</ins>, then, select Style tab and play with the Style Panel. Here are some ideas.

:eyes: Changing style properties of a given style (e.g., default) applies (if supported) to all the networks using such style in the current session.*

### Change the style of the entire network

* In the drop-down menu (on top), play with predefined styles, e.g., "BioPAX", "Minimal", "Curved", "Directed", or others.

:eyes: In common file formats, edges are specified only once. Regardingless that a direction (source --> target) could be specified, or not, in the file, the applications can visualize any network as an undirected or directed one, depending on the layout chosen.

### Name nodes

* Select `Node tab` (at the bottom).
* Deploy "Label" property, create a "Discrete mapping", and choose a couple of nodes to write a name for them in its attribute "name".
* You can keep the new names or remove the mapping (trash can icon).

### Change the shape of the nodes

* Click on the column "Def." (on the left) of the "Shape" property and choose a new shape.

### Change the edge width (edge width mapping)

<ins>Select Star Wars network</ins> in `Control Panel` `Network tab`.

* Select the node with name "DART VADER" and move it out of the nodes cloud. If you need some help read Section "3. User interface and basic information" of the document "cytoscape_fast_guide.md".
* Select `Style tab` and `Edge tab` (on the bottom).
* Deploy "Width" property (or press "Map." button).
* Assign Column = scenes (number of scenes in common). More scenes should mean thicker edges.
* Change Mapping Type = Continuous Mapping (if already assigned, reassign). Use column "Scene" to map.
* Click and edit the "Current Mapping" function and broad the range of edge width values to get a clearer visual separation between thin and thick edges.

### Change the entire layout

Try some layouts in the Layout menu. For example:

* `Degree Sorted Circle Layout > All nodes`.
* `Edge Weighted Spring Embedded Layout`. Try this with the Karate club and look for nodes 1 and 34.
* `Prefuse Force Directed Layout`.

# 3. Performing basic network analysis

Perform network analysis as follows.

### Analyze the network

<ins>Select Karate club network</ins>.

* Select ``Tools > Analyze network`` (consider the network is not directed). The analysis adds some attributes: network attributes (right), node and edge attributes (Table View).
* Look at the node attributes.
* [**REPORT**] Indicate which are the two nodes with largest betweenness centrality.
* Change the fill color of nodes to be a *continuous mapping* of the column *Betweenness Centrality*; choose the colors so that higher betweenness centrality is associated with a darker color.
* [**REPORT**] Include this graph in your report.

### Plot distributions

* Try hiding and showing the analysis results panel from ``View > Show results panel``.
* [**REPORT**] Include two plots with degree distributions from <ins>Karate Club</ins> and <ins>Star Wars networks</ins> (button "Node Degree Distribution")
warning: because you are dealing with node analysis you must previously select the Node Table View in the bottom right window.
* [**REPORT**] Include two plots with the distribution of the average shortest path lengths in <ins>Karate Club</ins> and <ins>Star Wars networks</ins> (button "Node Degree Distribution").

Notice that the explanatory variables (attributes) available to plot vary depending on if the node, edge or network table is selected in Table View.

### Style the network using the new attributes

<ins>Select Star Wars network</ins>.

* Make the size of the node larger either for nodes with high degree or nodes with high betweenness.
* [**REPORT**] Include an image of the graph styled as indicated above.

# 4. Using a Cytoscape App (ClusterMaker2)

Cytoscape has "apps" that can be installed and used.

### Install ClusterMaker2

Install [ClusterMaker2 release](https://apps.cytoscape.org/apps/clustermaker2). Section "3. User interface and basic information" of the document "cytoscape_fast_guide.md" explains how to.

### Apply ClusterMaker2 to Star Wars

<ins>Select Star Wars network</ins>.

* In the Apps menu, look for and select the [Affinity Propagation cluster](https://en.wikipedia.org/wiki/Affinity_propagation) clustering algorithm in ClusterMaker (select any temporary folder if prompted).
* ClusterMaker2 requires an attribute for the weight: use ``Array source = scenes``.
* Run it; then, check that a new attribute in the node table named ``_APCluster`` has been added. Move this column by the scenes column and order their values: you will find that several groups of nodes have been formed.
* Use the new attribute in the nodes for "Fill color" using a "Discrete mapping" on ``_APCluster.`` You might have to pick the color for each group; just pick a color for the three largest groups.
* [**REPORT**] Include in your report an image of the graph with the three largest clusters in three different colors.
* [**REPORT**] Include a brief commentary on what do you see in these clusters, what do you think they represent and why.

### Apply ClusterMaker2 to Karate Club

<ins>Select Karate club network</ins>.

* Run the affinity propagation algorithm in ClusterMaker2.
* Use "Edge betweenness" as the attribute for the weight (``Array source``). You must have run the network analyzer first so you can have "Edge betweenness" as an attribute in edges.
* Run the module; then, you should get two groups led by #1 and #34. Are they close to the actual way in which this club splitted?
* [**REPORT**] Include in your report an image of the graph with nodes painted according to clusters.
* [**REPORT**] Include a brief commentary on what do you see in these clusters, and whether they have some relationship with the way in which the Karate Club actually splitted.

# DELIVER (INDIVIDUALLY)

:warning: Have you read the README file in the root of this repository? If not, check the delivery requirements.

Deliver a brief report of at most 4 pages (it can be less!), in PDF format. Organize your report as follows:

* The first section should briefly describe the three networks, including the number of nodes and edges in each one; you can make a table with this.
* Then, you should have one section about the *Karate Club*, one section about *Star Wars*, and one brief section about the *US Companies* network; include in each section the elements marked [**REPORT**] above.

**Please be brief,** you do not need to write too much, specially if you are not going to say anything substantive: your report can be less than four pages. A "brief commentary" means one or two paragraphs.

Your report should end with the following text:

**I/we hereby declare that, except for the code provided by the course instructors, all of my/our code, report, and figures were produced by myself/ourselves.**
