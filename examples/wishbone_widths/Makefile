# Wishbone generator
WBGEN = wbgen2

# Wishbone generator flags
WBGENFLAGS = -lverilog

# Directory where generated include files will be stored
INCLUDE_DIR = include
# Directory where generated documentation will be stored
DOCU_DIR = docs
# Directory where generated HDL code will be store
RTL_DIR = rtl

# Source directory
SRC_DIR = .
# Source files
SRC_FILES = $(wildcard $(SRC_DIR)/*.wb)

# Include files (generated)
INCLUDE_FILES = $(patsubst $(SRC_DIR)/%.wb, $(INCLUDE_DIR)/%.h, $(SRC_FILES))
# Documentation files (generated)
DOCU_FILES = $(patsubst $(SRC_DIR)/%.wb, $(DOCU_DIR)/%.htm, $(SRC_FILES))
# RTL files (generated)
RTL_FILES = $(patsubst $(SRC_DIR)/%.wb, $(RTL_DIR)/%.v, $(SRC_FILES))

all: $(INCLUDE_FILES) $(DOCU_FILES) $(RTL_FILES)

# Rule to create include files
$(INCLUDE_DIR)/%.h: $(SRC_DIR)/%.wb | $(INCLUDE_DIR)
	$(WBGEN) $(WBGENFLAGS) -C$@ $<

# Rule to create documentation files
$(DOCU_DIR)/%.htm: $(SRC_DIR)/%.wb | $(DOCU_DIR)
	$(WBGEN) $(WBGENFLAGS) -D$@ $<

# Rule to create include files
$(RTL_DIR)/%.v: $(SRC_DIR)/%.wb | $(RTL_DIR)
	$(WBGEN) $(WBGENFLAGS) -V$@ $<

$(INCLUDE_DIR):
	mkdir -p $(INCLUDE_DIR)
$(DOCU_DIR):
	mkdir -p $(DOCU_DIR)
$(RTL_DIR):
	mkdir -p $(RTL_DIR)


clean:
	rm -rf $(INCLUDE_FILES) $(DOCU_FILES) $(RTL_FILES)

.PHONY: all clean
