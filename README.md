# Topaz Offline Download Server

A local **HTTP/HTTPS mirror and preservation server** for **Topaz Photo**, **Topaz Gigapixel**, **Topaz Video**, **Topaz Photo AI**, **Topaz Sharpen AI**, and related AI model, support, and GPU files.

This project allows supported Topaz applications to install, restore, and retrieve captured files from a local server instead of repeatedly downloading them from the Internet.

It is intended for **offline installations, system rebuilds, custom Windows images, virtual machines, archival use, and long-term software preservation**.

---

## Features

- Offline AI model installation and restoration
- Local HTTP and HTTPS Topaz download mirror
- Exact host, protocol, and route ownership
- Supports multiple Topaz products and application generations
- Windows, macOS, and Linux support
- SHA-256 verification for authoritative V2 inventory files
- ZIP content/CRC validation for supplemental packages without authoritative SHA-256 metadata
- Automatic recovery of eligible files reported through 404/error logging
- Recovered-file provenance with actual size, SHA-256, path, and source URL
- Preserves captured models and support files that may later disappear upstream
- Eliminates repeated multi-gigabyte downloads after system reinstalls
- Resumable downloads and `.part` recovery
- Local HTTPS certificate creation, installation, expiration, and removal support
- Cross-platform Downloader and SHA-256 Verifier
- Manifest V2 inventory and integrity database
- Server Assets Manifest for recovered and support-file integrity
- Detection and reporting of missing, corrupt, incomplete, or unavailable files

---

## Why?

Even when the correct AI model files are already present locally, Topaz installers and applications may still attempt to contact Topaz download servers before continuing.

This project recreates the expected Topaz download structure and network routes locally so supported applications can retrieve captured files from your own mirror whenever possible.

This is especially useful when:

- Reinstalling Windows or another operating system
- Rebuilding a workstation
- Deploying a custom Windows image
- Restoring a virtual machine
- Installing software without Internet access
- Avoiding repeated downloads of very large model packages
- Preserving files that may no longer remain available from their original source

---

## Installation Time

**Offline estimate:** > 13 Minutes

**Online estimate:** approximately 20–45 Minutes

Actual time depends on storage performance, network speed, file verification, certificate setup, and the Topaz products being installed.

---

## Repository Statistics

### Platform Support

- **Windows**
- **macOS**
- **Linux**

### Tested Hardware

- **GPU Tested:** NVIDIA GeForce RTX 5090

### Logical Inventory

- **Video 1.6.1:** 127
- **Gigapixel 1.3.1:** 97
- **Gigapixel 8.4.4:** 87
- **Photo 1.6.1:** 126
- **Photo AI 4.0.1:** 98
- **Sharpen AI 4.1.0:** 98
- **Raw Models:** 132  -  (Will be removed into other inventory in future updates)
- **Video AI 7.1.5 Extra Packages:** 6
- **Video 1.6.1 Extra Packages:** 5
- **Starlight 2.5 Extra Packages:** 1

### Inventory Totals

- **Snapshot Manifests:** 10
- **Logical Inventory Entries:** 777
- **Unique Physical Files:** 606
- **Known Logical Inventory Size:** 180.03 GB
- **Known Unique Physical Size:** 154.67 GB
- **Missing Inventory Metadata:** 1
- **Recovery Mode:**
- 777 + 322 = 1099 logical **V 7.0.2**
- 606 + 322 = 928 physical **V 7.0.2**

- Resume Fix for non https will be fixed in **V 7.0.3**

### Known Unavailable Package

One captured Video AI package currently remains unavailable upstream and does not have authoritative size or SHA-256 metadata:

`astra_support/20250825/models.zip`

The URL remains preserved in the inventory history rather than being removed simply because the upstream file is unavailable.

---

## Integrity Model

Topaz Offline Download Server uses multiple integrity stages depending on how much authoritative information is available for a file.

### Recovery Integrity

Newly discovered recoverable files can be downloaded from approved Topaz hosts and validated before being accepted.

Recovered files are recorded with:

- Source URL
- Mirror path
- Actual file size
- SHA-256
- Recovery provenance

ZIP files also receive full ZIP member/content validation before successful recovery.

### Supplemental Inventory Integrity

Captured packages that do not yet have authoritative V2 SHA-256 metadata remain supported as supplemental inventory.

Depending on available metadata, validation can include:

- File existence
- Exact byte size
- ZIP structure
- ZIP member CRC/content validation

### Manifest V2 Integrity

Authoritative inventory records use:

- Exact URL
- Exact mirror path
- Exact expected byte size
- SHA-256

These records are verified by the generated SHA-256 Verifier and used as the authoritative offline inventory.

---

## Intended Uses

- Offline Installation
- Local Topaz Download Server
- Local AI Model Mirror
- Windows Deployment
- OOBE / Sysprep Images
- Virtual Machines
- Workstation Rebuilds
- Software Preservation
- Archival of Legacy and Current Topaz Releases
- Recovery of Previously Captured Topaz Assets

---

## Capture Method

The inventory was assembled through direct observation of Topaz application behavior, including:

- Application and installer logs
- Download URLs
- Server requests
- HTTP/HTTPS traffic observation
- File-system activity
- Model metadata
- Application state data
- Controlled installation and download testing

Captured URLs, protocols, hosts, paths, file sizes, and hashes are preserved as accurately as possible rather than assuming that similarly named resources are interchangeable.

What's in you're wallet?

---

## Goal

The goal of this project is to preserve the ability to reinstall and restore supported Topaz applications and their required model files in the future, even if official download locations change or individual files become unavailable.

Availability does not determine whether a captured file belongs in the historical inventory.

If a file was legitimately captured as part of a supported Topaz workflow, its route and metadata are preserved even when the original upstream source later disappears.

No unofficial replacement source is substituted for an original Topaz asset simply because the official source becomes unavailable.

---

## Version 7.0.0

Version 7.0.0 was extensively rebuilt from the earlier 6.2.0 architecture.

Major changes include:

- HTTP and HTTPS local serving
- Exact protocol-aware route ownership
- Manifest V2 inventory
- SHA-256 verification
- Supplemental ZIP integrity validation
- 404 recovery and provenance tracking
- Server Assets Manifest
- Cross-platform launchers
- Automated certificate lifecycle
- Downloader integrity and resume handling
- Expanded Topaz application coverage
- Reclassified and expanded model inventory
- Built-in regression and self-testing
- Explicit SUCCESS / INCOMPLETE / FAILED / CANCELLED exit codes

The original 6.2.0 inventory was preserved during the rebuild. All 338 download paths represented by 6.2.0 remain represented in 7.0.0, while the current inventory has expanded to 606 unique physical files and 777 logical inventory entries.

---

## Local Access

Access through `localhost` or a direct IP address is intentionally disabled while the server is running.

This behavior is by design and there is no setting, toggle, or on/off switch to enable it.



---

![github-small](https://github.com/91ajames/Topaz-Offline-Download-Server/blob/main/Topaz_Offline_Download_Creator_7.0.0.png)
