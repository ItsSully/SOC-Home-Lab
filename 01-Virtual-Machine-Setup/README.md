# 01 - Virtual Machine Setup

## Objective

Build an isolated Windows 11 virtual machine to use as the endpoint for my SOC Analyst home lab.

The virtual machine will be used to generate security telemetry, simulate suspicious activity, collect Windows event logs and investigate security incidents.

---

## Environment

| Component | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Guest OS | Windows 11 Pro 64-bit |
| Virtual CPUs | 4 |
| RAM | 6144 MB |
| Virtual Disk | 80 GB |
| Firmware | EFI |
| TPM | TPM 2.0 |
| Secure Boot | Enabled |
| Network | NAT |
| Graphics Controller | VBoxSVGA |
| Guest Additions | Installed |

---

## Installation Process

### 1. Created Windows 11 Virtual Machine

Created a new VirtualBox VM named:

`SOC-Windows`

The VM was configured with 4 virtual CPUs, 6 GB RAM and an 80 GB virtual disk.


![VirtualBox VM Configuration](Screenshots/Creating%20VM.png)


![VirtualBox VM Configuration](Screenshots/VM%20Created.png)


### 2. Windows 11 Installation

Mounted the official Windows 11 ISO and installed Windows 11 Pro.

During installation, Windows reported that the processor did not meet the minimum requirements.

The VM configuration was checked and the number of virtual CPUs was increased to 4.

The installation then continued successfully.


![Windows 11 Installation](Screenshots/Windows%20Installation%20Working.png)


### 3. Windows Configuration

After installation:

- Completed Windows setup
- Configured the Windows user account
- Ran Windows Update
- Installed available updates
- Verified the system booted successfully

### 4. VirtualBox Guest Additions

VirtualBox Guest Additions was installed to improve integration between the host machine and the virtual machine.

This enabled:

- Mouse integration
- Dynamic screen resizing
- Improved interaction between the host and guest operating system


![Guest Additions](Screenshots/VM%20Guest%20Addition%20Download.png)


### 5. Final VM

After installation and configuration, the Windows 11 virtual machine was successfully booted and verified.


![Final SOC Windows VM](Screenshots/Final%20SOC%20Window.png)


### 6. Baseline Snapshot

Created a VirtualBox snapshot:

`Clean Windows 11 - Before SOC Lab`

A clean VirtualBox snapshot was created before beginning SOC lab configuration. This snapshot provides a clean rollback point.


![Clean Baseline Snapshot](Screenshots/Clean%20Baseline%20Snapshot.png)


---

## Problems Encountered

### VM Windows 11 initially failed to boot

VirtualBox reported that no bootable operating system could be found.

The Windows 11 ISO was reattached to the VM's optical drive and the installation was restarted.

### Windows 11 processor requirement

Windows Setup reported:

> The processor needs to have two or more cores.

The VM was checked and configured with 4 virtual CPUs.

### Guest Additions failed to mount

VirtualBox initially reported that the VM had no optical drive.

A virtual optical drive was added through:

VirtualBox → Settings → Storage

The `VBoxGuestAdditions.iso` image was then mounted successfully.

### Result

The Windows 11 VM was successfully installed, updated and configured with Guest Additions.

A clean baseline snapshot was created before beginning SOC lab configuration.

### Lessons Learned

This setup process reinforced the importance of:

- Correct VM hardware configuration
- Understanding virtual optical drives
- Checking boot order when a VM fails to start
- Using snapshots before making major configuration changes
- Installing Guest Additions for improved VM usability


---

## Current Status

**Status: COMPLETE ✅**

The VM is ready for the next stage:

- Windows security configuration
- Security auditing
- Sysmon installation
- Event log collection
- SIEM integration
- Detection engineering
- Security investigations
