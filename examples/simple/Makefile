# Include the nanopb provided Makefile rules
include ../../extra/nanopb.mk

# Compiler flags to enable all warnings & debug info
CFLAGS = -Wall -Werror -g -O0
CFLAGS += -I$(NANOPB_DIR)

#NANOPB_DIR= ,/home/jie/code/nanopb
#NANOPB_CORE= ,/home/jie/code/nanopb/pb_encode.c /home/jie/code/nanopb/pb_decode.c /home/jie/code/nanopb/pb_common.c

# C source code files that are required
CSRC  = simple.c                   # The main program
CSRC += simple.pb.c                # The compiled protocol definition
CSRC += $(NANOPB_DIR)/pb_encode.c  # The nanopb encoder
CSRC += $(NANOPB_DIR)/pb_decode.c  # The nanopb decoder
CSRC += $(NANOPB_DIR)/pb_common.c  # The nanopb common parts
.PHONY:clean
# Build rule for the main program
simple: $(CSRC)
	@echo "NANOPB_DIR= ",${NANOPB_DIR}
	@echo "NANOPB_CORE= ",${NANOPB_CORE}
	$(CC) $(CFLAGS) -osimple $(CSRC)

# Build rule for the protocol
simple.pb.c: simple.proto
	$(PROTOC) $(PROTOC_OPTS) --nanopb_out=. simple.proto
clean:
	@rm -rf simple 
