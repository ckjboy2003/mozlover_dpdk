#   BSD LICENSE
#
#   Copyright 2016 NXP.
#
#   Redistribution and use in source and binary forms, with or without
#   modification, are permitted provided that the following conditions
#   are met:
#
#     * Redistributions of source code must retain the above copyright
#       notice, this list of conditions and the following disclaimer.
#     * Redistributions in binary form must reproduce the above copyright
#       notice, this list of conditions and the following disclaimer in
#       the documentation and/or other materials provided with the
#       distribution.
#     * Neither the name of NXP nor the names of its
#       contributors may be used to endorse or promote products derived
#       from this software without specific prior written permission.
#
#   THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
#   "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
#   LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
#   A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
#   OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
#   SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
#   LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
#   DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
#   THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
#   (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
#   OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

include $(RTE_SDK)/mk/rte.vars.mk

#
# library name
#
LIB = librte_bus_fslmc.a

ifeq ($(CONFIG_RTE_LIBRTE_DPAA2_PMD),y)
CONFIG_RTE_LIBRTE_FSLMC_BUS = $(CONFIG_RTE_LIBRTE_DPAA2_PMD)
endif

ifeq ($(CONFIG_RTE_LIBRTE_DPAA2_DEBUG_INIT),y)
CFLAGS += -O0 -g
CFLAGS += "-Wno-error"
else
CFLAGS += -O3
CFLAGS += $(WERROR_FLAGS)
endif

CFLAGS += -I$(RTE_SDK)/drivers/bus/fslmc
CFLAGS += -I$(RTE_SDK)/drivers/bus/fslmc/mc
CFLAGS += -I$(RTE_SDK)/drivers/bus/fslmc/qbman/include
CFLAGS += -I$(RTE_SDK)/lib/librte_eal/linuxapp/eal

# versioning export map
EXPORT_MAP := rte_bus_fslmc_version.map

# library version
LIBABIVER := 1

SRCS-$(CONFIG_RTE_LIBRTE_FSLMC_BUS) += \
        qbman/qbman_portal.c

SRCS-$(CONFIG_RTE_LIBRTE_FSLMC_BUS) += \
	mc/dpmng.c \
        mc/dpbp.c \
        mc/dpio.c \
        mc/mc_sys.c \
	mc/dpcon.c \
	mc/dpci.c

SRCS-$(CONFIG_RTE_LIBRTE_FSLMC_BUS) += portal/dpaa2_hw_dpio.c
SRCS-$(CONFIG_RTE_LIBRTE_FSLMC_BUS) += portal/dpaa2_hw_dpbp.c
SRCS-$(CONFIG_RTE_LIBRTE_FSLMC_BUS) += portal/dpaa2_hw_dpci.c
SRCS-$(CONFIG_RTE_LIBRTE_FSLMC_BUS) += fslmc_vfio.c
SRCS-$(CONFIG_RTE_LIBRTE_FSLMC_BUS) += fslmc_bus.c

include $(RTE_SDK)/mk/rte.lib.mk
