#!/usr/bin/make -f

include ../scripts/check.mk

ARCH ?= amd64
PACKER ?= packer
PACKER_LOG ?= 0
TIMEOUT ?= 1h

export PACKER_LOG

.PHONY: all clean

all: rocky9.tar.gz

$(eval $(call check_packages_deps))

rocky9.tar.gz: check-deps clean
	${PACKER} init rocky9_${ARCH}.pkr.hcl && ${PACKER} build -var timeout=${TIMEOUT} rocky9_${ARCH}.pkr.hcl

clean:
	${RM} -rf output-rocky9 rocky9.tar.gz
