#
# Makefile for the GraphLCD tool showpic
#

-include ../../Make.config

PRGNAME = lcdtestpattern

OBJS = lcdtestpattern.o

INCLUDES += -I../../
LIBDIRS += -L../../glcdgraphics/ -L../../glcddrivers/


all: $(PRGNAME)
.PHONY: all

# Implicit rules:

%.o: %.c
	$(CXX) $(CXXEXTRA) $(CXXFLAGS) -c $(DEFINES) $(INCLUDES) $<

# Dependencies:

DEPFILE = $(OBJS:%.o=%.d)

-include $(DEPFILE)

# The main program:

$(PRGNAME): $(OBJS)
	$(CXX) $(CXXFLAGS) $(LDFLAGS) -rdynamic $(OBJS) $(LIBS) $(LIBDIRS) -lglcddrivers -lglcdgraphics -lstdc++ -o $(PRGNAME)

install: $(PRGNAME)
	install -d $(BINDIR)
	install -m 755 -o root -g root $(HAVE_STRIP) $(PRGNAME) $(BINDIR)

uninstall:
	rm -f $(BINDIR)/$(PRGNAME)

clean:
	@-rm -f $(OBJS) $(DEPFILE) $(PRGNAME) *~

