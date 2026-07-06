# Topaz Offline Download Server

A local mirror for **Topaz Photo**, **Topaz Gigapixel**, **Topaz Video** and related AI model & GPU files.

This project allows you to install and restore Topaz AI models from a local server instead of downloading them from the Internet each time. It is intended for offline installations, system rebuilds, custom Windows images, and long-term software preservation.

---

## Features

* Offline AI model installation
* Local mirror using a simple HTTP server
* Supports multiple Topaz products and versions
* Preserves models that may no longer be distributed
* Eliminates repeated downloads after system reinstalls
* Error reporting of files and 404 from backup server pin pointing file location in v6.1.0

---

## Why?

Even when the correct AI model files are already present, Topaz installers and applications may still attempt to contact Topaz's servers before continuing.

This project recreates the expected download structure locally, allowing the software to retrieve model files from your own server whenever possible.

## Installation Time

Offline Est: > 13 Minutes

Online Est: < 20-45 Minutes

---

## Repository Statistics

* **GPU TESTED:** 5070

* **Model files:** 325
* **StarLight 1.0:** 3
* **Neuroserver:** 2
* **StarLight 2.5:** 1
* **Approximate size:** 92.4 GB

---

## Intended Uses

* Offline installation
* Local backup offline server
* Windows deployment (OOBE/Sysprep)
* Virtual machines
* Software preservation
* Archival of Legacy & New Topaz Releases

---

## Goal

Preserve the availability of Topaz applications for future installations, even if official download sources change or become unavailable.

Archive download source will be implemented once discontinued from Topaz.

## Not Possible at this time

Topaz Sharpen AI

## UnTested Legacy Softwares

Adjust AI

Mask AI

Jpeg to Raw AI

DeNoise AI

Sharpen AI

Plugins


![github-small](https://github.com/91ajames/Topaz-Offline-Download-Server/blob/main/Topaz%20Model%20Downloader%205.5.0.png)

![github-small](https://github.com/91ajames/Topaz-Offline-Download-Server/blob/main/Topaz%20Model%20Downloader%205.0.3.png)

![github-small](https://github.com/91ajames/Topaz-Offline-Download-Server/blob/main/Topaz%20Model%20Downloader%205.0.0.png)

![github-small](https://raw.githubusercontent.com/91ajames/Topaz-Offline-Mirror-Server/refs/heads/main/TopazMirrorServer.png)
