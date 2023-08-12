Rather than connected the TX to your computer, it's much quicker to just eject the SD card from the TX and insert it into your laptop.

The SD card was named "NO NAME" so, I renamed it "EdgeTX".

Note: the card is formatted as _FAT16_ - the one that came in my Boxer was a tiny 256MB card (anything less than 32GB is hard to find through retail channels these days). Remember that _FAT16_ is limited to 32GB so, if buying a replacement card, there's no point getting one bigger than 32GB.

Copy, the current contents to a backup folder and then delete everything on the SD card.

If you already have any custom scripts or models, you can copy them from the `SCRIPTS` and `MODELS` folders, that you backed up, at the end of the process.

* Go to [EdgeTX releases](https://github.com/EdgeTX/edgetx/releases), find the latest non pre-release version (v2.8.5 at the time of writing), go to the _Assets_ section and download `edgetx-firmware-vX.X.X.zip`.
* Go to [EdgeTX SD card releases](https://github.com/EdgeTX/edgetx-sdcard/releases), find the corresponding version of the SD card contents (v2.8.0 at the time of writing) and download the `bw128x64.zip` (the setup suitable for the 128x64 B&W display of the Boxer).
* Go to [EdgeTX SD card sounds releases](https://github.com/EdgeTX/edgetx-sdcard-sounds/releases) and find the corresponding sound pack version, i.e. v2.8.0 in my case. Expand the _Assets_ section and download the `edgetx-sdcard-sounds-en-X.X.X.zip` version (the default English sound pack, there are lots of others for different languages and for different English voices).

So, now you have three ZIP files, something like this:

* `edgetx-firmware-v2.8.5.zip`
* `bw128x64.zip`
* `edgetx-sdcard-sounds-en-2.8.0.zip`

```
$ mkdir edgetx-zips
$ cd edgetx-zips
$ mv ~/Downloads/edgetx-firmware-v2.8.5.zip .
$ mv ~/Downloads/edgetx-sdcard-sounds-en-2.8.0.zip .
$ mv ~/Downloads/bw128x64.zip .
$ mkdir sd-card
$ cd sd-card
$ unzip ../bw128x64.zip 
$ cd FIRMWARE
$ unzip -x ../../edgetx-firmware-v2.8.5.zip boxer-cbac106.bin
$ cd ..
$ unzip ../edgetx-sdcard-sounds-en-2.8.0.zip 
$ ls SOUNDS
README.txt  en
```
Notes:

* The sounds should have ended unpacked into a subfolder of `SOUNDS` called `en`.
* The `edgetx-firmware` firmware ZIP contains firmwares for many different TXes, I extracted the Boxer one (I'm not sure what the `cbac106` part of the name means).

I'd already setup two models so, at this point I copied them from my backup into the new setup:

```
$ cd edgetx-backup-20230812
$ cd MODELS
$ cp model04.yml model05.yml ../edgetx-zips/sd-card/MODELS
```

I ejected and reinserted the SD card in the Boxer and powered it up in bootloader mode.

I.e. push the T1 and T4 trim buttons (see diagram above) inwards towards each other with one hand and with your other hand press and release the power button (don't keep it held down like you do when normally starting the TX) and then release the T1 and T4 buttons.

It should show the _Bootloader_ screen and the _Write Firmware_ option should be selected so, just press the scroll wheel. Press it again when it shows you the name of the firmware file that its found, and press it down slightly longer to start the writing process. This takes a few seconds. Press the scroll key one more time to return to the _Bootloader_ screen and click _Exit_.

### Calibration

The TX restarts and (in my case) warned about bad radio data (presumably old data from the previous release) and then went straight to the calibration page for the sticks.

If the calibration step doesn't automatically show up at this point then press the _SYS_ button, use the _PAGE_ buttons to page to the _HARDWARE_ page and select the _[Calibration]_ option.

Do this as shown in the second image in OL's [gimbal calibration section](https://oscarliang.com/setup-radiomaster-boxer/#Gimbal-Calibration), i.e. move the sticks up and down, left and right rather than in a circular potion and twist the S1 and S2 pots (see diagram above) all the way clockwise and all the way counter clockwise. Do this slowly and deliberartely - I did each movement twice, you'll see tha tthe stick or pot position may jump the first time you do a particular movement but follows your movement properly the second time you do it.

### Mode

After updating the firmware, I found I got throttle warning in situations where the left stick was clearly at 0.

It turned out that updating the firmware had caused the _Mode_ setting to switch to mode 1 (where the right stick is used to control the throttle).

So, I had to press the _SYS_ button, use the _PAGE_ buttons to page to the _RADIO SETUP_ page and scroll all the way down to the _Mode_ option and update it from 1 to 2.

### Basic settings

Press the _SYS_ button, page to the _RADIO SETUP_ page and:

* Set _Date_ and _Time_.
* Set _Batt range_ to 6.4V – 8.2V (assuming you're using two 18650 Li-ion batteries to power the TX).
* Down lower, in the _Alarms_ section, set _Battery low_ to 6.4V.
* In the _Backlight_ section, set _Mode_ to _Keys_.
* Set the _Country Code_ to `US`, `EU` or `JP` as appropriate.
* Make sure the _Mode_ (the very last setting) is set to 2.

If you notice the _Owner ID_ option - this isn't for your name, it's an option specific to FrSky ACCESS ISRM modules and not relevant.

Important: now, page to the _HARDWARE_ page and scroll down to the _ADC filter_ and untick it - this is a setting that's appropriate for RC planes without an FC but is not appropriate for anything with an FC (as the FC handles the ADR filtering and does a better job of it than the TX can do).

### Models

I created two models:

* Press the _MDL_ button, select the _MODEL01_ entry (by clicking the scroll wheel and selecting _Select model_)) if it's not already selected (marked by an `*` to the left of its name).
* Page to the _SETUP_ page and:
  * Set _Model name_ to "Sim".
  * Scroll all the way down to the _Internel RF_ section and set its _Mode_ to _OFF_, Do the same for the _Mode_ in the _External RF_ section below. This makes sure the power hungry radio hardware isn't on when using this model with simulators like Liftoff.

Back on the main _MODELSEL_ page, click the "Sim" model (with the scroll wheel) and select _Copy model_ and then scroll to a free slot and click the scroll wheel again.

Now, select this model (with the scroll wheel, as above, so, it is now marked with the `*`), page to _SETUP_ and:

* Rename it to "QAV-R 2 DC" (the name of the quad frame or given it some more personalized name).
* Scroll down to _Internel RF_ section and set the _Mode_ to _CSRF 400k_.

When the model, that has the internal RF enabled, is selected, you'll hear the internal fan spinning up to keep it cool.

### Updating the TX's ELRS firmware

Sources: OL's [complete guide to ELRS flashing and set up](https://oscarliang.com/setup-expresslrs-2-4ghz/), OL's much shorter [update guide for the Radiomaster Zorro internal ELRS module](https://oscarliang.com/update-zorro-elrs-firmware/), JB's [getting started guide to ELRS for both TX and RX](https://www.youtube.com/watch?v=J3Hg2f7RL1A), JB's [speed-run version of his getting started guide](https://www.youtube.com/watch?v=MFFUsN9ZHSU), JB's [ELRS model match explanation](https://www.youtube.com/watch?v=3S6eUWCqvUY)

We updated the TX firmware, i.e. EdgeTX but the internal radio module that communicates with the quad has its own firmware called ExpressLRS (ELRS).

Go to [ExpressLRS Configurator releases](https://github.com/ExpressLRS/ExpressLRS-Configurator/releases) and download the latest version for the Mac (`ExpressLRS-Configurator-1.6.0.dmg` at the time of writing). Install the configuration, then find _ExpressLRS Configurator_ in your _Applications_ folder, right click is and select _Open_ (for the same reasons as outlined before for previous tools). For some reason it didn't start the first time I tried this but it worked fine on trying again.

* In the _Target_ section, select _RadioMaster 2.4GHz_ for _Device category_ and _RadioMaster Boxer Internal 2.4GHz TX_ as the _Device_.
* Select _EdgeTxPassthrough_ as the _Flashing Method_ (once you've set things up once, you can do later updates using the WiFi method).
* Under _Regulatory domains_ select _EU_CE_2400_ if you're in the EU otherwise select _ISM_2400_.
* Enter a _Custom binding phrase_, choose anything unique, you'll use the same phrase when setting up the quad RX and only a TX and RX that have the same binding phrase can talk to each other.

**Update:** I didn't want to set the TX up to connect to my home WiFi network but in the end I had to do this for the RX so (while not required for the TX), I went back and also:

* Ticked _HOME_WIFI_SSID_ and entered the name of my home WiFi network.
* Ticked _HOME_WIFI_PASSWORD_ and entered the relevant password.

Note: the binding phrase can be whatever length you want (as internally it's just stored as a hash).

Then turn on your TX, connect it to your laptop by USB and on the TX, select the _USB Serial (VCP)_ option.

Back in the _ExpressLRS Configurator_, press the _FLASH_ button and it should flash the update (with your passphrase and other settings) to your TX's RF module.

Once complete (this step is far quicker since the introduction of cloud builds in ELRS v3.3.0), the configurator encourages you to update your TX's ELRS lua script.

So, click the _DOWNLOAD LUA SCRIPT_ and save the `elrsV3.lua` file somewhere.

Disconnect your TX from your laptop and then reconnect it, this time selecting the _USB Storage (SD)_ mode. Open the drive corresponding to the TX's SD card (I called mine "EdgeTX" when setting things up above). Open the _SCRIPTS_ folder, then _TOOLS_ and copy the `elrsV3.lua` file, that you downloaded, into this folder. If there's was already an older ELRS script there make sure to remove it.

Eject the TX drive and disconnect the TX from your laptop. Press the TX's _SYS_ button and you should get to the _TOOLS_ page and see _ExpressLRS_ there now - this is the LUA script you just installed. Click it and (after a short loading step), scroll to the bottom and you should see the updated version shown there (`3.3.0 CE_LBT` in my case).

Note: to exit the _ExpressLRS_ LUA script, I had to long press the _RTN_ button - short pressing it just caused the script to reload.

Note: after the flashing step above my TX was unresponsive to button presses until I disconnected it from USB.

### Updating the RX's ELRS firmware

Just as we flashed the internal RF module on the TX by using EdgeTX passthru, we're going to connect to the FC and use BF passthru to flash the RX module.

Return to _ExpressLRS Configurator_. Assuming, you've just finished flashing the TX's RF module, press the _BACK_ button and return to the main _Configurator_ page.

* This time select _BETAFPV 2.4GHz_ as the _Device category_ and _BETAFPV SuperD 2.4GHz RX_ as the _Device_.
* Select _BetaflightPassthru_ as the _Flashing Method_.
* Leave the _Regulatory domains_ and _Custom binding phrase_ as before, i.e. use the same values as for your TX.
* Connect your FC to your laptop with USB (you don't also need battery power).
* In the _Actions_ section, it's supposed to automatically detect the serial port corresponding to your FC but I had to manually select the device clearly labelled as Betaflight in the dropdown list.
* Then press the _FLASH_ button.

At this point it complained `Wrong target selected your RX is 'HAPPYMODEL_EP_DUAL_2400_RX', trying to flash 'UNIFIED_ESP32_2400_RX'`.

And indeed, Happymodel has an extremely similar model - the [Happymodel EP1 Dual](https://www.happymodel.cn/index.php/2022/09/01/happymodel-ep1-dual-receiver-true-diversity-2-4ghz-expresslrs-rx/).

I don't know what the relationship between BetaFPV and Happymodel is but it seems to be a common thing for BetaFPV models to initially come with firmware labelled as being for Happymodel.

So, I went back to the main _Configurator_ page and ticked _Force Flash_ and pressed _FLASH_ again.

Again things failed, with output like this:

```
No CLI available. Already in passthrough mode?, If this fails reboot FC and try again!
...
.
.
.
.
```

And after output dots for a while, it gave up.

I tried various things, including trying to update it as if it were the Happymodel model that it's current firmware claimed it was and trying to update it via WiFi by connecting to it in access point mode (rather than connecting it to my home WiFi network which is what I eventually did).

### Updating via WiFi

In the end, I went down the route that I'd wanted to avoid initially.

Plug out your FC and reconnect it, the LED on the RX brieftly flashes different colors, then slowly flashes orange for about 60 seconds, then flashing green.

When it's flashing orange, it's waiting for a TX to connect, when it starts flashing green it's switched into WiFi upgrade mode.

Important: remember this when you're out in the field with your quad - if you power up the quad and then wait too long before also turning on your TX then it won't be able to connect to the RX because it's gong into this WiFi mode - just plug the quad out and in to force the RX to restart.

When the RX is in WiFi upgrade mode, look at the WiFi networks that your laptop can see, it should now be able to see _ExpressLRS RX_ - which is the RX. Change your laptop network to this one using the password `expresslrs` and it should ask you to join the network:

![Join elrs_rx network](images/join-elrs_rx-network.png),

Switch to the _WIFI_ tab, click in the _WiFi SSID_ field and select your home network, then the password for your home network in the _WiFi password_ field and click _Confirm_.

It'll briefly show a dialog telling you that the RX will now connect to your home network and that you can connect to it then using the link <http://elrs_rx.local/>

Then it disconnects and you should reconnect your laptop to your home network (if it didn't just do that automatically).

Return to _ExpressLRS Configurator_ and switch the _Flashing Method_ to _WIFI_ and scroll down to the bottom of the _Configurator_ page and if all's gone well you should see something like this:

![ELRS devices](images/elrs_devices.png)

Click _SELECT_ for your device and then click _FLASH_.

The process took around 12 seconds with output like this:

```
Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
 15 1019k    0     0   15  162k      0   385k  0:00:02 --:--:--  0:00:02  387k
 24 1019k    0     0   24  246k      0   183k  0:00:05  0:00:01  0:00:04  183k
 33 1019k    0     0   33  337k      0   139k  0:00:07  0:00:02  0:00:05  139k'
...
 76 1019k    0     0   76  781k      0   106k  0:00:09  0:00:07  0:00:02 91931
 85 1019k    0     0   85  868k      0   103k  0:00:09  0:00:08  0:00:01 90'
100 1019k    0     0  100 1019k      0  93861  0:00:11  0:00:11 --:--:-- 73773
100 1019k    0     0  100 1019k      0  86093  0:00:12  0:00:12 --:--:-- 58210
100 1019k  100   114  100 1019k      9  85141  0:00:12  0:00:12 --:--:-- 49846

UPLOADING TO: http://192.168.0.235/update

UPLOAD SUCCESS
 [32mUpdate complete. Please wait for the LED to resume blinking before disconnecting power. [0m
```

![RX successfully updated](images/elrs_rx-updated.png)

The warning was a little confusing as the LED started flashing immediately, but a few seconds later the green _Success!_ message appeared which looked to be the end of the process.

Conclusion: I found this whole proces underwhelming. I had to redo various steps several times before they worked, the RX forgot the home WiFi network at least once (with it returning to access point mode) and it would sometimes switch out of WiFi upgrading mode (and return to flashing orange). This combined with having to wait a minute after restarting the RX made the process a bit exasperating.

### Enabling WiFi via the TX

Initially, I set up the TX so that it didn't connect to my home WiFi network. But after setting up the RX to connect like this, I went back (and as noted above) reflashed the TX with the details for my home WiFi network.

Once done, I could go to the _ExpressLRS_ LUA script on the TX, go down to _WiFi Connectivity_, click it and then click _Enable WiFi_, this pops up an odd little dialog showing `WiFi Running... [X]` where the `X` bit flickered madly. But once enabled the TX shows up in _ExpressLRS Configurator_:

![elrs_tx device](images/elrs_tx-devices.png)

The only way to exit the WiFi dialog on the TX seemed to be press _RTN_ and exit WiFi mode, it didn't seem to be possible to leave it running in the background.

Below _Enable WiFi_, is an _Enable Rx WiFi_ option - this can be used if the TX is connected to an RX to tell the RX to go into WiFi mode.

As with the RX, I didn't find the TX WiFi entirely reliable - sometimes it disappeared only to reconnect again a few seconds later.

Future updating
---------------

I hope future updating will go a bit more smoothly - I don't plan to try EdgeTX or BF passthru again. Instead, I'll push the TX into WiFi mode via the _ExpressLRS_ LUA script and either also use the LUA script to push the RX into WiFi mode or simply wait it to enter WiFi upgrading mode automatically after being left 60 seconds after powering up (without being connected to by the TX).

When connected to your WiFi network, you should be able to access the RX and the TX via your browser with these links:

* RX: <http://elrs_rx.local/>
* TX: <http://elrs_tx.local/>

Connecting TX and RX
--------------------

The whole point of this, in particular setting matching binding phrases on the TX and RX was to get the two to talk to each other.

With the TX already powered up, power up the quad (USB power is enough).

The LED on the RX should briefly alternate through its "rainbow" power on colors and then go a solid red or actually any color on the spectrum - the important thing is that its not blinking. The color indicates the current packet rate value:

![packet rate](images/packet-rate.png)

Note: this diagram is one of the very few useful bits of information in the BetaFPV manual for the SuperD diversity RX.

If you look at the TX LCD, you'll now see a set of bars on the main screen to the right of the little block showing the current voltage of the TX battery, these show that it's connected to the TX. The bars are just a static icon - they don't go up or down to show signal strength.

We'll actually change the rate later 

If you unplug the quad, the TX will announce "telemetry lost" and if you plug the quad back in it'll eventually announce "telemetry recovered". In the field "telemetry lost" would be a very bad thing and gnerally mean the quad has flown out of radio distance and you've lost control of it.

In the next section, we'll get to the _Receiver_ section in _Betaflight Configurator_ and see somewhat more impressive evidence that the TX can now talk to the RX.

BF RX setup
-----------

When wiring the RX up to the FC, we made sure to wire it up to UART6 which is the BF default for the RX. If you go to the _Ports_ tab, you'll see _Serial RX_ is enabled for this UART:

![RX UART](images/rx-uat.png)

If for some reason, the RX had to be connected to some other UART, then you'd have to disable _Serial RX_ for UART6 and enable it for the actual one being used.

#######
HERE. I've finished <https://oscarliang.com/setup-radiomaster-boxer/> and OL's Zorro guide.
So set packet rate etc. as per JB's "you can" video.

So, go to _Receiver_ tab - this is where things get cool.

I think, I should set packet rate and do the _Receiver_ tab setup as per JB's "you can" video. And then come back to <https://oscarliang.com/setup-expresslrs-2-4ghz/#Betaflight-Setup-for-ExpressLRS-Receiver> and make sure failsafe etc. are done if they weren't part of JB's video.

Also look if there's any additional info in JB's three other guides linked to above.
#######

BF bluetooth
------------

If you look at the ports shown above, you'll see UART0 is called UART VCP and is actually used for the connection between BF and your laptop. UART1 is used for the VTX - which we've already covered. UART6 is for the RX.

So, what about UART2? It's shown with _Configuration/MSP_ enabled. It turns out that if your FC has a Bluetooth module then it uses this UART.

If you enable Bluetooth on your phone and download the [SpeedyBee app](https://www.speedybee.com/speedy-bee-app/), you'll be able to use it to connect to your FC and do many of the same things that you can with _Betaflight Configurator_. This can be useful if you're out in the field without a laptop and a USB connection.

As with all things Bluetooth, it can be a bit flaky - sometimes I have to restart the quad to be able to reconnect again after disconnecting.


