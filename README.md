# libyal Bundle COPR for Fedora

This repository provides a bundle of libyal forensics libraries for Fedora 40, 41, 42, and rawhide through COPR.

## What is libyal?

libyal is a collection of libraries for digital forensics and data recovery. These libraries are used by various forensics tools to:
- Parse file formats
- Access encrypted volumes
- Read disk images
- Analyze Windows artifacts
- Handle various data structures

## Libraries Included

This bundle includes 14 core libyal libraries:

| Library | Purpose |
|---------|---------|
| **libcerror** | Cross-platform error handling |
| **libcthreads** | Cross-platform thread support |
| **libcdata** | Cross-platform data structures (arrays, lists, trees) |
| **libclocale** | Cross-platform locale support |
| **libcnotify** | Cross-platform notification/logging support |
| **libcsplit** | Cross-platform string splitting |
| **libuna** | Unicode and ASCII conversion support |
| **libcfile** | Cross-platform file I/O |
| **libcpath** | Cross-platform path handling |
| **libbfio** | Basic file input/output abstraction |
| **libfcache** | File data caching |
| **libfdata** | File data handling with caching |
| **libfguid** | GUID/UUID support |
| **libfvalue** | Value type support |

## Quick Installation

Once the COPR repository is active:

```bash
# Enable the COPR repository (replace YOUR_USERNAME with actual username)
sudo dnf copr enable YOUR_USERNAME/libyal-bundle

# Install the bundle
sudo dnf install libyal-bundle

# For development
sudo dnf install libyal-bundle-devel
```

## Why Use This Bundle?

### Benefits:
- **Single package**: Install all core libyal libraries at once
- **Dependency resolution**: Libraries are built in correct order
- **Forensics ready**: Enables tools like libvhdi, libbde, libewf, etc.
- **Regular updates**: Automated builds from upstream releases
- **Fedora native**: Built specifically for Fedora 40-42 and rawhide

### Use Cases:
- Digital forensics investigations
- Data recovery operations
- Building forensics tools that depend on libyal
- Academic research in digital forensics
- Security incident response

## Building Locally

### Prerequisites

```bash
sudo dnf install -y gcc make autoconf automake libtool \
                    gettext-devel rpm-build rpmdevtools
```

### Build Process

```bash
# Clone this repository
git clone https://github.com/YOUR_USERNAME/libyal-copr
cd libyal-copr

# Test the COPR Makefile locally
make -f .copr/Makefile srpm outdir=.

# Or build RPMs directly
rpmdev-setuptree
cp *.src.rpm ~/rpmbuild/SRPMS/
rpmbuild --rebuild ~/rpmbuild/SRPMS/libyal-bundle-*.src.rpm
```

## COPR Setup Instructions

### 1. Push to GitHub

```bash
git remote add origin https://github.com/YOUR_USERNAME/libyal-copr.git
git add -A
git commit -m "Initial commit: libyal bundle for Fedora"
git push -u origin master
```

### 2. Create COPR Project

1. Go to https://copr.fedorainfracloud.org/
2. Sign in with Fedora Account System (FAS) credentials
3. Click "New Project"
4. Fill in:
   - **Project Name:** `libyal-bundle`
   - **Description:** `Bundle of libyal forensics libraries for Fedora`
   - **Homepage:** `https://github.com/libyal`

### 3. Add Package

1. Go to "Packages" tab
2. Click "New Package"
3. Configure:
   - **Package name:** `libyal-bundle`
   - **Clone URL:** `https://github.com/YOUR_USERNAME/libyal-copr.git`
   - **Type:** `make srpm`

### 4. Enable Build Targets

Select chroots:
- fedora-40-x86_64
- fedora-41-x86_64
- fedora-42-x86_64
- fedora-rawhide-x86_64

## Integration with Other Tools

### Using with libvhdi

If you need libvhdi with separate libyal libraries:

```bash
# Install libyal bundle first
sudo dnf install libyal-bundle libyal-bundle-devel

# Then build libvhdi against system libyal
# (Requires modified spec file - not the bundled version)
```

### Building Other libyal Tools

With this bundle installed, you can build other libyal tools:

```bash
# Examples of other libyal tools that can use this bundle:
# - libbde (BitLocker Drive Encryption)
# - libewf (Expert Witness Format)
# - libpff (Personal Folder File - Outlook PST)
# - libregf (Windows Registry File)
# - libvshadow (Volume Shadow Snapshots)
```

## Version Information

Current bundle version: **20240415**

Individual library versions:
- libcerror: 20240413
- libcthreads: 20240413
- libcdata: 20240414
- libclocale: 20240414
- libcnotify: 20240414
- libcsplit: 20240414
- libuna: 20240414
- libcfile: 20240414
- libcpath: 20240414
- libbfio: 20240414
- libfcache: 20240414
- libfdata: 20240414
- libfguid: 20240415
- libfvalue: 20240415

## Troubleshooting

### Build Failures

If COPR build fails:
1. Check build.log in COPR web interface
2. Verify all source URLs are accessible
3. Ensure library versions match available releases

### Missing Dependencies

The bundle is self-contained but requires:
- gcc, make, autoconf, automake, libtool
- gettext-devel (for internationalization)

### Conflicts

If you have individual libyal packages installed:
```bash
# Remove individual packages first
sudo dnf remove libcerror libcthreads libcdata
# Then install the bundle
sudo dnf install libyal-bundle
```

## Contributing

To update library versions:
1. Edit version variables in `.copr/Makefile`
2. Test locally with `make -f .copr/Makefile srpm outdir=.`
3. Commit and push changes
4. COPR will automatically rebuild

## License

All libyal libraries are licensed under LGPL-3.0-or-later

## Links

- **Upstream libyal**: https://github.com/libyal
- **Documentation**: https://github.com/libyal/libyal/wiki
- **COPR Project**: https://copr.fedorainfracloud.org/coprs/YOUR_USERNAME/libyal-bundle/
- **Related Projects**:
  - [libvhdi-copr](https://github.com/YOUR_USERNAME/libvhdi-copr)
  - [dfVFS](https://github.com/log2timeline/dfvfs)
  - [Plaso](https://github.com/log2timeline/plaso)

## Support

- **Issues**: Open issue in this repository
- **Upstream Issues**: Report to respective libyal/[library] repositories
- **Fedora COPR**: #fedora-buildsys on Libera.Chat IRC