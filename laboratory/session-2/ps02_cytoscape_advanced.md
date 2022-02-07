# Practice Session 02: Cytoscape advanced

## Contents

1. Working with a large network
1. Creating sub-networks
1. Adding attributes to an existing network
1. Creating a network on CSV files

### Datasets for this session

* Marvel Universe Social Graph [hero-network.csv](data/hero-network.csv)
* Game of Thrones Characters [got-characters.csv](data/got-characters.csv) and [got-relationships.csv](data/got-relationships.csv)

# 1. Working with a large network

The Marvel Universe Social Graph contains characters from the Marvel Universe that appear in the same comic number. It contains over half a million edges. It is formatted in the following way (<tab> as a separator):

    BLACK PANTHER/T'CHAL<tab>HAWK
    BLACK PANTHER/T'CHAL<tab>LOKI [ASGARDIAN]
    BLACK PANTHER/T'CHAL<tab>HULK/DR. ROBERT BRUC
    SPIDER-MAN/PETER PAR<tab>HULK/DR. ROBERT BRUC
    ...

To import Marvel Universe SG into Cytoscape:

* `File > Import > Network from File ...`
* Select `hero-network.csv`
* `Advanced Options ...`: indicate the delimiter is only a tabulator (**TAB**).
  * :warning: If you keep the default delimiter, a comma, or you use tabulator and comma, you will mistakenly get too many nodes (as node names include commas inside) and Cytoscape may hang for a long time or crash.
* As a result, Column 1 should be "Source" (green disc) and Column 2 should be "Target" (red target)
* Press `OK` to calcule the view (it will be fast)

Tips: you may want to change the style to "Marquee" to see the graph slightly better (particularly if you zoom). Pick on the navigator (bottom right) to move to a specific part of the graph.

[**REPORT - Q1**] Include this graph in your report.

[**REPORT - Q2**] Answer the following question: what are the small components that are disconnected from the largest connected component?

# 2. Creating sub-networks

* Search and select for the node named "BLACK PANTHER/T'CHAL"
  * Option 1: use the search box located on top of the display. 
      * :warning: in this version of Cytoscape the search does not work as expected: **use the pattern " \*CHAL" to obtain the expected results**.
      * :warning: Depending on the OS (usually in Linux-based systems) you may need to add \ in order to exclude special characters (+ - & | ! ( ) { } [ ] ^ " ~ * ? : \). Also, spaces and quotes are not well managed. Use * as a wildcard.
  * Option 2: find this node in the node table (you may want to sort the column alphabetically), select it, and then use the secondary button to indicate `Select nodes from selected rows`
* Select the neighbors of a character: select the caracter and click on the `two-house icon on the top bar`. Note that edges among neighbors are also shown.
* Create a subnetwork with the selected nodes: `File > New Network > From selected nodes, all edges`
* Rename the new network as "BLACK".

[**REPORT - Q3**] Indicate the number of nodes and edges of this sub-graph (they are shown in the Network Panel).

* Do the same for a less popular character "ENCHANTRESS/AMORA/HE": select this node and its neighbors, create a subnetwork, and rename it as "ENCHANTRESS".
    Note that the number of nodes is much smaller but the number of edges is not proportionally as small. Think of why do this happens?

[**REPORT - Q4**] Indicate the number of nodes and edges in the sub-graph of nodes connected to "ENCHANTRESS".

You can also make selections by other characteristics, such as degree by creating a filter in the Filter Panel.

[**REPORT - Q5**] Include a brief commentary on the number of nodes and edges in different sub-graphs from different characters. What do you think influences these numbers?

:warning: **Important**: by default Cytoscape has a [level of detail](http://manual.cytoscape.org/en/stable/Rendering_Engine.html#what-is-level-of-detail-lod) setting that is similar to the one found in videogames. If the current view contains more than *render.nodeLabelThreshold*, the node labels are not displayed. You can toggle between full details and reduced details using "View > Show Graphics Details" and "View > Hide Graphics Details." You can also permanently adjust this by going to "Edit > Preferences". Depending on the computer, you can set this up to 2000 from the default of 200. Be careful: this will block your computer when dealing with large networks such as the hero network.

# 2. Adding attributes to an existing network

When working with CSV files, the node attibutes have to be supplied in a separated file from the edges file. Following, we will create a network from two CSV files: `got-characters.csv` contains the name and house of the characters in the series *Game of Thrones* (let's name it, *attribute file*) and `got-relationships.csv` contains relationships between characters (let's name it, *network file*).

First, import the edges:

* ``File > Import > Network from file ...``
* Use the file ``got-relationships.csv``
* Select for `src` column: "Source Node" (green disc)
* Select for `dest` column: "Target Node" (red target)
* Select "Edge Attribute" for the other columns

As a result, source and target nodes are assigned to the node table. Have a look at both node and edge tables.

Then, import the node attributes to be added:

* Select the node table; we are going to add new attributes as columns.
* ``File > Import > Table from file ...``
* Use the file ``got-characters.csv``
* Import data "To selected networks only" and select "got-relationships.csv"
* Import data as "Node Table Columns"
* The first column ("Id") should be the key
* The other columns should be attributes

Check the changes in the node table.

Now, style the network:

* Use the *character-name* of the character as the node label.
* Use the *degree* as the size of the node (you will need to run the network analysis first with `Tools > Analyze Network`)
* Use the *house-birth* attribute to determine the shape and color of nodes. Use style, shape, fill-color, and discrete mappings.
* Use the *relationship* attribute to label edges. Leave edges in color black, except for edges representing killing, which should be in red.

[**REPORT - Q6**] Include the graph of *Game of Thrones*.

[**REPORT - Q7**] Show one example of a multi-edge in this graph. Indicate which characters are involved.

[**REPORT - Q8**] Show one example of a loop in this graph. Indicate which characters are involved.

[**REPORT - Q9**] Indicate a brief commentary on any interesting phenomenon you observe on this graph.

# 3. Creating a network on CSV files

Now, create a network on your own, on whatever topic of your choice as long as the network is **real**. As indicated above, you will need two CSV files: one for the network and one for the attributes. The network should include between 15 and 30 nodes.

Some ideas:

* Nodes can be characters in a movie, edges connecting characters depending on their affinity.
* Nodes can be music bands or artists, attributes whether the node is a band or an artist, edges connect artists to the bands they've played in.
* Nodes can be countries, attributes can be population sizes, connections can be countries that share a border.
* Note that edges can also have attributes, which you can use to change the color or style of lines in the graph.

These are only ideas. Be creative.

Tip: to include a legend, you can use the Cytoscape app [legend creator](https://apps.cytoscape.org/apps/legendcreator).

[**REPORT - Q10**] Describe the graph you created.

[**REPORT - Q11**] Include two tables with the contents of the CSV files you created (not screenshots).

[**REPORT - Q12**] Draw the graph in Cytoscape and include it in your report.

# DELIVER (INDIVIDUALLY)

Deliver a report describing these networks, having at most 4 pages in PDF. The report should have **three numbered sections**: one for the *Marvel* network, one for *Game of Thrones*, and one for the network you created. Remember to include all of the elements marked [**REPORT - Q**] above.

Your report should end with the following text:

**I/we hereby declare that, except for the code provided by the course instructors, all of my/our code, report, and figures were produced by myself/ourselves.**

