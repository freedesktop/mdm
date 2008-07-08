VERSION = 0.0.1

all: tree

ubuntu-8.04-install:
	@echo "Installing the mdm-xephyr-gdm package"
	@dpkg -i packages/mdm_$(VERSION)_i386.deb

ubuntu-8.04: tree
	@echo "Creating .deb"
	@cp -r tree ubuntu-8.04-tree
	@cp -r distro/ubuntu-8.04/DEBIAN ubuntu-8.04-tree
	@mkdir -p packages
	@fakeroot dpkg -b ubuntu-8.04-tree packages

tree: prefix
	@echo "Creating file tree in temporary folder tree/"
	@misc/make-tree.sh

prefix:
	@if test ! -z "$(DESTDIR)"; then                        \
                echo "Changing prefix to $(DESTDIR)";           \
                misc/change-prefix.sh $(DESTDIR);               \
        fi

clean:
	rm -rf *tree
	rm -rf packages