There's no instruction manual either online or with the frame fro the QAV-R 2 DC.

DrainMan FPV build of non-DC variant - <https://www.youtube.com/watch?v=npAWcTUKCpU>

At 8m 47s, he refers to the the two sets of slots at the back of the upper plate as zip-tie holes for the antenna.

Slots for camera mark front of bottom plate.

Lock nuts face into body of quad.

The M3x8mm 28pcs are for motors.

M3x30mm are for the center stack.

The M3x14mm are for the places where there are stadoffs.

And the M3x12mm are for where there aren't stadoffs.

---

More detailed build from SF PV - <https://www.youtube.com/watch?v=OcpguW2v5es>

He notes the middle screw is different from all the others but the DC doesn't seem to come with a one off special screw.

He uses race wire - see README.

Mr. Steele uses wire protectors (see 46m 18s in video below) which looks simpler. And he attaches them with two wraps of electrical tape.

He trims off 2mm from ends of motor wires before attaching to ESC.

Tape over ESC with Kapton tape.

---

Huginn FPV - <https://www.youtube.com/watch?v=P3TvvqX3dTg>

Actual builds the DC variant.

He says the odd little plastic pieces are for mounting micro cameras if you don't want to use the carbon fiber side plates. And indeed you can find lots of images of this style of mounting:

