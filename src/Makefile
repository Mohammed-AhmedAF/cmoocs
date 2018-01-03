#******************************************************************************
# Copyright (C) 2017 by Alex Fosdick - University of Colorado
#
# Redistribution, modification or use of this software in source or binary
# forms is permitted as long as the files maintain this copyright. Users are 
# permitted to modify this and use it to learn about the field of embedded
# software. Alex Fosdick and the University of Colorado are not liable for any
# misuse of this material. 
#
#*****************************************************************************

#------------------------------------------------------------------------------
# <Put a Description Here>
#
# Use: make [TARGET] [PLATFORM-OVERRIDES]
#
# Build Targets:
#      <Put a description of the supported targets here>
#
# Platform Overrides:
#      <Put a description of the supported Overrides here
#
#------------------------------------------------------------------------------
include sources.mk

# Platform Overrides
PLATFORM = 

# Architectures Specific Flags
LINKER_FILE = 
CPU =  cortex-m4
ARCH = thumb
SPECS = nosys.specs

# Compiler Flags and Defines
CC = gcc
LD = arm-none-eabi-ld
LDFLAGS = -Wl -Map=c1m2.map 
CFLAGS = -Wall -Werror -g -O0 -std=c99 -I ../include
CPPFLAGs = 



ifeq ($(PLATFORM),HOST)
	CC = gcc
else 
	CC = gcc-arm-none-eabi
	SOURCES += interrupts
	LDFLAGS = -T msp432p401r.lds
	CFLAGS += -I ../include/ -mcpu=cortex-m4 -mthump --specs=nosys.specs --mfloat-abi=hard -mfbu=fbv4-sp-d16 -march=armv7e-m
endif


%.o : $(SRC)
	$(CC) $^ -o $@ $(CFLAGS) -c

%.asm : $(SRC)
	$(CC) $^ -o $@ $(CFLAGS) -S

.PHONY all :
	$(CC) $(CFLAGS)
.PHONY build :
	$(CC) $^ -o $@ $(CFLAGS) 

.PHONY clean :
		rm *.o *.asm *.i *.map *.out
