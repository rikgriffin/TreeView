ccFlags = -c -depend !Depend -IC: -throwback -fafh -apcs 3/32/fpe2/swst/fp/nofpr
Linkflags = -rmf
AsmFlags = -throwback -depend !Depend
Squeezeflags = -v
LibFileflags = -c -o
cc = cc
asm = objasm
rm = BASIC -quit Run:rm
Binary = TreeView
Library = TreeViewLib.o
SVCccFlags = -fz -zM

LibraryFiles = o.veneers

CommonObjFiles = o.Header o.Sprites

NormalObjFiles = o.Main o.Filters o.M_Move o.M_Add o.M_Plot o.M_Remove o.SetState o.M_Method o.Tree o.Debug o.Redraw o.RedrawTree o.RedrawFlat o.Select o.Events o.Rename o.Drag o.DragBox o.TreeFind o.Utils o.glib o.glib3 o.rmensure

NormalLibFiles = C:o.Stubs C:o.toolboxlib C:o.wimplib

# Final targets:
.SUFFIXES:	.o .c .s .m .p

$(Binary): $(NormalLibFiles) $(NormalObjFiles) $(CommonObjFiles)
	Link $(LinkFlags) -o $(Binary) \
	$(NormalLibFiles) $(CommonObjFiles) $(NormalObjFiles)

$(Library):	$(LibraryFiles)
	libfile $(LibFileflags) $(Library) $(LibraryFiles)

all:	$(Binary) $(Library)

Clean:  Run:rm
	rm $(CommonObjFiles)
	rm $(NormalObjFiles)
	rm $(MCObjFiles)
	rm $(HPObjFiles)
	rm $(Binary)
	rm $(Library)
	rm $(LibraryFiles)
	rm h.Header
	rm c.Sprites
	rm Debug
	trim -file MakeFile -line "<35> Dynamic dependencies:"

# Static dependencies:
h.Header:	o.Header
	| nothing

o.Header:	cmhg.Header h.Version
	cmhg -d h.Header -p cmhg.Header o.Header

o.veneers:	c.Veneers
	$(cc) $(ccflags) -o o.Veneers c.Veneers

o.Sprites:	c.Sprites
	$(cc) -c -depend !Depend -faf $(SVCccFlags) -o o.Sprites c.Sprites

c.Sprites:	Sprites
	size -format "const unsigned int Sprites_c[] = { 0x%x," Sprites > c.Sprites
	bin2c -in Sprites -footer "};" -width 70 -indent 2 -word >> c.Sprites


.c.o:;	$(cc) $(ccflags) $(SVCccFlags) -o $@ $<
.s.o:;	$(asm) $(AsmFlags) -from $< -to $@

# Dynamic dependencies:
