first_rule: all

all: build install

PACKAGE_NAME := ffmpeg-3.4.2
PACKAGE_DIR := ffmpeg-3.4.2

# Configuration
PACKAGE_CONF := \
    --prefix=$(CURDIR)/../../OBJ/ \
    --disable-x86asm \

test_directory:
	if [ ! -d $(CURDIR)/../../TARGET ]; then \
	   mkdir $(CURDIR)/../../TARGET/; \
	fi
	if [ -d $(CURDIR)/../../TARGET/$(PACKAGE_DIR) ]; then \
	       echo "Folder existed"; \
	else \
	       tar xvf $(CURDIR)/$(PACKAGE_NAME).tar.bz2 -C $(CURDIR)/../../TARGET/; \
	fi

build_lib: test_directory
	cd $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ && ./configure $(PACKAGE_CONF); \

build: build_lib
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ all

pre_install_check:
	if [ ! -d $(CURDIR)/../../OBJ/lib ]; then \
	    mkdir -p $(CURDIR)/../../OBJ/lib; \
	fi
	if [ ! -d $(CURDIR)/../../OBJ/bin ]; then \
	    mkdir -p $(CURDIR)/../../OBJ/bin; \
	fi

install: pre_install_check
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ install
	
config_rule:

clean_rule:

uninstall_rule:
