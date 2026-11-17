# Customized Odoo — public upstream sources

هذا المستودع العام يجمع **أودو Community الأصلي** وإضافات الطرف الثالث الأصلية، دون تخصيصات MIFSmart الخاصة أو بيانات تشغيل العملاء.

| Component | Source / location | License |
|---|---|---|
| Odoo Community 20.0 | `odoo/` — pinned Git submodule from [odoo/odoo](https://github.com/odoo/odoo) | LGPL-3.0 |
| 8 original Odoo Mates addons | `third_party/odoomates/` — 326 files, unchanged | LGPL-3.0 |
| MIFSmart addons and deployment tools | [private odoo_mif_addons repository](https://github.com/RealFarghaly/odoo_mif_addons) | Per-module license |

## Get all source files

```bash
git clone --recurse-submodules https://github.com/RealFarghaly/custom-odoo.git
cd custom-odoo
```

For an existing clone:

```bash
git submodule update --init --recursive
```

**GitHub Download ZIP does not include Git submodule contents.** Use the commands above to obtain Odoo core, or use the checksum-pinned official corresponding-source archive in `sources.lock.json`. The original Python dependency list is `odoo/requirements.txt`; dependencies retain their original public sources and licenses.

## Version and ownership

`sources.lock.json` pins the official Odoo source revision, the official nightly package and corresponding-source checksums used by the current pinned MIFSmart runtime, and the original Odoo Mates revision. Nightly packaging sets its own version metadata. The production build continues using the tested official package checksum, rather than rebuilding an unverified Git revision.

`upstream-files.json` records every Odoo Mates file's original Git blob hash and size. The private runtime fetches only those exact paths from an immutable commit of this public repository and verifies each byte before building. Changes and integrations belong in our separately named private addons; no third-party ownership is claimed.

This repository alone is upstream source, not the configured MIFSmart runtime. The public 7-day demonstration of Customized Odoo uses **one existing shared Odoo database** and creates **one ordinary Odoo user per verified signup**, not an isolated installation or database per trial. The signup service and user-account provisioning tools live in the private MIFSaaS and odoo_mif_addons repositories. Commercial customer installations remain independent deployments managed separately. The checked-in upstream Odoo submodule and package remain checksum-pinned; fetching this repository does not automatically upgrade the live Odoo image.
