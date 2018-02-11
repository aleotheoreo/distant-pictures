# distant-pictures
A simple server that serves webcam pictures to a website. 

I set up a selfie booth that allows a user to remotely (i.e., using the Arduino button) snap
pictures. On the web application itself, I further implemented 41 Instagram filters to allow users
to select a filter on the taken image. Changing the filter would automatically apply the filter to
the most recently taken image.

The Instagram filters were implemented using a node package called Filterous 2. This package in
particular was selected because it applied the filter to the saved file itself, as opposed to just
the html DOM object. Filterous is dependent on other node packages, including Cairo, Pango, and 
Canvas.

Successes:
The filtering works! The webpage is able to feed the selected filter option (in the dropdown menu)
to the Raspberry Pi server. A new picture is created by applying the filter to the base image.

Failures:
Part of the Filterous functionality involves saving the file. However, the newly created file needs
to be created before the browser can call the file for display. Since the saving occurs
asynchronously, I experimented with different forms of synchronization, including the fs, async, 
and promise node packages. Unfortunately, I could not get these packages to work, so instead, I
opted for the simpler "waiting" strategy, calling on the inherent setTimeout function.
