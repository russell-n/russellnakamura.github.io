.. title: Documentation Links
.. slug: index
.. date: 2016-03-23 14:39:42 UTC-07:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

These are links to documentation pages for projects I've worked on.

Test Frameworks
---------------

These were written to test the performance of consumer-devices (primarily Android tablets, but also Windows and MacOS PCs).

The APE
~~~~~~~

`The APE <https://russellnakamura.github.io/theape>`_ was written to add a rudimentary plugin system to the existing framework (renamed *Old APE*) so that code written by others that wasn't meant to be included in my framework could be used without changing the external code. 

The Old APE
~~~~~~~~~~~

The `Old APE <https://russellnakamura.github.io/oldape>`_ was an earlier testing framework which was primarily used to test the wireless performance of various consumer devices in an over the air environment. Various external controllers were used to simulate changing environments (e.g. networked power supplies to switch access points on and off and a turntable to set the angle of the device relative to the access points) so the *Old APE* used a tree-based parameter system. So for each angle of the turntable you could enable a sequence of wireless access points and for each access points you could run different kinds of testing (primarily iperf network goodput). A request was made to be able to use arbitrary parameters (e.g. running some angles with one access point, some with three, etc.) which was difficult to implement with the recursive tree, precipitating the start of the APE (above).

Commands
--------

These were command-line tools built to help run tests and examine their data.

AP Command
~~~~~~~~~~

The `AP Command <https://russellnakamura.github.io/apcommand>`_ was created so that users could query and configure wireless access points. The intended user is someone who wants to write a simple shell-script that requires configuring an access point without knowing the underlying means to control the access point. Two specific access points were targeted, neither of which is commercially availabale, but hopefully the methods used to control the access points can be re-used.

Iperf Lexer
~~~~~~~~~~~

The `Iperf Lexer <https://russellnakamura.github.io/iperflexer>`_ was written to extract time-series data from the default (human-readable) `iperf <https://en.wikipedia.org/wiki/Iperf>`_ output. It used with iperf 2 and hasn't yet been tested with iperf 3. While iperf has a clever use of unix commands could achieve a similar result, this was meant to be used either at the command line or integrated into the testing code. Additionally, although iperf has a csv-format, some hardware being tested had versions whose csv-format didn't function correctly and testers preferred being able to see the iperf output while the tests were run.

Course Work
-----------

These are things that I created while taking online courses.

Boston Housing
~~~~~~~~~~~~~~

The `Boston Housing Project <https://necromuralist.github.io/boston_housing>`_  was the initial project for the Udacity Machine Learning nanodegree. It's meant to be an introduction to machine learning with scikit-learn.

Student Intervention
~~~~~~~~~~~~~~~~~~~~

The `Student Intervention Project <https://necromuralist.github.io/boston_housing>`_ was the second project for the Udacity Machine Learning nanodegree. Its goal is to create a model that predicts the likelihood of a student passing his or her final exam based on various attributes related to the student.

