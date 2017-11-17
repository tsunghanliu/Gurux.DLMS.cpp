# project name (generate executable with this name)
TARGET   = gurux.dlms.client.bin

CC       = gcc

# compiling flags here
CFLAGS   = -c
CPPFLAGS = -std=c++11

LINKER   = gcc -o

# linking flags here
LFLAGS   = -L../development/lib
LIBS     = -lgurux_dlms_cpp -lpthread -lstdc++ -lm

# change these to set the proper directories where each files shoould be

SRCDIR   = src
OBJDIR   = obj
BINDIR   = bin

SOURCES  := $(wildcard $(SRCDIR)/*.cpp)
INCLUDES := $(wildcard $(SRCDIR)/*.h)

OBJECTS  := $(SOURCES:$(SRCDIR)/%.cpp=$(OBJDIR)/%.o)
rm       = rm -f
mkdir    = mkdir -p

all: dirs $(BINDIR)/$(TARGET)

$(BINDIR)/$(TARGET): $(OBJECTS)
	@$(LINKER) $@ $(LDFLAGS) $(OBJECTS) $(LIBS)
	@echo "Linking complete!"

$(OBJECTS): $(OBJDIR)/%.o : $(SRCDIR)/%.cpp
	@$(CC) $(CFLAGS) $(CPPFLAGS) -c $< -o $@
	@echo "Compiled "$<" successfully!"

.PHONEY: clean
clean:
	@$(rm) $(OBJECTS)
	@$(rm) -r $(OBJDIR)
	@echo "Cleanup complete!" 
	@echo $(OBJECTS)

.PHONEY: remove
remove: clean
	@$(rm) $(BINDIR)/$(TARGET)
	@$(rm) -r $(BINDIR)
	@echo "Executable removed!"

.PHONEY: dirs
dirs: $(OBJDIR) $(BINDIR)

$(OBJDIR):
	@$(mkdir) $(OBJDIR)

$(BINDIR):
	@$(mkdir) $(BINDIR)

