R2P_LIB=r2pipe.dll
MCS=mcs
MONO=mono
# See http://sourceforge.net/projects/narrange/files/narrange/NArrange%20Beta%20Version%200.2.9/NArrange-0.2.9-net-2.0.zip/download
NARRANGE_WD=~/Downloads/NArrange/bin
NARRANGE=$(NARRANGE_WD)/narrange-console.exe
MCS_LIB=$(MCS) -optimize -target:library -out:$(R2P_LIB)
MCS_LINK=$(MCS) -optimize -reference:$(R2P_LIB)

all: $(R2P_LIB) main.exe http.exe

$(R2P_LIB): r2pipe.cs
	$(MCS_LIB) r2pipe.cs

main.exe: main.cs $(R2P_LIB)
	$(MCS_LINK) main.cs

http.exe: http.cs $(R2P_LIB)
	$(MCS_LINK) http.cs

run:
	$(MONO) main.exe

clean:
	rm -f main.exe http.exe $(R2P_LIB)

indent:
	for a in *.cs ; do $(MONO) $(NARRANGE) $$a ; done

.PHONY: run all clean indent
