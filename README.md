Brownout RUBBoS
===============

Brownout is a software engineering paradigm to make cloud services more robust to capacity shortages. It requires the developer to mark a part of the response as optional and only serve it with a probability given by a dynamic parameter, called the _dimmer_. A controller monitors the response time of the service and adjusts the dimmer, so as to keep the application responsive. Details can be found in [this](http://www8.cs.umu.se/~cklein/publications/icse2014-preprint.pdf) article.

This repository contains the source code of the brownout version of [RUBBoS](http://jmob.ow2.org/rubbos.html), a bulleting-board website prototype, mimicking Slashdot. RUBBoS is a popular benchmark choice in cloud computing research.

Brownout-compliance was added to the PHP-version of RUBBoS at two levels: First, comments were marked as optional and, second, recommendations were added as optional code. These are only displayed with a certain probability, the dimmer value, read from `/tmp/serviceLevel`, which is also reflected in the `X-Dimmer` response header. Furthermore, each script sends the measured response time through [UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol) to `localhost` port 2712. To enable brownout, the local controller need to be running, which is located in `PHP/localController.py`.

Usage
-----

Setting up RUBBoS is a fairly involving task. It requires installing a web server, a database server and initializing the database. Furthermore, to make precise performance measurements, you need to make sure that the obtained deployment does not feature "noise", such as cron jobs firing up unexpectedly. If you want to go through this exercise by yourself, you may do so by following the instructions in `README-RUBBOS.md`.

However, we recommend you to contact us, so we can provide you with ready-to-use Xen VM images, of about 16GB, based on Ubuntu 12.04.3 LTS. Even if you are using a different hypervisor or prefer using a different operating system, starting from these VM images may save you a lot of time.

For questions or comments, please contact Cristian Klein <firstname.lastname@cs.umu.se>.
