.. _ppdec:

==============================
PPDEC: picture decoding engine
==============================

.. contents::

.. todo:: write me


Introduction
============

.. todo:: write me


.. _ppdec-falcon:

falcon parameters
=================

Present on:
    v0:
        G98, MCP77, MCP79
    v1:
        GT215:GF100
    v2:
        GF100:GF119
    v3:
        GF119:GM107
BAR0 address:
    0x085000
PMC interrupt line:
    17
PMC enable bit:
    17
Secretful:
    v0,v1:
        no
    v2:
        yes
    v3:
        no
Version:
    v0:
        0
    v1-v2:
        3
    v3:
        4
Code segment size:
    v0:
        0x1000
    v1-v3:
        0x1400
Data segment size:
    0x1000
Fifo size:
    0x10
Xfer slots:
    8
Code TLB index bits:
    8
Code ports:
    1
Data ports:
    1
Version 4 unknown caps:
    31
Unified address space:
    no
IO addressing type:
    indexed
Core clock:
    v0:
        :ref:`g98-clock-vdclk`
    v1:
        :ref:`gt215-clock-vdclk`
    v2-v3:
        :ref:`gf100-clock-vdclk`
Tesla VM engine:
    0x1
Tesla VM client:
    0x0c
Tesla context DMA:
    0x4
Fermi VM engine:
    0x14
Fermi VM client:
    HUB 0x0b
Interrupts:
    ===== ===== ========== ================== ===============
    Line  Type  Present on Name               Description
    ===== ===== ========== ================== ===============
    8     edge  G98:GF100  MEMIF_PORT_INVALID :ref:`MEMIF port not initialised <falcon-memif-intr-port-invalid>`
    9     edge  G98:GF100  MEMIF_FAULT        :ref:`MEMIF VM fault <falcon-memif-intr-fault>`
    9     edge  GF100-     MEMIF_BREAK        :ref:`MEMIF breakpoint <falcon-memif-intr-break>`
    10    level all        VUC                :ref:`vµc interrupt <ppdec-intr-vuc>`
    11    level all        ???                ???
    12    level v0-v1      ???                ???
    12    level v2         CRYPT              :ref:`crypto coprocessor <falcon-crypt-intr>`
    12    level v3         ???                ???
    13    level all        ???                ???
    14    level all        ???                ???
    15    level all        UNK680             ???
    ===== ===== ========== ================== ===============
Status bits:
    ===== ========== ========== ============
    Bit   Present on Name       Description
    ===== ========== ========== ============
    0     all        FALCON     :ref:`Falcon unit <falcon-status>`
    1     all        MEMIF      :ref:`Memory interface <falcon-memif-status>`
    2     all        VUC        :ref:`vµc unit <ppdec-status-vuc>`
    3     all        ???        ???
    4     all        ???        ???
    5     all        ???        ???
    6     all        ???        ???
    7     all        ???        ???
    8     all        ???        ???
    9     all        ???        ???
    10    v2         ???        ???
    11    v3         ???        ???
    ===== ========== ========== ============
IO registers:
    :ref:`ppdec-io`
MEMIF ports:
    ==== ======= ============
    Port Name    Description
    ==== ======= ============
    1    MBRING  :ref:`vµc input <vuc-mbring>`
    2    MVSURF  :ref:`vµc MV surfaces <vuc-mvsurf>`
    3    UNK640+ ??? used for writes
    4    UNK680+ ??? used for reads
    ==== ======= ============

.. todo:: interrupts
.. todo:: more MEMIF ports?


.. _ppdec-io:

IO registers
============

.. space:: 8 ppdec 0x1000 VP3 picture decoding engine

   .. todo:: write me

============ =============== ========== =========== ===========
Host         Falcon          Present on Name        Description
============ =============== ========== =========== ===========
0x000:0x400  0x00000:0x10000 all        N/A         :ref:`Falcon registers <falcon-io-common>`
0x400:0x500  0x10000:0x14000 all        VUC         :ref:`vµc registers <ppdec-io-vuc>`
0x500:0x540  0x14000:0x15000 all        XFRM        :ref:`block transform <ppdec-io-xfrm>`
0x540:0x580  0x15000:0x16000 all        UNK540      ???
0x580:0x5c0  0x16000:0x17000 all        UNK580      ???
0x5c0:0x600  0x17000:0x18000 all        UNK5C0      ???
0x600:0x630  0x18000:0x18c00 v0         MEMIF       :ref:`Memory interface <falcon-memif-io>`
0x600:0x640  0x18000:0x19000 v1-        MEMIF       :ref:`Memory interface <falcon-memif-io>`
0x630:0x640  0x18c00:0x19000 v0         UNK630      ???
0x640:0x680  0x19000:0x1a000 all        UNK640      ???
0x680:0x700  0x1a000:0x1c000 all        UNK680      ???
0x700:0x740  0x1c000:0x1d000 v1-        JOE         ???
0x740:0x780  0x1d000:0x1e000 v2         ???         ???
0x800:0x900  0x20000:0x24000 v2         CRYPT       :ref:`Crypto coprocessor <falcon-crypt-io>`
0x900:0xa00  0x24000:0x28000 v2         ???         :ref:`??? <falcon-crypt-io>`
0xc00:0xc40  0x30000:0x31000 v2         ???         :ref:`??? <falcon-crypt-io>`
0xd00:0xd40  0x31000:0x32000 v2         ???         :ref:`??? <falcon-crypt-io>`
0xfe0:0x1000 \-              v0:v3      FALCON_HOST :ref:`Falcon host registers <falcon-io-common>`
============ =============== ========== =========== ===========

.. todo:: unknowns
.. todo:: fix list


Block transform
===============

.. todo:: write me


.. _ppdec-io-xfrm:

IO registers
------------

.. todo:: write me
