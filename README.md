### clutch

I wrote clutch to let me use this $9 foot pedal to control vim without hardware modification.

http://www.amazon.com/gp/product/B0098PLPOI/ref=oh_details_o00_s00_i00?ie=UTF8&psc=1

By default the pedal just sends a "b key pressed" event when you push it down and a "b key released" when you lift your foot.

This very small utility lets you define what keys you *actually* want to happen when the pedal sends these events.

By default, it will emulate tapping the `i` key when you put your foot down and will emulate tapping the `ESCAPE` key when you lift your foot up.

Please read the very short one-file source to see what other keys are available.

### Use:

clutch *MUST* be run as root.  OSX only allows root programs to hijack USB keyboards ( the os thinks the foot pedal is a one-key keyboard... )

default: `i` on down, `ESCAPE` on up:

	sudo ./clutch 

Example: `a` on down, `ESCAPE` on up:

	sudo ./clutch a

Example: `a` on down, `ESCAPE` on up, but ensure that `SHIFT` is held down while `a` is being pressed (has the effect of A in your editor)

	sudo ./clutch a ESCAPE SHIFT


#### Similar work:

https://github.com/alevchuk/vim-clutch is the first implementation that I was aware of.  Unfortunately, it requires hardware hacking.  I just use the operating system's accessibility API to fake the key sends, so no hardware hacking needed for "organ playing".

### TODO:

I would really like to be able to program a series of keyboard events for each foot pedal event.

I am currently thinking of a mini dsl like this:

	./clutch 'ESCAPE,+SHIFT,a,-SHIFT' 'ESCAPE'

This would let you specify arbitrary key events (using + for pressing and - for releasing, with neither for a simulated 'tap')
