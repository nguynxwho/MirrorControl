# MirrorControl source publication

MirrorControl is a Windows desktop AirPlay receiver with optional Bluetooth HID input for an iPhone using AssistiveTouch. The application and modified receiver source are licensed under GPL-3.0-only. Third-party components retain their own licenses; see `notices/` and `provenance/`.

## Status

This tree prepares the source publication for a **new runtime candidate**, not the already uploaded 0.3.1 Store package. It does not change the Store submission or install an update. The candidate is not Store-signed, installed or live-tested. Some TikTok videos still have an unresolved AirPlay compatibility issue; no fix is claimed.

The application code is based on the 0.3.1 unified UI. The receiver base is leapbtw/libuxplay commit `437f37514257d9cb513ac7fbdee743b4da85852e`. Internal mDNS uses FDH2/UxPlay commit `b48a6bbf89eb751a6c041fc0b40155952cdc6b4a`. Bluetooth report/GATT implementation references RayrenSX/iPhoneMirror. Modified source and existing copyright notices are retained in this tree.

## Third-party sources

The separately prepared release asset `MirrorControl-runtime-sources-20261029.zip` contains 92 MSYS2 source archives, including source inputs and packaging patches, and provenance manifests. It must be uploaded as a release asset, not committed as a large Git blob. It is approximately 1.21 GB (decimal), below GitHub's individual 2 GiB release-asset limit. No download URL is claimed until the actual public release has been created and checked.

`provenance/runtime-files.json` maps all 138 candidate runtime DLLs to exact matching files from installed MSYS2 packages. `runtime-packages.json` lists 95 binary packages. Several binary subpackages share source archives. `source-archives.json` records the hashes of the 92 retained source archives. Package metadata and byte equality establish provenance; they are not a claim of independent code review or live functionality.

`notices/` contains original installed/upstream notices, including notices read from the pinned x264 and rtmpdump Git source inputs. The source header for JBIG-KIT 2.1 specifies GPL version 2 or any later version, clarifying the shorter GPL-2.0 label in package metadata. FFmpeg's embedded configuration enables GPL and version 3 and does not enable nonfree. Upstream license terms govern each component.

## Build

Use `source/build.ps1` on Windows 11 x64 with .NET Framework 4.8 and Windows WinRT metadata. The native build is documented in `receiver-source/BUILD.md` and `receiver-source/build.sh`. The candidate used MSYS2 UCRT64 GCC 16.2.0, GStreamer 1.28.8, OpenSSL 3.6.5 and libplist 2.7.0.

`packaging/Build-Msix.ps1` takes the MSYS2 `ucrt64/bin` directory as `RuntimeSource` and `ucrt64/lib/gstreamer-1.0` as `PluginRoot`. It traces required PE imports and selected plugins. Use the official Windows SDK MakeAppx. `Get-RuntimeProvenance.ps1`, `Get-RuntimeSources.ps1` and `Collect-RuntimeNotices.ps1` document the collection process; source packages are treated as data, not executed by these scripts.

Before releasing an updated application, increment its Store package version, include the notices and the verified public source URL, and test the changed runtime. Successful packaging does not imply Store certification or Smart App Control compatibility.


## Public source release

The source archives and checksums are published at https://github.com/nguynxwho/MirrorControl/releases/tag/sources-20261029 . GitHub release-asset digests were checked against the retained local files. This release contains source material, not an application installer.
