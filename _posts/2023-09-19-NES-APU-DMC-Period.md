---
layout: default
title:  "NES APU DMC Period"
---

# DMC Channel in Kung Fu ("スパルタンX" in Japanese title)

I have been struggling with making DMC channel work for my NES Emulator.
The channel sounded low pitch and low volume. I overlooked the very
important thing for timer period described in NES DEV Wiki.

> The rate determines for how many CPU cycles happen between changes in the output level
> during automatic delta-encoded sample playback. For example, on NTSC (1.789773 MHz),
> a rate of 428 gives a frequency of 1789773/428 Hz = 4181.71 Hz. These periods are all
> even numbers because there are 2 CPU cycles in an APU cycle. A rate of 428 means
> the output level changes every 214 APU cycles.

It clearly says the numbers in the lookup table are CPU cycles **NOT** APU cycles.
That means the timer should be decreased 2 when the timer is clocked. For example,
if you have code for timers like this,

```cpp
void APU::clock_timers()
{
    if (clock_ % 2 == 0) {
        clock_pulse_timer(pulse1_);
        clock_pulse_timer(pulse2_);
        clock_noise_timer(noise_);
        clock_dmc_timer(dmc_);
    }

    clock_triangle_timer(triangle_);
}
```

the dmc timer is clocked every other CPU cycle. So in the `clock_dmc_timer()`,
we have to decrease timer count by 2. Similarly, the noise period needs to be
decreased by 2 in the `clock_noise_timer()`.

```cpp
static void clock_dmc_timer(DmcChannel &dmc)
{
    if (dmc.timer == 0) {
        dmc.timer = dmc.timer_period;

        // read sample
        read_dmc_memory(dmc);

        // clock sample
        clock_dmc_shift_register(dmc);
    }
    else {
        // DMC timer period table is based on CPU cycles
        dmc.timer -= 2;
    }
}
```

I felt the noise sounded a little
different than other solid emulators but I just leave it as it at the beginning.
It was harder to listen apart the noise sounds, but the DMC channel in "Kung Fu"
has been made a big difference by the period bug.

Check my emulator's code if you like. Hope this help your NES development!
[Famulator Famicom/NES Emulator](https://github.com/tsubo164/Famulator)
