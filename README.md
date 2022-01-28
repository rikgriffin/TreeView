# TreeView
Toolbox TreeView gadget for RISC OS

Welcome to the open source release of the TreeView Toolbox gadget.

I've uploaded the source to github using a RISC OS style directory structure (eg ".c" files are in a directory called "c"), and LanManFS style file names (eg an Obey file will be called "file,feb"). My assumption is that anyone downloading from github will be doing so on Windows/Linux and then transferring the files to RISC OS using SMB of some sort. If you download a ZIP of the entire source tree, then extract it on the Windows/Linux side before copying files to RISC OS, then LanManFS will get the correct file types.

Build instructions:

You need to download the small helper programs in the "Utilities" repo. Two of these, "bin2c" and "size", require compilation - just double click the included Make obey file.

TreeView was written using the Acorn (later ROOL) development environment, and the Norcroft compiler. It needs the standard C library and the Toolbox libraries - both the header files for compilation and the libraries to link against.

I removed a dependency on Acorn's "glib", simply by including the required files from the ROOL source in this distribution. There are the "glib", "glib3" and "rmensure" source files - they are all Apache licensed and copyright Acorn. These files were taken from RISCOS.Sources.Toolbox.Gadgets in the ROOL source tree, although I added some bits that were in my old (Acorn) copy of glib that aren't in the ROOL version.

I've never tried building this under any other environment, or with any other compiler, but I'm sure someone will make that work!

To build, just run the "Make" obey file. This just runs "amu all" in a TaskWindow. There's a pretty standard Makefile that you can probably use with some other make utility if you wish.

Note that to run "make clean", you need an "rm" command on your Run$Path which behaves similarly to the unix/linux "rm". You also need a "trim" command which is used to snip off the "Dynamic dependencies" part of the Makefile. Simple BASIC versions of these commands are vailable in the "Utilities" repo. Just copy them into your Library directory, or elsewhere on Run$Path.

Also note that you may need to create a directory called "o" for the compiler to put object files in to.

Rik Griffin Jan 2022
