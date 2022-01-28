CCflags = -c -depend !Depend -IC: -throwback -faf -apcs 3/32/fpe2/swst/fp/nofpr
Linkflags = -aif
ObjAsmflags = -throwback -depend !Depend
Squeezeflags =
cc = cc
asm = objasm
rm = rm

CommonObjFiles =

NormalObjFiles = o.MainWindow o.Init o.Handlers o.Main o.Errorbox o.Messtrans

CommonLibs = C:o.Stubs C:o.eventlib C:o.toolboxlib C:o.wimplib

NormalLibs =	TreeView:o.TreeViewLib Tabs:o.TabsLib

# Final targets:
.SUFFIXES:	.o .c .s .m

Harness:	!RunImage

!RunImage:\
	$(NormalLibs) $(CommonLibs) $(CommonObjFiles) $(NormalObjFiles)
	Link $(LinkFlags) -o !RunImage \
	$(NormalLibs) $(CommonLibs) $(CommonObjFiles) $(NormalObjFiles)
#	Squeeze $(Squeezeflags) !RunImage

Clean:  Run:rm
	rm $(CommonObjFiles)
	rm $(NormalObjFiles)
	rm $(MCObjFiles)
	rm !RunImage
	trim -file MakeFile -line "<35> Dynamic dependencies:"

# Static dependencies:

.c.o:;	$(cc) $(ccflags) -o $@ $<
.s.o:;	$(asm) $(asmflags) -from $< -to $@


# Dynamic dependencies:
