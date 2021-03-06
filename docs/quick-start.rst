SNARE
=====

Super Next generation Advanced Reactive honEypot

SNARE is a web application honeypot and is the successor of Glastopf_, which has many of the same
features as Glastopf_ as well as ability to convert existing Web pages into attack surfaces with TANNER_.
Every event sent from SNARE to TANNER_ is evaluated, and TANNER_ decides how SNARE should respond to
the client. This allows the honeypot to produce dynamic responses which improves its camouflage. SNARE when fingerprinted by attackers shows that it is a Nginx Web application server.

.. _TANNER: https://github.com/mushorg/tanner
.. _Glastopf: https://github.com/mushorg/glastopf

Basic Concepts
""""""""""""""

* Surface first. Focus on the attack surface generation. Clone with ``Cloner``.
* Sensors and masters. Lightweight collectors (SNARE) and central decision maker (tanner).

Getting started
"""""""""""""""

 You need Python3. We tested primarily with >=3.4

 This was tested with a recent Ubuntu based Linux.

**Steps to setup:**

1. Get SNARE: ``git clone https://github.com/mushorg/snare.git`` and ``cd snare``

2. Install requirements: ``pip3 install -r requirements.txt``

3. Setup snare: ``sudo python3 setup.py install``

4. Clone a page: ``sudo clone --target http://example.com``

5. Run SNARE: ``sudo snare --port 8080 --page-dir example.com`` (See :doc:`parameters` description for more info)

6. Test: Visit http://localhost:8080/index.html

7. (Optionally) Have your own tanner_ service running.

.. _tanner: https://github.com/mushorg/tanner

[Note : Cloner clones the whole website, to restrict to a desired depth of cloning add ``--max-depth`` parameter]

You obviously want to bind to 0.0.0.0 and port 80 when running in *production*.

**Docker build instructions**
1. Change current directory to ``snare`` project directory
2. ``docker-compose build``
3. ``docker-compose up``

More information about running ``docker-compose`` can be found `here <https://docs.docker.com/compose/gettingstarted/>`_.