![micr camera mount](https://files.cults3d.com/uploaders/6148699/illustration-file/ec66db2d-3b8c-4e69-aa17-65d9d97e0d37/IMG_20190325_203111_1.jpg)

Oddly, his middle small X hsa different width arms (front two for front arms are narrower), but for mine all arms are the same width.

He just uses a "medium" screw (the 12mm, I guess) for the middle hole.

All the stadoffs just go thru one layer of carbon fiber - so, he only uses the longer (14mm) ones for the two standoffs at the back of the triple layers of carbon fiber.

He puts the rubber o-rings at the bottom of the stack bolts.

---

Mr. Steele - <https://www.youtube.com/watch?v=17RaCAcFh4A>

At 32m 14s he cuts down the pigtail to 55mm.

Then he cuts the red 5mm shorter - he wants it to come out the right-hand side.

He pushes in an unreal amount of solder when tinning.

He uses neddle pliers rather than tweezers.

He only puts on stadoffs etc. once he's soldered up the ESC.

He puts an isolation plate beneath the VTX. But if you use metal screws this is a bit pointless (he uses nylon).

He sticks his RX to the top of his VTX - see notes on JB and Ummagawd doings this in README.

---

JB 2022 Freestyle FPV Drone Build:

<https://www.youtube.com/watch?v=2T_JC4v5T3E&list=PLwoDb7WF6c8neIAQBkchfiXf-C8KbzG5M>

At the 2m 50s mark, he comments he uses Gemfan Hurricance 51477 fans - I got the 51466 variant - I don't know what the difference is.

If you look at JB's video, you can see the o-rings make sense if you ESC has short gummies but the Tekko have tall gummies.

He does reduce motor slack at the ESC end rather than the motor end due to fear of the cable being cut by the props.

Twisting cables to stop them splaying.

Rounting the XT60 pigtail at 90&deg; looks like your only option

Or you rotate the ESC 180&deg; - but you can't flip it upside down - otherwise you can't get at the ESC pads.

---

When putting in motor screws make sure screws don't push into motor body and make sure not to overtighten and strip aluminium threads of motor.

The motors come with their own screws for 3mm, 4mm and 5mm thick arms - my calipers says the arms aren't a consistent thickness - they vary between 4.55mm and 4.74mm.

---

Put the cap on the opposite side of ESC to XT60 pigtain?

---

My build
========

Bolt or screw? Be consistent.

I started by loosely screwing down the X between the small plate and the bottom plate. I used thread locker for the following screws but not for this first one.

Then I put in one of the back arms, got it to engage with one of the arms of the X and swivilled things until all the appropriate holes lined up.

I emptied the 12mm bolts into a tiny dish.

There are three holes for the back arm but only two have press nuts on the opposite side of the main bottom plate. The center one is for the main stack - I left the stack holes for all arms until later.

I just screwed a bolt into the hole that had a press nut and wasn't for the stack.

Then I did the same for the other back leg.

Then I inserted the front legs - in their case both the holes to either side of the center stack hole have press nuts so, I screwed bolts into both these holes.

Then once everything was secure, I backed out the center nut, applied thread locker and screwed it back in.

See in the photo that the bolts are not quite flush with the press nuts - they'd have to be about 11mm for this. And see that there are two bolts screwed in for each of the front arms but only one for each of the back arms.

Don't overdo things when tightening the bolts - the rule-of-thumb I've heard is never screw things in more tightly that you can do with comfortably with thumb and forefinger.

For each screw, I just applied a tiny drop of thread locker to the end of the screw (i.e. the bit that would end up in the press nut) and rotated the screw, using glue nozel to spread the the blob thinly around the bolt.

Then I took out the 30mm screws - here it was a little trickier to work out which bit of the bolt would end up in the press nut and apply the threadlocker there.

Gummis
------

I found inserting the first gummy difficult and looked for tips for how to do it on YouTube. Some people clearly had way more trouble than I did and came up with solutions involving pliers and other tools. I don't think that's necessary. After one or two I found I could do it fairly easily - by pushing one side of the gummy up through the hole, then once it was through, twisting it around (while also pushing upwards) until the rest was through.

TODO
----

Plan all cabling for ESC before you start soldering.

Which side of main VTX unit is the top.

Weirdly, the QAV R-2 doesn't come with nuts of any kind for top of stack.

ESC wiring
----------

JB almost has his XT60 leads pointing back into the ESC rather than away - that seems likely to result in the wires knocking against the stack and causing vibration.

Mr. Steele creates the pigtail, then cuts the length of cable extending beyond the connector down to 55mm, then cuts 5mm off the red one so that it when soldered down it protrudes at 45&deg;.

So, I cut 5mm off the black one as my ESC is pointing the opposite direction.

So:

| 4mm bare wire | 4mm inside hood | 55mm

Second time around, I switched to:

| 4mm bare wire | 4mm inside hood | 60mm sheathed | 4mm bare wire

And chopped the shorter wire down by 8mm.


---

I decided I wanted my cable, when twisted, to be about 3cm longer than the untwisted length of the longer of the two supplied ready to plug cables.

So, I twisted the the ESC to FC wire and then cut it down to 95mm, not including header, i.e. 95mm of cable extending out of the header.

Then I untwisted the wire and the length of wire was about 107mm.

On untwisting them, one wire turned out to be noticeably shorter than the others - so the sensible thing would have been to cut just one of the wires when twisted then untwist and cut the rest.

Then I used the smallest setting on my clipper thingy to remove about 2mm from the end of each wire.

Unlike JB, he tins all the pads and attaches the XT60 leads before installing in the frame.

---

Soldering up the ESC didn't work out very well.

Soldering on the connection to the FC was very stressful.

Despite my cool soldering iron, the solder didn't go down well on the large negative and positive pads.

The cap is fat and needs to be bent upwards substantially before it'll clear the bottom plate.

Even with 5 or 6mm clearance for the cap, the leads still intersect with it - if doing again, I'd go with JB's straight out sideways rather than Mr. Steele's 45&deg;

But I think that'd be hard to combine with the cap on the underside - I think I'd go with it on the top - solder them in first then tin the pads.

I did redo it - with the cap on the top-side, I completely over compensated for having been too near the first time and moved the cap so far away from the FC that I might as well have used a tall cap.

---

Note for future - you can plug the ESC into the FC at this point and do a wiring continuity check (see below) and smoke test and then check that everything's good with the ESC as in <https://www.youtube.com/watch?v=5ke6LabvtGM&list=PLwoDb7WF6c8neIAQBkchfiXf-C8KbzG5M&index=4> before doing the FC wiring.

If I'd done that, I'd have found an ESC issue before all the other wiring made it far more complex to diagnose and address.

---

If redoing the wiring, I'd do the tinning as JB does in his soldering into video.

I let solder wick way too far into the wires making the solid and unbendy - JB holds the iron in place, dabs a little solder on the end then, while feeding solder, draws the wire over it so you end at the tip.

---

The motors come with three sets of screws - for arms that are 3mm, 4mm and 5mm thick.

The 5mm thick ones are the same size as the 8mm screws that come with the frame so, I used them rather than the ones that came with the motors.

----

Unbelieveably annoyingly, the motor wires for the rear arms were too short so I had to add extenstions.

---

I screwed in the bolts for the motors very loosely initially and only once all four were in place did I tighten them up. Here in particular, you don't want to overtighten due to the risk of stripping the aluminium threads in the motor - the thread locker should keep things in place.

Wires
-----

I chopped off one end of the GPS cable.

I took the JST-GH to DF13 SiK cable and chopped off the DF13 end 

FC wiring
---------

The FC side, the plastic coating of the wire of  VTX connector could be stripped with the 28AWG hole (26AWG almost worked but sometimes slipped).

For the VTX side, with silicone coating, I nipped off the ends with my nails - using even 30AWG with the wire stripper sometimes just took the whole end off.

I cut the VTX side down to 70mm plus 3mm bare wire.

I cut the FC side down 2cm plus 3mm bare wire.

Don't forget to put shrink wrap on before soldering wires together.

I cut the buzzer wires down to 110mm plues 2mm bare wire at both ends - I tinned the ends that were later soldered to the buzzer.

For no good reason, I soldered the wires to the buzzer before soldering them to the FC - for everything else I soldered the wires to the FC first.

I didn't chop down the RX wires - at 65mm they already felt short enough. Using 28AWG, I exposed a bit more wire on both ends so they'd poke thru the PDB holes (the FC it thicker than the FC so, one end needs more exposed wire than the other). I didn't trim off the ends and can't honestly tell if they're tinned or not.

I did not retin them - it's just too fiddly when trying to push them thru holes afterwards.

I cut the GPS wire down to 140mm plus 3mm of bare wire. Again, I used the 28AWG gauge when stripping. I didn't tin them.

I cut the SiK wires down to 70mm plus 3mm of bare wire - I gave up on using my nails to strip them, it's easier with 28AWG on the wire stripper. The plastic on the wires definitely isn't silicone, it shrivelled near heat and it stuck to the solder tip like stringy cheese.

---

In retrospect, I'd install the VTX and camera before the ESC - detaching the camera connector from the VTX was stressful and I wouldn't recommend it.

Unlike the antenna side (which is super simple), the little latch on the camera side of the VTX is stuck down with a little pad but just ease it off (it won't pull anything else with it). To remove the camera connector, go in under the cable with somthing thin and narrow and pry the connector up from its center.

You can see someone making it look easy (working with the same kind of camera connector but on a DJI VTX module) at around the 24s mark in this [video](https://www.youtube.com/watch?v=r9Yb4ThHNGA).

I then used the shortest screws (there was a set of 8 

8 x 4mm M2 screws
4 x 5mm M2 screws
4 x 6mm M2 screws
4 x 14mm M2 screws
4 x 0.5mm M2 washers (0.5mm thick, 5mm outer diameter)

And I used the 6mm ones for attaching the board that the RX sits on. Pulling the back off the double-sided tape was a  pain.

---

Smoke check
-----------

<https://www.youtube.com/watch?v=8gQpO5jTHP4&list=PLwoDb7WF6c8neIAQBkchfiXf-C8KbzG5M&index=2>

On checking the XT60, I got a very slight beep on first contact (when JB got) none - then I got the long-ish beep on reversing the prongs (as expected due to the cap) and got a similar long beep each time I reversed the prongs after that (i.e. a beep each way, not just on one particular "side").

My FC has no VBAT pad so, I used B+ on ESC port 1 - holding the probe to the point where the pin enters the connector lead to a much better beep than touching the pin where it connects to the FC PCB.

My VTX is powered off a 9V BEC on the FC so, I can't check it for VBAT continuity.

For ground, I found (oddly) that most of the outside of the USB connector responded poorly - for whatever reason, touching the probe off the edge around the main opening of the connector gave the best results. Using a GND pad also worked well.

On watching JB again, I noticed he touches the probe to one of the little indentations on the top of the USB connector - this worked very well too.

Checking the antenna connector for GND also worked. I couldn't check the RX's GND pin itself as I'd already shrink wrapped it.

Then I got to the smoke stopper part - for this you need a charged battery (see next section).

JB reminds you - when powering up any device that has an antenna, e.g. the RX on your quad, your TX or your goggles, make sure the antenna is connected before you power it up or you may damage the device - really!

I plugged the battery into the smoke stopper - the yellow LED went on. Then I plugged the smoke stopper into the quad, the LED stayed yellow - so, all good so far.

There's two buttons on the Short Saver - ignore the one at the edge of the boards - it's for changing the current that it'll allow to flow (useful if you want a bit more current while doing more than basic smoke testing).

Just short press the other button (long pressing lets you adjust the sensitivity, again a feature we don't need for basic short testing).

On pressing it, the LED went green and the FC beeped and LEDs went on on the TC, FC and GPS. The one on the TX was annoyingly bright - I find [Light Dim stickers](https://www.lightdims.com/store.htm) work very well (the web site is quite cheesy but they work way better than e.g. using black electrical tape).

For more details on the Short Saver see OL's [page](https://oscarliang.com/vifly-short-saver-2/) and for a short intro (including using the other button and adjusting sensitivity), see Mads Tech's [video](https://www.youtube.com/watch?v=RT_5AQTq5Ig).

The Short Saver is also really nice as it allows you to turn on and off the quad without prising the XT60 connectors apart - if you leave the quad powered up most of the components will get hot and some will get very hot (they rely on being cooled by moving air when in flight).

Note: the one horrible feature of the Short Saver is that it has a weird XT60 that gives you almost nothing to grip and so makes unplugging it even more trouble that a normal XT60 (I found it easier gripping the connector with a dish cloth).

Charging batteries
------------------

The fan is super noticeable on the charger.

TODO: upgrade firmware - my charger came with 1.0.46 but 1.0.47 came out in mid 2023.

As usual with Chinese instructions, it's all very unclear and lots of people have trouble getting this working - this video shows how <https://www.youtube.com/watch?v=SUoooEZjDCY>

JB also shows himself doing this process - <https://www.youtube.com/watch?v=XIf8cKKiGJg> - while discussing a new HOTA firmware feature called "continuous work" (which may or may not be in that 1.0.47 update - I don't know as I haven't done it).

Go to this page: <http://www.hota-exp.com/index.php/service_l_2.html?t=en>

You need the _D6 Pro Firmware_ and the _HTLoader_ - unfortunately, _HTLoader_ is a Windows only program.

On this page, you can also find the _D6 Pro Manual_ PDF.

Note: the HOTA D6 Pro and the Hobbymate D6 Duo Pro are the same product - Hobbymate's site has out-of-date firmware so, HOTA seems the place to go.

Basics:

* There's a _CH_ button on the left and a scroll whell on the right.
* Long press it to get to settings (scroll to the bottom to get to the _Back_ option).
* Press the button to switch between the left and right channels (i.e. the connections for the left and right batteries).
* When you've plugged in batteries, press the _CH_ button to select the first channel and then short press the scroll wheel to get to what HOTA call the task options.

The balance leads are so short that it's quite tricky to plug them in after plugging in the main lead. It _might_ be worth getting an extension lead - <https://www.getfpv.com/balance-lead-extension-cable-4s-jst-xh.html>

The balance connectors will take different size balance leads (anything from a 2S to a 6S lead) so make sure your 4S balance lead is plugged in all the way to the right (so that the connector pins to the left are empty and the right most pin of your lead is under the negative minus symbol on the charger's connector). You can't plug the lead in upside down and if you accidentally connect the lead so that it's not all the way to the right the charger will warn you.

OL and others say connect the main lead first then the balance charger.

Once both batteries were plugged in, I pressed the _CH_ button and then short pressed the scroll wheel to get to the task options. Everything, defaulted to the correct values:

* Task: _Charge_
* Battery type: _LiPo_
* Cell voltage: 4.2V
* Cell count: 4S (14.8V)

The only thing I had to change was the current setting, set this to match the mAh value of your battery - mine are 2200mAh batteries so I set the current to 2.2A.

Then scroll down to _Start task_ and short press the scroll wheel to start the charging process.

Press the _CH_ button again and do the same for the second battery (it copied across the current setting so, I didn't have to set it again).

Once you've started the charging process for the second battery, press _CH_ again to watch both batteries charging.

You may notice that the battery capacity is in Ah while the selected current is in A - charging a 2200mAh battery and 2.2A means you're charging it at 1C which is considered the safe level at which to charge batteries - many batteries will handle higher C values but 1C is always safe. The 75C or higher value shown on your battery is a _discharge_ rate and unrelated to how fast you can safely charge the battery.

Charging any capacity battery (from their recommended lower voltage bound) at 1C should take about an hour. See <https://oscarliang.com/lipo-battery-guide/>

Charging my batteries (which came from the factory at storage voltage) took 36m.

Do not leave the batteries charging unattended - even though the fan noise is quite annoying don't leave them charging in another room as LiPos can be dangerous and may spontaneously combust.

And if you think the fan was loud when you first plugged in the charger, it'll get really loud later in the charging process (around the 15m mark for my batteries).

When the charging is finished, it'll beep and the side of the screen for the battery that's finished well go green, this means it's completed and that the maximum cell voltage difference is 20mV. Let it run a little longer and it'll beep again and it'll go from green to blue - this means it's balanced things out even more and the maximum difference is now 10mV.

I chopped off the large _DO NOT PULL_ stickers on the main leads of my batteries. It's there to remind you not to disconnect the battery from the charger (or your quad) by pulling on the leads - instead hold the connector and wiggle it out.

Once finished, I didn't press anything on the charger, for each battery, I just disconnected the balance lead first and then the main lead.

For a nice intro to the HOTA D6 Pro, see Matt Pochwat's ["What Makes a Great LiPo Charger?"](https://www.youtube.com/watch?v=No0sv3GgwdE) video.

For a more detailed look at getting started with charging batteries, see Supa FPV's ["The ONLY Battery Charger You'll Need!"](https://www.youtube.com/watch?v=eM4VlJTtARQ) - there's a rather rambling start, so just jump to the 11m 3s mark where he actually shows how to use the charger. Flitetest have a more detailed [overview](https://www.youtube.com/watch?v=1LBTmiaRQK0), where they go into C ratings etc. and how to use the charger but they don't show this bit in quite as much details as Supa FPV's video.

The other nice feature of the D6 Pro is that you can use it as a desktop power supply, i.e. if you had a XT60 female to Xt60 female cable, you can switch the task (see above) _Power Supply_ and adjust this tasks output voltage setting to 14.8V (or whatever voltage you want), then use it to power your quad rather than a battery, e.g. while testing things on your desk. When doing this you can also adjust the maximum current down to e.g. 5A to make sure you never provide enough power to accidentally spin up the props or anything else dangerous. It also has short circuit protection which means if you do short anything it _should_ shut down very quickly. However, for smoke testing,  people still seem to favor a specialized smoke stopper like the VIFLY one.

FC configuration
----------------

Go to <https://betaflight.com/download>, click _Latest configurator releases_ and download `betaflight-configurator_10.9.0_macOS.dmg` or whatever the latest version currently is for Mac.

Install it, open the _Applications_ folder, find it there, right click it and select _Open_ (just for the first time you use it to get past your Mac trying to protect you against applications that macOS can't verify). It's extremely slow to load so, I presume they're still just building x86_64 binaries and macOS is converting it for M1 or M2 chips.

JB powers his quad from a battery while doing all this - I did not, 

For the first steps you just need the USB power from the laptop is enough (and doing this meant everything except the RX stayed cooler than with the battery).

[ JB initially shows a setup with the battery also connected but it's clear later that you should only connect it when you need it to test the motors. ]

Once the Configurator is running, connect the FC to your laptop using its USB-C connector (macOS will ask you if you want to allow the device to connect). The FC and other components power on but it doesn't beep when there's no battery connected - surprisingly, it's the motors that make the beeps and without the battery the ESC and the motors aren't powered.

You get a very scary warning for the Configurator on first connecting (see images/betaflight folder).

It auto-connects, so go to the _Presets_ tab and click _Save Backup_ - when it's done it quickly disconnects and reconnects (and you see the scary warning again).

Looking at the save `BTFL_cli_backup_20230727_144658.txt`, there's absolutely no changes from the defaults except for:

```
feature -RX_PARALLEL_PWM
```

[ This disables support for parallel PWN receivers - see <https://betaflight.com/docs/development/Rx> ]

The files does show some useful information:

```
# Betaflight / STM32H743 (SH74) 4.3.1 Jul 13 2022 / 03:37:48 (8d4f005) MSP API: 1.44
# config: manufacturer_id: HBRO, board_name: KAKUTEH7V2, version: cd183ad2, date: 2022-06-08T04:12:46Z
```

So, it came with Betaflight 4.3.1 and the board name is `KAKUTEH7V2`.

So now click the _Disconnect_ button (upper right) in the Configurator, then select the _Firmware Flasher_ tab (left side) and click the _Auto-detect_ button (upper-left panel).

It correctly detects `KAKUTEH7V2` and shows the latest firmware version (4.4.2 at the time of writing).

Unlike JB, I didn't select _Show unstable releases_ as the current latest version was fine.

Click _Load Firmware [Online]_ (lower right) and then _Flash Firmware_ - it'll actually switch the FC into a special DFU mode so, to macOS it'll look like a new device and it'll ask you again if you want to allow it to connect.

Once the flashing is finished, click the _Connect_ button - it'll ask you if you want to apply custom defauls - you do so, select this. The same scary warning appears again.

Let's fix that warning...

It should go to the _Setup_ tab - place the quad flat on the table and click _Calibrate Accelerometer_ - this just takes a second.

Note: it's probably a good idea to put on landing pads later and redo this step when the quad can lie flatter better (without them, the antennas under the back legs cause the quad to tip forward slightly).

I hoped it might detect the compass in the GPS but the _Calibrate Magnetometer_ is greyed out.

Then I went to the _Motors_ tab and selected _DSHOT600_ in the _ESC/Motor Features_ panel (the H7 is a powerful MCU and can support _DSHOT600_).

NOTE: the Tekko32 product page says it supports DSHOT1200 - but it turns out that Betaflight removed DSHOT1200 support back in late 2019 (see this [post](https://intofpv.com/t-dshot1200-removed-from-betaflight-4-1)) so, _DSHOT600_ is as good as it gets.

Then I selected _Bidirectional DSHOT_ and agreed to the warning that popped up.

Then I clicked _Save and Reboot_.

Once it reconnects, go back to the _Motors_ tab - you'll see "E: 100%" (errors at 100% which means bidirectional DSHOT is enabled but the ESC isn't powered up).

Now's the time to plug in the battery (it'd be good to have a small desktop fan to keep air moving over everything and help keep things cool). So, I folded over two strips of black electrical tape and hid them under them.

Once plugged in the _E_ values should go to 0%.

At this point I found one of my motors wasn't working - one of the _E_ values stayed at 100%.

HERE

Now, click _Reorder motors_, enable the _I understand the risks_ option and click _Start_.

---

BLHeli_32
---------

Note: BLHeliSuite32xm crashed on me a couple of times (often when it disconnected from the FC), sometimes killing it and restarting it wasn't enough - I had to power down the quad and power it up again.

Note that if you've got Betaflight Configurator, it'll automatically reconnect to the quad each time you plug it in - the Configurator always has to be disconnected for BLHeliSuite32xm to be able to access the ESCs (via the FC).

The BLHeli_32 main page is in a rather odd place, they don't have a website and the main page is in the `BLHeli_32 ARM` subdirectory of their GitHub repo <https://github.com/bitdump/BLHeli/tree/master/BLHeli_32%20ARM>

But just go to [releases](https://github.com/bitdump/BLHeli/releases) and select the latest MacOS release (`BLHeliSuite32xm_MacOS64_1042.zip` at the time of writing), the `.zip` file contains a `.dmg` file and from this you can install _BLHeliSuite32xm_. As with the Betaflight Configurator, right click it and select _Open_ the first time you use it.

Important: initially, I connected the battery first then the USB and the USB didn't show up. Turning the battery off (using the Short Saver on/off switch) and then plugging in and out the USB fixed things.

TODO: check this is always the case.

For me, _BLHeliSuite32xm_ was already set up to use _Betaflight/Cleanflight_ as the interface (and so to use what's called _passthru_ whereby it takes to the ESC via Betaflight on the FC) and when I plugged in USB it auto detected the correct port.

So, I just turned on the battery and then clicked _Connect_ and then _Read Setup_ - the reading was quite slow but it found 3 ESCs (the Tekk 32 is a 4-in-1 ESC) but couldn't talk to the forth one.

The ESCs had rev 32.8 of BLHeli_32 (released Mar 14th, 2012).

From the _ESC Setup_ menu, I selected _Save MultipleESC Setup to ini file_ and saved `BLHeli32_TEKKO32_F4_4in1_H - Rev. 32.8 - Multi_230727.ixi`.

**NEXT TIME** try the _ESC flash_ tab - is its behavior any different (can you just say yes to all four at once there?).

I pressed _Flash BLHeli_ and it suggested 32.9 as the latest version (I checked - at the time of writing it is the latest version, released Mar 10th, 2022 but patch releases seem to be release every so often - 32.9.0.5 released Aug 29th, 2022 is the latest shown on GitHub but maybe those patch releases only relate to BLHeliSuite32 and not to the firmware).

You have to go through the process of saying yes to the desired version for all four ESCs in the 4-in-1.

---

Back right is the problem motor.

---

TODO: redo _Calibrate Accelerometer_ (see above) once you've added landing pads.
