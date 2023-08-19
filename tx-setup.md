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

Note: the `*` to the left of a model name indicates that it's the currently selected model (TODO: maybe add a picture).

I created two models:

* Press the _MDL_ button, scroll to a free slot, click the scroll wheel and and select _Create model_.
* Page to the _SETUP_ page and:
  * Set _Model name_ to "Sim".
  * Scroll all the way down to the _Internel RF_ section and set its _Mode_ to _OFF_ (if it's not already off). Do the same for the _Mode_ in the _External RF_ section below. This makes sure the power hungry radio hardware isn't on when using this model with simulators like Liftoff.

Back on the main _MODELSEL_ page, click on the entry for the "Sim" model (with the scroll wheel) and select _Copy model_ and then scroll to a free slot and click the scroll wheel again.

Now, select this model (by clicking it with the scroll wheel and selecting _Select model_ so, it is now marked with the `*`), page to _SETUP_ and:

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

**Update:** it may be that holding down the tiny boot button on the RX, as it's powered up, might have resolved things - see these [Betaflight passthru notes](https://www.expresslrs.org/software/updating/betaflight-passthrough/). However, in the end, despite initial reservations, I was satisfied with the WiFi approach described in the next section.

**Update 2:** the most bomb proof way to update an RX is to do the updating _before_ soldering it up to the FC using something like the BetaFPV ExpressLRS [recovery dongle](https://betafpv.com/products/expresslrs-recovery-dongle). The electronics of this dongle are completely generic - it's just equivalent to a 5V FTDI breakout, like this [one](https://www.sparkfun.com/products/9716) from Sparkfun. But the BetaFPV dongle is very cheap and, even better, comes with a pogo-pin adapter (needed for connecting to something like the RX without having to solder down connections). I have a pogo pin adapter (bought [here](https://www.aliexpress.com/item/4001197263516.html) on AliExpress) and an FTDI breakout - while a full FTDI breakout is a bit more capable (it also breaks out RTS and CTS), the combined cost is far more than the BetaFPV dongle. The boot button is definitely used when using this approach, see RC Video Review's [video](https://www.youtube.com/watch?v=AH6e-ItZCo0) on how to do things using the BetaFPV dongle.

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

**Update:** it's not an icon - if you move far enough away, you'll eventually see the biggest bar dissappear.

We'll actually change the rate later 

If you unplug the quad, the TX will announce "telemetry lost" and if you plug the quad back in it'll eventually announce "telemetry recovered". In the field "telemetry lost" would be a very bad thing and gnerally mean the quad has flown out of radio distance and you've lost control of it.

Note: if you move the TX too close to the RX, the TX may also report "telemetry lost" - this is because the signal is actually too strong and "flooding" the RX.

In the next section, we'll get to the _Receiver_ tab in _Betaflight Configurator_ and see somewhat more impressive evidence that the TX can now talk to the RX.

BF RX setup
-----------

When wiring the RX up to the FC, we made sure to wire it up to UART6 which is the BF default for the RX. If you go to the _Ports_ tab, you'll see _Serial RX_ is enabled for this UART:

![RX UART](images/rx-uat.png)

If for some reason, the RX had to be connected to some other UART, then you'd have to disable _Serial RX_ for UART6 and enable it for the actual one being used.

### BF Receiver tab

Now, we're going to really see that the TX is talking to the RX and has the ability to control it.

Power up your TX, _then_ connect your quad to your laptop via USB and check that the LED on the RX has stopped blinking at that TX shows the little connected icon (the bars mentioned above).

Then connect to the FC with _Betaflight Configurator_, switch to the _Receiver_ tab and move the sticks on your TX about - you should see the movement reflected in the bars to _Roll_, _Pitch_, _Yaw_ and _Throttle_ and you should see the quad in the _Preview_ panel moving as you'd expect in response to the stick movements.

Now, move each stick all the way up and down and left and right. You might think, after the calibration process done earlier, that the sticks would move from the 1000 to 2000 values that BF wants. But they don't - most of mine moved from 989 to 2012.

So, on the TX, press the _MDL_ button, make sure the correct model is selected (i.e. has the `*` to the left of its name). Then page to the _OUTPUTS_ page and:

* Click _CH1_, select _Edit_, scroll to the _Min_ option and click again.
* Move the right stick to the bottom-left corner.
* While watching the _Roll_ bar in _BF Configurator_, adjust (i.e. scroll) the _Min_ value until the _Roll_ bar reaches 1000.
* Click to finish the adjustment of _Min_.

That's it, now, do push the right stick to upper-right corner and adjust the _Max_ value in the same way until the _Roll_ bar reaches 2000.

On my TX, the final _Min_ and _Max_ values were -97.8 and 97.7 respectively.

If you find the value shown in _BF Configurator_ jumping around when you push the stick into a corner, try releasing the stick and pushing it there again or instead of using a corner push it to one of the  center markers around the edge of the gimbal (or anywhere where things are stable, just as long as the stick is at maximum on the particular axis that's relevant).

Note: JB favors pushing towards the center markers while OL favors the corners.

Now, do the same for _CH2_, _CH3_ and _CH4_ - you don't have to know which channels maps to which stick, just select a channel, e.g. _CH2_, look at the &mu;s value in the upper-right corner and move each stick in turn when you see the &mu;s value change you know you've got the relevant stick. Push the stick to the lower-left and do the process above, i.e. adjust _Min_ and look to see which bar in _BF Configurator_ changes and adjust things until that bar reaches 1000. And so on.

**Update:** I don't think you even have to look at _BF Configurator_, you just have to look at the &mu;s value and adjust the _Min_ and _Max_ values so that this value shows 1000&mu;s for _Min_ and 2000&mu;s for _Max_ when the relevant stick is pushed to its minimum and maximum values. Given this, it seems it _should_ be possible for EdgeTX to do all this for you as part of the calibration process (and be specific to the TX rather than individual models).

Note: when adjusting the values on the TX, I found that typically e.g. 97.7 to 97.9 would map to 2000 so, I'd choose the value if the middle of this range, i.e. 97.8 for this example.

My final values were -97.8 and 97.7 for all channels.

#### Thresholds

Now, the endpoints have been corrected, the thresholds can be adjusted from their conservative values (that assume you may not have gone through the process above).

In _BF Configurator_, change:

* The _'Stick Low' Threshold_ from 1050 down to 1010.
* The _'Stick High' Threshold_ from 1900 up to 1990.

And, as always, remeber to hit _Save_.

### ELRS packet rate

See OL's section on [packet rate](https://oscarliang.com/setup-expresslrs-2-4ghz/#Packet-Rate) if you want more details.

On the TX, press the _SYS_, click the _ExpressLRS_ LUA script - you should see a little `C` if your TX is connected to your RX.

Now, click the _Packet Rate_ option and adjust the rate to 150Hz.

The TX should announce a few warnings before announcing "telemetry recovered" (meaning "all's good") and the RX should become a purple color (see the color to frequency diagram above).

Note: JB suggests going all the way down to 50Hz but when I tried that things seemed to work, _but_ the radio would never announce "telemetry recovered" and the `C` would never show up again. 50Hz was the only problematic frequency - no other frequency had this issue. So, I switched to the next lowest _normal_ rate, i.e. 150Hz - 100Hz and 333Hz are special [_full resolution switch configuration modes_](https://www.expresslrs.org/software/switch-config/#full-resolution-switch-configuration-modes) so ignore them (for more see the ExpressLRS [documentation](https://www.expresslrs.org/software/switch-config/#full-resolution-switch-configuration-modes)). I don't know if the 50Hz issue is specific to my RX or to my version of ELRS or something else.

Note: by default my _Packet Rate_ was set to _F1000_ - this has the fastest packet rate but the shortest range - we want the opposite (long range with no noticeable change in "feel" for anyone other than expert pilots).

Once the _Packet Rate_ is set, go down to the _Switch Mode_ option and make sure it's set to _Wide_ (for more on wide and hybrid, see the [switch mode chapter](https://www.youtube.com/watch?v=J3Hg2f7RL1A&t=2058s) of JB's "ExpressLRS definitive getting started guide").

Now, to to the _TX Power_ section, click it and adjust the _Max Power_ value. Mine showed _ERR_ initially and I suspect this was because the radio was configured with a higher power setting than the 100mW allowed in the EU.

I adjusted my _Max Power_ to the 100mW maximum allowed in the EU and JB suggests 250mW for the US (I believe 250mW is anyway the max for the internal ELRS module).

TODO: move this section somewhere more sensible above - it's in the middle of unrelated _BF Configurator_ stuff.

```
########################################################################
```

I've finished <https://oscarliang.com/setup-radiomaster-boxer/> and OL's Zorro guide.

But come back to <https://oscarliang.com/setup-expresslrs-2-4ghz/#Betaflight-Setup-for-ExpressLRS-Receiver> and make sure FAILSAFE etc. are done if they weren't part of JB's video.

Also look if there's any additional info in JB's three other guides linked to above in the ELRS section.

```
########################################################################
```

Presets
-------

[`30-pre-elrs-presets-etc.txt`](30-pre-elrs-presets-etc.txt) contains my configuration _before_ I started applying JB's suggested presets (32m 30s mark in video 3 of his 2022 build series).

#### ELRS Presets

In _Betaflight Configurator_, go to the _Presets_ tab, enter "ELRS" in the search field and select the preset for the frequency you chose (for me that was 150Hz, you might have chosen 50Hz if it worked for you).

Note: in the preset dialog, it includes the warning "make ABSOLUTELY SURE that the OpenTx or EdgeTx Hardware ADC Filter is un-checked!" We already took care of that when setting up the TX.

Then under options, I just chose _Serial, separated Rx_ and the _connection method_ and _Single Cell value_ under _Voltage readings_. I did not choose any of the _Fine-tuning_ options.

Then I clicked _Pick_ and then _Save and Reboot_.

This resulted in the following changes:

```
set feedforward_smooth_factor = 30
set report_cell_voltage = ON
```

At other frequencies, more things are changed, e.g. at 250MHz the same options result in:

```
set feedforward_smooth_factor = 45
set feedforward_averaging = 2_POINT
set feedforward_jitter_factor = 6
set report_cell_voltage = ON
```

Selecting _serial_ as the connection method resulted in no change (as serial was already the default).

By default `report_cell_voltage` is off but as JB points out, you want it on. See OL's [explanation](https://oscarliang.com/averaged-cell-voltage-crossfire/) for more details. In short, the telemetry value for the battery voltage by default gives you the total voltage, but turning this setting on gives you an average cell voltage. This means that as you get to the end of your flight, you'll always see the voltage nearing 3.5V, and know it's time to come into land, rather than seeing a value that depends on the number of cells in the battery you're currently using (around 14V when flying with a 4S battery or 21V with a 6S).

TODO: I suspect if one sets `report_cell_voltage` one gets _both_ the total and the average - see TODO in telemetry section below.

For details on what every single option affects, including the fine tuning ones for racing, freestyle etc., see [`elrs-preset-options.md`](elrs-preset-options.md).

It was only at this point that I noticed that _Pick_ just outlines a given preset in green - it's pressing _Save and Reboot_ that causes it to be marked with a star (and appear from then ahead of all the non-stared presets).

Rates
-----

Sources: OL's ["Demystifying FPV Drone Rates"](https://oscarliang.com/rates/) and JB's ["Find YOUR perfect rates! With science!"](https://www.youtube.com/watch?v=Ql62iRkLX3s) video.

If you go to the _PID Tuning_ tab in _BF Configurator_, switch to _Rateprofile Settings_, you'll see there's a dropdown called _Rate Types_.

Basically, this allows you to select between different ways of defining the curves you see in the _Rates Preview_ panel below.

If we ignore the throttle, you'll find, when you're flying, that the you'll spend most of your time making tiny movements around the center point of the sticks - you'll almost never push them to their extremes. In general (as a beginner), you'd like far more control towards the center of the sticks - and you can configure this through the curves. JB does a good job of explaining this in an intuitive manner in the "What are rates?" chapter of his "find your perfect rates" video (see link above).

Over time people have come up with what they feel are  more intuitive ways to specify the curves in terms of a set of numbers - these different approaches are what you find in the _Rate Types_ menu.

So, people have gotten used to different systems over time and may want to stick with them but basically _Betaflight_ rates was the classic system of expressing rates and then in BF 4.2 they introduced a more intuitive system called _Actual_ rates. So, it comes down to a choice between one or the other. As OL puts it:

> Betaflight Rates are slightly more complex [than Actual rates] as the three terms are interdependent, making them less intuitive to use. However, as the oldest rate system in Betaflight, many experienced pilots continue to rely on them.

JB has more on why _Betaflight_ are hard to work with and why _Actual_ rates are more intuitive in his ["what are ACTUAL RATES and how to convert them"](https://www.youtube.com/watch?v=m3A9xgRmcws).

So, if you're starting out, then _Actual_ rates seem the obvious choice and it's the system JB uses in all his videos since _Actual_ became available.

Nearly, everything I've done has fairly closely followed along with his [2022 drone build for beginners](https://www.youtube.com/playlist?list=PLwoDb7WF6c8neIAQBkchfiXf-C8KbzG5M) series.

But here, I'm going to do something different - he uses presets to quickly chose a set of canned rates - this may be quick but it's opaque and makes one think the process may be more complicated than it is.

So, instead, of a preset, find the _Rates Types_ dropdown, as described above and select _Actual_.

These are the rates you get if you try the presets that JB suggests:

_Headsup racing rates_
![headsup racing rates](images/betaflight/010-headsup-racing-rates-actual.png)

_JB rates_
![JB rates](images/betaflight/011-jb-rates-actual.png)

As JB explains, as a beginner you're probably going to want something closer to the more precise racing rates than to the JB's own rates that allow for extreme freestyle moves.

After looking at these and watching his "pefect rates" video and looking into pages and videos on beginner rates, I went for this super conservative setup:

![My rates](images/betaflight/012-my-rates.png)

All you have to do is select _Actual_ as the _Rates Types_ and then enter the numbers shown for _ROLL_, _PITCH_ and _YAW_ - try adjusting them and see how they affects the curves.

And _Save_ - done.

These are the setting changes that result:

```
set pitch_expo = 76
set pitch_rc_rate = 10
set pitch_srate = 40
set roll_expo = 76
set roll_rc_rate = 10
set roll_srate = 40
set yaw_expo = 64
set yaw_rc_rate = 15
set yaw_srate = 35
```

As you can see, it's three numbers each for pitch, roll and yaw. The setting `rates_type` isn't changed as its default is `ACTUAL`.

Acro trainer mode
-----------------

OL explains the various BF flight modes in the [flight modes](https://oscarliang.com/betaflight-modes/#Flight-Modes) section of his guide to BF modes.

The ones we're interested in are:

* Acro mode - this is the no hand-holding mode that experienced pilots use.
* Angle mode - this is a much easier to fly self-levelling mode with various limits to ensure things don't get out of control and 
* Acro trainer mode - this is a form of acro mode with various limits that prevent flipping over and behaviors that are likely to end in a crash while learning.

Lot's of videos discourage you from using _angle_ mode as it's felt to teach you bad habits that you'll have to unlearn once you switch to acro but it's the safest thing for your first flights when you're still working out if everything is setup correctly.

The number of features that BF supported grew so large that including them all outgrew the memory available on many FCs. So, with BF 4.4 only a certain subset of features is included by default.

Acro trainer isn't one of these features so, if you want it you have to do the same steps as when updating the firmware. Except this time go to the _Build Configuraton_ section of the _Firmware Flasher_, click in the _Other Options_ section and add _Acro Trainer_ from the dropdown list of choices - and then flash the firmware as before

AUX switches
------------

Source: the ["NON-DJI ONLY: Set up Aux switches and Modes"](https://www.youtube.com/watch?v=5ke6LabvtGM&list=PLwoDb7WF6c8neIAQBkchfiXf-C8KbzG5M&index=3&t=2079s) chapter of JB's of the third video ("Configuration and Setup") in his "2022 Freestyle FPV Drone Build" series.

Turn on your TX, press _MDL_ and page to the _MIXES_ screen. In JB's video the channels after 1 to 4 (which are assigned to the sticks) are free. Oddly, on my setup, channels 5 to 10 were already assigned to switches `SA` to `SF`.

The EdgeTX interface is a bit confusing here, clicking an entry allows you to "drag" the switch associated with that entry either to a free slot or to an existing slot (in which case multiple switches become associated with a single channel and the value of the most recently flipped switch becomes the channels value).

Anyway, if you accidentally click an entry, just press _RTN_ to cancel dragging.

Instead, long click an entry to being up a set of options that includes _Edit_ and _Delete_ - the easiest thing is just to delete the entries 5 to 10 if, as I found, they've already been assigned default values.

The TX can transmit value on 12 channels (the number of available channels is a function of various factors but for us it's 12). The first four are already set up to communicate the stick values. And the remaining eight are free for us to associate with whatever we want. Here we're going to associate them with switch positions and then _BF Configurator_ we're going to associate those positions with various functions (like arming the quad).

So, the channels you see on the _MIXES_ screen map to the values you see in the _Receiver_ tab of _BF Configurator_ like so:

| EdgeTX | BF       |
|--------|----------|
| CH1    | Roll     |
| CH2    | Pitch    |
| CH3    | Yaw      |
| CH4    | Throttle |
| CH5    | AUX 1    |
| CH6    | AUX 2    |
| CH7    | AUX 3    |
| CH8    | AUX 4    |
| CH9    | AUX 5    |
| CH10   | AUX 6    |
| CH11   | AUX 7    |
| CH12   | AUX 8    |

Note: that roll, pitch etc. are mapped to those particular channels is just convention and it happens that the TX and _BF Configurator_ agree on the convention but some TX manufacturers assume a different convention and for these case you'd have to change the _Channel Map_ setting in _BF Configurator_ to match.

So, we're going to associate switches with with AUX 1 to 3, i.e. `CH5` to `CH8` in EdgeTX.

So, on the _MIXES_ page (assuming you've deleted any existing assignments for `CH5` and up) and:

* Go to `CH5`, click it (if the slot is free, you don't have to long click), go to _Source_, click it and press switch _SE_, click the scroll wheel again (to stop the _Source_ value blinking) and press _RTN_ twice to get back to the main _MIXES_ page.
* Then do the same for `CH6`, `CH7` and `CH8` but use switches _SF_, _SC_ and _SD_ respectively.

Note that _SC_ is a three position switch and _SD_ is a two position switch.

We've completed the setup on the TX side (just press _RTN_ a few times to get back to the main EdgeTX screen).

Now, open _BF Configurator_, go to the _Receiver_ tab and try using switches _SE_, _SF_, _SC_ and _SD_ and see that the values of the expected AUX channels also change between 1000 and 2000 (or in the case of _SC_ the middle position maps to ~1500).

Then switch to the _Modes_ tab and go to _ARM_, click its _Add Range_ button - see the little yellow marker below the bar, initially its at 1500, click the _SE_ switch in and out and see the marker move about. Now, with _SE_ pressed in, so the marker is at 2000, drag the yellow bar so the center of the bar is above the marker (or, as 2000 is too near the upper end of the scale, as near as possible).

Note: you can adjust the size of the yellow bars - reducing their size would make sense if you wanted to associate lots of positions on a single channel with different modes but isn't needed here.

Now, go to _BEEPER_ and do the same, this time pressing _SF_ (you don't have to keep it pressed while dragging the yellow bar - you just need to know where the marker will be when it's pressed).

Now, go to _FLIP OVER AFTER CRASH_ and set it to be enabled when _SD_ is down.

Now, go to _ANGLE_ and flip the _SC_ switch to its down position and place the yellow bar. Finally, go to _ACRO TRAINER_ (which will only be listed if you reflashed the firmware, as discussed above, with _Acro Trainer_ added as an option) and flip _SC_ not to its middle position and place the yellow bar.

Press _Save_ after setting up the modes and then enable the _Hide unused modes_ toggle.

Now, try pressing _SE_ and the other switches, you should see the _ARM_ go red when you press _SE_ (but with "(DISABLED)" shown as you can only really arm once various checks are passed, including not being connected to USB), _ANGLE_ and _ACRO TRAINER_ should go yellow as you flip _SC_ and _FLIP OVER AFTER CRASH_ and _BUZZER_ when you press _SD_ and _SF_ respectively.

as you might have noticed, _SC_ is associated with two flight modes (and when no flight mode is explicitly selected BF defaults to _ACRO_) so:

* _ACRO_ flight mode is used when _SC_ is up (this position isn't mapped to any mode so, BF uses the default).
* _ACRO TRAINER_ flight mode is used when it's in its middle position,
* _ANGLE_ flight mode is used when it's down.

Make sure to flip _SC_ all the way down to _ANGLE_ mode for your first flights.

TODO: get some screenshots of what you see in the goggles when you arm/disarm, change flight modes or switch on the buzzer.

### Beeper

If you power the quad from your charger (or a battery), you can also test the beeper.

Press down the _SF_ button and it should make a very loud beeping sound that will help you find it when it crashes.

Note: up until this point I hadn't removed the "REMOVE SEAL AFTER WASHING" sticker on the beeper (washing is done as part of the production process after soldering in order to remove flux). Removing it makes a surprising difference to the loudness of the beep.

### AUX 1

Normally, you're free to assign AUX channels to whatever function you want. However, you must assign ARM to AUX 1 (and the armed state must be set to ~2000) - as we did above.

This is because the RX wants to know the armed state and assumes it's associated with AUX 1. See the [mode section](https://www.expresslrs.org/quick-start/pre-1stflight/#modes) of the ELRS first-flight checklist for an explanation of why using another channels is a bad idea and for more details, including further assumptions like unarmed being ~1000 and armed being ~2000. This ELRS documentaion notes that there are only between 1 and 4 bits available per AUX channel - that's not case for us as we're using _wide_ switch mode (this was covered when doing the main ELRS setup).

**Question:** why does the RX look at this channel, surely the FC can communicate the armed state to the RX using CRSF?

### AUX 11 and 12

In our setup, there are only eight useable AUX channels, but in the _Receiver_ tab, you'll see that _AUX 11_ and _AUX 12_ may be around 1940 and 2010 respectively (these are the values they have when my Radiomaster Boxer TX is about 1m away from the BetaFPV SuperD ELRS RX) and the values may be jiggling around.

Generally, it's the TX that then generates the value you see for a given channel. However, for _AUX 11_ or _AUX 12_, it's the RX generating theses values - it's using them to indicate link quality (LQ) and received signal strength (RSSI) respectively.

Using AUX channels is essentially a backup way to make these values available and only of interest to users of the DJI system (who don't want to [root](https://oscarliang.com/fpv-wtf-root-hack-dji/) them so, they can take advantage of full BF OSD support). The RX talks to the FC, using a protocl called CRSF, and communicates LQ and RSSI (and lots of other information) to the FC this way. For everyone, except users of unrooted DJI goggles, it's this data, rather than the AUX channel data, that's displayed as the _Link Quality_ and _RSSI dBm_ values in the OSD.

Note: there are actually two RSSI values - _RSSI dBm_ and the confusingly named _RSSI Value_ - the second is a historical oddity and should be ignored whenever you have a choice between the two (e.g. when setting up the values displayed in your OSD).

For everyone, except users of DJI goggles, go to the _Receiver_ tab in _BF Configurator_ and make sure:

* The _RSSI_ADC_ toggle is set to disabled.
* _Disabled_ is selected in the _RSSI Channel_ dropdown.

For even more information on LQ and RSSI and how they related to each other, see the ELRS page on [signal health](https://www.expresslrs.org/info/signal-health/). However, the "RSSI Value OSD field" section is a bit confusing - it seems to suggest that setting _RSSI Channel_ to _Disabled_ in _BF Configurator_ is not recommnded - this is _just for DJI users_ who have to use one of these channels if they want LQ or RSSI information in their googles.

DJI setup
----------

We've largely been following JB's "2022 Freestyle FPV Drone Build" but at this point, he also covers setting up things for DJI and even though DJI is a digital system and we're also using a digital system (Walksnail) there's no additional useful information in the DJI specific chapters.

OSD part 2
----------

After the DJI sections, JB gets on to setting up the OSD for analog. Oddly, this section is more relevant to Walksnail that the corresponding DJI one. This is because the DJI system is more locked down and can't take advantage of the full _BF_ OSD support whereas Walksnail is more open and can take advantage of all the features that _BF_ already supported for analog systems.

However, we've already set up the OSD, driven by OL's guides (TODO: <link-here>). So, nearly all of JB's analog OSD chapter can be ignored BUT at 55m 28s he discusses the meaning and limits for e.g. battery cell voltage and link quality and corecting the ELRS RSSI warning.

### Battery voltage

We already setup single cell battery voltage above and now JB notes that once you see it hitting 3.5V it's time to come home.

Note: 3.5V is also the value OL recommends in the ["when to land"](https://oscarliang.com/lipo-battery-guide/#When-to-Land) section of LiPo battery guide. He also has a whole ["Monitor Battery Voltage & Decide When to Land"](https://oscarliang.com/monitor-measure-battery-voltage-alarm-drone/) page where he discusses monitoring the voltage _and current_ via FC, OSD and TX and the related alarms.

Note: OL states that the 3.5V rule applies for all cell counts except 1S. 1S suffer extreme voltage sag and so, it's normal to keep flying them until 3.2V (they'll recover to 3.5V after resting for 10 to 15 mins).

### RSSI OSD alarm

When setting up the OSD, JB sets `osd_rssi_dbm_alarm` to -110.

You can see what this 110 value means on OL's ["LQ and RSSI explained for ELRS" page](https://oscarliang.com/lq-rssi/). The 110 value is at the limit of what OL considers safe for 50Hz.

OL suggests a universal value of 95 which is conservative and safe for all ELRS packet rates.

Basically, you just take the dBm value shown for your packet rate in OL's [lowest RSSI section](https://oscarliang.com/lq-rssi/#The-Lowest-RSSI), and add 10 as a safety margin. So, e.g. for 150Hz the value is -112dBm, this becomes (-112 + 10), i.e. -102.

I went to the _CLI_ tab and set the value to -100 for my 150Hz setup:

```
set osd_rssi_dbm_alarm = -100
save
```

Setup (almost) complete
-----------------------

JB then covers VTX tables for an analog VTX. This isn't relevant for Walksnail or other HD system (thankfully the digital systems are much smarter/convenient/safer when it comes to VTX channel selection).

So, at this stage, the setup of _FC_ and the other components is complete.

The last chapter (in JB's "Configuration and Setup" video) covers some minor points - setting how flat on the ground the quad has to be before the FC will let you arm and using the motors as beepers.

As we've got a real beeper, we don't need to configure the motors to act as beepers (which one could do using the _Dshot Beacon Configuration_ panel on the _Configuration_ tab).

But, if you want, go to the _Configuration_ tab and, in the _Arming_ panel, change the _Maximum ARM Angle_ from 25 to 180 so, you can arm even when your quad is at a very odd angle. Then _Save and Reboot_.

That's it - now it's time to finish assembly and finally fly the quad.

ELRS checklist
--------------

Above, we covered `osd_rssi_dbm_alarm`, setting _RSSI_ADC_ and _RSSI Channel_ to disabled and setting AUX 1 as your arm channel.

If you've got all these things done then you've completed everything relevant in the ELRS ["Before First Flight"](https://www.expresslrs.org/quick-start/pre-1stflight) checklist.

Telemetry
---------

Press _MDS_, page backward to _TELEMETRY_ (it's the second last page so, paging backward is quicker). Go down to the _Sensors_ section and click _Discover new_.

It'll discover a whole list of telemetry data items that are transmitted back to the TX by the RX. Click _stop_ to tell it so stop trying to discover further items.

**TODO:** none of them looked like the battery voltage (see `report_cell_voltage` above) and if I press the _TELEM_ button I just see the TX battery voltate and the time. How do I get the quad battery voltage and RSSI as shown here <https://oscarliang.com/averaged-cell-voltage-crossfire/>  it looks like I should get both the total and the individual.

Note: the telemetry data transmitted via the RX to your TX isn't the only telemetry data channel - similar data is transmitted via the VTX to your goggles. In an FPV setup, you can't see the TX while you're flying so it's telemetry data is, relatively speaking, less important (but you can still hear audio warnings from the TX).

Somehow, the `feature TELEMETRY` got disabled (perhaps it was automatically disabled for one of the passthru operations and never got correctly reset). Re-enable it in the CLI tab with:

```
feature TELEMETRY
```

Or go to the _Receiver_ tab in _BF Configurator_ and enable it there.

Now, if you retry the discover option (see above), it will discover many more sensors - RxBAT is now there but it still shows up as 0% for me.

Buzzer
------

Kind of cool is that it looks like you can do without a buzzer altogether and use the motors to beep - see <https://oscarliang.com/esc-beacon-lost-model-alarm/>

As OL notes (and JB in his comment near the top of the comments section on [this video](https://www.youtube.com/watch?v=3LL2caB3r88)), beeping too loud and too long can be very bad for your motors.

BF bluetooth
------------

If you look at the ports shown above, you'll see UART0 is called UART VCP and is actually used for the connection between BF and your laptop. UART1 is used for the VTX - which we've already covered. UART6 is for the RX.

So, what about UART2? It's shown with _Configuration/MSP_ enabled. It turns out that if your FC has a Bluetooth module then it uses this UART.

If you enable Bluetooth on your phone and download the [SpeedyBee app](https://www.speedybee.com/speedy-bee-app/), you'll be able to use it to connect to your FC and do many of the same things that you can with _Betaflight Configurator_. This can be useful if you're out in the field without a laptop and a USB connection.

As with all things Bluetooth, it can be a bit flaky - sometimes I have to restart the quad to be able to reconnect again after disconnecting.


