# Cytoscape - Quick start guide

## Contents of this session

1. About Cytoscape
2. Importing a network
3. User interface and basic information
4. Layouts
5. Filtering
6. Annotations
7. Styles
8. Apps installation

# 1. About Cytoscape

[Cytoscape](http://www.cytoscape.org/) is an open source software platform for visualizing complex networks and integrating these with any type of attribute data.

You can look up the user manual at https://manual.cytoscape.org/en/stable.

# 2. Importing a network

* `File > Import > Network from File ...`

If asked, select *shared name* for the node identifier column. This will transform node identifiers into a column named "shared name" internally.

# 3. User interface and basic information

[Manual](https://manual.cytoscape.org/en/stable/Quick_Tour_of_Cytoscape.html#basic-features)

### Control Panel (left window)

 You can switch the following panels:

* Network manager

    Loaded networks are listed along with their number of nodes and edges. Select a network to display.

* Style

    Detailed styles for the information to be displayed can be applied to nodes, edges, entire networks, and tables by selecting the corresponding tab at the bottom of the panel (see section Styles).

* Filter

    Filters on columns and degrees can be created and applied to be displayed (see section Filtering).

* Annotations

    Anotations are created in the Network View and the text and properties can be modified here (see section Annotations).

### Table Panel (bottom right window)

You can select among Node, Edge, and Network tables to show columns of selected (or all) nodes and edges. The values can be ordered and modified. Nodes and edges can be selected using the secondary button to indicate "Select nodes/edges from selected rows". Selected nodes are shown in a specific color in the graph.

### Network View (top right window)

Displays the network graph. At the bottom there are a set of tools. 

You can move (click and drag) and zoom (scroll) the view. Nodes and edges can be selected/deselected by [CTRL+] clicking. Use the search box on the top right panel to select nodes and edges by name. 

# 4. Layouts

[Manual](https://manual.cytoscape.org/en/stable/Navigation_and_Layout.html?highlight=layouts#automatic-layout-algorithms)

* `Layout > Compound Spring Embedder`

    Algorithm derived from force-directed graph layout algorithms.

* `Layout > Prefuse Force Directed Layout > All nodes > scenes` 

    Based on the force-directed paradigm, it is very fast and with the right parameters can provide a very visually pleasing layout.

    [Wikipedia](https://en.wikipedia.org/wiki/Force-directed_graph_drawing)

Layout calculation may take several minutes for large networks.

# 5. Filtering

[Manual](https://manual.cytoscape.org/en/stable/Finding_and_Filtering_Nodes_and_Edges.html#filters)

* `Select Filter tab in the Control Panel` to access Filter Panel
* Modify default filter or add a new filter
* `Select Column, Degree, or Topology filter and apply`. Examine changes in the Table Panel and Network View
* Try "Select" and "Show" visualization modes (at bottom)

*Note: Changing style properties of a given style (e.g., default) applies (if supported) to all the networks using such style in the current session.*

# 6. Annotations

* Right click on blank space in the Network View -> add Text anotation
* `Select Annotations tab in the Control Panel` to access the Annotation Panel and modify the text or its properties.
* You can add arrows in the Network View to point nodes by right-clicking on the text -> add Arrow.

# 7. Styles

[Manual](https://manual.cytoscape.org/en/stable/Styles.html)

* `Select Style tab in the Control Panel`
* `Select Node/Edge/Network/Table tab` to choose a target to style
* You can select a predefined style from the Style drop-down to be applied (default is used the first time)
* You can modify any property of the current style (properties are shown if selected in the Properties drop-down)

# 8. Apps installation

Choose one of the following options to install an APP:

1. Install from [Cytoscap store](https://apps.cytoscape.org/apps) (keep Cytoscape application open)
1. Select ``Apps > App Manager``, search for the plug-in name, select, and press ``Install``.
1. Download a jar file from [Cytoscap store](https://apps.cytoscape.org/apps) and then select ``Apps > App Manager`` and ``Install from file ...``.

---------------------------------------------------------------------------------


