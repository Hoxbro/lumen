# Lumen compared to other dashboarding tools

Here we will first talk about the most fundamental differences that set Lumen apart from other tools, and then compare Lumen to specific competitive or complementary tools so that it is clear how Lumen fits in.

## General considerations

As listed at [pyviz.org/tools](https://pyviz.org/tools.html#dashboarding) and [pyviz.org/dashboarding](https://pyviz.org/dashboarding/), there are many other Python-based open-source tools for building analytics dashboards. There are [hundreds more](https://www.capterra.com/dashboard-software/) if you consider commercial tools or ones not based on Python. How can you choose between Lumen and all these other tools?

What sets Lumen apart is that it lets _anyone_ on your team make apps that build on custom Python code, without requiring that _everyone_ learn Python. Lumen is a great choice if you have some people on a team or in an organization who can write custom Python code that does _precisely_ what your organization needs in a particular case, whether that's connecting to some custom data source, applying some custom transform or analysis method, viewing things in some custom chart or type of table, or literally anything else you can do in Python (which is literally anything!). Ideally those Python programmers will be using the Python ecosystem to do their daily work, using tools like those from [HoloViz](https://holoviz.org), and when they build custom functionality for their own work, that same functionality can be made available to non-Python users using Lumen. That way everyone in the organization can benefit from all of the innovation being developed.

Of course, traditional BI analytics tools like Tableau, PowerBI, or Superset also let non-technical or non-Python users with domain knowledge build visualizations and dashboards. These longer-established BI tools will generally have a more polished and friendly user interface than Lumen has, meeting more of the needs of less-technical users with no coding at all. If those tools do what's required, use them!

But what do you do when you reach the limits of those tools? Many of them do include Python or other scripting tools for that purpose, but generally as an add-on that's not fully integrated. Unlike those other tools, Lumen itself is built directly on the scientific Python stack, such as the Intake and Panel libraries, which lets Lumen (a) provide a very rich basis of functionality to non-technical users comparable to what is available to Python users, and (b) treat custom functionality as a "first class citizen", provided exactly the same way as any of Lumen's native functionality. That way an organization can customize _anything_, with new customizations requiring Python code contributed by the Python experts and then immediately usable by _every_ Lumen user, technical or not.

Lumen and the rest of the HoloViz and scientific Python stack are thus designed to meet _all_ of the needs of an organization, no matter how specialized or esoteric those needs are. By design, standard BI tools will do a great job at the _typical_ needs common across a market segment, but won't do as well at providing "headroom" or a "release valve" for those rarer but individually important bits that can otherwise dominate a workflow or greatly reduce its effectiveness.


## [Tableau](https://www.tableau.com), [PowerBI](https://powerbi.microsoft.com), [Looker](https://looker.com), [Spotfire](https://www.tibco.com/products/tibco-spotfire), etc.

The leading commercial dashboarding tools focus first on providing an intuitive, full-featured user interface for building apps without explicit coding, which makes them good choices for the needs of less-technical users. Unlike open-source tools like Lumen, they also include commercial support, which again can be important for the same audience. They also provide a wide swath of out-of-the-box data integrations, which can save a lot of development time for accessing supported data sources. When you reach the limits of the already-provided functionality, these tools even let you provide custom Python code that you can integrate into your applications. Finally, the tools generally include deployment platforms so that users can share deployed apps with each other in the organization, while Lumen apps need a separate deployment system.

So if you can afford these tools, what's the catch? Depends on your organization's mix of data science and analytics users. If you have an organization dominated by non-technical analytics users, plus maybe a few Python programmers to support them, then you can make good use of the commercial tools plus a little bit of customization on the side as needed, with everything organized around the commercial tool. Lumen is designed for the opposite situation: it takes the power available in the Python open-source ecosystem, and makes much of it available immediately (plus almost anything else available with small customizations) to non-technical users. So Lumen is a good choice if you have a successful Python-based data science team driving innovation in your organization, and now your problem is how you can make them have a bigger impact on your whole organization's processes and decision making. Lumen is designed for the case where the Python data-science team (not the commercial tool vendors!) owns the process of analytics and visualization in your organization, either directly (in their Jupyter Notebooks, Panel or Voila apps, etc.) or by making functionality available to all through Lumen. The Python users can then use Python tools through Jupyter or scripts as they normally do, with full power over their machine-learning or analytic code, while then being able to publish those same components for non-technical users when they are developed. Non-technical users with domain knowledge can then apply these tools to their problems using Lumen, feeding back requirements and desired improvements to the Python team. This way domain-specific ideas can flow freely between domain experts and the data-science team, while Python-based solutions can flow freely out from the data-science team, without costly and time-consuming artificial barriers from switching from one tool or ecosystem to the other at such departmental boundaries.


## [Apache Superset](https://superset.apache.org)

Like Tableau and other commercial tools, Superset provides a very polished environment for exploring data, and like Lumen, Superset is an open-source Python+JavaScript tool that anyone can install. Compared to Lumen, however, Superset is a very heavyweight tool (despite being billed as "lightweight"), making it difficult for a Python data-science team to customize. Superset includes a database that needs installation and management, along with various user management and account features that make it difficult for a single user to install and make use of Superset locally; it's primarily geared towards departments and companies to install with dedicated administers to maintain it. Lumen can easily be installed by an individual user, immediately giving the ability to use text-based specifications to build apps and dashboards, without necessarily requiring the central administrators to agree to support it. Lumen is also inherently extensible, accepting custom-written or existing Python-ecosystem transform, filter, and view components on the same basis as its own components, while Superset's Python configurability is limited to specific bits of customizable behavior that a user needs to implement just for Superset. Overall, Superset focuses on providing its own world or platform to live in, while Lumen focuses narrowly on exposing the power of existing and custom Python data science code within an interface for non-technical users.


## [Datasette](https://datasette.io)

Like Superset and the commercial packages, Datasette provides a web-based interface for exploring data and selecting values to plot or display in tables. As a more specialized open-source tool, Datasette's UI is not as extensive or polished as the commercial tools, but the functionality provided is nonetheless powerful because it is based around an underlying relational database.

In contrast, Lumen does not require that the data being processed be inserted into a database, and is thus more similar to working with a [data lake](https://en.wikipedia.org/wiki/Data_lake) than with a database (for both good and bad!). With Lumen, the data remains wherever it was originally located, without necessarily being processed before the app begins, which is a decentralized approach that can be messier but works well for querying live data sources and for large, remote datasets processed lazily. Because only the required subsets of the data are ever pulled into the Lumen app, big-data processing tools and workflows like [Datashader](https://datashader.org) can be used with Lumen, where the data is read as-needed from an efficient file format like [Parquet](https://parquet.apache.org/). This approach makes Lumen useful for a broad range of data sizes not suitable for a standard relational database approach.


## [Perspective](https://perspective.finos.org)

Like the other tools listed above, Perspective provides a GUI interface for selecting dimensions and columns for plots and tables, making it simple to explore columnar data. Like the non-Lumen HoloViz tools, Perspective is usable in Jupyter, which helps integrate configurable analytics into an otherwise custom workflow. Perspective is thus an alternative to Lumen in some cases, but we suggest using both in combination: Use Perspective to design plots, then Lumen for the full workflow consisting of data sources, arbitrary transforms, and laying out the results into a polished deployable application.


## [Panel](https://panel.holoviz.org) and [Bokeh](https://bokeh.org)

Like Lumen, Panel and the underlying Bokeh library let users build dashboards that expose the power of the Python data-science ecosystem. Panel and Bokeh do so using a Python programming interface, with users writing Python code to configure each component and the overall dashboard. Like Lumen, Panel's programming model is declarative in nature, but it also allows specification of arbitrary Python code as part of the configuration of each component, and it requires custom non-declarative Python code for specifying data sources and transformations. Lumen is a purely declarative approach that provides a text-based language for building _all_ the components of a Panel app, keeping all Python code separate from the configuration of a particular dashboard. Lumen is thus a good choice for users who want the power of Panel and Bokeh but are not Python programmers, and is a particularly good choice for people working on a team with Panel users who can extend Lumen's capabilities and make the custom additions available to non-Python users.


## [Dash](https://plotly.com/dash), [Streamlit](https://streamlit.io), [Voila](https://github.com/voila-dashboards/voila)+[IPyWidgets](https://ipywidgets.readthedocs.io)

Lumen's underlying Panel library is one of a number of dashboarding technologies available in Python. Just as Lumen is built on Panel, declarative text-based user interfaces could be developed for the other availble dashboarding tools, such as Dash, Streamlit, or Voila+IPyWidgets. For data-science teams built around one of these other dashboarding tools, such a declarative interface could play a similar role to Lumen for that developer and user commnunity. In the meantime, because Panel supports nearly every common visualization tool available for Python, Lumen can already be useful as a declarative interface providing the power of the same underlying Python data-science libraries that will be used in those dashboarding tools, such as Plotly, Matplotlib, bqplot, and ipywidgets, all of which can be used in Panel apps and thus potentially with Lumen.