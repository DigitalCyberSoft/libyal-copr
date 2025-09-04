# COPR Makefile for automated libyal bundle builds
# This is self-contained - generates spec file and downloads sources

# Version identifiers for each library
# Note: Only including libraries that have actual GitHub releases
LIBCERROR_VERSION = 20240413
LIBCTHREADS_VERSION = 20240413
LIBCDATA_VERSION = 20240414
LIBCLOCALE_VERSION = 20240414
LIBCNOTIFY_VERSION = 20240414
LIBUNA_VERSION = 20240414
LIBCFILE_VERSION = 20240414
LIBCPATH_VERSION = 20240414
LIBBFIO_VERSION = 20240414
LIBFCACHE_VERSION = 20240414
LIBFGUID_VERSION = 20240415

# Bundle version (use latest library date)
BUNDLE_VERSION = 20240415

# GitHub base URL
GITHUB_URL = https://github.com/libyal

# SRPM target is required by COPR
srpm:
	@echo "Starting libyal bundle SRPM build for version $(BUNDLE_VERSION)"
	
	# Download all library tarballs
	@echo "Downloading libyal library sources..."
	curl -L -o libcerror-beta-$(LIBCERROR_VERSION).tar.gz $(GITHUB_URL)/libcerror/releases/download/$(LIBCERROR_VERSION)/libcerror-beta-$(LIBCERROR_VERSION).tar.gz
	curl -L -o libcthreads-alpha-$(LIBCTHREADS_VERSION).tar.gz $(GITHUB_URL)/libcthreads/releases/download/$(LIBCTHREADS_VERSION)/libcthreads-alpha-$(LIBCTHREADS_VERSION).tar.gz
	curl -L -o libcdata-alpha-$(LIBCDATA_VERSION).tar.gz $(GITHUB_URL)/libcdata/releases/download/$(LIBCDATA_VERSION)/libcdata-alpha-$(LIBCDATA_VERSION).tar.gz
	curl -L -o libclocale-alpha-$(LIBCLOCALE_VERSION).tar.gz $(GITHUB_URL)/libclocale/releases/download/$(LIBCLOCALE_VERSION)/libclocale-alpha-$(LIBCLOCALE_VERSION).tar.gz
	curl -L -o libcnotify-beta-$(LIBCNOTIFY_VERSION).tar.gz $(GITHUB_URL)/libcnotify/releases/download/$(LIBCNOTIFY_VERSION)/libcnotify-beta-$(LIBCNOTIFY_VERSION).tar.gz
	curl -L -o libuna-alpha-$(LIBUNA_VERSION).tar.gz $(GITHUB_URL)/libuna/releases/download/$(LIBUNA_VERSION)/libuna-alpha-$(LIBUNA_VERSION).tar.gz
	curl -L -o libcfile-alpha-$(LIBCFILE_VERSION).tar.gz $(GITHUB_URL)/libcfile/releases/download/$(LIBCFILE_VERSION)/libcfile-alpha-$(LIBCFILE_VERSION).tar.gz
	curl -L -o libcpath-alpha-$(LIBCPATH_VERSION).tar.gz $(GITHUB_URL)/libcpath/releases/download/$(LIBCPATH_VERSION)/libcpath-alpha-$(LIBCPATH_VERSION).tar.gz
	curl -L -o libbfio-alpha-$(LIBBFIO_VERSION).tar.gz $(GITHUB_URL)/libbfio/releases/download/$(LIBBFIO_VERSION)/libbfio-alpha-$(LIBBFIO_VERSION).tar.gz
	curl -L -o libfcache-alpha-$(LIBFCACHE_VERSION).tar.gz $(GITHUB_URL)/libfcache/releases/download/$(LIBFCACHE_VERSION)/libfcache-alpha-$(LIBFCACHE_VERSION).tar.gz
	curl -L -o libfguid-alpha-$(LIBFGUID_VERSION).tar.gz $(GITHUB_URL)/libfguid/releases/download/$(LIBFGUID_VERSION)/libfguid-alpha-$(LIBFGUID_VERSION).tar.gz
	
	# Generate the spec file using echo commands
	@echo "Generating spec file..."
	@echo '%global giturl https://github.com/libyal' > libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo 'Name:           libyal-bundle' >> libyal-bundle.spec
	@echo 'Version:        $(BUNDLE_VERSION)' >> libyal-bundle.spec
	@echo 'Release:        1%{?dist}' >> libyal-bundle.spec
	@echo 'Summary:        Bundle of libyal forensics libraries for Fedora' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo 'License:        LGPL-3.0-or-later' >> libyal-bundle.spec
	@echo 'URL:            %{giturl}' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '# Core libraries needed by libvhdi and other forensics tools' >> libyal-bundle.spec
	@echo 'Source0:        libcerror-beta-$(LIBCERROR_VERSION).tar.gz' >> libyal-bundle.spec
	@echo 'Source1:        libcthreads-alpha-$(LIBCTHREADS_VERSION).tar.gz' >> libyal-bundle.spec
	@echo 'Source2:        libcdata-alpha-$(LIBCDATA_VERSION).tar.gz' >> libyal-bundle.spec
	@echo 'Source3:        libclocale-alpha-$(LIBCLOCALE_VERSION).tar.gz' >> libyal-bundle.spec
	@echo 'Source4:        libcnotify-beta-$(LIBCNOTIFY_VERSION).tar.gz' >> libyal-bundle.spec
	@echo 'Source5:        libuna-alpha-$(LIBUNA_VERSION).tar.gz' >> libyal-bundle.spec
	@echo 'Source6:        libcfile-alpha-$(LIBCFILE_VERSION).tar.gz' >> libyal-bundle.spec
	@echo 'Source7:        libcpath-alpha-$(LIBCPATH_VERSION).tar.gz' >> libyal-bundle.spec
	@echo 'Source8:        libbfio-alpha-$(LIBBFIO_VERSION).tar.gz' >> libyal-bundle.spec
	@echo 'Source9:        libfcache-alpha-$(LIBFCACHE_VERSION).tar.gz' >> libyal-bundle.spec
	@echo 'Source10:       libfguid-alpha-$(LIBFGUID_VERSION).tar.gz' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo 'BuildRequires:  gcc' >> libyal-bundle.spec
	@echo 'BuildRequires:  make' >> libyal-bundle.spec
	@echo 'BuildRequires:  autoconf' >> libyal-bundle.spec
	@echo 'BuildRequires:  automake' >> libyal-bundle.spec
	@echo 'BuildRequires:  libtool' >> libyal-bundle.spec
	@echo 'BuildRequires:  gettext-devel' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '%description' >> libyal-bundle.spec
	@echo 'This package bundles multiple libyal libraries required for forensics tools' >> libyal-bundle.spec
	@echo 'like libvhdi. It includes libcerror, libcthreads, libcdata, and other' >> libyal-bundle.spec
	@echo 'supporting libraries.' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo 'These libraries provide:' >> libyal-bundle.spec
	@echo '- Error handling (libcerror)' >> libyal-bundle.spec
	@echo '- Thread support (libcthreads)' >> libyal-bundle.spec
	@echo '- Data structures (libcdata)' >> libyal-bundle.spec
	@echo '- Locale support (libclocale)' >> libyal-bundle.spec
	@echo '- Notification support (libcnotify)' >> libyal-bundle.spec
	@echo '- Unicode support (libuna)' >> libyal-bundle.spec
	@echo '- File I/O abstraction (libbfio, libcfile, libcpath)' >> libyal-bundle.spec
	@echo '- Caching support (libfcache)' >> libyal-bundle.spec
	@echo '- GUID support (libfguid)' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '%package        devel' >> libyal-bundle.spec
	@echo 'Summary:        Development files for libyal libraries' >> libyal-bundle.spec
	@echo 'Requires:       %{name}%{?_isa} = %{version}-%{release}' >> libyal-bundle.spec
	@echo 'Requires:       pkgconfig' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '%description    devel' >> libyal-bundle.spec
	@echo 'The %{name}-devel package contains libraries and header files for' >> libyal-bundle.spec
	@echo 'developing applications that use libyal libraries.' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '%prep' >> libyal-bundle.spec
	@echo '# Extract all sources' >> libyal-bundle.spec
	@echo 'tar xzf %{SOURCE0}' >> libyal-bundle.spec
	@echo 'tar xzf %{SOURCE1}' >> libyal-bundle.spec
	@echo 'tar xzf %{SOURCE2}' >> libyal-bundle.spec
	@echo 'tar xzf %{SOURCE3}' >> libyal-bundle.spec
	@echo 'tar xzf %{SOURCE4}' >> libyal-bundle.spec
	@echo 'tar xzf %{SOURCE5}' >> libyal-bundle.spec
	@echo 'tar xzf %{SOURCE6}' >> libyal-bundle.spec
	@echo 'tar xzf %{SOURCE7}' >> libyal-bundle.spec
	@echo 'tar xzf %{SOURCE8}' >> libyal-bundle.spec
	@echo 'tar xzf %{SOURCE9}' >> libyal-bundle.spec
	@echo 'tar xzf %{SOURCE10}' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '%build' >> libyal-bundle.spec
	@echo '# Build order matters - dependencies first' >> libyal-bundle.spec
	@echo '# Note: Each library is in its own versioned directory' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '# Build libcerror first (error handling)' >> libyal-bundle.spec
	@echo 'cd libcerror-$(LIBCERROR_VERSION)' >> libyal-bundle.spec
	@echo '%configure --disable-static --enable-wide-character-type' >> libyal-bundle.spec
	@echo '%make_build' >> libyal-bundle.spec
	@echo 'cd ..' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '# Build remaining libraries in dependency order' >> libyal-bundle.spec
	@echo 'for lib in libcthreads-$(LIBCTHREADS_VERSION) libcdata-$(LIBCDATA_VERSION) \\' >> libyal-bundle.spec
	@echo '           libclocale-$(LIBCLOCALE_VERSION) libcnotify-$(LIBCNOTIFY_VERSION) \\' >> libyal-bundle.spec
	@echo '           libuna-$(LIBUNA_VERSION) libcfile-$(LIBCFILE_VERSION) \\' >> libyal-bundle.spec
	@echo '           libcpath-$(LIBCPATH_VERSION) libbfio-$(LIBBFIO_VERSION) \\' >> libyal-bundle.spec
	@echo '           libfcache-$(LIBFCACHE_VERSION) libfguid-$(LIBFGUID_VERSION); do' >> libyal-bundle.spec
	@echo '    cd $$lib' >> libyal-bundle.spec
	@echo '    %configure --disable-static --enable-wide-character-type' >> libyal-bundle.spec
	@echo '    %make_build' >> libyal-bundle.spec
	@echo '    cd ..' >> libyal-bundle.spec
	@echo 'done' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '%install' >> libyal-bundle.spec
	@echo '# Install all libraries' >> libyal-bundle.spec
	@echo 'for lib in libcerror-$(LIBCERROR_VERSION) libcthreads-$(LIBCTHREADS_VERSION) \\' >> libyal-bundle.spec
	@echo '           libcdata-$(LIBCDATA_VERSION) libclocale-$(LIBCLOCALE_VERSION) \\' >> libyal-bundle.spec
	@echo '           libcnotify-$(LIBCNOTIFY_VERSION) libuna-$(LIBUNA_VERSION) \\' >> libyal-bundle.spec
	@echo '           libcfile-$(LIBCFILE_VERSION) libcpath-$(LIBCPATH_VERSION) \\' >> libyal-bundle.spec
	@echo '           libbfio-$(LIBBFIO_VERSION) libfcache-$(LIBFCACHE_VERSION) \\' >> libyal-bundle.spec
	@echo '           libfguid-$(LIBFGUID_VERSION); do' >> libyal-bundle.spec
	@echo '    cd $$lib' >> libyal-bundle.spec
	@echo '    %make_install' >> libyal-bundle.spec
	@echo '    cd ..' >> libyal-bundle.spec
	@echo 'done' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '# Remove libtool archives' >> libyal-bundle.spec
	@echo "find %{buildroot} -name '*.la' -delete" >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '%ldconfig_scriptlets' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '%files' >> libyal-bundle.spec
	@echo '%license libcerror-$(LIBCERROR_VERSION)/COPYING*' >> libyal-bundle.spec
	@echo '%doc libcerror-$(LIBCERROR_VERSION)/AUTHORS' >> libyal-bundle.spec
	@echo '%{_libdir}/lib*.so.*' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '%files devel' >> libyal-bundle.spec
	@echo '%{_includedir}/*' >> libyal-bundle.spec
	@echo '%{_libdir}/lib*.so' >> libyal-bundle.spec
	@echo '%{_libdir}/pkgconfig/*.pc' >> libyal-bundle.spec
	@echo '%{_mandir}/man3/*.3*' >> libyal-bundle.spec
	@echo '' >> libyal-bundle.spec
	@echo '%changelog' >> libyal-bundle.spec
	@echo '* Thu Jan 09 2025 COPR Builder - $(BUNDLE_VERSION)-1' >> libyal-bundle.spec
	@echo '- Automated build from COPR' >> libyal-bundle.spec
	@echo '- Bundle of core libyal libraries for forensics tools' >> libyal-bundle.spec
	@echo '- Includes 11 essential libyal libraries with releases' >> libyal-bundle.spec
	
	# Create SRPM
	@echo "Building SRPM..."
	rpmbuild -bs \
		--define "_sourcedir $(PWD)" \
		--define "_specdir $(PWD)" \
		--define "_builddir $(PWD)" \
		--define "_srcrpmdir $(outdir)" \
		--define "_rpmdir $(PWD)" \
		libyal-bundle.spec
	
	@echo "SRPM build complete"

# Clean target for local testing
clean:
	rm -f *.tar.gz *.spec *.src.rpm

.PHONY: srpm clean