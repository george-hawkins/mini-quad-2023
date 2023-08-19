Progress:

* On hay stacks - just getting to the point where I wasn't crashing every few seconds and could move about a bit but in a very uncontrolled manner and without practicing anything specific.
* Moved of to drill 1, first happy if I could hover (badly) at the height of the top of the middle pilon - after nudging forward and sideways to mean I was continously adjusting pitch and roll as well as throttle just to stay steady.
* Then I moved on to trying to swing right and left at the height of the top of the pilons and swinging right once I'd reached the left pilon and swinging left when I'd reached the right. Around this time I adjusted my camera angle up from 5&deg; to 10&deg;.
* I didn't try to reach the point where I could do the up-down/left-right manoever that was the ultimate goal of the first drill. Instead, I move onto drill 2.
* Initially, I was happy if I could charge up and down the laid out lane - over time I tried to get lower and lower, i.e. run down the lane very low without bouncing off the ground.
* Only, after about 20 hours (of total Liftoff flight time) did I try slowing down and speeding up again at the dividers on the lane. At this point, I adjusted my camera angle up from 5&deg; to the 10&deg; suggested by Jack (FPV Academy) for this stage. And removed the expo from my throttle - I didn't find this a problem to adjust to.

Liftoff
=======

First off - I thought this was impossible at first - and you can find many videos where people have the same experience. But trust me - it does get better. Some people seem to pick things up really fast. For me it took about 4 hours before I stopped crashing every few seconds.

My one liner opening advise - initially, you'll continuously crash and then reset due to your motors burning out (your quad being like a turle on its back, the motors push groundward rather than skyward). Once, you've gained a minimum of control, don't let this happen - once you've hit the ground, cut throttle and press the _T_ (turtle) button to flip the quad right-side-up, take off again and use yaw to turn the quad (using the LEDs on the back of the quad as a visual aid) so you know what direction its facing and carry on.

Aside: amazingly, turtle is something real quads are capable of, it's not just a game feature (though in reality, it doesn't work as consistently).

---

Copy an existing model and turn off the internal radio or it'll heat up pointlessly (and the resulting fan noise may become annoying). Also, not transmitting serious reduces battery consumption.

Twist your antenna clockwise until it's not getting in the way of the USB port and connect the TX to your laptop with a USB-C cable.

Note: always twist clockwise - you don't want to loosen your antenna (twist counter-clockwise) - if the antenna isn't properly installed the transmitter may potentially burn out.

Not GTA IV - only so much end user testing.

Had to do recalibrate several times.

And in the final page of the  calibration process, I had to move the sticks and confirm that the quad shown lower-left moved as expected - it didn't and I had to invert some of the axes.

The only button I set up wsa _Arm_, I set it to be flipping SA (the upper-left-most switch) down. I dis also bind disarm to flipping SA up - but disrm isn't much use if Liftoff.

The tutorial seems fairly so-so.

To start choose:

* Single player - free flight.
* Level - Straw Bale.
* Track - no track.
* Drone - Borum 180 X (Tutorial).

There's a non-tutorial version of the Borum 180 X - the tutorial version has lower thrust and speed and so should be easier to control.

There are various parameters shown for each drone, one of these parameters is called _Control_ - I thought the higher this value, the easier it was to control. But actually, _Control_ is just the flight style and its one of _Drifty_, _Freestyle_, _Racing_ and _Super_ and _Control_ just goes up and down reflecting the first, second, third or forth of the these styles.

I've had it crash a few times on one or other of the loading steps (generally around the 50% mark)  - using _Force Quit_ and restarting always worked.

