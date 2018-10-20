FAQ
=========
* How does Mini-NDN work?
Mini-NDN's principles of operation most heavily rely on the underlying Mininet code it relies on.
Mininet uses a combination of limited containerization via network namespaces (which give processes 
isolated interfaces and routing tables) and emulated ethernet connections via veth connections.
In practical terms, Mini-NDN ensures that processes running on distinct nodes will run seperately
and without interfering with each other.

* How does Mini-NDN apply link loss/delay/etc.?
Mini-NDN relies on Mininet's code, which in turn uses the Linux tc utility on a stations' virtualized
interfaces to apply configurations known as qdiscs to these links. Note that these will only be applied
on egress packets from a station where it's applied.
For more information on qdiscs and tc, view the information `here <http://wiki.linuxwall.info/doku.php/en%3aressources%3adossiers%3anetworking%3atraffic_control>`_.

* Why use Mini-NDN rather than a simulator such as ndnSIM?
Mini-NDN is easier and faster to use because, rather than serving as a mathematical model of a network,
it is instead running real NDN code on a real Linux kernel. This also means it's quite useful for testing
code changes, as it can more accurately test the interaction of software componenents.