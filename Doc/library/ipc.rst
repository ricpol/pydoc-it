.. _ipc:

*****************************************
Networking and Interprocess Communication
*****************************************


.. topic:: Traduzione italiana:

   commit: XXXXXXXXXXX | data: XXXX-XX-XX

   Questo file deve ancora essere tradotto.


The modules described in this chapter provide mechanisms for
networking and inter-processes communication.

Some modules only work for two processes that are on the same machine, e.g.
:mod:`signal` and :mod:`mmap`.  Other modules support networking protocols
that two or more processes can use to communicate across machines.

The list of modules described in this chapter is:


.. toctree::
   :maxdepth: 1

   asyncio.rst
   socket.rst
   ssl.rst
   select.rst
   selectors.rst
   asyncore.rst
   asynchat.rst
   signal.rst
   mmap.rst
