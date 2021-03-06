Python PCAP module
------------------

|travis| `Read the Docs <http://pypcap.rtfd.org>`__

This is a simplified object-oriented Python wrapper for libpcap -
the current tcpdump.org version, and the WinPcap port for Windows.

Example use:

>>> import pcap
>>> sniffer = pcap.pcap(name=None, promisc=True, immediate=True)
>>> addr = lambda pkt, offset: '.'.join(str(ord(pkt[i])) for i in xrange(offset, offset + 4)).ljust(16)
>>> for ts, pkt in sniffer:
...     print ts, '\tSRC', addr(pkt, sniffer.dloff + 12), '\tDST', addr(pkt, sniffer.dloff + 16)
...

Installation
------------

This package requires:

* libpcap-dev

* python-dev

To install run::

    pip install pypcap


Installation from sources
~~~~~~~~~~~~~~~~~~~~~~~~~

Please clone the sources and run::

    python setup.py install

Note for Windows users: WinPcap doesn't provide the development package, therefore
the additional actions are required.
Please download the latest compiled library from https://github.com/patmarion/winpcap
and put it into the sibling directory as ``wpdpack`` (``setup.py`` will discover it)::

    cd ..
    git clone https://github.com/patmarion/winpcap.git wpdpack
    cd pypcap
    python setup.py install


Support
-------

Visit https://github.com/pynetwork/pypcap for help!

.. |travis| image:: https://img.shields.io/travis/pynetwork/pypcap.svg
   :target: https://travis-ci.org/pynetwork/pypcap


Building docs
-------------

To build docs you need the following additional dependencies:

```
pip install sphinx mock sphinxcontrib.napoleon
```
