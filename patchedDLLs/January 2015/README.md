Creating patched DLLs
=====================

Note: the instructions will only work for 32-bit right now.


You can use the IL assembler tools from Microsoft or Mono to
create patched DLL files.


To do this, you need to disassemble the DLL files to the
Common Intermediate Language. After that you have to
change some strings like the Login Server IP. At last, you
assemble the IL back to its binary form.


I already created some patch files to make this more easier.
These are located in the `patches` folder-
Simply follow the instructions listed below.


Before starting you have to copy the `patches` directory to
LoE's `Data/Managed/` folder. The files in this directory are
already patched.

Windows
-------

The IL Assembler tools come with Visual Studio.

Mono
----

Mono has its own disassembler called monodis.

Assembly-CSharp.dll
-------------------

`ildasm /text Assembly-CSharp.dll /output=Assembly-CSharp.il`

`patch -p1 < patches/Assembly-CSharp.il.patch`

`ilasm /dll Assembly-CSharp.il /output:Assembly-CSharp.dll`

LegendsOfEquestria.Data.dll
-------------------

`ildasm /text LegendsOfEquestria.Data.dll /output=LegendsOfEquestria.Data.il`

`patch -p1 < patches/LegendsOfEquestria.Data.il.patch`

`ilasm /dll LegendsOfEquestria.Data.il /output:LegendsOfEquestria.Data.dll`

LoE.Shared.dll
-------------------

`ildasm /text LoE.Shared.dll /output=LoE.Shared.il`

`patch -p1 < patches/LoE.Shared.il.patch`

`ilasm /dll LoE.Shared.il /output:LoE.Shared.dll`