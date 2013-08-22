
Launch :

java -cp daisyDemo.jar uk.ac.ncl.cs.daisy.Main


"Provenance source and user"

* The input panel defines the source of provenance data.  Data can either be loaded from a provN file or from one of the built in data sets.



"Policy"

The "select policy" button permits the loading of a pre-defined policy into the policy editing text pane.  Note it is not necessary to load one, a user may simply type a policy into this pane.

The policy editing pane (text area) is the place where the policy should be entered (manually or from a file).  Upon editing or loading the text will become red.. this indicates that the policy in the text area may not be consistent with the executable version of the policy inside the tool.  Clicking on the "parse policy" button causes the program to read the policy from the text area and, if it is syntactically correct, create an executable version within the tool. If the text turns blue after clicking that button, this policy was read in successfully.

The "parse policy" button reads the policy from the text area and creates the objects that evaluate the policy.  If the text tursn blue to red then this was successful, if not there is some error in the policy.  If the names defined in the property clause part of the rule or the effects part of the rule do not match those in the structure part of the rule, this is reported via a dialog box and the policy reverts to an empty state (no rules).

The "apply policy" button, applies the policy rule objects to the currently loaded provenance graph.  When the tool is first launched there is an empty policy object, i.e. it contains no rules and will have no effects.  If a policy has been loaded into the text are and is blue then that policy will be applied.

Examples rules can be found in propub.pol



"abstraction"

This is a slightly modified version of the window you have seen before.  It has the nodes list on the left, the white list in the middle and black list on the right.

Then click on  the to black list, to white list, from black list and from white list buttons does what you would expect.

Clicking on "Abstract graph to activity(s)" and "Abstract graph to entity(s)" perform the abstraction and writes the results in to the directory specified.  If "Abstract graph to activity(s)" is clicked, then each abstraction operation will aim to produce an abstract activity node, if "Abstract graph to entity(s)" is clicked then each abstraction will aim to produce an abstract entity node.

Once the abstraction is complete a results dialog will be shown with the F-number in (calculations only work properly if there were nodes in the white list).  Clicking ok returns control to the main window.  The program will then reset the prov graph and re-apply the policy rules, the white list and black list boxes will be cleared when this is complete.

There are two combo boxes under the black list box.  The lower one sets a threshold at which nodes will automatically be placed into the black list.  The thresholds are created automatically based on the results of applying the policy.  It starts of at "none" as no nodes will be in the black list, clicking down will lower the threshold at which nodes go to black and clicking up will increase it.  The combobox above that dictates whether the nodes automatically placed in the black list are abstracted as a single group "abstract together" or as a series of individiaul abstractions "abstract individiually".  The values of the two comboboxes are recorded in the experiment html output.  If the user uses the to black list or remove from black list buttons to alter the black list sets, this is recorded in the html with a threshold value of "manual selection"

The "update view" button generates an svg view of the current graph with the current black list highlighted with a thick red border. this can be found in results/current/.
This directory also contains the svg view showing the sensitivities due to the current policy, this file is updated whenever the "apply policy" button is pressed.

You can swap between the policy rules tab and abstraction tab as much as you like.. clicking apply policy will update the data in the abstraction tab to respect the new policy rules.



Once all abstractions on the graph are complete, you will be presented with an alert box with the basic results in (true positives etc).  Closing this box will return you to the manual abstraction sequencer and will reset the data base (takes a few seconds, complete when the white list and black list boxes are clear).  You can then choose another black / white list and perform the abstraction and repeat this as many times is you desire.



Results of abstractions are stored under the "results" directory.  In there is an "index.html".  This file contains links to the history of experimental sessions.  A new session is created when
* the username box is clicked in "Provenance source and user"
* a new dataset is selected in ""Provenance source and user"
* the program is started and an abstraction performed.

This index.html lists the experimental sessions by date, dataset used and by user (always newest at the top)  Clicking on a session will open the origina type of index.html in its ow subdirectory (that index.html is explained below).  Sessisions are stored in their own subdirectories under "results".. the naming of the directory is the date and time at which the session was started, so there is no need for the user to think up unique names any more.


Index.html contains a clickable list of all experiments run up till that point, it also holds the svg of the initial provenance graph.  Clicking on any of the experiment pages shows you the black and white lists chosen selected for that abstraction along with the true positives, false negatives etc.  At the bottom of the page is the svg of the abstracted graph showing the structure.

If you still have the tool open and run further experiments, refreshing the index.html page will add the hyperlinks to find the results.
