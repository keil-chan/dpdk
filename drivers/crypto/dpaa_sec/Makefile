# SPDX-License-Identifier: BSD-3-Clause
# Copyright (c) 2016 Freescale Semiconductor, Inc. All rights reserved.
# Copyright 2017 NXP

include $(RTE_SDK)/mk/rte.vars.mk

#
# library name
#
LIB = librte_pmd_dpaa_sec.a

# build flags
CFLAGS += -D _GNU_SOURCE
ifeq ($(CONFIG_RTE_LIBRTE_DPAA_SEC_DEBUG_INIT),y)
CFLAGS += -O0 -g
CFLAGS += "-Wno-error"
else
CFLAGS += -O3
CFLAGS += $(WERROR_FLAGS)
endif

CFLAGS += -I$(RTE_SDK)/drivers/bus/dpaa
CFLAGS += -I$(RTE_SDK)/drivers/bus/dpaa/include
CFLAGS += -I$(RTE_SDK)/drivers/crypto/dpaa_sec/
#sharing the hw flib headers from dpaa2_sec pmd
CFLAGS += -I$(RTE_SDK)/drivers/crypto/dpaa2_sec/
CFLAGS += -I$(RTE_SDK)/lib/librte_eal/common/include
CFLAGS += -I$(RTE_SDK)/lib/librte_eal/linuxapp/eal
LDLIBS += -lrte_eal -lrte_mbuf -lrte_mempool -lrte_ring
LDLIBS += -lrte_cryptodev

# versioning export map
EXPORT_MAP := rte_pmd_dpaa_sec_version.map

# library version
LIBABIVER := 1

# library source files
SRCS-$(CONFIG_RTE_LIBRTE_PMD_DPAA_SEC) += dpaa_sec.c

# library dependencies

LDLIBS += -lrte_bus_dpaa
LDLIBS += -lrte_mempool_dpaa

include $(RTE_SDK)/mk/rte.lib.mk
