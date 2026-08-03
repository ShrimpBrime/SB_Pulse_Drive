SB Pulse Drive

Short, controlled multi-drive activity pulses for Windows.

SB Pulse Drive is a lightweight portable utility created to wake and exercise multiple HDDs and SSDs at the same time. It was designed as a companion to SB SSD Temps, making it easy to check multi-drive activity gauges while producing useful short-duration throughput snapshots.

It is a testing app with benchmark perks—not a deep storage-analysis, endurance, or certification tool.

Highlights

Select and pulse multiple physical drives simultaneously

Dedicated 2-second and 5-second Extreme benchmark buttons

Equal-weight Multi-Drive Average for mixed HDD and SSD systems

Read + Write, Read Only, and Write Only modes

Multi-Tach, Light, Medium, Heavy, and Extreme activity levels

Simultaneous or one-drive-at-a-time scheduling

Windows-reported model, media type, interface, firmware, filesystem, size, and free space

Scrollable drive list and expandable results panel

Copyable results with run settings and system details

Application-window and full-desktop screenshots

Custom accent colors, themes, and font selection

Built-in Support and About windows

Single portable EXE—no installer required

Why the tests are short

SB Pulse Drive intentionally uses brief storage loads. The goal is to wake drives, create visible activity, and provide a quick comparison while keeping writes and drive wear to a practical minimum.

The 2-second and 5-second Extreme presets request a short burst of available bandwidth. Results can be affected by Windows caching, controllers, adapters, RAID configurations, drive firmware, thermal state, background activity, and the selected drive set. Compare results only when these conditions—and the application version—remain consistent.

Multi-Drive Average

Each selected physical drive receives equal weight, so a fast NVMe drive does not hide a slower SATA SSD or HDD.

For N selected drives:

Average Read  = Sum of verified drive read rates  / N
Average Write = Sum of verified drive write rates / N

Final Multi-Drive Average = (Average Read + Average Write) / 2

Rates are calculated from completed bytes divided by measured phase time. Speed is displayed using decimal units: 1 MB = 1,000,000 bytes, with the display changing to GB/s at 1,000 MB/s.

The final result is an equal-weight average, not the system's combined aggregate bandwidth. A score is displayed only when every selected drive returns verified read and write phase averages.

Benchmark presets

Preset

Operation

Schedule

Activity

2s Extreme Bench

2-second write + 2-second read

Simultaneous

Unthrottled Extreme

5s Extreme Bench

5-second write + 5-second read

Simultaneous

Unthrottled Extreme

The dedicated buttons apply their fixed settings immediately before launch, so manual controls cannot accidentally alter the benchmark configuration. Completed 2-second and 5-second averages remain visible together until Clear Results is pressed or the application is restarted.

Temporary-file transparency

SB Pulse Drive never performs raw-disk access. Write modes work through the mounted Windows filesystem using a unique temporary directory on each selected volume:

<Drive>:\SB_Pulse_Drive_Temp_<32-character GUID>\

Depending on the selected mode, the directory contains:

write-pulse.tmp for limited write activity, or

extreme-write-0.tmp through extreme-write-3.tmp for Extreme activity

The payload is pseudo-random data generated in memory. Each Extreme file is limited to 256 MiB, for a maximum combined temporary-file footprint of 1 GiB per selected drive. Files grow only through completed writes; initialized contents may then be overwritten repeatedly for the selected phase duration.

The app attempts cleanup after completion, cancellation, or a handled failure. If Windows or a sudden interruption prevents cleanup, the clearly named abandoned temporary directory can be removed manually after confirming that SB Pulse Drive is no longer running.

Write modes require the visible acknowledgment before they can start. Read Only makes no intentional writes and does not create this temporary payload.

Safety model

Mounted local volumes only

One selected volume per detected physical disk

No formatting, partitioning, optimization, or raw-disk commands

Live free-space validation before write activity

Extreme temporary footprint limited to 1 GiB per selected drive

Automatic cleanup after normal completion, cancellation, or handled failure

Drive selections and run settings locked while activity is in progress

STOP requests cancellation and allows cleanup to finish

As with any utility that performs storage I/O, keep important data backed up. Do not disconnect, power off, or remove a selected drive while a pulse is running.

System requirements

64-bit Windows 10 or Windows 11

Administrator access for complete drive discovery and operation

A mounted local volume on each drive being tested

Drive identity and hardware details are reported conservatively from information exposed by Windows and the active storage controller or adapter. Unsupported or unavailable fields are not estimated from model names.

Quick start

Download and extract the signed release ZIP.

Run SB_Pulse_Drive_v1.2.exe.

Approve administrator access.

Select the drives you want to test.

Choose 2s Extreme Bench, 5s Extreme Bench, or configure a manual pulse.

For a write mode, read and select the required temporary-file acknowledgment.

Review the results, copy them, or save a screenshot.

For a non-writing wake-up test, choose Read Only or use the Multi-Tach preset.

Release verification

SB Pulse Drive v1.2 — Release 013

The public EXE is Authenticode-signed and timestamped to Jon Bauer
SB_Pulse_Drive_v1.2.exe
SHA-256: 63DAE6D782FAD4B6489D7E6118EFB353A790482E8E3751410EB0D0C236B878EE

SB_Pulse_Drive_v1.2_RELEASE_013_SIGNED.zip
SHA-256: 76D763B51AED475C46D28A89F01F1EB4932E12FC06786D4837E7B754BC6C300F

To verify a downloaded file in PowerShell:

Get-FileHash ".\SB_Pulse_Drive_v1.2.exe" -Algorithm SHA256
Get-AuthenticodeSignature ".\SB_Pulse_Drive_v1.2.exe" |
    Format-List Status, StatusMessage, SignerCertificate, TimeStamperCertificate

Support

Documentation and troubleshooting are built into the application under Support.

Community support: SB SSD Temps Forum

Libre Hardware Monitor is not bundled with SB Pulse Drive; where referenced in support material, it is used only as an optional source of additional drive information—not temperature monitoring. Temperature and multi-tach monitoring remain the responsibility of SB SSD Temps.

Project status

Version 1.2 is the finished portable release. Feedback and reproducible test results are welcome, especially when they include the app version, Windows version, selected drive models, run preset, and copied results.

Copyright © 2026 Jon Bauer. All rights reserved.ShrimpBrime™ is an unregistered trademark of Jon Bauer.

SB Pulse Drive, its original interface, documentation, and application-specific implementation are the intellectual property of Jon Bauer except where third-party components or platform technologies retain their respective ownership.
