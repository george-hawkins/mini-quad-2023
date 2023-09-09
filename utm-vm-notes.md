I tried Win11 - but Win11 setup just said my machine, i.e. the VM, didn't meet the requirements for Win11.
UTM recommends using <https://github.com/TuringSoftware/CrystalFetch> which is a frontend to <https://uupdump.net/>
I didn't find CrystalFetch or Uupdump very satisfactory (in CrystalFetch, I couldn't see how to get Windows Home N, and Uupdump ended up being too involved on Mac - it generates a shell script that you run to download everything and the shell script requires various bits and pieces included an old openssl version from a secondary tap/cask).
So, I just downloaded the multi-edition ISO from <https://www.microsoft.com/en-us/software-download/windows10ISO>
Had to disable TPM 2.0 (otherwise I got Windows verification errors related to `vioscsi.sys`).

Set the CPU to 'Force multicore' and select 6 cores.

I only have 4 performance cores and 4 efficiency cores but, despite giving it 6 cores, things rarely reached 80%.

I chose "Windows Home N" to get none of the multimedia features and none of the irrelevant Pro features like Bitwarden.

Just accept every default to do with US keyboard, region etc. - I tried and it always failed.
It seemed to go thru the initial steps of asking about setting up an additional keyboard etc. a few times but eventually it completed setup.
Don't enable anything you're allowed skip - like Cortana.

https://support.microsoft.com/en-us/windows/tips-to-improve-pc-performance-in-windows-b3b3ef5b-5953-fb6a-2528-4bbed82fba96

Only points 6 and 8 are relevant - it actually became somewhat useable afterwards.

I re-enabled "Smooth edges of screen fonts".

You can send ctrl-alt-del with ctrl-opt-fn-del (del on Mac is backspace on Win - you have to combine fn and del to get Win del).

Turn off New & Weather and Meet Now areas in the task bar (just right click them).

I disabled all virus and firewall options.

I let update and reboot overnight.

I removed the crown in the search bar by right clicking on the task bar and going to Search / Search Highlights and unticking it.

After Spice guest additions had installed, I cleared both DVD drives (the Windows ISO and Spice drive) - which resulted in odd startup errors but it eventually booted.

Created a share - call it "vm-share".

U-Center 2 just blanked on doing almost anything - the problem seems to have been the default virtio-vga-gl display card.

Switching to virtio-ramfb-gl fixed this but is noticeably slower (and I had to capture the mouse for it to work - press ctrl-opt to uncapture). And also caused the VM to crash.

Hmm... switching just meant it took longer before it failed.

virtio-gpu-gl-pci had the same U-Center 2 as virtio-vga-gl and also caused the VM to crash.

Perhaps Spice needs to be reinstalled after switching to virtio-vga-gl. No - made no difference.

In the end virtio-vga (the version without GPU) worked best - it could handle full screen and didn't require mouse capture. Hmm... it just survived a bit longer but U-Center 2 still failed (could it be U-Center 2 that's the turkey?).

---

Following <https://www.youtube.com/watch?v=za2CyrxKYFs>

He uses Parallels to download the Windows ARM64 ISO. I've tried Windows Insider but oddly, there you can just download ARM64 VM images rather than ISOs.

I used CrystalFetch but I find it weird that currently (v2.0.0) the Edition dropdown just contains lots of identically labelled "Windows 11" entries (presumably it's over stripping some useful version information). I just assume that the default selected entry corresponds to the most up-to-date version.

See <https://github.com/TuringSoftware/CrystalFetch/issues/17>

Uninstalled OneDrive, Teams, ClipChamp, Office

Classic U-Center required Visual Studio 2013 Redistributable Package for x86. But not for U-Center 2.

### Copy & paste

It turns out copy and paste and a few other features like sharing don't work for VMWare Fusion Player 13.0.2.

VMWare don't seem to go out of their way to make this clear - but see:

* <https://communities.vmware.com/t5/VMware-Fusion-Discussions/Copy-Paste-file-sharing-between-Ventura-and-Windows-11-ARM-doesn/m-p/2940220/highlight/true#M180487>
* The PDF attached to the forum post ["The Unofficial Fusion 13 for Apple Silicon Companion Guide"](https://communities.vmware.com/t5/VMware-Fusion-Documents/The-Unofficial-Fusion-13-for-Apple-Silicon-Companion-Guide/ta-p/2939907) is a great help.

It seems these features are already supported in the [_VMware Fusion Public Tech Preview 2023_](https://customerconnect.vmware.com/downloads/get-download?downloadGroup=FUS-TP2023) so, it seems probably they will be included in the next major version of VMware Fusion Player.
It seems these features will be in the next major release and are already in the Tech Preview
