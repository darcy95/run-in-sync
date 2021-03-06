# run-in-sync

Do you sometimes need to run a test or experiment hundreds to thousand times
for obtaining more data points in your graph? Do you also feel like being a
monkey when pressing the enter button on a keyboard every 5 minutes for
conducting the experiment? It should be easy to automate such an
experiment when it is performed on a single computer. However, if your
measurement points are spread in different computers or even in different
networks, any link or node delays will ruin your experiments. Meaning that you
have to stay in front of the computer(s) and press the enter button every 5
minutes until the entire experiment is done.

This simple program will automate your experiment in a networking environment.
This program consists of the two ruby scripts, namely, Controller and
Controllee. The Controller is, as the name suggests, the master process that
gives orders to Controllees, for example, to start an experiment or to wait for
other machines to finish their job. In this way, the machines will work alone
and you can spend your time on a more useful stuff. How does it sound?

Ok, to give you more insight about these scripts, here's my experiment setup when
I used them:

                           +----------+
                           |Controller|
                           +-----+----+
                                 |
         +----------------+------+------+---------------+
         |                |             |               |
         |                |             |               |
         |                |             |               |
       +-+-+            +-+-+         +-+-+           +-+-+
       |EE1+------------+EE2+---------+EE3+-----------+EE4|
       +---+            +---+         +---+           +---+

I had to record network packets that are generated from EE1 and forwarded to
EE4 via EE2 and EE3. The same packet had to be recorded on every nodes (EE1 ~ EE4). 
Normally in such a setup, when one of these machines experiences a delay, all 
subsequent experiments will be out of their joint work. So, by using this program,
Controllees send the status message to the Controller on every experiment
steps. The Controller can orchestrate the experiment based on the status sent
by Controllees. For example, Controllees will only start an experiment when the
Controller gives them an order to start it. 

These scripts are simple and easy to read, so modify them as you want and help
youself to escape from the experiment slavery. ;) A step-by-step instruction
may be added in this document in the future.
