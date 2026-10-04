# Topaz Offline Download Creator **v7.0.3**

Version **7.0.3** is the current major update to the Offline Download Creator.

One of the biggest changes is **application/version selection**, so you can build the offline mirror around the Topaz versions you actually want instead of downloading the entire inventory.

v7.0.3 also expands captured application coverage, adds **Video 1.7.1**, improves interrupted and resumable downloads, strengthens Error.txt recovery/discovery, and updates the local HTTPS certificate workflow.

The project Wiki contains the deeper architecture, testing, recovery, certificate, and inventory details. This README is intended to stay as the shorter project overview.

---

# Topaz Offline Download Server

A local **HTTP/HTTPS mirror and preservation server** for **Topaz Photo**, **Topaz Gigapixel**, **Topaz Video**, **Topaz Photo AI**, **Topaz Sharpen AI**, and related AI model, support, and GPU files.

This project allows supported Topaz applications to install, restore, and retrieve captured files from a local server instead of repeatedly downloading them from the Internet.

It is intended for **offline installations, system rebuilds, custom Windows images, virtual machines, archival use, and long-term software preservation**.

---

## Features

- Application/version selection for targeted offline mirror creation
- Offline AI model installation and restoration
- Local HTTP and HTTPS Topaz download mirror
- Exact host, protocol, and route ownership
- HTTPS-only upstream acquisition and recovery
- Supports multiple Topaz products and application generations
- Windows, macOS, and Linux support
- SHA-256 verification for authoritative V2 inventory files
- ZIP content/CRC validation for supplemental packages without authoritative SHA-256 metadata
- Automatic recovery of eligible files reported through Error.txt
- Recovered-file provenance with actual size, SHA-256, path, and source URL
- Discovered Inventory and Discovered Assets tracking
- Preserves captured models and support files that may later disappear upstream
- Resumable downloads and authenticated `.part` recovery
- Protection against mixing HTTP partial data with an HTTPS replacement
- Local HTTPS Root CA and rotating server-certificate support
- Portable Client-CA install/remove helpers for Windows, macOS, and Linux
- Cross-platform Downloader and SHA-256 Verifier
- Manifest V2 inventory and integrity database
- Server Assets Manifest for recovered and support-file integrity
- Detection and reporting of missing, corrupt, incomplete, or unavailable files
- Built-in route, recovery, certificate, generated-program, and determinism self-tests

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

**Offline estimate:** approximately 13+ minutes

**Online estimate:** approximately 20–45 minutes

Actual time depends on storage performance, network speed, file verification, certificate setup, selected applications, and the amount of inventory that needs to be downloaded.

---

## Repository Statistics

### Platform Support

- **Windows**
- **macOS**
- **Linux**

### Tested Hardware

- **GPU Tested:** NVIDIA GeForce RTX 5090

### Logical Inventory

- **Video AI 3.1.8:** 2147
- **Video 1.6.1:** 127
- **Video 1.7.1:** 332 - StarLight 2.6 included
- **Gigapixel 1.3.1:** 97
- **Gigapixel 5.5.2:** 120
- **Gigapixel 8.4.4:** 87
- **Photo 1.6.1:** 126
- **Photo AI 4.0.1:** 98
- **Sharpen AI 4.1.0:** 98
- **Raw Models:** 132
- **Video AI 7.1.5 Extra Packages:** 6
- **Video 1.6.1 Extra Packages:** 5
- **Starlight 2.5 Extra Packages:** 1

### Inventory Totals

- **Snapshot Manifests:** 13
- **Logical Inventory Entries:** 3246
- **Known Logical Inventory Size:** 358.71 GB
- **Probing Inventory Entries:** 976
- **Probing Logical Inventory Size:** 186.35 GB
- **Unique Physical Files:** 3073
- **Known Unique Physical Size:** 319.18 GB
- **Missing Inventory Metadata:** 1
- **Approved Host Alias Paths:** 81
- **Additional URLs:** 111

The logical inventory total can be larger than the unique physical-file total because multiple captured logical references may resolve to the same physical mirror file.

### Known Unavailable Package

One captured Video AI package currently remains unavailable upstream and does not have authoritative size or SHA-256 metadata:

`astra_support/20250825/models.zip`

The captured route remains preserved instead of inventing metadata or removing the package simply because the upstream file is unavailable.

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

---

## Goal

The goal of this project is to preserve the ability to reinstall and restore supported Topaz applications and their required model files in the future, even if official download locations change or individual files become unavailable.

Availability does not determine whether a captured file belongs in the historical inventory.

If a file was legitimately captured as part of a supported Topaz workflow, its route and metadata are preserved even when the original upstream source later disappears.

No unofficial replacement source is substituted for an original Topaz asset simply because the official source becomes unavailable.

---

## Version 7.0.3

Version **7.0.3 Build 263** expands the 7.0.x architecture with a larger inventory and a more selective, recoverable, and portable offline workflow.

Major updates include:

- Application/version selection
- Video 1.7.1 inventory and route support
- Expanded inventory to **1109 logical entries** and **936 unique physical files**
- Improved interrupted-download and `.part` resume handling
- HTTPS-only acquisition with protected recovery boundaries
- Error.txt-driven recovery with `URL :` and `REPORTED-FIXED :` state tracking
- Discovered Inventory and Discovered Assets support
- Exact-path route ownership and probing inventory
- Four-hour private Root CA with 30-minute CA-signed server certificates
- Portable Client-CA helpers for remote Windows, macOS, and Linux computers
- Stronger generated Downloader, Verifier, Repeater, and launcher validation
- Consolidated regression and determinism testing

Build 263 has completed the consolidated self-test successfully on both **Windows** and **Linux**.

The earlier 7.0.0 release was the major rebuild from the 6.2.0 architecture. Detailed version history and implementation notes are kept in the project Wiki and changelog.

---

## Local Access

Access through `localhost` or a direct IP address is intentionally disabled while the server is running.

This behavior is by design and there is no setting, toggle, or on/off switch to enable it.

---

Download Selection results

2nd picture below is a normal flow run.

![github-small](https://github.com/91ajames/Topaz-Offline-Download-Server/blob/main/Topaz_Offline_Download_Creator_7.0.3-application-selection.png)

![github-small](https://github.com/91ajames/Topaz-Offline-Download-Server/blob/main/Topaz_Offline_Download_Creator_7.0.3.png)
