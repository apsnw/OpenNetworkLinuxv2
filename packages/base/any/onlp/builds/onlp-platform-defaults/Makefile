# -*- Makefile -*-
############################################################
# <bsn.cl fy=2014 v=onl>
#
#           Copyright 2014 BigSwitch Networks, Inc.
#
# Licensed under the Eclipse Public License, Version 1.0 (the
# "License"); you may not use this file except in compliance
# with the License. You may obtain a copy of the License at
#
#        http://www.eclipse.org/legal/epl-v10.html
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
# either express or implied. See the License for the specific
# language governing permissions and limitations under the
# License.
#
# </bsn.cl>
############################################################
#
# Build the ONLP Default Platform Library.
#
# This library provides the baseline stub implementations
# for all required ONLP entry points.
#
# All ONLP applications are linked against this library.
#
#
############################################################
include $(ONL)/make/any.mk

MODULE := libonlp-platform-defaults-module
include $(BUILDER)/standardinit.mk

#
# We use the onlp_platform_defaults entry points as
# the link stubs
#
DEPENDMODULES := AIM onlplib onlp_platform_defaults IOF sff

include $(BUILDER)/dependmodules.mk

SHAREDLIB := libonlp-platform-defaults.so
$(SHAREDLIB)_TARGETS := $(ALL_TARGETS)
LDFLAGS += -Wl,--version-script=$(ONL)/make/onlp.version
include $(BUILDER)/so.mk

.DEFAULT_GOAL := sharedlibs

GLOBAL_CFLAGS += -DAIM_CONFIG_INCLUDE_CTOR_DTOR=1
GLOBAL_CFLAGS += -DONLP_PLATFORM_DEFAULTS_CONFIG_AS_PLATFORM=0
GLOBAL_CFLAGS += -I$(onlp_BASEDIR)/module/inc
GLOBAL_CFLAGS += -fPIC
GLOBAL_LINK_LIBS += -lpthread

include $(BUILDER)/targets.mk

.PHONY: deb
deb:
	$(MAKE) -C deb