When starting it asks you to select between a _default_ and a _Metal rendering_ launch option - Metal rendering offers improved performance (so, I don't know it's not the default). on my 2022 Macbook Air, I see a little red warning icon in the upper-right of my screen when not using Metal rendering - according to [support](https://www.liftoff-game.com/support?topic=3&category=15&post=28), this icon indicates that Liftoff is running at less that 30fps. When using Metal rendering, the warning icon doesn't show.

### Key bindings cheatsheat

* Flight mode: A
* Viewpoint: V
* Line-of-sight (LoS): B
* Walk: Return
* Reset: R
* Turtle: T

Once started, make sure you're in _ACRO_ mode - press _A_ until you see (ACRO) in the upper-left of the screen (actually, it should be in acro mode by default).

To start with go into line-of-sight mode, i.e. looking at the drone without googles rather than viewing the world through the drone's camera and goggles.

Press _Return_ to go into walk mode - you can walk with the W, A, S and D keys but really we just want to be in this mode to place the quad much closer to you so you can watch as you apply throttle and it takes off. When you press _Return_, you'll see a red blob that moves as you look around - that's you quad, just move it to a point nearer to you (where it'll turn white) and click to place it.

Before powering up make sure the arm switch is in the up position and the throttle is all the way down - Liftoff should warn you to do this each time before you take off but it doesn't.

Try gently applying throttle and taking off slowly - adjust the throttle up and done until you're hovering.

This should turn out to be almost impossible - there are no end of videos on why hovering is hard in acro mode.

Once you've got frustrated, note that there's a big LED on the back of the quad - this will help you later to tell if it's facing away or towards you. I think it would have been nice if, in the _Workbench_ section, you could have added LEDs on the rear arms to make things even clearer when flying line-of-sight.

Let's put on some training wheels:

* Press _Escape_ to enter the _Pause Menu_, select _Options_, then _Game Options_ and turn on _Use On Screen Display_ - this will turn on an artificial horizon (how it can help you is covered in lots of videos introducing FPV using Liftoff).
* Back in the main _Pause Menu_, select _Flight Controller Settings_ this time, it'll ask you "Would you like to copy this drone to your Fleet?" Click _Yes_.
  * And in the _Rates_ section:
    * Set _Selected Model_ to _Actual_.
    * And then for _Roll_, _Pitch_ and _Yaw_ set the _Center Sensitivity_ to 100, the _Max Rate_ to 500 and the _Expo_ to 0.76.
  * And in the _Throttle_ section set _Expo_ to 50.

These values are at the complete beginner end of the range and are based on watching JB's video on rates <https://www.youtube.com/watch?v=Ql62iRkLX3s> and reading Oscar Liang's page on rates <https://oscarliang.com/rates/>

Adjusting rates to your liking seems fairly uncontroversial but setting expo on the throttle seems to be frowned upon so, maybe adjust it back down to 0 as you improve.

Note: you can turn the artificial horizon on and off in-game with F1. There a couple of other function keys - F9 to toggle bars showing pitch, roll and yaw and F12 to take a screenshot (this seems to be a hidden feature, I just found it by trying all the function keys).

### Artificial horizon

If the side bars aren't at 90&deg; to the top bar then you're still doing a manouver - so, after applying roll and/or yaw, always be aiming to get back to having the bars at right angles.

And when you're turning try to keep the horizontal bar steady relative to the real horizon - if it's changing it's swinging up and down relative to the horizon then you're not just turning and things will probably quickly get out of control.

---

To quickly choose the same track and drone, that you used last time, _Quick Play_ / _Last Session_ in the main menu.

Camera angles
-------------

Liftoff defaults to a camera angle of 30&deg; which is considered way too high for a beginner - most videos etc. recommend between 5&deg; and 10&deg; - I started at 5&deg;.

You can adjust the camera angle while playing with the up and down arrows but it'll revert to 30&deg; each time you restart.

To make a permanent angle change, go to the main menu and:

* Select _Tools_, then select _Drone Editor_ in the _Workbench_ section. 
* Select your drone (the copy you created in the previous step).
* Here, you can give it a cooler name than "[Copy] Borrum 180 X (Tutorial)"
* Now, select the camera and click _Edit Part_ and under _Set Camera Angle_ adjust the value to 5&deg;
* Click _Save_ and then _Exit_.

While on the workbench, I also changed the color of the front two props to red and the back two to cyan (as [How to fly Line Of Sight : Acro Tutorial Part 1](https://www.youtube.com/watch?v=RSaPPGa626c) recommended this for keeping track of orientation when doing LoS). I was sceptical the colors would be very visible but it actually does help.

---

Unplug USB _before_ turning off - it won't turn back on.

TODO: actually, I suspect it goes into bootloader mode if you power on with USB already connected (it lights up the flight mode button in turn before stopping on the first one).

---

The only way to adjust down the volume, e.g. before switching to another app, seems to be to press _Esc_, go to _Options_ / _Audio options_ and drag down the _Master Volume_ - there _really_ don't seem to be any key bindings related to audio.
