## title: First Sounds

# First Sounds

This is the first chapter of the Strudel Workshop, nice to have you on board!

## Code Fields

The workshop is full of interactive code fields. Let's learn how to use those. Here is one:

```javascript
sound("casio");
```

<Box>

1. ⬆️ click into the text field above ⬆️
2. press `ctrl`+`enter` to play
3. change `casio` to `metal`
4. press `ctrl`+`enter` to update
5. press `ctrl`+`.` to stop

</Box>

Congratulations, you are now live coding!

## Sounds

We have just played a sound with `sound` like this:

```javascript
sound("casio");
```

<Box>

`casio` is one of many standard sounds.

Try out a few other sounds:

```
insect wind jazz metal east crow casio space numbers
```

You might hear a little pause while the sound is loading

</Box>

**Change Sample Number with :**

One Sound can contain multiple samples (audio files).

You can select the sample by appending `:` followed by a number to the name:

```javascript
sound("casio:1");
```

<Box>

Try different sound / sample number combinations.

Not adding a number is like doing `:0`

</Box>

Now you know how to use different sounds.
For now we'll stick to this little selection of sounds, but we'll find out how to load your own sounds later.

## Drum Sounds

By default, Strudel comes with a wide selection of drum sounds:

```javascript
sound("bd hh sd oh");
```

<Box>

These letter combinations stand for different parts of a drum set:

<img src="/img/drumset.png" />

<a class="text-right text-xs" href="https://de.wikipedia.org/wiki/Schlagzeug#/media/Datei:Drum_set.svg" target="_blank">
  original image by Pbroks13
</a>

- `bd` = **b**ass **d**rum
- `sd` = **s**nare **d**rum
- `rim` = **rim**shot
- `hh` = **h**i**h**at
- `oh` = **o**pen **h**ihat
- `lt` = **l**ow tom
- `mt` = **m**iddle tom
- `ht` = **h**igh tom
- `rd` = **r**i**d**e cymbal
- `cr` = **cr**ash cymbal

Try out different drum sounds!

</Box>

To change the sound character of our drums, we can use `bank` to change the drum machine:

```javascript
sound("bd hh sd oh").bank("RolandTR909");
```

In this example `RolandTR909` is the name of the drum machine that we're using.
It is a famous drum machine for house and techno beats.

<Box>

Try changing `RolandTR909` to one of

- `AkaiLinn`
- `RhythmAce`
- `RolandTR808`
- `RolandTR707`
- `ViscoSpaceDrum`

There are a lot more, but let's keep it simple for now

🦥 Pro-Tip: Mark a name via double click. Then just copy and paste!

</Box>

## Sequences

In the last example, we already saw that you can play multiple sounds in a sequence by separating them with a space:

```javascript
sound("bd hh sd hh");
```

Notice how the currently playing sound is highlighted in the code and also visualized below.

<Box>

Try adding more sounds to the sequence!

</Box>

**The longer the sequence, the faster it runs**

```javascript
sound("bd bd hh bd rim bd hh bd");
```

The content of a sequence will be squished into what's called a cycle. A cycle is 2s long by default.

**One per cycle with `< .. >`**

Here is the same sequence, but this time sourrounded with `< .. >` (angle brackets):

```javascript
sound("<bd bd hh bd rim bd hh bd>");
```

This will play only one sound per cycle. With these brackets, the tempo doesn't change when we add or remove elements!

Because this is now very slow, we can speed it up again like this:

```javascript
sound("<bd bd hh bd rim bd hh bd>*8");
```

Here, the `*8` means we make the whole thing 8 times faster.

<Box>

Wait a minute, isn't this the same as without `< ... >*8`? Why do we need it then?

That's true, the special thing about this notation is that the tempo won't change when you add or remove elements, try it!

Try also changing the number at the end to change the tempo!

</Box>

**changing the tempo with setcpm**

```javascript
setcpm(90 / 4);
sound("<bd hh rim hh>*8");
```

<Box>

cpm = cycles per minute

By default, the tempo is 30 cycles per minute = 120/4 = 1 cycle every 2 seconds

In western music terms, you could say the above are 8ths notes at 90bpm in 4/4 time.
But don't worry if you don't know these terms, as they are not required to make music with Strudel.

</Box>

**Add a rests in a sequence with '-' or '~'**

```javascript
sound("bd hh - rim - bd hh rim");
```

**Sub-Sequences with [brackets]**

```javascript
sound("bd [hh hh] sd [hh bd] bd - [hh sd] cp");
```

<Box>

Try adding more sounds inside a bracket!

</Box>

Similar to the whole sequence, the content of a sub-sequence will be squished to its own length.

**Multiplication: Speed things up**

```javascript
sound("bd hh*2 rim hh*3 bd [- hh*2] rim hh*2");
```

**Multiplication: Speed up subsequences**

```javascript
sound("bd [hh rim]*2 bd [hh rim]*1.5");
```

**Multiplication: Speeeeeeeeed things up**

```javascript
sound("bd hh*32 rim hh*16");
```

<Box>

Pitch = really fast rhythm

</Box>

**Sub-Sub-Sequences with [[brackets]]**

```javascript
sound("bd [[rim rim] hh] bd cp");
```

<Box>

You can go as deep as you want!

</Box>

**Play sequences in parallel with comma**

```javascript
sound("hh hh hh, bd casio");
```

You can use as many commas as you want:

```javascript
sound("hh hh hh, bd bd, - casio");
```

Commas can also be used inside sub-sequences:

```javascript
sound("hh hh hh, bd [bd,casio]");
```

<Box>

Notice how the 2 above are the same?

It is quite common that there are many ways to express the same idea.

</Box>

**Multiple Lines with backticks**

```javascript
sound(\
```

**selecting sample numbers separately**

Instead of selecting sample numbers one by one:

```javascript
sound("jazz:0 jazz:1 [jazz:4 jazz:2] jazz:3*2");
```

We can also use the `n` function to make it shorter and more readable:

```javascript
n("0 1 [4 2] 3*2").sound("jazz");
```

## Examples

**Basic rock beat**

```javascript
setcpm(100 / 4);
sound("[bd sd]*2, hh*8").bank("RolandTR505");
```

**Classic house**

```javascript
sound("bd*4, [- cp]*2, [- hh]*4").bank("RolandTR909");
```

<Box>

Notice that the two patterns are extremely similar.
Certain drum patterns are reused across genres.

</Box>

We Will Rock you

```javascript
setcpm(81 / 2);
sound("bd*2 cp").bank("RolandTR707");
```

**Yellow Magic Orchestra - Firecracker**

```javascript
setcpm(120 / 2);
sound("bd sd, - - - hh - hh - -, - perc - perc:1*2").bank(
  "RolandCompurhythm1000",
);
```

**Imitation of a 16 step sequencer**

```javascript
setcpm(90/4)
sound(\
```

**Another one**

```javascript
setcpm(88/4)
sound(\
```

**Not your average drums**

```javascript
setcpm(100/2)
s(\
```

---

---

## title: First Notes

import { midi2note } from '@strudel/core';

# First Notes

Let's look at how we can play notes

## numbers and notes

**play notes with numbers**

```javascript
note("48 52 55 59").sound("piano");
```

<Box>

Try out different numbers!

Try decimal numbers, like 55.5

</Box>

**play notes with letters**

```javascript
note("c e g b").sound("piano");
```

<Box>

Try out different letters (a - g).

Can you find melodies that are actual words? Hint: ☕ 😉 ⚪

</Box>

**add flats or sharps to play the black keys**

```javascript
note("db eb gb ab bb").sound("piano");
```

```javascript
note("c# d# f# g# a#").sound("piano");
```

**play notes with letters in different octaves**

```javascript
note("c2 e3 g4 b5").sound("piano");
```

<Box>

Try out different octaves (1-8)

</Box>

If you are not comfortable with the note letter system, it should be easier to use numbers instead.
Most of the examples below will use numbers for that reason.
We will also look at ways to make it easier to play the right notes later.

## changing the sound

Just like with unpitched sounds, we can change the sound of our notes with `sound`:

```javascript
note("36 43, 52 59 62 64").sound("piano");
```

<Box>

Try out different sounds:

- gm_electric_guitar_muted
- gm_acoustic_bass
- gm_voice_oohs
- gm_blown_bottle
- sawtooth
- square
- triangle
- how about bd, sd or hh?
- remove `.sound('...')` completely

</Box>

**switch between sounds**

```javascript
note("48 67 63 [62, 58]").sound("piano gm_electric_guitar_muted");
```

**stack multiple sounds**

```javascript
note("48 67 63 [62, 58]").sound("piano, gm_electric_guitar_muted");
```

<Box>

The `note` and `sound` patterns are combined!

We will see more ways to combine patterns later..

</Box>

## Longer Sequences

**Divide sequences with `/` to slow them down**

```javascript
note("[36 34 41 39]/4").sound("gm_acoustic_bass");
```

<Box>

The `/4` plays the sequence in brackets over 4 cycles (=8s).

So each of the 4 notes is 2s long.

Try adding more notes inside the brackets and notice how it gets faster.

</Box>

**Play one per cycle with `< ... >`**

In the last section, we learned that `< ... >` (angle brackets) can be used to play only one thing per cycle,
which is useful for longer melodies too:

```javascript
note("<36 34 41 39>").sound("gm_acoustic_bass");
```

<Box>

Try adding more notes inside the brackets and notice how the tempo stays the same.

The angle brackets are actually just a shortcut:

`<a b c>` = `[a b c]/3`

`<a b c d>` = `[a b c d]/4`

...

</Box>

**Play one sequence per cycle**

We can combine the 2 types of brackets in all sorts of different ways.
Here is an example of a repetitive bassline:

```javascript
note("<[36 48]*4 [34 46]*4 [41 53]*4 [39 51]*4>").sound("gm_acoustic_bass");
```

**Alternate between multiple things**

```javascript
note("60 <63 62 65 63>").sound("gm_xylophone");
```

This is also useful for unpitched sounds:

```javascript
sound("bd*4, [~ <sd cp>]*2, [~ hh]*4").bank("RolandTR909");
```

## Scales

Finding the right notes can be difficult.. Scales are here to help:

```javascript
setcpm(60);
n("0 2 4 <[6,8] [7,9]>").scale("C:minor").sound("piano");
```

<Box>

Try out different numbers. Any number should sound good!

Try out different scales:

- C:major
- A2:minor
- D:dorian
- G:mixolydian
- A2:minor:pentatonic
- F:major:pentatonic

</Box>

**automate scales**

Just like anything, we can automate the scale with a pattern:

```javascript
setcpm(60);
n("<0 -3>, 2 4 <[6,8] [7,9]>").scale("<C:major D:mixolydian>/4").sound("piano");
```

<Box>

If you have no idea what these scale mean, don't worry.
These are just labels for different sets of notes that go well together.

Take your time and you'll find scales you like!

</Box>

## Repeat & Elongate

**Elongate with @**

```javascript
note("c@3 eb").sound("gm_acoustic_bass");
```

<Box>

Not using `@` is like using `@1`. In the above example, c is 3 units long and eb is 1 unit long.

Try changing that number!

</Box>

**Elongate within sub-sequences**

```javascript
setcpm(60);
n("<[4@2 4] [5@2 5] [6@2 6] [5@2 5]>*2")
  .scale("<C2:mixolydian F2:mixolydian>/4")
  .sound("gm_acoustic_bass");
```

<Box>

This groove is called a `shuffle`.
Each beat has two notes, where the first is twice as long as the second.
This is also sometimes called triplet swing. You'll often find it in blues and jazz.

</Box>

**Replicate**

```javascript
setcpm(60);
note("c!2 [eb,<g a bb a>]").sound("piano");
```

<Box>

Try switching between `!`, `*` and `@`

What's the difference?

</Box>

## Examples

**Classy Bassline**

```javascript
note("<[c2 c3]*4 [bb1 bb2]*4 [f2 f3]*4 [eb2 eb3]*4>")
  .sound("gm_synth_bass_1")
  .lpf(800); // <-- we'll learn about this soon
```

**Classy Melody**

```javascript
n(\
```

**Classy Drums**

```javascript
sound("bd*4, [~ <sd cp>]*2, [~ hh]*4").bank("RolandTR909");
```

**If there just was a way to play all the above at the same time.......**

<Box>

You can use `$:` 😙

</Box>

## Playing multiple patterns

If you want to play multiple patterns at the same time, make sure to write `$:` before each:

```javascript
$: note("<[c2 c3]*4 [bb1 bb2]*4 [f2 f3]*4 [eb2 eb3]*4>")
  .sound("gm_synth_bass_1").lpf(800)

$: n(\
```

<Box>

Try changing `$` to `_$` to mute a part!

</Box>

---

---

## title: First Effects

# First Effects

We have sounds, we have notes, now let's look at effects!

## Some basic effects

**low-pass filter**

```javascript
note("<[c2 c3]*4 [bb1 bb2]*4 [f2 f3]*4 [eb2 eb3]*4>")
  .sound("sawtooth")
  .lpf(800);
```

<Box>

lpf = **l**ow **p**ass **f**ilter

- Change lpf to 200. Notice how it gets muffled. Think of it as standing in front of the club with the door closed 🚪.
- Now let's open the door... change it to 5000. Notice how it gets brighter ✨🪩

</Box>

**pattern the filter**

```javascript
note("<[c2 c3]*4 [bb1 bb2]*4 [f2 f3]*4 [eb2 eb3]*4>")
  .sound("sawtooth")
  .lpf("200 1000 200 1000");
```

<Box>

- Try adding more values
- Notice how the pattern in lpf does not change the overall rhythm

We will learn how to automate with waves later...

</Box>

**vowel**

```javascript
note("<[c3,g3,e4] [bb2,f3,d4] [a2,f3,c4] [bb2,g3,eb4]>")
  .sound("sawtooth")
  .vowel("<a e i o>");
```

**gain**

```javascript
$: sound("hh*16").gain("[.25 1]*4");

$: sound("bd*4,[~ sd:1]*2");
```

<Box>

Rhythm is all about dynamics!

- Remove `.gain(...)` and notice how flat it sounds.
- Bring it back by undoing (ctrl+z)

</Box>

Let's combine all of the above into a little tune:

```javascript
$: sound("hh*8").gain("[.25 1]*4");

$: sound("bd*4,[~ sd:1]*2");

$: note("<[c2 c3]*4 [bb1 bb2]*4 [f2 f3]*4 [eb2 eb3]*4>")
  .sound("sawtooth")
  .lpf("200 1000 200 1000");

$: note("<[c3,g3,e4] [bb2,f3,d4] [a2,f3,c4] [bb2,g3,eb4]>")
  .sound("sawtooth")
  .vowel("<a e i o>");
```

**shape the sound with an adsr envelope**

```javascript
note("c3 bb2 f3 eb3")
  .sound("sawtooth")
  .lpf(600)
  .attack(0.1)
  .decay(0.1)
  .sustain(0.25)
  .release(0.2);
```

<Box>

Try to find out what the numbers do.. Compare the following

- attack: `.5` vs `0`
- decay: `.5` vs `0`
- sustain: `1` vs `.25` vs `0`
- release: `0` vs `.5` vs `1`

Can you guess what they do?

</Box>

<QA q="Click to see solution" client:visible>

- attack: time it takes to fade in
- decay: time it takes to fade to sustain
- sustain: level after decay
- release: time it takes to fade out after note is finished

![ADSR](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/ADSR_parameter.svg/1920px-ADSR_parameter.svg.png)

</QA>

**adsr short notation**

```javascript
note("c3 bb2 f3 eb3").sound("sawtooth").lpf(600).adsr(".1:.1:.5:.2");
```

**delay**

```javascript
$: note("[~ [<[d3,a3,f4]!2 [d3,bb3,g4]!2> ~]]*2")
  .sound("gm_electric_guitar_muted")
  .delay(0.5);

$: sound("bd rim").bank("RolandTR707").delay(".5");
```

<Box>

Try some `delay` values between 0 and 1. Btw, `.5` is short for `0.5`

What happens if you use `.delay(".8:.125")` ? Can you guess what the second number does?

What happens if you use `.delay(".8:.06:.8")` ? Can you guess what the third number does?

</Box>

<QA q="Click to see solution" client:visible>

`delay("a:b:c")`:

- a: delay volume
- b: delay time
- c: feedback (smaller number = quicker fade)

</QA>

**room aka reverb**

```javascript
n("<4 [3@3 4] [<2 0> ~@16] ~>")
  .scale("D4:minor")
  .sound("gm_accordion:2")
  .room(2);
```

<Box>

Try different values!

Add a delay too!

</Box>

**little dub tune**

```javascript
$: note("[~ [<[d3,a3,f4]!2 [d3,bb3,g4]!2> ~]]*2")
  .sound("gm_electric_guitar_muted")
  .delay(0.5);

$: sound("bd rim").bank("RolandTR707").delay(0.5);

$: n("<4 [3@3 4] [<2 0> ~@16] ~>")
  .scale("D4:minor")
  .sound("gm_accordion:2")
  .room(2)
  .gain(0.5);
```

Let's add a bass to make this complete:

```javascript
$: note("[~ [<[d3,a3,f4]!2 [d3,bb3,g4]!2> ~]]*2")
  .sound("gm_electric_guitar_muted")
  .delay(0.5);

$: sound("bd rim").bank("RolandTR707").delay(0.5);

$: n("<4 [3@3 4] [<2 0> ~@16] ~>")
  .scale("D4:minor")
  .sound("gm_accordion:2")
  .room(2)
  .gain(0.4);

$: n("[0 [~ 0] 4 [3 2] [0 ~] [0 ~] <0 2> ~]/2")
  .scale("D2:minor")
  .sound("sawtooth,triangle")
  .lpf(800);
```

<Box>

Try adding `.hush()` at the end of one of the patterns in the stack...

</Box>

**pan**

```javascript
sound("numbers:1 numbers:2 numbers:3 numbers:4").pan("0 0.3 .6 1");
```

**speed**

```javascript
sound("bd rim [~ bd] rim").speed("<1 2 -1 -2>").room(0.2);
```

**fast and slow**

We can use `fast` and `slow` to change the tempo of a pattern outside of Mini-Notation:

```javascript
sound("bd*4,~ rim ~ cp").slow(2);
```

<Box>

Change the `slow` value. Try replacing it with `fast`.

What happens if you use a pattern like `.fast("<1 [2 4]>")`?

</Box>

By the way, inside Mini-Notation, `fast` is `*` and `slow` is `/`.

```javascript
sound("[bd*4,~ rim ~ cp]*<1 [2 4]>");
```

## modulation with signals

Instead of changing values stepwise, we can also control them with signals:

```javascript
sound("hh*16").gain(sine);
```

<Box>

The basic waveforms for signals are `sine`, `saw`, `square`, `tri` 🌊

Try also random signals `rand` and `perlin`!

The gain is visualized as transparency in the pianoroll.

</Box>

**setting a range**

By default, waves oscillate between 0 to 1. We can change that with `range`:

```javascript
sound("hh*16").lpf(saw.range(500, 2000));
```

<Box>

What happens if you flip the range values?

</Box>

We can change the modulation speed with slow / fast:

```javascript
note("<[c2 c3]*4 [bb1 bb2]*4 [f2 f3]*4 [eb2 eb3]*4>")
  .sound("sawtooth")
  .lpf(sine.range(100, 2000).slow(4));
```

<Box>

The whole modulation will now take 8 cycles to repeat.

</Box>

---

---

## title: Pattern Effects

# Pattern Effects

Up until now, most of the functions we've seen are what other music programs are typically capable of: sequencing sounds, playing notes, controlling effects.

In this chapter, we are going to look at functions that are more unique to tidal.

**reverse patterns with rev**

```javascript
n("0 1 [4 3] 2 0 2 [~ 3] 4").sound("jazz").rev();
```

**play pattern left and modify it right with jux**

```javascript
n("0 1 [4 3] 2 0 2 [~ 3] 4").sound("jazz").jux(rev);
```

This is the same as:

```javascript
$: n("0 1 [4 3] 2 0 2 [~ 3] 4").sound("jazz").pan(0);
$: n("0 1 [4 3] 2 0 2 [~ 3] 4").sound("jazz").pan(1).rev();
```

Let's visualize what happens here:

```javascript
$: n("0 1 [4 3] 2 0 2 [~ 3] 4").sound("jazz").pan(0).color("cyan");
$: n("0 1 [4 3] 2 0 2 [~ 3] 4").sound("jazz").pan(1).color("magenta").rev();
```

<Box>

Try commenting out one of the two by adding `//` before a line

</Box>

**multiple tempos**

```javascript
note("c2, eb3 g3 [bb3 c4]").sound("piano").slow("0.5,1,1.5");
```

This is like doing

```javascript
$: note("c2, eb3 g3 [bb3 c4]").s("piano").slow(0.5).color("cyan");
$: note("c2, eb3 g3 [bb3 c4]").s("piano").slow(1).color("magenta");
$: note("c2, eb3 g3 [bb3 c4]").s("piano").slow(1.5).color("yellow");
```

<Box>

Try commenting out one or more by adding `//` before a line

</Box>

**add**

```javascript
setcpm(60);
note("c2 [eb3,g3] ".add("<0 <1 -1>>"))
  .color("<cyan <magenta yellow>>")
  .adsr("[.1 0]:.2:[1 0]")
  .sound("gm_acoustic_bass")
  .room(0.5);
```

<Box>

If you add a number to a note, the note will be treated as if it was a number

</Box>

We can add as often as we like:

```javascript
setcpm(60);
note("c2 [eb3,g3]".add("<0 <1 -1>>").add("0,7"))
  .color("<cyan <magenta yellow>>")
  .adsr("[.1 0]:.2:[1 0]")
  .sound("gm_acoustic_bass")
  .room(0.5);
```

**add with scale**

```javascript
n("0 [2 4] <3 5> [~ <4 1>]".add("<0 [0,2,4]>"))
  .scale("C5:minor")
  .release(0.5)
  .sound("gm_xylophone")
  .room(0.5);
```

**time to stack**

```javascript
$: n("0 [2 4] <3 5> [~ <4 1>]".add("<0 [0,2,4]>"))
  .scale("C5:minor")
  .sound("gm_xylophone")
  .room(0.4)
  .delay(0.125);
$: note("c2 [eb3,g3]".add("<0 <1 -1>>"))
  .adsr("[.1 0]:.2:[1 0]")
  .sound("gm_acoustic_bass")
  .room(0.5);
$: n("0 1 [2 3] 2").sound("jazz").jux(rev);
```

**ply**

```javascript
sound("hh hh, bd rim [~ cp] rim").bank("RolandTR707").ply(2);
```

this is like writing:

```javascript
sound("hh*2 hh*2, bd*2 rim*2 [~ cp*2] rim*2").bank("RolandTR707");
```

<Box>

Try patterning the `ply` function, for example using `"<1 2 1 3>"`

</Box>

**off**

```javascript
n(
  "0 [4 <3 2>] <2 3> [~ 1]".off(1 / 16, (x) => x.add(4)),
  //.off(1/8, x=>x.add(7))
)
  .scale("<C5:minor Db5:mixolydian>/2")
  .s("triangle")
  .room(0.5)
  .dec(0.1);
```

<Box>

In the notation `.off(1/16, x=>x.add(4))`, says:

- take the original pattern named as `x`
- modify `x` with `.add(4)`, and
- play it offset to the original pattern by `1/16` of a cycle.

</Box>

off is also useful for modifying other sounds, and can even be nested:

```javascript
s("bd sd [rim bd] sd,[~ hh]*4")
  .bank("CasioRZ1")
  .off(2 / 16, (x) =>
    x
      .speed(1.5)
      .gain(0.25)
      .off(3 / 16, (y) => y.vowel("<a e i o>*8")),
  );
```

| name | description                    | example                                                  |
| ---- | ------------------------------ | -------------------------------------------------------- |
| rev  | reverse                        | `n("0 2 4 6 ~ 7 9 5").scale("C:minor").rev()`            |
| jux  | split left/right, modify right | `n("0 2 4 6 ~ 7 9 5").scale("C:minor").jux(rev)`         |
| add  | add numbers / notes            | `n("0 2 4 6 ~ 7 9 5").add("<0 1 2 1>").scale("C:minor")` |
| ply  | speed up each event n times    | `s("bd sd [~ bd] sd").ply("<1 2 3>")`                    |
| off  | copy, shift time & modify      | `s("bd sd [~ bd] sd, hh*8").off(1/16, x=>x.speed(2))`    |

---

---

## title: Samples

# Samples

Samples are the most common way to make sound with tidal and strudel.
A sample is a (commonly short) piece of audio that is used as a basis for sound generation, undergoing various transformations.
Music that is based on samples can be thought of as a collage of sound. [Read more about Sampling](<https://en.wikipedia.org/wiki/Sampling_(music)>)

Strudel allows loading samples in the form of audio files of various formats (wav, mp3, ogg) from any publicly available URL.

# Default Samples

By default, strudel comes with a built-in "sample map", providing a solid base to play with.

```javascript
s("bd sd [~ bd] sd,hh*16, misc");
```

Here, we are using the `s` function to play back different default samples (`bd`, `sd`, `hh` and `misc`) to get a drum beat.

For drum sounds, strudel uses the comprehensive [tidal-drum-machines](https://github.com/ritchse/tidal-drum-machines) library, with the following naming convention:

| Drum                 | Abbreviation |
| -------------------- | ------------ |
| Bass drum, Kick drum | bd           |
| Snare drum           | sd           |
| Rimshot              | rim          |
| Clap                 | cp           |
| Closed hi-hat        | hh           |
| Open hi-hat          | oh           |
| Crash                | cr           |
| Ride                 | rd           |
| High tom             | ht           |
| Medium tom           | mt           |
| Low tom              | lt           |

<img src="/img/drumset.png" />

<a class="text-right text-xs" href="https://de.wikipedia.org/wiki/Schlagzeug#/media/Datei:Drum_set.svg" target="_blank">
  original von Pbroks13
</a>

More percussive sounds:

| Source                              | Abbreviation |
| ----------------------------------- | ------------ |
| Shakers (and maracas, cabasas, etc) | sh           |
| Cowbell                             | cb           |
| Tambourine                          | tb           |
| Other percussions                   | perc         |
| Miscellaneous samples               | misc         |
| Effects                             | fx           |

Furthermore, strudel also loads instrument samples from [VCSL](https://github.com/sgossner/VCSL) by default.

Available sample names:

```
agogo(5) anvil(9) balafon(6) balafon_hard(6) balafon_soft(6) ballwhistle(2) bassdrum1(8) bassdrum2(30) belltree(6) bongo(28) brakedrum(17) cabasa(6) cajon(18) casio(3) clap(10) clash(10) clash2(5) clave(6) clavisynth(19) conga(34) cowbell(13) crow(4) dantranh(17) dantranh_tremolo(16) dantranh_vibrato(16) darbuka(20) didgeridoo(12) east(9) fingercymbal(1) flexatone(8) fmpiano(22) folkharp(29) framedrum(18) glockenspiel(7) gong(7) gong2(6) guiro(5) handbells(3) handchimes(19) harmonica(9) harmonica_soft(10) harmonica_vib(10) harp(23) hihat(15) insect(3) jazz(8) kalimba(11) kalimba2(25) kalimba3(22) kalimba4(22) kalimba5(14) kawai(37) marimba(10) marktrees(6) metal(10) num(21) numbers(9) ocarina(11) ocarina_small(10) ocarina_small_stacc(13) ocarina_vib(10) oceandrum(3) organ_4inch(27) organ_8inch(27) organ_full(27) piano(29) piano1(22) pipeorgan_loud(21) pipeorgan_loud_pedal(11) pipeorgan_quiet(21) pipeorgan_quiet_pedal(11) psaltery_bow(11) psaltery_pluck(11) psaltery_spiccato(11) ratchet(8) recorder_alto_stacc(12) recorder_alto_sus(12) recorder_alto_vib(12) recorder_bass_stacc(15) recorder_bass_sus(12) recorder_bass_vib(14) recorder_soprano_stacc(12) recorder_soprano_sus(13) recorder_tenor_stacc(12) recorder_tenor_sus(13) recorder_tenor_vib(14) sax(23) sax_stacc(23) sax_vib(19) saxello(8) saxello_stacc(8) saxello_vib(8) shaker_large(6) shaker_small(16) siren(5) slapstick(5) sleighbells(6) slitdrum(6) snare_hi(8) snare_low(20) snare_modern(72) snare_rim(4) space(18) steinway(42) strumstick(19) super64(13) super64_acc(13) super64_vib(13) sus_cymbal(25) sus_cymbal2(23) tambourine(7) tambourine2(7) timpani(30) timpani_roll(10) timpani2(204) tom_mallet(8) tom_rim(6) tom_stick(8) tom2_mallet(8) tom2_rim(6) tom2_stick(8) trainwhistle(6) triangles(37) tubularbells(9) tubularbells2(11) vibraphone(11) vibraphone_bowed(6) vibraphone_soft(11) vibraslap(4) wind(10) wineglass(4) wineglass_slow(4) woodblock(10) xylophone_hard_ff(8) xylophone_hard_pp(8) xylophone_medium_ff(8) xylophone_medium_pp(8) xylophone_soft_ff(8) xylophone_soft_pp(8)
```

You can also create custom aliases for existing sounds using the `soundAlias` function:

```javascript
soundAlias("RolandTR808_bd", "kick");
s("kick");
```

Note that only the sample maps (mapping names to URLs) are loaded initially, while the audio samples themselves are not loaded until they are actually played.
This behaviour of loading things only when they are needed is also called `lazy loading`.
While it saves resources, it can also lead to sounds not being audible the first time they are triggered, because the sound is still loading.
[This might be fixed in the future](https://codeberg.org/uzu/strudel/issues/187)

# Sound Banks

If we open the `sounds` tab and then `drum-machines`, we can see that the drum samples are all prefixed with drum machine names:

```
9000_bd(1) 9000_cb(2) 9000_cr(2) 9000_hh(1) 9000_ht(2) 9000_lt(2) 9000_mt(1) 9000_oh(1) 9000_perc(3) 9000_rd(2) 9000_rim(1) 9000_sd(1) 9000_tb(1) ace_bd(3) ace_hh(1) ace_ht(1) ace_lt(1) ace_oh(1) ace_perc(6) ace_sd(3) ajkpercusyn_bd(1) ajkpercusyn_cb(2) ajkpercusyn_ht(1) ajkpercusyn_sd(1) akailinn_bd(1) akailinn_cb(1) akailinn_cp(1) akailinn_cr(1) akailinn_hh(1) akailinn_ht(1) akailinn_lt(1) akailinn_mt(1) akailinn_oh(1) akailinn_rd(1) akailinn_sd(1) akailinn_sh(1) akailinn_tb(1) akaimpc60_bd(2) akaimpc60_cp(1) akaimpc60_cr(1) akaimpc60_hh(1) akaimpc60_ht(1) akaimpc60_lt(1) akaimpc60_misc(2) akaimpc60_mt(1) akaimpc60_oh(1) akaimpc60_perc(5) akaimpc60_rd(1) akaimpc60_rim(1) akaimpc60_sd(3) akaixr10_bd(10) akaixr10_cb(1) akaixr10_cp(1) akaixr10_cr(3) akaixr10_hh(2) akaixr10_ht(1) akaixr10_lt(2) akaixr10_misc(4) akaixr10_mt(2) akaixr10_oh(1) akaixr10_perc(15) akaixr10_rd(1) akaixr10_rim(2) akaixr10_sd(10) akaixr10_sh(1) akaixr10_tb(1) alesishr16_bd(1) alesishr16_cp(1) alesishr16_hh(1) alesishr16_ht(1) alesishr16_lt(1) alesishr16_oh(1) alesishr16_perc(8) alesishr16_rim(1) alesishr16_sd(1) alesishr16_sh(3) alesissr16_bd(13) alesissr16_cb(1) alesissr16_cp(1) alesissr16_cr(2) alesissr16_hh(3) alesissr16_misc(3) alesissr16_oh(4) alesissr16_perc(7) alesissr16_rd(3) alesissr16_rim(1) alesissr16_sd(12) alesissr16_sh(1) alesissr16_tb(1) bd(8) bossdr110_bd(1) bossdr110_cp(1) bossdr110_cr(1) bossdr110_hh(1) bossdr110_oh(1) bossdr110_rd(1) bossdr110_sd(1) bossdr220_bd(1) bossdr220_cp(1) bossdr220_cr(1) bossdr220_hh(1) bossdr220_ht(1) bossdr220_lt(1) bossdr220_mt(1) bossdr220_oh(1) bossdr220_perc(1) bossdr220_rd(1) bossdr220_sd(1) bossdr55_bd(2) bossdr55_hh(2) bossdr55_rim(1) bossdr55_sd(8) bossdr550_bd(5) bossdr550_cb(2) bossdr550_cp(1) bossdr550_cr(1) bossdr550_hh(2) bossdr550_ht(3) bossdr550_lt(3) bossdr550_misc(3) bossdr550_mt(2) bossdr550_oh(2) bossdr550_perc(11) bossdr550_rd(2) bossdr550_rim(1) bossdr550_sd(6) bossdr550_sh(2) bossdr550_tb(1) brk(1) casiorz1_bd(1) casiorz1_cb(1) casiorz1_cp(1) casiorz1_cr(1) casiorz1_hh(1) casiorz1_ht(1) casiorz1_lt(1) casiorz1_mt(1) casiorz1_rd(2) casiorz1_rim(1) casiorz1_sd(1) casiosk1_bd(1) casiosk1_hh(1) casiosk1_ht(1) casiosk1_mt(1) casiosk1_oh(1) casiosk1_sd(1) casiovl1_bd(1) casiovl1_hh(1) casiovl1_sd(1) cb(1) circuitsdrumtracks_bd(1) circuitsdrumtracks_cb(1) circuitsdrumtracks_cp(1) circuitsdrumtracks_cr(1) circuitsdrumtracks_hh(1) circuitsdrumtracks_ht(1) circuitsdrumtracks_oh(1) circuitsdrumtracks_rd(1) circuitsdrumtracks_rim(1) circuitsdrumtracks_sd(1) circuitsdrumtracks_sh(1) circuitsdrumtracks_tb(1) circuitstom_bd(1) circuitstom_cp(1) circuitstom_cr(1) circuitstom_hh(1) circuitstom_ht(2) circuitstom_oh(1) circuitstom_sd(1) compurhythm1000_bd(1) compurhythm1000_cb(1) compurhythm1000_cp(1) compurhythm1000_cr(1) compurhythm1000_hh(1) compurhythm1000_ht(1) compurhythm1000_lt(1) compurhythm1000_mt(1) compurhythm1000_oh(1) compurhythm1000_perc(3) compurhythm1000_rd(1) compurhythm1000_rim(1) compurhythm1000_sd(1) compurhythm78_bd(1) compurhythm78_cb(1) compurhythm78_hh(2) compurhythm78_misc(4) compurhythm78_oh(2) compurhythm78_perc(8) compurhythm78_sd(1) compurhythm78_tb(1) compurhythm8000_bd(1) compurhythm8000_cb(1) compurhythm8000_cp(1) compurhythm8000_cr(1) compurhythm8000_hh(1) compurhythm8000_ht(1) compurhythm8000_lt(1) compurhythm8000_mt(1) compurhythm8000_oh(1) compurhythm8000_perc(2) compurhythm8000_rim(1) compurhythm8000_sd(1) concertmatemg1_bd(3) concertmatemg1_sd(2) cp(2) cr(2) d110_bd(1) d110_cb(2) d110_cr(1) d110_hh(1) d110_lt(1) d110_oh(2) d110_perc(3) d110_rd(1) d110_rim(1) d110_sd(3) d110_sh(1) d110_tb(1) d70_bd(4) d70_cb(1) d70_cp(1) d70_cr(1) d70_hh(1) d70_lt(1) d70_mt(1) d70_oh(1) d70_perc(1) d70_rd(1) d70_rim(1) d70_sd(5) d70_sh(1) ddm110_bd(1) ddm110_cp(1) ddm110_cr(1) ddm110_hh(1) ddm110_ht(2) ddm110_lt(2) ddm110_oh(1) ddm110_rim(1) ddm110_sd(1) ddr30_bd(8) ddr30_ht(4) ddr30_lt(4) ddr30_sd(8) dmx_bd(3) dmx_cp(1) dmx_cr(1) dmx_hh(1) dmx_ht(1) dmx_lt(1) dmx_mt(1) dmx_oh(1) dmx_rd(1) dmx_rim(1) dmx_sd(3) dmx_sh(1) dmx_tb(1) doepferms404_bd(2) doepferms404_hh(1) doepferms404_lt(1) doepferms404_oh(1) doepferms404_sd(1) dpm48_bd(3) dpm48_cp(1) dpm48_cr(1) dpm48_hh(2) dpm48_ht(1) dpm48_lt(2) dpm48_mt(1) dpm48_oh(1) dpm48_perc(2) dpm48_rd(1) dpm48_rim(1) dpm48_sd(2) dpm48_sh(2) dr110_bd(1) dr110_cp(1) dr110_cr(1) dr110_hh(1) dr110_oh(1) dr110_rd(1) dr110_sd(1) dr220_bd(1) dr220_cp(1) dr220_cr(1) dr220_hh(1) dr220_ht(1) dr220_lt(1) dr220_mt(1) dr220_oh(1) dr220_perc(1) dr220_rd(1) dr220_sd(1) dr55_bd(2) dr55_hh(2) dr55_rim(1) dr55_sd(8) dr550_bd(5) dr550_cb(2) dr550_cp(1) dr550_cr(1) dr550_hh(2) dr550_ht(3) dr550_lt(3) dr550_misc(3) dr550_mt(2) dr550_oh(2) dr550_perc(11) dr550_rd(2) dr550_rim(1) dr550_sd(6) dr550_sh(2) dr550_tb(1) drumulator_bd(1) drumulator_cb(1) drumulator_cp(1) drumulator_cr(1) drumulator_hh(1) drumulator_ht(1) drumulator_lt(1) drumulator_mt(1) drumulator_oh(1) drumulator_perc(1) drumulator_rim(1) drumulator_sd(1) emudrumulator_bd(1) emudrumulator_cb(1) emudrumulator_cp(1) emudrumulator_cr(1) emudrumulator_hh(1) emudrumulator_ht(1) emudrumulator_lt(1) emudrumulator_mt(1) emudrumulator_oh(1) emudrumulator_perc(1) emudrumulator_rim(1) emudrumulator_sd(1) emumodular_bd(2) emumodular_misc(1) emumodular_perc(2) emusp12_bd(14) emusp12_cb(1) emusp12_cp(1) emusp12_cr(1) emusp12_hh(2) emusp12_ht(6) emusp12_lt(6) emusp12_misc(7) emusp12_mt(4) emusp12_oh(1) emusp12_perc(1) emusp12_rd(1) emusp12_rim(2) emusp12_sd(21) hh(5) hr16_bd(1) hr16_cp(1) hr16_hh(1) hr16_ht(1) hr16_lt(1) hr16_oh(1) hr16_perc(8) hr16_rim(1) hr16_sd(1) hr16_sh(3) ht(1) jd990_bd(10) jd990_cb(1) jd990_cp(1) jd990_cr(1) jd990_hh(4) jd990_ht(1) jd990_lt(5) jd990_misc(12) jd990_mt(2) jd990_oh(2) jd990_perc(6) jd990_rd(1) jd990_sd(15) jd990_tb(1) korgddm110_bd(1) korgddm110_cp(1) korgddm110_cr(1) korgddm110_hh(1) korgddm110_ht(2) korgddm110_lt(2) korgddm110_oh(1) korgddm110_rim(1) korgddm110_sd(1) korgkpr77_bd(1) korgkpr77_cp(1) korgkpr77_hh(1) korgkpr77_oh(1) korgkpr77_sd(1) korgkr55_bd(1) korgkr55_cb(1) korgkr55_cr(1) korgkr55_hh(1) korgkr55_ht(1) korgkr55_oh(1) korgkr55_perc(2) korgkr55_rim(1) korgkr55_sd(1) korgkrz_bd(1) korgkrz_cr(1) korgkrz_fx(2) korgkrz_hh(1) korgkrz_ht(1) korgkrz_lt(1) korgkrz_misc(1) korgkrz_oh(1) korgkrz_rd(1) korgkrz_sd(2) korgm1_bd(3) korgm1_cb(1) korgm1_cp(1) korgm1_cr(1) korgm1_hh(2) korgm1_ht(2) korgm1_misc(16) korgm1_mt(1) korgm1_oh(2) korgm1_perc(7) korgm1_rd(1) korgm1_rim(1) korgm1_sd(4) korgm1_sh(1) korgm1_tb(1) korgminipops_bd(7) korgminipops_hh(4) korgminipops_misc(4) korgminipops_oh(4) korgminipops_sd(13) korgpoly800_bd(4) korgt3_bd(5) korgt3_cp(1) korgt3_hh(2) korgt3_misc(4) korgt3_oh(2) korgt3_perc(4) korgt3_rim(1) korgt3_sd(5) korgt3_sh(3) kpr77_bd(1) kpr77_cp(1) kpr77_hh(1) kpr77_oh(1) kpr77_sd(1) kr55_bd(1) kr55_cb(1) kr55_cr(1) kr55_hh(1) kr55_ht(1) kr55_oh(1) kr55_perc(2) kr55_rim(1) kr55_sd(1) krz_bd(1) krz_cr(1) krz_fx(2) krz_hh(1) krz_ht(1) krz_lt(1) krz_misc(1) krz_oh(1) krz_rd(1) krz_sd(2) linn_bd(1) linn_cb(1) linn_cp(1) linn_cr(1) linn_hh(1) linn_ht(1) linn_lt(1) linn_mt(1) linn_oh(1) linn_rd(1) linn_sd(1) linn_sh(1) linn_tb(1) linn9000_bd(1) linn9000_cb(2) linn9000_cr(2) linn9000_hh(1) linn9000_ht(2) linn9000_lt(2) linn9000_mt(1) linn9000_oh(1) linn9000_perc(3) linn9000_rd(2) linn9000_rim(1) linn9000_sd(1) linn9000_tb(1) linndrum_bd(1) linndrum_cb(1) linndrum_cp(1) linndrum_cr(1) linndrum_hh(3) linndrum_ht(2) linndrum_lt(2) linndrum_mt(1) linndrum_oh(1) linndrum_perc(6) linndrum_rd(1) linndrum_rim(3) linndrum_sd(3) linndrum_sh(1) linndrum_tb(1) linnlm1_bd(4) linnlm1_cb(1) linnlm1_cp(1) linnlm1_hh(1) linnlm1_ht(1) linnlm1_lt(1) linnlm1_oh(1) linnlm1_perc(3) linnlm1_rim(1) linnlm1_sd(1) linnlm1_sh(1) linnlm1_tb(1) linnlm2_bd(4) linnlm2_cb(1) linnlm2_cp(1) linnlm2_cr(1) linnlm2_hh(2) linnlm2_ht(1) linnlm2_lt(1) linnlm2_mt(1) linnlm2_oh(2) linnlm2_rd(1) linnlm2_rim(2) linnlm2_sd(4) linnlm2_sh(1) linnlm2_tb(1) lm1_bd(4) lm1_cb(1) lm1_cp(1) lm1_hh(1) lm1_ht(1) lm1_lt(1) lm1_oh(1) lm1_perc(3) lm1_rim(1) lm1_sd(1) lm1_sh(1) lm1_tb(1) lm2_bd(4) lm2_cb(1) lm2_cp(1) lm2_cr(1) lm2_hh(2) lm2_ht(1) lm2_lt(1) lm2_mt(1) lm2_oh(2) lm2_rd(1) lm2_rim(2) lm2_sd(4) lm2_sh(1) lm2_tb(1) lm8953_bd(3) lm8953_cr(1) lm8953_hh(2) lm8953_ht(2) lm8953_lt(2) lm8953_mt(2) lm8953_oh(1) lm8953_rd(1) lm8953_rim(2) lm8953_sd(5) lm8953_tb(1) lt(1) m1_bd(3) m1_cb(1) m1_cp(1) m1_cr(1) m1_hh(2) m1_ht(2) m1_misc(16) m1_mt(1) m1_oh(2) m1_perc(7) m1_rd(1) m1_rim(1) m1_sd(4) m1_sh(1) m1_tb(1) mc202_bd(5) mc202_ht(3) mc202_perc(1) mc303_bd(16) mc303_cb(2) mc303_cp(8) mc303_fx(2) mc303_hh(6) mc303_ht(5) mc303_lt(5) mc303_misc(8) mc303_mt(6) mc303_oh(5) mc303_perc(39) mc303_rd(2) mc303_rim(6) mc303_sd(26) mc303_sh(7) mc303_tb(5) mfb512_bd(1) mfb512_cp(1) mfb512_cr(1) mfb512_hh(1) mfb512_ht(1) mfb512_lt(1) mfb512_mt(1) mfb512_oh(1) mfb512_sd(1) microrhythmer12_bd(1) microrhythmer12_hh(1) microrhythmer12_oh(1) microrhythmer12_sd(1) minipops_bd(7) minipops_hh(4) minipops_misc(4) minipops_oh(4) minipops_sd(13) misc(5) moogconcertmatemg1_bd(3) moogconcertmatemg1_sd(2) mpc1000_bd(5) mpc1000_cp(1) mpc1000_hh(4) mpc1000_oh(1) mpc1000_perc(1) mpc1000_sd(4) mpc1000_sh(1) mpc60_bd(2) mpc60_cp(1) mpc60_cr(1) mpc60_hh(1) mpc60_ht(1) mpc60_lt(1) mpc60_misc(2) mpc60_mt(1) mpc60_oh(1) mpc60_perc(5) mpc60_rd(1) mpc60_rim(1) mpc60_sd(3) mridangam_ardha(20) mridangam_chaapu(13) mridangam_dhi(7) mridangam_dhin(8) mridangam_dhum(7) mridangam_gumki(14) mridangam_ka(12) mridangam_ki(7) mridangam_na(12) mridangam_nam(8) mridangam_ta(9) mridangam_tha(7) mridangam_thom(7) ms404_bd(2) ms404_hh(1) ms404_lt(1) ms404_oh(1) ms404_sd(1) mt(1) mt32_bd(1) mt32_cb(1) mt32_cp(1) mt32_cr(1) mt32_hh(1) mt32_ht(1) mt32_lt(1) mt32_mt(1) mt32_oh(2) mt32_perc(13) mt32_rd(1) mt32_rim(1) mt32_sd(2) mt32_sh(2) mt32_tb(1) oberheimdmx_(3) oberheimdmx_bd(3) oberheimdmx_cp(1) oberheimdmx_cr(1) oberheimdmx_hh(1) oberheimdmx_ht(1) oberheimdmx_lt(1) oberheimdmx_mt(1) oberheimdmx_oh(1) oberheimdmx_rd(1) oberheimdmx_rim(1) oberheimdmx_sd(3) oberheimdmx_sh(1) oberheimdmx_tb(1) oh(4) percysyn_bd(1) percysyn_cb(2) percysyn_ht(1) percysyn_sd(1) polaris_bd(4) polaris_misc(4) polaris_sd(4) poly800_bd(4) r8_bd(7) r8_cb(1) r8_cp(1) r8_cr(1) r8_hh(2) r8_ht(4) r8_lt(4) r8_mt(4) r8_oh(1) r8_perc(8) r8_rd(2) r8_rim(2) r8_sd(12) r8_sh(2) r8_tb(1) r88_bd(1) r88_cr(1) r88_hh(1) r88_oh(1) r88_sd(2) rd(1) rhodespolaris_bd(4) rhodespolaris_misc(4) rhodespolaris_sd(4) rhythmace_bd(3) rhythmace_hh(1) rhythmace_ht(1) rhythmace_lt(1) rhythmace_oh(1) rhythmace_perc(6) rhythmace_sd(3) rim(2) rm50_bd(103) rm50_cb(6) rm50_cp(2) rm50_cr(22) rm50_hh(18) rm50_ht(25) rm50_lt(49) rm50_misc(28) rm50_mt(34) rm50_oh(12) rm50_perc(56) rm50_rd(13) rm50_sd(108) rm50_sh(6) rm50_tb(3) rolandcompurhythm1000_bd(1) rolandcompurhythm1000_cb(1) rolandcompurhythm1000_cp(1) rolandcompurhythm1000_cr(1) rolandcompurhythm1000_hh(1) rolandcompurhythm1000_ht(1) rolandcompurhythm1000_lt(1) rolandcompurhythm1000_mt(1) rolandcompurhythm1000_oh(1) rolandcompurhythm1000_perc(3) rolandcompurhythm1000_rd(1) rolandcompurhythm1000_rim(1) rolandcompurhythm1000_sd(1) rolandcompurhythm78_bd(1) rolandcompurhythm78_cb(1) rolandcompurhythm78_hh(2) rolandcompurhythm78_misc(4) rolandcompurhythm78_oh(2) rolandcompurhythm78_perc(8) rolandcompurhythm78_sd(1) rolandcompurhythm78_tb(1) rolandcompurhythm8000_bd(1) rolandcompurhythm8000_cb(1) rolandcompurhythm8000_cp(1) rolandcompurhythm8000_cr(1) rolandcompurhythm8000_hh(1) rolandcompurhythm8000_ht(1) rolandcompurhythm8000_lt(1) rolandcompurhythm8000_mt(1) rolandcompurhythm8000_oh(1) rolandcompurhythm8000_perc(2) rolandcompurhythm8000_rim(1) rolandcompurhythm8000_sd(1) rolandd110_bd(1) rolandd110_cb(2) rolandd110_cr(1) rolandd110_hh(1) rolandd110_lt(1) rolandd110_oh(2) rolandd110_perc(3) rolandd110_rd(1) rolandd110_rim(1) rolandd110_sd(3) rolandd110_sh(1) rolandd110_tb(1) rolandd70_bd(4) rolandd70_cb(1) rolandd70_cp(1) rolandd70_cr(1) rolandd70_hh(1) rolandd70_lt(1) rolandd70_mt(1) rolandd70_oh(1) rolandd70_perc(1) rolandd70_rd(1) rolandd70_rim(1) rolandd70_sd(5) rolandd70_sh(1) rolandddr30_bd(8) rolandddr30_ht(4) rolandddr30_lt(4) rolandddr30_sd(8) rolandjd990_bd(10) rolandjd990_cb(1) rolandjd990_cp(1) rolandjd990_cr(1) rolandjd990_hh(4) rolandjd990_ht(1) rolandjd990_lt(5) rolandjd990_misc(12) rolandjd990_mt(2) rolandjd990_oh(2) rolandjd990_perc(6) rolandjd990_rd(1) rolandjd990_sd(15) rolandjd990_tb(1) rolandmc202_bd(5) rolandmc202_ht(3) rolandmc202_perc(1) rolandmc303_bd(16) rolandmc303_cb(2) rolandmc303_cp(8) rolandmc303_fx(2) rolandmc303_hh(6) rolandmc303_ht(5) rolandmc303_lt(5) rolandmc303_misc(8) rolandmc303_mt(6) rolandmc303_oh(5) rolandmc303_perc(39) rolandmc303_rd(2) rolandmc303_rim(6) rolandmc303_sd(26) rolandmc303_sh(7) rolandmc303_tb(5) rolandmt32_bd(1) rolandmt32_cb(1) rolandmt32_cp(1) rolandmt32_cr(1) rolandmt32_hh(1) rolandmt32_ht(1) rolandmt32_lt(1) rolandmt32_mt(1) rolandmt32_oh(2) rolandmt32_perc(13) rolandmt32_rd(1) rolandmt32_rim(1) rolandmt32_sd(2) rolandmt32_sh(2) rolandmt32_tb(1) rolandr8_bd(7) rolandr8_cb(1) rolandr8_cp(1) rolandr8_cr(1) rolandr8_hh(2) rolandr8_ht(4) rolandr8_lt(4) rolandr8_mt(4) rolandr8_oh(1) rolandr8_perc(8) rolandr8_rd(2) rolandr8_rim(2) rolandr8_sd(12) rolandr8_sh(2) rolandr8_tb(1) rolands50_bd(4) rolands50_cb(1) rolands50_cp(1) rolands50_cr(2) rolands50_ht(1) rolands50_lt(2) rolands50_misc(6) rolands50_mt(1) rolands50_oh(1) rolands50_perc(14) rolands50_rd(1) rolands50_sd(3) rolands50_sh(4) rolands50_tb(2) rolandsh09_bd(43) rolandsystem100_bd(15) rolandsystem100_hh(2) rolandsystem100_misc(2) rolandsystem100_oh(3) rolandsystem100_perc(19) rolandsystem100_sd(21) rolandtr505_bd(1) rolandtr505_cb(2) rolandtr505_cp(1) rolandtr505_cr(1) rolandtr505_hh(1) rolandtr505_ht(1) rolandtr505_lt(1) rolandtr505_mt(1) rolandtr505_oh(1) rolandtr505_perc(3) rolandtr505_rd(1) rolandtr505_rim(1) rolandtr505_sd(1) rolandtr606_bd(1) rolandtr606_cr(1) rolandtr606_hh(1) rolandtr606_ht(1) rolandtr606_lt(1) rolandtr606_oh(1) rolandtr606_sd(1) rolandtr626_bd(2) rolandtr626_cb(1) rolandtr626_cp(1) rolandtr626_cr(2) rolandtr626_hh(1) rolandtr626_ht(2) rolandtr626_lt(2) rolandtr626_mt(2) rolandtr626_oh(1) rolandtr626_perc(8) rolandtr626_rd(2) rolandtr626_rim(1) rolandtr626_sd(3) rolandtr626_sh(1) rolandtr626_tb(1) rolandtr707_bd(2) rolandtr707_cb(1) rolandtr707_cp(1) rolandtr707_cr(1) rolandtr707_hh(1) rolandtr707_ht(1) rolandtr707_lt(1) rolandtr707_mt(1) rolandtr707_oh(1) rolandtr707_rim(1) rolandtr707_sd(2) rolandtr707_tb(1) rolandtr727_perc(10) rolandtr727_sh(2) rolandtr808_bd(25) rolandtr808_cb(2) rolandtr808_cp(5) rolandtr808_cr(25) rolandtr808_hh(1) rolandtr808_ht(5) rolandtr808_lt(5) rolandtr808_mt(5) rolandtr808_oh(5) rolandtr808_perc(16) rolandtr808_rim(1) rolandtr808_sd(25) rolandtr808_sh(2) rolandtr909_bd(4) rolandtr909_cp(5) rolandtr909_cr(5) rolandtr909_hh(4) rolandtr909_ht(9) rolandtr909_lt(9) rolandtr909_mt(9) rolandtr909_oh(5) rolandtr909_rd(5) rolandtr909_rim(3) rolandtr909_sd(16) rx21_bd(1) rx21_cp(1) rx21_cr(1) rx21_hh(1) rx21_ht(1) rx21_lt(1) rx21_mt(1) rx21_oh(1) rx21_sd(1) rx5_bd(2) rx5_cb(1) rx5_fx(1) rx5_hh(1) rx5_lt(1) rx5_oh(1) rx5_rim(1) rx5_sd(3) rx5_sh(1) rx5_tb(1) ry30_bd(13) ry30_cb(2) ry30_cp(1) ry30_cr(2) ry30_hh(4) ry30_ht(3) ry30_lt(3) ry30_misc(8) ry30_mt(2) ry30_oh(4) ry30_perc(13) ry30_rd(3) ry30_rim(2) ry30_sd(21) ry30_sh(2) ry30_tb(1) rz1_bd(1) rz1_cb(1) rz1_cp(1) rz1_cr(1) rz1_hh(1) rz1_ht(1) rz1_lt(1) rz1_mt(1) rz1_rd(2) rz1_rim(1) rz1_sd(1) s50_bd(4) s50_cb(1) s50_cp(1) s50_cr(2) s50_ht(1) s50_lt(2) s50_misc(6) s50_mt(1) s50_oh(1) s50_perc(14) s50_rd(1) s50_sd(3) s50_sh(4) s50_tb(2) sakatadpm48_bd(3) sakatadpm48_cp(1) sakatadpm48_cr(1) sakatadpm48_hh(2) sakatadpm48_ht(1) sakatadpm48_lt(2) sakatadpm48_mt(1) sakatadpm48_oh(1) sakatadpm48_perc(2) sakatadpm48_rd(1) sakatadpm48_rim(1) sakatadpm48_sd(2) sakatadpm48_sh(2) sd(5) sds400_ht(3) sds400_lt(6) sds400_mt(8) sds400_sd(3) sds5_bd(12) sds5_hh(5) sds5_ht(3) sds5_lt(8) sds5_mt(6) sds5_oh(2) sds5_rim(7) sds5_sd(21) sequentialcircuitsdrumtracks_bd(1) sequentialcircuitsdrumtracks_cb(1) sequentialcircuitsdrumtracks_cp(1) sequentialcircuitsdrumtracks_cr(1) sequentialcircuitsdrumtracks_hh(1) sequentialcircuitsdrumtracks_ht(1) sequentialcircuitsdrumtracks_oh(1) sequentialcircuitsdrumtracks_rd(1) sequentialcircuitsdrumtracks_rim(1) sequentialcircuitsdrumtracks_sd(1) sequentialcircuitsdrumtracks_sh(1) sequentialcircuitsdrumtracks_tb(1) sequentialcircuitstom_bd(1) sequentialcircuitstom_cp(1) sequentialcircuitstom_cr(1) sequentialcircuitstom_hh(1) sequentialcircuitstom_ht(2) sequentialcircuitstom_oh(1) sequentialcircuitstom_sd(1) sergemodular_bd(1) sergemodular_misc(1) sergemodular_perc(5) sh(1) sh09_bd(43) simmonssds400_ht(3) simmonssds400_lt(6) simmonssds400_mt(8) simmonssds400_sd(3) simmonssds5_bd(12) simmonssds5_hh(5) simmonssds5_ht(3) simmonssds5_lt(8) simmonssds5_mt(6) simmonssds5_oh(2) simmonssds5_rim(7) simmonssds5_sd(21) sk1_bd(1) sk1_hh(1) sk1_ht(1) sk1_mt(1) sk1_oh(1) sk1_sd(1) soundmastersr88_bd(1) soundmastersr88_cr(1) soundmastersr88_hh(1) soundmastersr88_oh(1) soundmastersr88_sd(2) sp12_bd(14) sp12_cb(1) sp12_cp(1) sp12_cr(1) sp12_hh(2) sp12_ht(6) sp12_lt(6) sp12_misc(7) sp12_mt(4) sp12_oh(1) sp12_perc(1) sp12_rd(1) sp12_rim(2) sp12_sd(21) spacedrum_bd(11) spacedrum_cb(1) spacedrum_hh(6) spacedrum_ht(7) spacedrum_lt(2) spacedrum_misc(2) spacedrum_mt(2) spacedrum_oh(3) spacedrum_perc(2) spacedrum_rim(1) spacedrum_sd(3) sr16_bd(13) sr16_cb(1) sr16_cp(1) sr16_cr(2) sr16_hh(3) sr16_misc(3) sr16_oh(4) sr16_perc(7) sr16_rd(3) sr16_rim(1) sr16_sd(12) sr16_sh(1) sr16_tb(1) system100_bd(15) system100_hh(2) system100_misc(2) system100_oh(3) system100_perc(19) system100_sd(21) t3_bd(5) t3_cp(1) t3_hh(2) t3_misc(4) t3_oh(2) t3_perc(4) t3_rim(1) t3_sd(5) t3_sh(3) tb(1) tg33_bd(4) tg33_cb(3) tg33_cp(1) tg33_cr(3) tg33_fx(1) tg33_ht(2) tg33_lt(2) tg33_misc(10) tg33_mt(2) tg33_oh(1) tg33_perc(12) tg33_rd(2) tg33_rim(1) tg33_sd(5) tg33_sh(1) tg33_tb(1) tr505_bd(1) tr505_cb(2) tr505_cp(1) tr505_cr(1) tr505_hh(1) tr505_ht(1) tr505_lt(1) tr505_mt(1) tr505_oh(1) tr505_perc(3) tr505_rd(1) tr505_rim(1) tr505_sd(1) tr606_bd(1) tr606_cr(1) tr606_hh(1) tr606_ht(1) tr606_lt(1) tr606_oh(1) tr606_sd(1) tr626_bd(2) tr626_cb(1) tr626_cp(1) tr626_cr(2) tr626_hh(1) tr626_ht(2) tr626_lt(2) tr626_mt(2) tr626_oh(1) tr626_perc(8) tr626_rd(2) tr626_rim(1) tr626_sd(3) tr626_sh(1) tr626_tb(1) tr707_bd(2) tr707_cb(1) tr707_cp(1) tr707_cr(1) tr707_hh(1) tr707_ht(1) tr707_lt(1) tr707_mt(1) tr707_oh(1) tr707_rim(1) tr707_sd(2) tr707_tb(1) tr727_perc(10) tr727_sh(2) tr808_bd(25) tr808_cb(2) tr808_cp(5) tr808_cr(25) tr808_hh(1) tr808_ht(5) tr808_lt(5) tr808_mt(5) tr808_oh(5) tr808_perc(16) tr808_rim(1) tr808_sd(25) tr808_sh(2) tr909_bd(4) tr909_cp(5) tr909_cr(5) tr909_hh(4) tr909_ht(9) tr909_lt(9) tr909_mt(9) tr909_oh(5) tr909_rd(5) tr909_rim(3) tr909_sd(16) univoxmicrorhythmer12_bd(1) univoxmicrorhythmer12_hh(1) univoxmicrorhythmer12_oh(1) univoxmicrorhythmer12_sd(1) viscospacedrum_bd(11) viscospacedrum_cb(1) viscospacedrum_hh(6) viscospacedrum_ht(7) viscospacedrum_lt(2) viscospacedrum_misc(2) viscospacedrum_mt(2) viscospacedrum_oh(3) viscospacedrum_perc(2) viscospacedrum_rim(1) viscospacedrum_sd(3) vl1_bd(1) vl1_hh(1) vl1_sd(1) xdrumlm8953_bd(3) xdrumlm8953_cr(1) xdrumlm8953_hh(2) xdrumlm8953_ht(2) xdrumlm8953_lt(2) xdrumlm8953_mt(2) xdrumlm8953_oh(1) xdrumlm8953_rd(1) xdrumlm8953_rim(2) xdrumlm8953_sd(5) xdrumlm8953_tb(1) xr10_bd(10) xr10_cb(1) xr10_cp(1) xr10_cr(3) xr10_hh(2) xr10_ht(1) xr10_lt(2) xr10_misc(4) xr10_mt(2) xr10_oh(1) xr10_perc(15) xr10_rd(1) xr10_rim(2) xr10_sd(10) xr10_sh(1) xr10_tb(1) yamaharm50_bd(103) yamaharm50_cb(6) yamaharm50_cp(2) yamaharm50_cr(22) yamaharm50_hh(18) yamaharm50_ht(25) yamaharm50_lt(49) yamaharm50_misc(28) yamaharm50_mt(34) yamaharm50_oh(12) yamaharm50_perc(56) yamaharm50_rd(13) yamaharm50_sd(108) yamaharm50_sh(6) yamaharm50_tb(3) yamaharx21_bd(1) yamaharx21_cp(1) yamaharx21_cr(1) yamaharx21_hh(1) yamaharx21_ht(1) yamaharx21_lt(1) yamaharx21_mt(1) yamaharx21_oh(1) yamaharx21_sd(1) yamaharx5_bd(2) yamaharx5_cb(1) yamaharx5_fx(1) yamaharx5_hh(1) yamaharx5_lt(1) yamaharx5_oh(1) yamaharx5_rim(1) yamaharx5_sd(3) yamaharx5_sh(1) yamaharx5_tb(1) yamahary30_bd(13) yamahary30_cb(2) yamahary30_cp(1) yamahary30_cr(2) yamahary30_hh(4) yamahary30_ht(3) yamahary30_lt(3) yamahary30_misc(8) yamahary30_mt(2) yamahary30_oh(4) yamahary30_perc(13) yamahary30_rd(3) yamahary30_rim(2) yamahary30_sd(21) yamahary30_sh(2) yamahary30_tb(1) yamahatg33_bd(4) yamahatg33_cb(3) yamahatg33_cp(1) yamahatg33_cr(3) yamahatg33_fx(1) yamahatg33_ht(2) yamahatg33_lt(2) yamahatg33_misc(10) yamahatg33_mt(2) yamahatg33_oh(1) yamahatg33_perc(12) yamahatg33_rd(2) yamahatg33_rim(1) yamahatg33_sd(5) yamahatg33_sh(1) yamahatg33_tb(1)
```

We _could_ use them like this:

```javascript
s("RolandTR808_bd RolandTR808_sd,RolandTR808_hh*16");
```

... but thats obviously a bit much to write. Using the `bank` function, we can shorten this to:

```javascript
s("bd sd,hh*16").bank("RolandTR808");
```

You could even pattern the bank to switch between different drum machines:

```javascript
s("bd sd,hh*16").bank("<RolandTR808 RolandTR909>");
```

Behind the scenes, `bank` will just prepend the drum machine name to the sample name with `_` to get the full name.
This of course only works because the name after `_` (`bd`, `sd` etc..) is standardized.
Also note that some banks won't have samples for all sounds!

# Selecting Sounds

If we open the `sounds` tab again, followed by tab `drum machines`, there is also a number behind each name, indicating how many individual samples are available.
For example `RolandTR909_hh(4)` means there are 4 samples of a TR909 hihat available.
By default, `s` will play the first sample, but we can select the other ones using `n`, starting from 0:

```javascript
s("hh*8").bank("RolandTR909").n("0 1 2 3");
```

Numbers that are too high will just wrap around to the beginning

```javascript
s("hh*8").bank("RolandTR909").n("0 1 2 3 4 5 6 7");
```

Here, 0-3 will play the same sounds as 4-7, because `RolandTR909_hh` only has 4 sounds.

Selecting sounds also works inside the mini notation, using "`:`" like this:

```javascript
s("bd*4,hh:0 hh:1 hh:2 hh:3 hh:4 hh:5 hh:6 hh:7").bank("RolandTR909");
```

# Loading Custom Samples

You can load a non-standard sample map using the `samples` function.

## Loading samples from file URLs

In this example we assign names `bassdrum`, `hihat` and `snaredrum` to specific audio files on a server:

```javascript
samples(
  {
    bassdrum: "bd/BT0AADA.wav",
    hihat: "hh27/000_hh27closedhh.wav",
    snaredrum: ["sd/rytm-01-classic.wav", "sd/rytm-00-hard.wav"],
  },
  "https://raw.githubusercontent.com/tidalcycles/Dirt-Samples/master/",
);

s("bassdrum snaredrum:0 bassdrum snaredrum:1, hihat*16");
```

You can freely choose any combination of letters for each sample name. It is even possible to override the default sounds.
The names you pick will be made available in the `s` function.
Make sure that the URL and each sample path form a correct URL!

In the above example, `bassdrum` will load:

```
https://raw.githubusercontent.com/tidalcycles/Dirt-Samples/master/bd/BT0AADA.wav
|----------------------base path --------------------------------|--sample path-|
```

Note that we can either load a single file, like for `bassdrum` and `hihat`, or a list of files like for `snaredrum`!
As soon as you run the code, your chosen sample names will be listed in `sounds` -> `user`.

## Loading Samples from a strudel.json file

The above way to load samples might be tedious to write out / copy paste each time you write a new pattern.
To avoid that, you can simply pass a URL to a `strudel.json` file somewhere on the internet:

```javascript
samples(
  "https://raw.githubusercontent.com/tidalcycles/Dirt-Samples/master/strudel.json",
);
s("bd sd bd sd,hh*16");
```

The file is expected to define a sample map using JSON, in the same format as described above.
Additionally, the base path can be defined with the `_base` key.
The last section could be written as:

```json
{
  "_base": "https://raw.githubusercontent.com/tidalcycles/Dirt-Samples/master/",
  "bassdrum": "bd/BT0AADA.wav",
  "snaredrum": "sd/rytm-01-classic.wav",
  "hihat": "hh27/000_hh27closedhh.wav"
}
```

Please note that browsers will often cache `strudel.json` on first load, and keep using the cached
version even if the orginal has been updated. If this bites you (for example while developing a new
sample pack), you can force the browser to download a new copy by i.e. changing capitalization of one
character in the URL, or adding a URL attribute, such as:

```javascript
samples(
  "https://raw.githubusercontent.com/tidalcycles/Dirt-Samples/master/strudel.json?version=2",
);
```

that gets ignored by GitHub (but changes the URL, forcing the browser to reload every time we increase
the version number).

It is also possible, of course, to just remove it from cache (deleting cache in browser Privacy settings,
or from the dev console if you're technically minded, or by using a cache deleting extension).

## Generating strudel.json

You can use [@strudel/sampler](https://www.npmjs.com/package/@strudel/sampler) to generate a strudel.json file for you, by running:

```sh
npx --yes @strudel/sampler --json > strudel.json
```

See other uses of strudel/sampler further below, under "From Disk via @strudel/sampler".

## Github Shortcut

Because loading samples from github is common, there is a shortcut:

```javascript
samples("github:tidalcycles/dirt-samples");
s("bd sd bd sd,hh*16");
```

The format is `samples('github:<user>/<repo>/<branch>')`. If you omit `branch` (like above), the `main` branch will be used.
It assumes a `strudel.json` file to be present at the root of the repository:

```
https://raw.githubusercontent.com/<user>/<repo>/<branch>/strudel.json
```

## From Disk via "Import Sounds Folder"

If you don't want to upload your samples to the internet, you can also load them from your local disk.
Go to the `sounds` tab in the REPL and open the `import-sounds` tab below the search bar.
Press the "import sounds folder" button and select a folder that contains audio files.
The folder you select can also contain subfolders with audio files.
Example:

```
└─ samples
   ├─ swoop
   │  ├─ swoopshort.wav
   │  ├─ swooplong.wav
   │  └─ swooptight.wav
   └─ smash
      ├─ smashhigh.wav
      ├─ smashlow.wav
      └─ smashmiddle.wav
```

In the above example the folder `samples` contains 2 subfolders `swoop` and `smash`, which contain audio files.
If you select that `samples` folder, the `user` tab (next to the `import-sounds` tab) will then contain 2 new sounds: `swoop(3) smash(3)`
The individual samples can the be played normally like `s("swoop:0 swoop:1 smash:2")`.
The samples within each sound use zero-based indexing in alphabetical order.

## From Disk via @strudel/sampler

Instead of loading your samples into your browser with the "import sounds folder" button, you can also serve the samples from a local file server.
The easiest way to do this is using [@strudel/sampler](https://www.npmjs.com/package/@strudel/sampler):

```sh
cd samples
npx @strudel/sampler
```

Then you can load it via:

```javascript
samples("http://localhost:5432/");

n("<0 1 2>").s("swoop smash");
```

The handy thing about `@strudel/sampler` is that it auto-generates the `strudel.json` file based on your folder structure.
You can see what it generated by going to `http://localhost:5432` with your browser.

Note: You need [NodeJS](https://nodejs.org/) installed on your system for this to work.

## Specifying Pitch

To make sure your samples are in tune when playing them with `note`, you can specify a base pitch like this:

```javascript
samples(
  {
    gtr: "gtr/0001_cleanC.wav",
    moog: { g3: "moog/005_Mighty%20Moog%20G3.wav" },
  },
  "github:tidalcycles/dirt-samples",
);
note("g3 [bb3 c4] <g4 f4 eb4 f3>@2").s("gtr,moog").clip(1).gain(0.5);
```

We can also declare different samples for different regions of the keyboard:

```javascript
setcpm(60);
samples(
  {
    moog: {
      g2: "moog/004_Mighty%20Moog%20G2.wav",
      g3: "moog/005_Mighty%20Moog%20G3.wav",
      g4: "moog/006_Mighty%20Moog%20G4.wav",
    },
  },
  "github:tidalcycles/dirt-samples",
);

note("g2!2 <bb2 c3>!2, <c4@3 [<eb4 bb3> g4 f4]>").s("moog").clip(1).gain(0.5);
```

The sampler will always pick the closest matching sample for the current note!

Note that this notation for pitched sounds also works inside a `strudel.json` file.

## Shabda

If you don't want to select samples by hand, there is also the wonderful tool called [shabda](https://shabda.ndre.gr/).
With it, you can enter any sample name(s) to query from [freesound.org](https://freesound.org/). Example:

```javascript
samples("shabda:bass:4,hihat:4,rimshot:2");

$: n("0 1 2 3 0 1 2 3").s("bass");
$: n("0 1*2 2 3*2").s("hihat").clip(1);
$: n("~ 0 ~ 1 ~ 0 0 1").s("rimshot");
```

You can also generate artificial voice samples with any text, in multiple languages.
Note that the language code and the gender parameters are optional and default to `en-GB` and `f`

```javascript
samples("shabda/speech:the_drum,forever");
samples("shabda/speech/fr-FR/m:magnifique");

$: s("the_drum*2").chop(16).speed(rand.range(0.85, 1.1));
$: s("forever magnifique").slow(4).late(0.125);
```

# Sampler Effects

Sampler effects are functions that can be used to change the behaviour of sample playback.

### begin

> **Note:** Metadata for `Pattern.begin` not found.

### end

The same as .begin, but cuts off the end off each sample.

**Parameters:**

- **length** _(number|Pattern)_: 1 = whole sample, .5 = half sample, .25 = quarter sample etc..

```javascript
s("bd*2,oh*4").end("<.1 .2 .5 1>").fast(2);
```

### loop

Loops the sample.
Note that the tempo of the loop is not synced with the cycle tempo.
To change the loop region, use loopBegin / loopEnd.

**Parameters:**

- **on** _(number|Pattern)_: If 1, the sample is looped

```javascript
s("casio").loop(1);
```

### loopBegin

Begin to loop at a specific point in the sample (inbetween `begin` and `end`).
Note that the loop point must be inbetween `begin` and `end`, and before `loopEnd`!
Note: Samples starting with wt\_ will automatically loop! (wt = wavetable)

**Parameters:**

- **time** _(number|Pattern)_: between 0 and 1, where 1 is the length of the sample

```javascript
s("space").loop(1).loopBegin("<0 .125 .25>")._scope();
```

### loopEnd

End the looping section at a specific point in the sample (inbetween `begin` and `end`).
Note that the loop point must be inbetween `begin` and `end`, and after `loopBegin`!

**Parameters:**

- **time** _(number|Pattern)_: between 0 and 1, where 1 is the length of the sample

```javascript
s("space").loop(1).loopEnd("<1 .75 .5 .25>")._scope();
```

### cut

In the style of classic drum-machines, `cut` will stop a playing sample as soon as another samples with in same cutgroup is to be played. An example would be an open hi-hat followed by a closed one, essentially muting the open.

**Parameters:**

- **group** _(number|Pattern)_: cut group number

```javascript
s("[oh hh]*4").cut(1);
```

### clip

Multiplies the duration with the given number. Also cuts samples off at the end if they exceed the duration.

**Parameters:**

- **factor** _(number|Pattern)_: <blockquote>
  = 0

</blockquote>

```javascript
note("c a f e").s("piano").clip("<.5 1 2>");
```

### loopAt

Makes the sample fit the given number of cycles by changing the speed.

```javascript
samples({
  rhodes: "https://cdn.freesound.org/previews/132/132051_316502-lq.mp3",
});
s("rhodes").loopAt(2);
```

### fit

Makes the sample fit its event duration. Good for rhythmical loops like drum breaks.
Similar to `loopAt`.

```javascript
samples({
  rhodes: "https://cdn.freesound.org/previews/132/132051_316502-lq.mp3",
});
s("rhodes/2").fit();
```

### chop

Cuts each sample into the given number of parts, allowing you to explore a technique known as 'granular synthesis'.
It turns a pattern of samples into a pattern of parts of samples.

```javascript
samples({
  rhodes: "https://cdn.freesound.org/previews/132/132051_316502-lq.mp3",
});
s("rhodes")
  .chop(4)
  .rev() // reverse order of chops
  .loopAt(2); // fit sample into 2 cycles
```

### striate

Cuts each sample into the given number of parts, triggering progressive portions of each sample at each loop.

```javascript
s("numbers:0 numbers:1 numbers:2").striate(6).slow(3);
```

### slice

Chops samples into the given number of slices, triggering those slices with a given pattern of slice numbers.
Instead of a number, it also accepts a list of numbers from 0 to 1 to slice at specific points.

```javascript
samples("github:tidalcycles/dirt-samples");
s("breaks165").slice(8, "0 1 <2 2*2> 3 [4 0] 5 6 7".every(3, rev)).slow(0.75);
```

```javascript
samples("github:tidalcycles/dirt-samples");
s("breaks125").fit().slice([0, 0.25, 0.5, 0.75], "0 1 1 <2 3>");
```

### splice

Works the same as slice, but changes the playback speed of each slice to match the duration of its step.

```javascript
samples("github:tidalcycles/dirt-samples");
s("breaks165").splice(8, "0 1 [2 3 0]@2 3 0@2 7");
```

### scrub

Allows you to scrub an audio file like a tape loop by passing values that represents the position in the audio file
in the optional array syntax ex: "0.5:2", the second value controls the speed of playback

```javascript
samples("github:switchangel/pad");
s("swpad:0").scrub("{0.1!2 .25@3 0.7!2 <0.8:1.5>}%8");
```

```javascript
samples("github:yaxu/clean-breaks/main");
s("amen/4").fit().scrub("{0@3 0@2 4@3}%8".div(16));
```

### speed

Changes the speed of sample playback, i.e. a cheap way of changing pitch.

**Parameters:**

- **speed** _(number|Pattern)_: inf to inf, negative numbers play the sample backwards.

```javascript
s("bd*6").speed("1 2 4 1 -2 -4");
```

```javascript
speed("1 1.5*2 [2 1.1]").s("piano").clip(1);
```

---

---

## title: Synths

# Synths

In addition to the sampling engine, strudel comes with a synthesizer to create sounds on the fly.

## Basic Waveforms

The basic waveforms are `sine`, `sawtooth`, `square` and `triangle`, which can be selected via `sound` (or `s`):

```javascript
note("c2 <eb2 <g2 g1>>".fast(2))
  .sound("<sawtooth square triangle sine>")
  ._scope();
```

If you don't set a `sound` but a `note` the default value for `sound` is `triangle`!

## Noise

You can also use noise as a source by setting the waveform to: `white`, `pink` or `brown`. These are different
flavours of noise, here written from hard to soft.

```javascript
sound("<white pink brown>")._scope();
```

Here's a more musical example of how to use noise for hihats:

```javascript
sound("bd*2,<white pink brown>*8").decay(0.04).sustain(0)._scope();
```

Some amount of pink noise can also be added to any oscillator by using the `noise` paremeter:

```javascript
note("c3").noise("<0.1 0.25 0.5>")._scope();
```

You can also use the `crackle` type to play some subtle noise crackles. You can control noise amount by using the `density` parameter:

```javascript
s("crackle*4").density("<0.01 0.04 0.2 0.5>".slow(2))._scope();
```

### Additive Synthesis

Periodic waveforms are composed of several [harmonics](https://en.wikipedia.org/wiki/Harmonic) above a fundamental frequency, lying at integer multiples. These overtones combine to give a sound its unique timbral quality.

For the basic waveforms, we offer you control over these harmonics with the `partials` and `phases` functions.

#### Partials

`partials` refers to the magnitude of each harmonic relative to the fundamental frequency. They can thus be used to spectrally filter these waveforms and tame some of their harshness:

```javascript
note("c2 <eb2 <g2 g1>>".fast(2))
  .sound("sawtooth")
  .partials([1, 1, "<1 0>", "<1 0>", "<1 0>", "<1 0>", "<1 0>"])
  ._scope();
```

`partials` can also be used to construct _new_ waveforms not present in our basic set with the 'user' sound source:

```javascript
note("c2 <eb2 <g2 g1>>".fast(2))
  .sound("user")
  .partials([1, 0, 0.3, 0, 0.1, 0, 0, 0.3])
  ._scope();
```

We may algorithmically construct lists of magnitudes with Javascript code like:

```javascript
const numHarmonics = 22;
note("c2 <eb2 <g2 g1>>".fast(2))
  .sound("saw")
  .partials(new Array(numHarmonics).fill(1))
  ._scope();
```

which acts as a spectral filter. Or:

```javascript
note("c2 <eb2 <g2 g1>>")
  .fast(2)
  .sound("user")
  .partials(
    new Array(50).fill(0).map((_, idx) => (-1) ** (idx + 1) / (idx + 1)),
  )
  ._scope();
```

which recovers a familiar waveform.

`partials` is also compatible with pattern functions designed to produce lists, like `randL` or `binaryL`:

```javascript
note("c2 <eb2 <g2 g1>>").fast(2).sound("user").partials(randL(10))._scope();
```

and with lists _of_ patterns:

```javascript
note("c2 <eb2 <g2 g1>>".fast(4))
  .sound("user")
  .partials([1, 0, "0 1", "0 1 0.3", rand])
  ._scope();
```

Note that the first value in the `partials` array controls the magnitude of the fundamental harmonic rather than the DC offset, which is fixed at 0.

#### Phases

Earlier, we mentioned that periodic waveforms can be broken into a set of harmonics above a fundamental frequency. Each harmonic has two defining properties: its magnitude (how loud it is) and its phase, which determines where in its cycle that sine wave starts when the waveform is built.

These phases too can be declared in Strudel and can give your sounds interesting depth.

```javascript
s("saw")
  .seg(16)
  .n(irand(12))
  .scale("F1:minor")
  .penv(48)
  .panchor(0)
  .pdec(0.05)
  .delay(0.25)
  .room(0.25)
  .compressor(-20)
  .vib(0.3)
  .partials(randL(200))
  .phases(randL(200));
```

## Vibrato

### vib

Applies a vibrato to the frequency of the oscillator.

**Parameters:**

- **frequency** _(number|Pattern)_: of the vibrato in hertz

```javascript
note("a e").vib("<.5 1 2 4 8 16>")._scope();
```

```javascript
// change the modulation depth with ":"
note("a e").vib("<.5 1 2 4 8 16>:12")._scope();
```

### vibmod

Sets the vibrato depth in semitones. Only has an effect if `vibrato` | `vib` | `v` is is also set

**Parameters:**

- **depth** _(number|Pattern)_: of vibrato (in semitones)

```javascript
note("a e").vib(4).vibmod("<.25 .5 1 2 12>")._scope();
```

```javascript
// change the vibrato frequency with ":"
note("a e").vibmod("<.25 .5 1 2 12>:8")._scope();
```

## FM Synthesis

FM Synthesis is a technique that changes the frequency of a basic waveform rapidly to alter the timbre.

You can use fm with any of the above waveforms, although the below examples all use the default triangle wave.

### fm

> **Note:** Metadata for `fm` not found.

### fmh

Sets the Frequency Modulation Harmonicity Ratio.
Controls the timbre of the sound.
Whole numbers and simple ratios sound more natural,
while decimal numbers and complex ratios sound metallic.

A number may be added afterwards to control the harmonicity of
any of the 8 individual FMs (e.g. `fmh2`)

**Parameters:**

- **harmonicity** _(number|Pattern)_

```javascript
note("c e g b g e").fm(4).fmh("<1 2 1.5 1.61>")._scope();
```

### fmattack

Attack time for the FM envelope: time it takes to reach maximum modulation

A number may be added afterwards to control the attack of the envelope of
any of the 8 individual FMs (e.g. `fmatt5`)

**Parameters:**

- **time** _(number|Pattern)_: attack time

```javascript
note("c e g b g e").fm(4).fmattack("<0 .05 .1 .2>")._scope();
```

### fmdecay

Decay time for the FM envelope: seconds until the sustain level is reached after the attack phase.

A number may be added afterwards to control the decay of the envelope of
any of the 8 individual FMs (e.g. `fmdec6`)

**Parameters:**

- **time** _(number|Pattern)_: decay time

```javascript
note("c e g b g e").fm(4).fmdecay("<.01 .05 .1 .2>").fmsustain(0.4)._scope();
```

### fmsustain

Sustain level for the FM envelope: how much modulation is applied after the decay phase

A number may be added afterwards to control the sustain of the envelope of
any of the 8 individual FMs (e.g. `fmsus7`)

**Parameters:**

- **level** _(number|Pattern)_: sustain level

```javascript
note("c e g b g e").fm(4).fmdecay(0.1).fmsustain("<1 .75 .5 0>")._scope();
```

### fmenv

Ramp type of fm envelope. Exp might be a bit broken..

A number may be added afterwards to control the envelope of
any of the 8 individual FMs (e.g. `fmenv4`)

**Parameters:**

- **type** _(number|Pattern)_: lin | exp

```javascript
note("c e g b g e").fm(4).fmdecay(0.2).fmsustain(0).fmenv("<exp lin>")._scope();
```

## Wavetable Synthesis

Available wavetables:

```
wt_digital(5) wt_digital_bad_day(1) wt_digital_basique(1) wt_digital_crickets(1) wt_digital_curses(1) wt_digital_echoes(1) wt_vgame(11)
```

Any sample preceded by the `wt_` prefix will be loaded as a wavetable. This means that the `loop` argument will be set to `1` by default. You can scan over the wavetable by using `loopBegin` and `loopEnd` as well.

```javascript
samples("bubo:waveforms");
note("<[g3,b3,e4]!2 [a3,c3,e4] [b3,d3,f#4]>")
  .n("<1 2 3 4 5 6 7 8 9 10>/2")
  .room(0.5)
  .size(0.9)
  .s("wt_flute")
  .velocity(0.25)
  .often((n) => n.ply(2))
  .release(0.125)
  .decay("<0.1 0.25 0.3 0.4>")
  .sustain(0)
  .cutoff(2000)
  .cutoff("<1000 2000 4000>")
  .fast(4)
  ._scope();
```

## ZZFX

The "Zuper Zmall Zound Zynth" [ZZFX](https://github.com/KilledByAPixel/ZzFX) is also integrated in strudel.
Developed by [Frank Force](https://frankforce.com/), it is a synth and FX engine originally intended to be used for size coding games.

It has 20 parameters in total, here is a snippet that uses all:

```javascript
note("c2 eb2 f2 g2") // also supports freq
  .s("{z_sawtooth z_tan z_noise z_sine z_square}%4")
  .zrand(0) // randomization
  // zzfx envelope
  .attack(0.001)
  .decay(0.1)
  .sustain(0.8)
  .release(0.1)
  // special zzfx params
  .curve(1) // waveshape 1-3
  .slide(0) // +/- pitch slide
  .deltaSlide(0) // +/- pitch slide (?)
  .noise(0) // make it dirty
  .zmod(0) // fm speed
  .zcrush(0) // bit crush 0 - 1
  .zdelay(0) // simple delay
  .pitchJump(0) // +/- pitch change after pitchJumpTime
  .pitchJumpTime(0) // >0 time after pitchJump is applied
  .lfo(0) // >0 resets slide + pitchJump + sets tremolo speed
  .tremolo(0.5) // 0-1 lfo volume modulation amount
  //.duration(.2) // overwrite strudel event duration
  //.gain(1) // change volume
  ._scope(); // vizualise waveform (not zzfx related)
```

Note that you can also combine zzfx with all the other audio fx (next chapter).

Available synths:

```
brown bytebeat crackle gm_accordion(7) gm_acoustic_bass(4) gm_acoustic_guitar_nylon(9) gm_acoustic_guitar_steel(10) gm_agogo(6) gm_alto_sax(6) gm_applause(15) gm_bagpipe(1) gm_bandoneon(10) gm_banjo(6) gm_baritone_sax(6) gm_bassoon(4) gm_bird_tweet(7) gm_blown_bottle(5) gm_brass_section(5) gm_breath_noise(8) gm_celesta(6) gm_cello(6) gm_choir_aahs(9) gm_church_organ(5) gm_clarinet(6) gm_clavinet(4) gm_contrabass(3) gm_distortion_guitar(7) gm_drawbar_organ(7) gm_dulcimer(5) gm_electric_bass_finger(4) gm_electric_bass_pick(5) gm_electric_guitar_clean(9) gm_electric_guitar_jazz(9) gm_electric_guitar_muted(10) gm_english_horn(4) gm_epiano1(11) gm_epiano2(9) gm_fiddle(9) gm_flute(5) gm_french_horn(5) gm_fretless_bass(2) gm_fx_atmosphere(13) gm_fx_brightness(12) gm_fx_crystal(10) gm_fx_echoes(10) gm_fx_goblins(9) gm_fx_rain(6) gm_fx_sci_fi(9) gm_fx_soundtrack(5) gm_glockenspiel(5) gm_guitar_fret_noise(8) gm_guitar_harmonics(3) gm_gunshot(12) gm_harmonica(6) gm_harpsichord(8) gm_helicopter(16) gm_kalimba(5) gm_koto(9) gm_lead_1_square(3) gm_lead_2_sawtooth(7) gm_lead_3_calliope(7) gm_lead_4_chiff(6) gm_lead_5_charang(10) gm_lead_6_voice(6) gm_lead_7_fifths(5) gm_lead_8_bass_lead(5) gm_marimba(7) gm_melodic_tom(9) gm_music_box(5) gm_muted_trumpet(5) gm_oboe(5) gm_ocarina(4) gm_orchestra_hit(5) gm_orchestral_harp(5) gm_overdriven_guitar(10) gm_pad_bowed(5) gm_pad_choir(6) gm_pad_halo(8) gm_pad_metallic(7) gm_pad_new_age(12) gm_pad_poly(7) gm_pad_sweep(7) gm_pad_warm(7) gm_pan_flute(8) gm_percussive_organ(6) gm_piano(32) gm_piccolo(5) gm_pizzicato_strings(6) gm_recorder(5) gm_reed_organ(8) gm_reverse_cymbal(9) gm_rock_organ(5) gm_seashore(16) gm_shakuhachi(5) gm_shamisen(7) gm_shanai(5) gm_sitar(7) gm_slap_bass_1(4) gm_slap_bass_2(4) gm_soprano_sax(5) gm_steel_drums(6) gm_string_ensemble_1(11) gm_string_ensemble_2(7) gm_synth_bass_1(9) gm_synth_bass_2(7) gm_synth_brass_1(4) gm_synth_brass_2(7) gm_synth_choir(5) gm_synth_drum(7) gm_synth_strings_1(7) gm_synth_strings_2(4) gm_taiko_drum(10) gm_telephone(10) gm_tenor_sax(4) gm_timpani(6) gm_tinkle_bell(1) gm_tremolo_strings(6) gm_trombone(5) gm_trumpet(4) gm_tuba(4) gm_tubular_bells(6) gm_vibraphone(6) gm_viola(5) gm_violin(9) gm_voice_oohs(6) gm_whistle(4) gm_woodblock(9) gm_xylophone(6) pink pulse saw sawtooth sbd sin sine sqr square supersaw tri triangle user white z_noise z_sawtooth z_sine z_square z_tan z_triangle zzfx
```

---

---

## title: Audio effects

# Audio Effects

Whether you're using a synth or a sample, you can apply any of the following built-in audio effects.
As you might suspect, the effects can be chained together, and they accept a pattern string as their argument.

# Signal chain

<img src="/img/strudel-signal-flow.png"></img>

The signal chain in Strudel is as follows:

- An sound-generating event is triggered by a pattern
  - This has a start time and a duration, which is usually
    controlled by the note length and ADSR parameters
  - If we exceed the max polyphony, old sounds begin to die off
  - Muted sounds (one whose `s` value is `-`, `~`, or `_`) are skipped
- A sound is produced (through, say, a sample or an oscillator)
  - This is where detune-based effects (like `detune`, `penv`, etc. occur)
- The following will occur _in order_ and only if they've been called in the pattern. Note that all of these are
  single use effects, meaning that multiple occurrences of them in a pattern will simply override the values
  (e.g. you can't do `s("bd").lpf(100).distort(2).lpf(800)` to lowpass, distort, and then lowpass
  again)
  - Phase vocoder (`stretch`)
  - Gain is applied (`gain`)
    - This is where the main (volume) ADSR happens
  - A lowpass filter (`lpf`)
  - A highpass filter (`hpf`)
  - A bandpass filter (`bandpass`)
  - A vowel filter (`vowel`)
  - Sample rate reduction (`coarse`)
  - Bit crushing (`crush`)
  - Waveshape distortion (`shape`)
  - Normal distortion (`distort`)
  - Tremolo (`tremolo`)
  - Compressor (`compressor`)
  - Panning (`pan`)
  - Phaser (`phaser`)
  - Postgain (`post`)
- The sound is then split into multiple destinations
  - Dry output (amount controlled by `dry` parameter)
  - The sends
    - Analyzers
      - These are used for tooling like `scope` and `spectrum` and their setup usually happens behind the scenes
    - Delay (amount controlled by `delay` parameter)
    - Reverb (amount controlled by `room` parameter)
- The dry output, delay, and reverb are joined into what is called the "orbit" of the pattern (see more in the section below)
  - The `duck` effect affects the volume of all signals in the orbit
  - The orbit is then sent to the mixer

## Orbits

Orbits are the way in which outputs are handled in Strudel. They also prescribe which delay and reverb to associate with the dry signal.
By default, all orbits are mixed down to channels `1` and `2` in stereo, however with the "Multi Channel Orbits" setting
(under Settings at the right) you can use them as individual 2 channel stereo outs (orbit `i` will be mapped to
to channels `2i` and `2i + 1`). You can then use routers like Blackhole 16 to retrieve and record all of the channels in a DAW for later processing.

The default orbit is `1` and it is set with `orbit`. You may send a sound to multiple orbits via mininotation

```javascript
s("white").orbit("2,3,4").gain(0.2);
```

but please be careful as this will create three copies of the sound behind the scenes, meaning that if they are mixed
down to a single output, they will triple the volume. We've reduced the gain here to save your ears.

⚠️ There is only one delay and reverb per orbit, so please be aware that if you attempt to change the parameters on two
patterns pointing to the same orbit, it can lead to unpredictable results. Compare, for example, this pretty pluck
with a large reverb:

```javascript
$: s("triangle*4")
  .decay(0.5)
  .n(irand(12))
  .scale("C minor")
  .room(1)
  .roomsize(10);
```

versus the same pluck with a muted kick drum coming in and overwriting the `roomsize` value:

```javascript
$: s("triangle*4")
  .decay(0.5)
  .n(irand(12))
  .scale("C minor")
  .room(1)
  .roomsize(10);

$: s("bd\*4").room(0.01).roomsize(0.01).postgain(0);
```

This is due to them sharing the same orbit: the default of `1`. It can be corrected simply by updating the orbits to be
distinct:

```javascript
$: s("triangle*4")
  .decay(0.5)
  .n(irand(12))
  .scale("C minor")
  .room(1)
  .roomsize(10)
  .orbit(2);

$: s("bd\*4").room(0.01).roomsize(0.01).postgain(0);
```

## Continuous changes

As all of the above is triggered by a _sound occurring_, it is often the case that parameters may not be
modified continuously in time. For example,

```javascript
s("supersaw").lpf(tri.range(100, 5000).slow(2));
```

Will not produce a continually LFO'd low-pass filter due to the `tri` only being sampled every time the note hits
(in this case the default of once per cycle). You can fake it by introducing more sound-generating events, e.g.:

```javascript
s("supersaw").seg(16).lpf(tri.range(100, 5000).slow(2));
```

Some parameters _do_ induce continuous variations in time, though:

- The ADSR curve (governed by `attack`, `sustain`, `decay`, `release`)
- The pitch envelope curve (governed by `penv` and its associated ADSR)
- The FM curve (`fmenv`)
- The filter envelopes (`lpenv`, `hpenv`, `bpenv`)
- Tremolo (`tremolo`)
- Phaser (`phaser`)
- Vibrato (`vib`)
- Ducking (`duckorbit`)

# Filters

Filters are an essential building block of [subtractive synthesis](https://en.wikipedia.org/wiki/Subtractive_synthesis).
Strudel comes with 3 types of filters:

- low-pass filter: low frequencies may _pass_, high frequencies are cut off
- high-pass filter: high frequencies may _pass_, low frequencies are cut off
- band-pass filters: only a frequency band may _pass_, low and high frequencies around are cut off

Each filter has 2 parameters:

- cutoff: the frequency at which the filter starts to work. e.g. a low-pass filter with a cutoff of 1000Hz allows frequencies below 1000Hz to pass.
- q-value: Controls the resonance of the filter. Higher values sound more aggressive. Also see [Q-Factor](https://en.wikipedia.org/wiki/Q_factor)

## lpf

Applies the cutoff frequency of the <strong>l</strong>ow-<strong>p</strong>ass <strong>f</strong>ilter.

When using mininotation, you can also optionally add the 'lpq' parameter, separated by ':'.

**Parameters:**

- **frequency** _(number|Pattern)_: audible between 0 and 20000

```javascript
s("bd sd [~ bd] sd,hh*6").lpf("<4000 2000 1000 500 200 100>");
```

```javascript
s("bd*16").lpf("1000:0 1000:10 1000:20 1000:30");
```

## lpq

Controls the <strong>l</strong>ow-<strong>p</strong>ass <strong>q</strong>-value.

**Parameters:**

- **q** _(number|Pattern)_: resonance factor between 0 and 50

```javascript
s("bd sd [~ bd] sd,hh*8").lpf(2000).lpq("<0 10 20 30>");
```

## hpf

Applies the cutoff frequency of the <strong>h</strong>igh-<strong>p</strong>ass <strong>f</strong>ilter.

When using mininotation, you can also optionally add the 'hpq' parameter, separated by ':'.

**Parameters:**

- **frequency** _(number|Pattern)_: audible between 0 and 20000

```javascript
s("bd sd [~ bd] sd,hh*8").hpf("<4000 2000 1000 500 200 100>");
```

```javascript
s("bd sd [~ bd] sd,hh*8").hpf("<2000 2000:25>");
```

## hpq

Controls the <strong>h</strong>igh-<strong>p</strong>ass <strong>q</strong>-value.

**Parameters:**

- **q** _(number|Pattern)_: resonance factor between 0 and 50

```javascript
s("bd sd [~ bd] sd,hh*8").hpf(2000).hpq("<0 10 20 30>");
```

## bpf

Sets the center frequency of the <strong>b</strong>and-<strong>p</strong>ass <strong>f</strong>ilter. When using mininotation, you
can also optionally supply the 'bpq' parameter separated by ':'.

**Parameters:**

- **frequency** _(number|Pattern)_: center frequency

```javascript
s("bd sd [~ bd] sd,hh*6").bpf("<1000 2000 4000 8000>");
```

## bpq

Sets the <strong>b</strong>and-<strong>p</strong>ass <strong>q</strong>-factor (resonance).

**Parameters:**

- **q** _(number|Pattern)_: q factor

```javascript
s("bd sd [~ bd] sd").bpf(500).bpq("<0 1 2 3>");
```

## ftype

Sets the filter type. The ladder filter is more aggressive. More types might be added in the future.

**Parameters:**

- **type** _(number|Pattern)_: 12db (0), ladder (1), or 24db (2)

```javascript
note("{f g g c d a a#}%8")
  .s("sawtooth")
  .lpenv(4)
  .lpf(500)
  .ftype("<0 1 2>")
  .lpq(1);
```

```javascript
note("c f g g a c d4")
  .fast(2)
  .sound("sawtooth")
  .lpf(200)
  .fanchor(0)
  .lpenv(3)
  .lpq(1)
  .ftype("<ladder 12db 24db>");
```

## vowel

Formant filter to make things sound like vowels.

**Parameters:**

- **vowel** _(string|Pattern)_: You can use a e i o u ae aa oe ue y uh un en an on, corresponding to [a] [e] [i] [o] [u] [æ] [ɑ] [ø] [y] [ɯ] [ʌ] [œ̃] [ɛ̃] [ɑ̃] [ɔ̃]. Aliases: aa = å = ɑ, oe = ø = ö, y = ı, ae = æ.

```javascript
note("[c2 <eb2 <g2 g1>>]*2").s("sawtooth").vowel("<a e i <o u>>");
```

```javascript
s("bd sd mt ht bd [~ cp] ht lt").vowel("[a|e|i|o|u]");
```

# Amplitude Modulation

Amplitude modulation changes the amplitude (gain) periodically over time.

## am

> **Note:** Metadata for `am` not found.

## tremolosync

Modulate the amplitude of a sound with a continuous waveform

**Parameters:**

- **cycles** _(number|Pattern)_: modulation speed in cycles

```javascript
note("d d d# d".fast(4)).s("supersaw").tremolosync("4").tremoloskew("<1 .5 0>");
```

## tremolodepth

Depth of amplitude modulation

**Parameters:**

- **depth** _(number|Pattern)_

```javascript
note("a1 a1 a#1 a1".fast(4)).s("pulse").tremsync(4).tremolodepth("<1 2 .7>");
```

## tremoloskew

Alter the shape of the modulation waveform

**Parameters:**

- **amount** _(number|Pattern)_: between 0 & 1, the shape of the waveform

```javascript
note("{f a c e}%16").s("sawtooth").tremsync(4).tremoloskew("<.5 0 1>");
```

## tremolophase

Alter the phase of the modulation waveform

**Parameters:**

- **offset** _(number|Pattern)_: the offset in cycles of the modulation

```javascript
note("{f a c e}%16").s("sawtooth").tremsync(4).tremolophase("<0 .25 .66>");
```

## tremoloshape

Shape of amplitude modulation

**Parameters:**

- **shape** _(number|Pattern)_: tri | square | sine | saw | ramp

```javascript
note("{f g c d}%16")
  .tremsync(4)
  .tremoloshape("<sine tri square>")
  .s("sawtooth");
```

# Amplitude Envelope

The amplitude [envelope](<https://en.wikipedia.org/wiki/Envelope_(music)>) controls the dynamic contour of a sound.
Strudel uses ADSR envelopes, which are probably the most common way to describe an envelope:

![ADSR](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/ADSR_parameter.svg/1920px-ADSR_parameter.svg.png)

[image link](https://commons.wikimedia.org/wiki/File:ADSR_parameter.svg)

## attack

Amplitude envelope attack time: Specifies how long it takes for the sound to reach its peak value, relative to the onset.

**Parameters:**

- **attack** _(number|Pattern)_: time in seconds.

```javascript
note("c3 e3 f3 g3").attack("<0 .1 .5>");
```

## decay

Amplitude envelope decay time: the time it takes after the attack time to reach the sustain level.
Note that the decay is only audible if the sustain value is lower than 1.

**Parameters:**

- **time** _(number|Pattern)_: decay time in seconds

```javascript
note("c3 e3 f3 g3").decay("<.1 .2 .3 .4>").sustain(0);
```

## sustain

Amplitude envelope sustain level: The level which is reached after attack / decay, being sustained until the offset.

**Parameters:**

- **gain** _(number|Pattern)_: sustain level between 0 and 1

```javascript
note("c3 e3 f3 g3").decay(0.2).sustain("<0 .1 .4 .6 1>");
```

## release

Amplitude envelope release time: The time it takes after the offset to go from sustain level to zero.

**Parameters:**

- **time** _(number|Pattern)_: release time in seconds

```javascript
note("c3 e3 g3 c4").release("<0 .1 .4 .6 1>/2");
```

## adsr

ADSR envelope: Combination of Attack, Decay, Sustain, and Release.

**Parameters:**

- **time** _(number|Pattern)_: attack time in seconds
- **time** _(number|Pattern)_: decay time in seconds
- **gain** _(number|Pattern)_: sustain level (0 to 1)
- **time** _(number|Pattern)_: release time in seconds

```javascript
note("[c3 bb2 f3 eb3]*2").sound("sawtooth").lpf(600).adsr(".1:.1:.5:.2");
```

# Filter Envelope

Each filter can receive an additional filter envelope controlling the cutoff value dynamically. It uses an ADSR envelope similar to the one used for amplitude. There is an additional parameter to control the depth of the filter modulation: `lpenv`|`hpenv`|`bpenv`. This allows you to play subtle or huge filter modulations just the same by only increasing or decreasing the depth.

```javascript
note("[c eb g <f bb>](3,8,<0 1>)".sub(12))
  .s("<sawtooth>/64")
  .lpf(sine.range(300, 2000).slow(16))
  .lpa(0.005)
  .lpd(perlin.range(0.02, 0.2))
  .lps(perlin.range(0, 0.5).slow(3))
  .lpq(sine.range(2, 10).slow(32))
  .release(0.5)
  .lpenv(perlin.range(1, 8).slow(2))
  .ftype("24db")
  .room(1)
  .juxBy(0.5, rev)
  .sometimes(add(note(12)))
  .stack(s("bd*2").bank("RolandTR909"))
  .gain(0.5)
  .fast(2);
```

There is one filter envelope for each filter type and thus one set of envelope filter parameters preceded either by `lp`, `hp` or `bp`:

- `lpattack`, `lpdecay`, `lpsustain`, `lprelease`, `lpenv`: filter envelope for the lowpass filter.
  - alternatively: `lpa`, `lpd`, `lps`, `lpr` and `lpe`.
- `hpattack`, `hpdecay`, `hpsustain`, `hprelease`, `hpenv`: filter envelope for the highpass filter.
  - alternatively: `hpa`, `hpd`, `hps`, `hpr` and `hpe`.
- `bpattack`, `bpdecay`, `bpsustain`, `bprelease`, `bpenv`: filter envelope for the bandpass filter.
  - alternatively: `bpa`, `bpd`, `bps`, `bpr` and `bpe`.

## lpattack

Sets the attack duration for the lowpass filter envelope.

**Parameters:**

- **attack** _(number|Pattern)_: time of the filter envelope

```javascript
note("c2 e2 f2 g2")
  .sound("sawtooth")
  .lpf(300)
  .lpa("<.5 .25 .1 .01>/4")
  .lpenv(4);
```

## lpdecay

Sets the decay duration for the lowpass filter envelope.

**Parameters:**

- **decay** _(number|Pattern)_: time of the filter envelope

```javascript
note("c2 e2 f2 g2").sound("sawtooth").lpf(300).lpd("<.5 .25 .1 0>/4").lpenv(4);
```

## lpsustain

Sets the sustain amplitude for the lowpass filter envelope.

**Parameters:**

- **sustain** _(number|Pattern)_: amplitude of the lowpass filter envelope

```javascript
note("c2 e2 f2 g2")
  .sound("sawtooth")
  .lpf(300)
  .lpd(0.5)
  .lps("<0 .25 .5 1>/4")
  .lpenv(4);
```

## lprelease

Sets the release time for the lowpass filter envelope.

**Parameters:**

- **release** _(number|Pattern)_: time of the filter envelope

```javascript
note("c2 e2 f2 g2")
  .sound("sawtooth")
  .clip(0.5)
  .lpf(300)
  .lpenv(4)
  .lpr("<.5 .25 .1 0>/4")
  .release(0.5);
```

## lpenv

Sets the lowpass filter envelope modulation depth.

**Parameters:**

- **modulation** _(number|Pattern)_: depth of the lowpass filter envelope between 0 and <em>n</em>

```javascript
note("c2 e2 f2 g2")
  .sound("sawtooth")
  .lpf(300)
  .lpa(0.5)
  .lpenv("<4 2 1 0 -1 -2 -4>/4");
```

# Pitch Envelope

You can also control the pitch with envelopes!
Pitch envelopes can breathe life into static sounds:

```javascript
n("<-4,0 5 2 1>*<2!3 4>")
  .scale("<C F>/8:pentatonic")
  .s("gm_electric_guitar_jazz")
  .penv("<.5 0 7 -2>*2")
  .vib("4:.1")
  .phaser(2)
  .delay(0.25)
  .room(0.3)
  .size(4)
  .fast(1.5);
```

You also create some lovely chiptune-style sounds:

```javascript
n(run("<4 8>/16"))
  .jux(rev)
  .chord("<C^7 <Db^7 Fm7>>")
  .dict("ireal")
  .voicing()
  .add(note("<0 1>/8"))
  .dec(0.1)
  .room(0.2)
  .segment("<4 [2 8]>")
  .penv("<0 <2 -2>>")
  .patt(0.02)
  .fast(2);
```

Let's break down all pitch envelope controls:

## pattack

Attack time of pitch envelope.

**Parameters:**

- **time** _(number|Pattern)_: time in seconds

```javascript
note("c eb g bb").pattack("0 .1 .25 .5").slow(2);
```

## pdecay

Decay time of pitch envelope.

**Parameters:**

- **time** _(number|Pattern)_: time in seconds

```javascript
note("<c eb g bb>").pdecay("<0 .1 .25 .5>");
```

## prelease

Release time of pitch envelope

**Parameters:**

- **time** _(number|Pattern)_: time in seconds

```javascript
note("<c eb g bb> ~")
  .release(0.5) // to hear the pitch release
  .prelease("<0 .1 .25 .5>");
```

## penv

Amount of pitch envelope. Negative values will flip the envelope.
If you don't set other pitch envelope controls, `pattack:.2` will be the default.

**Parameters:**

- **semitones** _(number|Pattern)_: change in semitones

```javascript
note("c").penv("<12 7 1 .5 0 -1 -7 -12>");
```

## pcurve

Curve of envelope. Defaults to linear. exponential is good for kicks

**Parameters:**

- **type** _(number|Pattern)_: 0 = linear, 1 = exponential

```javascript
note("g1*4").s("sine").pdec(0.5).penv(32).pcurve("<0 1>");
```

## panchor

Sets the range anchor of the envelope:

<ul>
<li>anchor 0: range = [note, note + penv]</li>
<li>anchor 1: range = [note - penv, note]
If you don't set an anchor, the value will default to the psustain value.</li>
</ul>

**Parameters:**

- **anchor** _(number|Pattern)_: anchor offset

```javascript
note("c c4").penv(12).panchor("<0 .5 1 .5>");
```

# Dynamics

## gain

Controls the gain by an exponential amount.

**Parameters:**

- **amount** _(number|Pattern)_: gain.

```javascript
s("hh*8").gain(".4!2 1 .4!2 1 .4 1").fast(2);
```

## velocity

Sets the velocity from 0 to 1. Is multiplied together with gain.

```javascript
s("hh*8").gain(".4!2 1 .4!2 1 .4 1").velocity(".4 1");
```

## compressor

Dynamics Compressor. The params are `compressor("threshold:ratio:knee:attack:release")`
More info <a href="https://developer.mozilla.org/en-US/docs/Web/API/DynamicsCompressorNode?retiredLocale=de#instance_properties">here</a>

```javascript
s("bd sd [~ bd] sd,hh*8").compressor("-20:20:10:.002:.02");
```

## postgain

Gain applied after all effects have been processed.

```javascript
s("bd sd [~ bd] sd,hh*8").compressor("-20:20:10:.002:.02").postgain(1.5);
```

## xfade

Cross-fades between left and right from 0 to 1:

<ul>
<li>0 = (full left, no right)</li>
<li>.5 = (both equal)</li>
<li>1 = (no left, full right)</li>
</ul>

```javascript
xfade(s("bd*2"), "<0 .25 .5 .75 1>", s("hh*8"));
```

# Panning

## jux

The jux function creates strange stereo effects, by applying a function to a pattern, but only in the right-hand channel.

```javascript
s("bd lt [~ ht] mt cp ~ bd hh").jux(rev);
```

```javascript
s("bd lt [~ ht] mt cp ~ bd hh").jux(press);
```

```javascript
s("bd lt [~ ht] mt cp ~ bd hh").jux(iter(4));
```

## juxBy

Jux with adjustable stereo width. 0 = mono, 1 = full stereo.

```javascript
s("bd lt [~ ht] mt cp ~ bd hh").juxBy("<0 .5 1>/2", rev);
```

## pan

Sets position in stereo.

**Parameters:**

- **pan** _(number|Pattern)_: between 0 and 1, from left to right (assuming stereo), once round a circle (assuming multichannel)

```javascript
s("[bd hh]*2").pan("<.5 1 .5 0>");
```

```javascript
s("bd rim sd rim bd ~ cp rim").pan(sine.slow(2));
```

# Waveshaping

## coarse

Fake-resampling for lowering the sample rate. Caution: This effect seems to only work in chromium based browsers

**Parameters:**

- **factor** _(number|Pattern)_: 1 for original 2 for half, 3 for a third and so on.

```javascript
s("bd sd [~ bd] sd,hh*8").coarse("<1 4 8 16 32>");
```

## crush

Bit crusher effect.

**Parameters:**

- **depth** _(number|Pattern)_: between 1 (for drastic reduction in bit-depth) to 16 (for barely no reduction).

```javascript
s("<bd sd>,hh*3").fast(2).crush("<16 8 7 6 5 4 3 2>");
```

## distort

Wave shaping distortion. CAUTION: it can get loud.
Second option in optional array syntax (ex: ".9:.5") applies a postgain to the output. Third option sets the waveshaping type.
Most useful values are usually between 0 and 10 (depending on source gain). If you are feeling adventurous, you can turn it up to 11 and beyond ;)

**Parameters:**

- **distortion** _(number|Pattern)_: amount of distortion to apply
- **volume** _(number|Pattern)_: linear postgain of the distortion
- **type** _(number|string|Pattern)_: type of distortion to apply

```javascript
s("bd sd [~ bd] sd,hh*8").distort("<0 2 3 10:.5>");
```

```javascript
note("d1!8").s("sine").penv(36).pdecay(0.12).decay(0.23).distort("8:.4");
```

```javascript
s("bd:4*4").bank("tr808").distort("3:0.5:diode");
```

# Global Effects

## Local vs Global Effects

While the above listed "local" effects will always create a separate effects chain for each event,
global effects use the same chain for all events of the same orbit:

## orbit

An `orbit` is a global parameter context for patterns. Patterns with the same orbit will share the same global effects.

**Parameters:**

- **number** _(number|Pattern)_

```javascript
stack(
  s("hh*6").delay(0.5).delaytime(0.25).orbit(1),
  s("~ sd ~ sd").delay(0.5).delaytime(0.125).orbit(2),
);
```

## Delay

### delay

Sets the level of the delay signal.

When using mininotation, you can also optionally add the 'delaytime' and 'delayfeedback' parameter,
separated by ':'.

**Parameters:**

- **level** _(number|Pattern)_: between 0 and 1

```javascript
s("bd bd").delay("<0 .25 .5 1>");
```

```javascript
s("bd bd").delay("0.65:0.25:0.9 0.65:0.125:0.7");
```

### delaytime

> **Note:** Metadata for `delaytime` not found.

### delayfeedback

Sets the level of the signal that is fed back into the delay.
Caution: Values >= 1 will result in a signal that gets louder and louder! Don't do it

**Parameters:**

- **feedback** _(number|Pattern)_: between 0 and 1

```javascript
s("bd").delay(0.25).delayfeedback("<.25 .5 .75 1>");
```

## Reverb

### room

Sets the level of reverb.

When using mininotation, you can also optionally add the 'size' parameter, separated by ':'.

**Parameters:**

- **level** _(number|Pattern)_: between 0 and 1

```javascript
s("bd sd [~ bd] sd").room("<0 .2 .4 .6 .8 1>");
```

```javascript
s("bd sd [~ bd] sd").room("<0.9:1 0.9:4>");
```

### roomsize

Sets the room size of the reverb, see `room`.
When this property is changed, the reverb will be recaculated, so only change this sparsely..

**Parameters:**

- **size** _(number|Pattern)_: between 0 and 10

```javascript
s("bd sd [~ bd] sd").room(0.8).rsize(1);
```

```javascript
s("bd sd [~ bd] sd").room(0.8).rsize(4);
```

### roomfade

Reverb fade time (in seconds).
When this property is changed, the reverb will be recaculated, so only change this sparsely..

**Parameters:**

- **seconds** _(number)_: for the reverb to fade

```javascript
s("bd sd [~ bd] sd").room(0.5).rlp(10000).rfade(0.5);
```

```javascript
s("bd sd [~ bd] sd").room(0.5).rlp(5000).rfade(4);
```

### roomlp

Reverb lowpass starting frequency (in hertz).
When this property is changed, the reverb will be recaculated, so only change this sparsely..

**Parameters:**

- **frequency** _(number)_: between 0 and 20000hz

```javascript
s("bd sd [~ bd] sd").room(0.5).rlp(10000);
```

```javascript
s("bd sd [~ bd] sd").room(0.5).rlp(5000);
```

### roomdim

Reverb lowpass frequency at -60dB (in hertz).
When this property is changed, the reverb will be recaculated, so only change this sparsely..

**Parameters:**

- **frequency** _(number)_: between 0 and 20000hz

```javascript
s("bd sd [~ bd] sd").room(0.5).rlp(10000).rdim(8000);
```

```javascript
s("bd sd [~ bd] sd").room(0.5).rlp(5000).rdim(400);
```

### iresponse

Sets the sample to use as an impulse response for the reverb.

**Parameters:**

- **sample** _(string|Pattern)_: to use as an impulse response

```javascript
s("bd sd [~ bd] sd").room(0.8).ir("<shaker_large:0 shaker_large:2>");
```

## Phaser

### phaser

Phaser audio effect that approximates popular guitar pedals.

**Parameters:**

- **speed** _(number|Pattern)_: speed of modulation

```javascript
n(run(8)).scale("D:pentatonic").s("sawtooth").release(0.5).phaser("<1 2 4 8>");
```

### phaserdepth

The amount the signal is affected by the phaser effect. Defaults to 0.75

**Parameters:**

- **depth** _(number|Pattern)_: number between 0 and 1

```javascript
n(run(8))
  .scale("D:pentatonic")
  .s("sawtooth")
  .release(0.5)
  .phaser(2)
  .phaserdepth("<0 .5 .75 1>");
```

### phasercenter

The center frequency of the phaser in HZ. Defaults to 1000

**Parameters:**

- **centerfrequency** _(number|Pattern)_: in HZ

```javascript
n(run(8))
  .scale("D:pentatonic")
  .s("sawtooth")
  .release(0.5)
  .phaser(2)
  .phasercenter("<800 2000 4000>");
```

### phasersweep

The frequency sweep range of the lfo for the phaser effect. Defaults to 2000

**Parameters:**

- **phasersweep** _(number|Pattern)_: most useful values are between 0 and 4000

```javascript
n(run(8))
  .scale("D:pentatonic")
  .s("sawtooth")
  .release(0.5)
  .phaser(2)
  .phasersweep("<800 2000 4000>");
```

## Duck

### duckorbit

Modulate the amplitude of an orbit to create a "sidechain" like effect.

Can be applied to multiple orbits with the ':' mininotation, e.g. `duckorbit("2:3")`

**Parameters:**

- **orbit** _(number|Pattern)_: target orbit

```javascript
$: n(run(16)).scale("c:minor:pentatonic").s("sawtooth").delay(0.7).orbit(2);
$: s("bd:4!4")
  .beat("0,4,8,11,14", 16)
  .duckorbit(2)
  .duckattack(0.2)
  .duckdepth(1);
```

```javascript
$: n(run(16)).scale("c:minor:pentatonic").s("sawtooth").delay(0.7).orbit(2);
$: s("hh*16").orbit(3);
$: s("bd:4!4")
  .beat("0,4,8,11,14", 16)
  .duckorbit("2:3")
  .duckattack(0.2)
  .duckdepth(1);
```

### duckattack

The time required for the ducked signal(s) to return to their normal volume.

Can vary across orbits with the ':' mininotation, e.g. `duckonset("0:0.003")`.
Note: this requires first applying the effect to multiple orbits with e.g. `duckorbit("2:3")`.

**Parameters:**

- **time** _(number|Pattern)_: The attack time in seconds

```javascript
sound: n(run(8)).scale("c:minor").s("sawtooth").delay(0.7).orbit(2);
ducker: s("bd:4!4")
  .beat("0,4,8,11,14", 16)
  .duckorbit(2)
  .duckattack("<0.2 0 0.4>")
  .duckdepth(1);
```

```javascript
moreduck: n(run(8)).scale("c:minor").s("sawtooth").delay(0.7).orbit(2);
lessduck: s("hh*16").orbit(5);
ducker: s("bd:4!4")
  .beat("0,4,8,11,14", 16)
  .duckorbit("2:5")
  .duckattack("0.4:0.1");
```

### duckdepth

The amount of ducking applied to target orbit

Can vary across orbits with the ':' mininotation, e.g. `duckdepth("0.3:0.1")`.
Note: this requires first applying the effect to multiple orbits with e.g. `duckorbit("2:3")`.

**Parameters:**

- **depth** _(number|Pattern)_: depth of modulation from 0 to 1

```javascript
stack(
  n(run(8)).scale("c:minor").s("sawtooth").delay(0.7).orbit(2),
  s("bd:4!4")
    .beat("0,4,8,11,14", 16)
    .duckorbit(2)
    .duckattack(0.2)
    .duckdepth("<1 .9 .6 0>"),
);
```

```javascript
$: n(run(16)).scale("c:minor:pentatonic").s("sawtooth").delay(0.7).orbit(2);
$: s("hh*16").orbit(3);
$: s("bd:4!4")
  .beat("0,4,8,11,14", 16)
  .duckorbit("2:3")
  .duckattack(0.2)
  .duckdepth("1:0.5");
```

---

---

## title: Recipes

# Recipes

This page shows possible ways to achieve common (or not so common) musical goals.
There are often many ways to do a thing and there is no right or wrong.
The fun part is that each representation will give you different impulses when improvising.

## Arpeggios

An arpeggio is when the notes of a chord are played in sequence.
We can either write the notes by hand:

```javascript
note("c eb g c4").clip(2).s("gm_electric_guitar_clean");
```

...or use scales:

```javascript
n("0 2 4 7").scale("C:minor").clip(2).s("gm_electric_guitar_clean");
```

...or chord symbols:

```javascript
n("0 1 2 3")
  .chord("Cm")
  .mode("above:c3")
  .voicing()
  .clip(2)
  .s("gm_electric_guitar_clean");
```

...using off:

```javascript
"0"
  .off(1 / 3, add(2))
  .off(1 / 2, add(4))
  .n()
  .scale("C:minor")
  .s("gm_electric_guitar_clean");
```

## Chopping Breaks

A sample can be looped and chopped like this:

```javascript
samples("github:yaxu/clean-breaks");
s("amen/4").fit().chop(32);
```

This fits the break into 8 cycles + chops it in 16 pieces.
The chops are not audible yet, because we're not doing any manipulation.
Let's add randmized doubling + reversing:

```javascript
samples("github:yaxu/clean-breaks");
s("amen/4")
  .fit()
  .chop(16)
  .cut(1)
  .sometimesBy(0.5, ply("2"))
  .sometimesBy(0.25, mul(speed("-1")));
```

If we want to specify the order of samples, we can replace `chop` with `slice`:

```javascript
samples("github:yaxu/clean-breaks");
s("amen/4").fit().slice(8, "<0 1 2 3 4*2 5 6 [6 7]>*2").cut(1).rarely(ply("2"));
```

If we use `splice` instead of `slice`, the speed adjusts to the duration of the event:

```javascript
samples("github:yaxu/clean-breaks");
s("amen").splice(8, "<0 1 2 3 4*2 5 6 [6 7]>*2").cut(1).rarely(ply("2"));
```

Note that we don't need `fit`, because `splice` will do that by itself.

## Filter Envelopes

Using `lpenv`, we can make the filter move:

```javascript
note("g1 bb1 <c2 eb2> d2").s("sawtooth").lpf(400).lpenv(4).scope();
```

The type of envelope depends on the methods you're setting. Let's set `lpa`:

```javascript
note("g1 bb1 <c2 eb2> d2")
  .s("sawtooth")
  .lpq(8)
  .lpf(400)
  .lpa(0.2)
  .lpenv(4)
  .scope();
```

Now the filter is attacking, rather than decaying as before (decay is the default). We can also do both

```javascript
note("g1 bb1 <c2 eb2> d2")
  .s("sawtooth")
  .lpq(8)
  .lpf(400)
  .lpa(0.1)
  .lpd(0.1)
  .lpenv(4)
  .scope();
```

You can play around with `lpa` | `lpd` | `lps` | `lpd` to see what the filter envelope will do.

## Layering Sounds

We can layer sounds by separating them with ",":

```javascript
note("<g1 bb1 d2 f1>")
  .s("sawtooth, square") // <------
  .scope();
```

We can control the gain of individual sounds like this:

```javascript
note("<g1 bb1 d2 f1>")
  .s("sawtooth, square:0:.5") // <--- "name:number:gain"
  .scope();
```

For more control over each voice, we can use `layer`:

```javascript
note("<g1 bb1 d2 f1>")
  .layer(
    (x) => x.s("sawtooth").vib(4),
    (x) => x.s("square").add(note(12)),
  )
  .scope();
```

Here, we give the sawtooth a vibrato and the square is moved an octave up.
With `layer`, you can use any pattern method available on each voice, so sky is the limit..

## Oscillator Detune

We can fatten a sound by adding a detuned version to itself:

```javascript
note("<g1 bb1 d2 f1>")
  .add(note("0,.1")) // <------ chorus
  .s("sawtooth")
  .scope();
```

Try out different values, or add another voice!

## Polyrhythms

Here is a simple example of a polyrhythm:

```javascript
s("bd*2,hh*3");
```

A polyrhythm is when 2 different tempos happen at the same time.

## Polymeter

This is a polymeter:

```javascript
s("<bd rim, hh hh oh>*4");
```

A polymeter is when 2 different bar lengths play at the same tempo.

## Phasing

This is a phasing:

```javascript
note("<C D G A Bb D C A G D Bb A>*[6,6.1]").piano();
```

Phasing happens when the same sequence plays at slightly different tempos.

## Running through samples

Using `run` with `n`, we can rush through a sample bank:

```javascript
samples("bubo:fox");
n(run(8)).s("ftabla");
```

This works great with sample banks that contain similar sounds, like in this case different recordings of a tabla.
Often times, you'll hear the beginning of the phrase not where the pattern begins.
In this case, I hear the beginning at the third sample, which can be accounted for with `early`.

```javascript
samples("bubo:fox");
n(run(8))
  .s("ftabla")
  .early(2 / 8);
```

Let's add some randomness:

```javascript
samples("bubo:fox");
n(run(8))
  .s("ftabla")
  .early(2 / 8)
  .sometimes(mul(speed("1.5")));
```

## Tape Warble

We can emulate a pitch warbling effect like this:

```javascript
note("<c4 bb f eb>*8")
  .add(note(perlin.range(0, 0.5))) // <------ warble
  .clip(2)
  .s("gm_electric_guitar_clean");
```

## Sound Duration

There are a number of ways to change the sound duration. Using clip:

```javascript
note("f ab bb c").clip("<2 1 .5 .25>");
```

The value of clip is relative to the duration of each event.
We can also create overlaps using release:

```javascript
note("f ab bb c").release("<2 1 .5 .25>");
```

This will smoothly fade out each sound for the given number of seconds.
We could also make the notes shorter by using a decay envelope:

```javascript
note("f ab bb c").decay("<2 1 .5 .25>");
```

When using samples, we also have `.end` to cut relative to the sample length:

```javascript
s("oh*4").end("<1 .5 .25 .1>");
```

Compare that to clip:

```javascript
s("oh*4").clip("<1 .5 .25 .1>");
```

or decay:

```javascript
s("oh*4").decay("<1 .5 .25 .1>");
```

## Wavetable Synthesis

You can loop a sample with `loop` / `loopEnd`:

```javascript
note("<c eb g f>").s("bd").loop(1).loopEnd(0.05).gain(0.2);
```

This allows us to play the first 5% of the bass drum as a synth!
To simplify loading wavetables, any sample that starts with `wt_` will be looped automatically:

```javascript
samples("github:bubobubobubobubo/dough-waveforms");
note("c eb g bb").s("wt_dbass").clip(2);
```

Running through different wavetables can also give interesting variations:

```javascript
samples("github:bubobubobubobubo/dough-waveforms");
note("c2*8").s("wt_dbass").n(run(8)).fast(2);
```

...adding a filter envelope + reverb:

```javascript
samples("github:bubobubobubobubo/dough-waveforms");
note("c2*8")
  .s("wt_dbass")
  .n(run(8))
  .lpf(perlin.range(100, 1000).slow(8))
  .lpenv(-3)
  .lpa(0.1)
  .room(0.5)
  .fast(2);
```

---

---

## title: Visual Feedback

# Visual Feedback

There are several function that add visual feedback to your patterns.

## Mini Notation Highlighting

When you write mini notation with "double quotes" or \`backticks\`, the active parts of the mini notation will be highlighted:

```javascript
n("<0 2 1 3 2>*8")
  .scale("<A1 D2>/4:minor:pentatonic")
  .s("supersaw")
  .lpf(300)
  .lpenv("<4 3 2>\*4");
```

You can change the color as well, even pattern it:

```javascript
n("<0 2 1 3 2>*8")
  .scale("<A1 D2>/4:minor:pentatonic")
  .s("supersaw")
  .lpf(300)
  .lpenv("<4 3 2>*4")
  .color("cyan magenta");
```

## Global vs Inline Visuals

The following functions all come with in 2 variants.

**Without prefix**: renders the visual to the background of the page:

```javascript
note("c a f e").color("white").punchcard();
```

**With `_` prefix**: renders the visual inside the code. Allows for multiple visuals

```javascript
note("c a f e").color("white")._punchcard();
```

Here we see the 2 variants for `punchcard`. The same goes for all others below.
To improve readability the following demos will all use the inline variant.

## Punchcard / Pianoroll

These 2 functions render a pianoroll style visual.
The only difference between the 2 is that `pianoroll` will render the pattern directly,
while `punchcard` will also take the transformations into account that occur afterwards:

```javascript
note("c a f e").color("white")._punchcard().color("cyan");
```

Here, the `color` is still visible in the visual, even if it is applied after `_punchcard`.
On the contrary, the color is not visible when using `_pianoroll`:

```javascript
note("c a f e").color("white")._pianoroll().color("cyan");
```

<br />

<Box>

`punchcard` is less resource intensive because it uses the same data as used for the mini notation highlighting.

</Box>

The visual can be customized by passing options. Those options are the same for both functions.

What follows is the API doc of all the options you can pass:

Visualises a pattern as a scrolling 'pianoroll', displayed in the background of the editor. To show a pianoroll for all running patterns, use `all(pianoroll)`. To have a pianoroll appear below
a pattern instead, prefix with `_`, e.g.: `sound("bd sd")._pianoroll()`.

**Parameters:**

- **options** _(Object)_: Object containing all the optional following parameters as key value pairs:
- **cycles** _(integer)_: number of cycles to be displayed at the same time - defaults to 4
- **playhead** _(number)_: location of the active notes on the time axis - 0 to 1, defaults to 0.5
- **vertical** _(boolean)_: displays the roll vertically - 0 by default
- **labels** _(boolean)_: displays labels on individual notes (see the label function) - 0 by default
- **flipTime** _(boolean)_: reverse the direction of the roll - 0 by default
- **flipValues** _(boolean)_: reverse the relative location of notes on the value axis - 0 by default
- **overscan** _(number)_: lookup X cycles outside of the cycles window to display notes in advance - 1 by default
- **hideNegative** _(boolean)_: hide notes with negative time (before starting playing the pattern) - 0 by default
- **smear** _(boolean)_: notes leave a solid trace - 0 by default
- **fold** _(boolean)_: notes takes the full value axis width - 0 by default
- **active** _(string)_: hexadecimal or CSS color of the active notes - defaults to #FFCA28
- **inactive** _(string)_: hexadecimal or CSS color of the inactive notes - defaults to #7491D2
- **background** _(string)_: hexadecimal or CSS color of the background - defaults to transparent
- **playheadColor** _(string)_: hexadecimal or CSS color of the line representing the play head - defaults to white
- **fill** _(boolean)_: notes are filled with color (otherwise only the label is displayed) - 0 by default
- **fillActive** _(boolean)_: active notes are filled with color - 0 by default
- **stroke** _(boolean)_: notes are shown with colored borders - 0 by default
- **strokeActive** _(boolean)_: active notes are shown with colored borders - 0 by default
- **hideInactive** _(boolean)_: only active notes are shown - 0 by default
- **colorizeInactive** _(boolean)_: use note color for inactive notes - 1 by default
- **fontFamily** _(string)_: define the font used by notes labels - defaults to 'monospace'
- **minMidi** _(integer)_: minimum note value to display on the value axis - defaults to 10
- **maxMidi** _(integer)_: maximum note value to display on the value axis - defaults to 90
- **autorange** _(boolean)_: automatically calculate the minMidi and maxMidi parameters - 0 by default

```javascript
note("c2 a2 eb2")
  .euclid(5, 8)
  .s("sawtooth")
  .lpenv(4)
  .lpf(300)
  .pianoroll({ labels: 1 });
```

## Spiral

Displays a spiral visual.

**Parameters:**

- **options** _(Object)_: Object containing all the optional following parameters as key value pairs:
- **stretch** _(number)_: controls the rotations per cycle ratio, where 1 = 1 cycle / 360 degrees
- **size** _(number)_: the diameter of the spiral
- **thickness** _(number)_: line thickness
- **cap** _(string)_: style of line ends: butt (default), round, square
- **inset** _(string)_: number of rotations before spiral starts (default 3)
- **playheadColor** _(string)_: color of playhead, defaults to white
- **playheadLength** _(number)_: length of playhead in rotations, defaults to 0.02
- **playheadThickness** _(number)_: thickness of playheadrotations, defaults to thickness
- **padding** _(number)_: space around spiral
- **steady** _(number)_: steadyness of spiral vs playhead. 1 = spiral doesn't move, playhead does.
- **activeColor** _(number)_: color of active segment. defaults to foreground of theme
- **inactiveColor** _(number)_: color of inactive segments. defaults to gutterForeground of theme
- **colorizeInactive** _(boolean)_: wether or not to colorize inactive segments, defaults to 0
- **fade** _(boolean)_: wether or not past and future should fade out. defaults to 1
- **logSpiral** _(boolean)_: wether or not the spiral should be logarithmic. defaults to 0

```javascript
note("c2 a2 eb2")
  .euclid(5, 8)
  .s("sawtooth")
  .lpenv(4)
  .lpf(300)
  ._spiral({ steady: 0.96 });
```

## Scope

Renders an oscilloscope for the time domain of the audio signal.

**Parameters:**

- **config** _(object)_: optional config with options:
- **align** _(boolean)_: if 1, the scope will be aligned to the first zero crossing. defaults to 1
- **color** _(string)_: line color as hex or color name. defaults to white.
- **thickness** _(number)_: line thickness. defaults to 3
- **scale** _(number)_: scales the y-axis. Defaults to 0.25
- **pos** _(number)_: y-position relative to screen height. 0 = top, 1 = bottom of screen
- **trigger** _(number)_: amplitude value that is used to align the scope. defaults to 0.

```javascript
s("sawtooth")._scope();
```

## Pitchwheel

Renders a pitch circle to visualize frequencies within one octave

**Parameters:**

- **hapcircles** _(number)_
- **circle** _(number)_
- **edo** _(number)_
- **root** _(string)_
- **thickness** _(number)_
- **hapRadius** _(number)_
- **mode** _(string)_
- **margin** _(number)_

```javascript
n("0 .. 12").scale("C:chromatic").s("sawtooth").lpf(500)._pitchwheel();
```

## Spectrum

Renders a spectrum analyzer for the incoming audio signal.

**Parameters:**

- **config** _(object)_: optional config with options:
- **thickness** _(integer)_: line thickness in px (default 3)
- **speed** _(integer)_: scroll speed (default 1)
- **min** _(integer)_: min db (default -80)
- **max** _(integer)_: max db (default 0)

```javascript
n("<0 4 <2 3> 1>*3")
  .off(1 / 8, add(n(5)))
  .off(1 / 5, add(n(7)))
  .scale("d3:minor:pentatonic")
  .s("sine")
  .dec(0.3)
  .room(0.5)
  ._spectrum();
```

## markcss

Overrides the css of highlighted events. Make sure to use single quotes!

```javascript
note("c a f e").markcss("text-decoration:underline");
```

---

---

## title: Patterns

# Patterns

Patterns are the essence of Tidal. Its patterns are abstract entities that represent flows of time as functions, adapting a technique called pure functional reactive programming. Taking a time span as its input, a Pattern can output a set of events that happen within that time span. It depends on the structure of the Pattern how the events are located in time.
From now on, this process of generating events from a time span will be called **querying**.
Example:

```javascript
const pattern = sequence("c3", ["e3", "g3"]);
const events = pattern.queryArc(0, 1);
console.log(events.map((e) => e.show()));
silence;
```

In this example, we create a pattern using the `sequence` function and **query** it for the time span from `0` to `1`.
Those numbers represent units of time called **cycles**. The length of one cycle depends on the tempo, which defaults to one cycle per second.
The resulting events are:

```js
[
  "[ 0/1 -> 1/2 | c3 ]", //
  "[ 1/2 -> 3/4 | e3 ]",
  "[ 3/4 -> 1/1 | g3 ]",
];
```

Each event has a value, a begin time and an end time, where time is represented as a fraction. In the above case, the events are placed in sequential order, where c3 takes the first half, and e3 and g3 together take the second half. This temporal placement is the result of the `sequence` function, which divides its arguments equally over one cycle. If an argument is an array, the same rule applies to that part of the cycle. In the example, e3 and g3 are divided equally over the second half of the whole cycle.

Note that the query function is not just a way to access a pattern, but true to the principles of functional programming, is the pattern itself. This means that in theory there is no way to change a pattern, it is opaque as a pure function. In practice though, Strudel and Tidal are all about transforming patterns, so how is this done? The answer is, by replacing the pattern with a new one, that calls the old one. This new one is only able to manipulate the query before passing it to the old pattern, and manipulate the results from it before returning them to caller. But, this is enough to support all the temporal and structural manipulations provided by Strudel (and Tidal's) extensive library of functions.

The above examples do not represent how Strudel is used in practice. In the live coding editor, the user only has to type in the pattern itself, the querying will be handled by the scheduler. The scheduler will repeatedly query the pattern for events, which are then scheduled as sound synthesis or other event triggers.

---

---

## title: JavaScript API

# Pattern Functions

Let's learn all about functions to create and modify patterns.
At the core of Strudel, everything is made of functions.

For example, everything you can do with the Mini-Notation can also be done with a function.
This Pattern in Mini Notation:

```javascript
note("c3 eb3 g3");
```

is equivalent to this Pattern without Mini Notation:

```javascript
note(seq("c3", "eb3", "g3"));
```

Similarly, there is an equivalent function for every aspect of the mini notation.

Which representation to use is a matter of context. As a rule of thumb, functions
are better suited in a larger context, while mini notation is more practical for individual rhythms.

## Limits of Mini Notation

While the Mini Notation is a powerful way to write rhythms concisely, it also has its limits. Take this example:

```javascript
stack(note("c2 eb2(3,8)").s("sawtooth").cutoff(800), s("bd(5,8), hh*8"));
```

Here, we are using mini notation for the individual rhythms, while using the function `stack` to mix them.
While stack is also available as `,` in mini notation, we cannot use it here, because we have different types of sounds.

## Combining Patterns

You can freely mix JS patterns, mini patterns and values! For example, this pattern:

```javascript
cat(
  stack("g3", "b3", "e4"),
  stack("a3", "c3", "e4"),
  stack("b3", "d3", "fs4"),
  stack("b3", "e4", "g4"),
).note();
```

...is equivalent to:

```javascript
cat("g3,b3,e4", "a3,c3,e4", "b3,d3,f#4", "b3,e4,g4").note();
```

... as well as:

```javascript
note("<[g3,b3,e4] [a3,c3,e4] [b3,d3,f#4] [b3,e4,g4]>");
```

While mini notation is almost always shorter, it only has a handful of modifiers: \* / ! @.
When using JS patterns, there is a lot more you can do.

---

---

## title: Creating Patterns

# Creating Patterns

The following functions will return a pattern.
These are the equivalents used by the Mini Notation:

| function                       | mini             |
| ------------------------------ | ---------------- |
| `cat(x, y)`                    | `"<x y>"`        |
| `seq(x, y)`                    | `"x y"`          |
| `stack(x, y)`                  | `"x,y"`          |
| `stepcat([3,x],[2,y])`         | `"x@3 y@2"`      |
| `polymeter([a, b, c], [x, y])` | `"{a b c, x y}"` |
| `polymeterSteps(2, x, y, z)`   | `"{x y z}%2"`    |
| `silence`                      | `"~"`            |

## cat

The given items are con<strong>cat</strong>enated, where each one takes one cycle.

**Parameters:**

- **items** _(any)_: The items to concatenate

```javascript
cat("e5", "b4", ["d5", "c5"]).note();
// "<e5 b4 [d5 c5]>".note()
```

```javascript
// As a chained function:
s("hh*4").cat(note("c4(5,8)"));
```

## seq

Like <strong>cat</strong>, but the items are crammed into one cycle.

```javascript
seq("e5", "b4", ["d5", "c5"]).note();
// "e5 b4 [d5 c5]".note()
```

```javascript
// As a chained function:
s("hh*4").seq(note("c4(5,8)"));
```

## stack

The given items are played at the same time at the same length.

```javascript
stack("g3", "b3", ["e4", "d4"]).note();
// "g3,b3,[e4 d4]".note()
```

```javascript
// As a chained function:
s("hh*4").stack(note("c4(5,8)"));
```

## stepcat

'Concatenates' patterns like `fastcat`, but proportional to a number of steps per cycle.
The steps can either be inferred from the pattern, or provided as a [length, pattern] pair.
Has the alias `timecat`.

```javascript
stepcat([3, "e3"], [1, "g3"]).note();
// the same as "e3@3 g3".note()
```

```javascript
stepcat("bd sd cp", "hh hh").sound();
// the same as "bd sd cp hh hh".sound()
```

## arrange

Allows to arrange multiple patterns together over multiple cycles.
Takes a variable number of arrays with two elements specifying the number of cycles and the pattern to use.

```javascript
arrange([4, "<c a f e>(3,8)"], [2, "<g a>(5,8)"]).note();
```

## polymeter

<em>Experimental</em>

Aligns the steps of the patterns, creating polymeters. The patterns are repeated until they all fit the cycle. For example, in the below the first pattern is repeated twice, and the second is repeated three times, to fit the lowest common multiple of six steps.

```javascript
// The same as note("{c eb g, c2 g2}%6")
polymeter("c eb g", "c2 g2").note();
```

## polymeterSteps

> **Note:** Metadata for `polymeterSteps` not found.

## silence

Does absolutely nothing..

```javascript
silence; // "~"
```

## run

A discrete pattern of numbers from 0 to n-1

```javascript
n(run(4)).scale("C4:pentatonic");
// n("0 1 2 3").scale("C4:pentatonic")
```

## binary

Creates a binary pattern from a number.

**Parameters:**

- **n** _(number)_: input number to convert to binary

```javascript
"hh".s().struct(binary(5));
// "hh".s().struct("1 0 1")
```

## binaryN

Creates a binary pattern from a number, padded to n bits long.

**Parameters:**

- **n** _(number)_: input number to convert to binary
- **nBits** _(number)_: pattern length, defaults to 16

```javascript
"hh".s().struct(binaryN(55532, 16));
// "hh".s().struct("1 1 0 1 1 0 0 0 1 1 1 0 1 1 0 0")
```

---

---

## title: Time Modifiers

# Time Modifiers

The following functions modify a pattern temporal structure in some way.
Some of these have equivalent operators in the Mini Notation:

| function               | mini         |
| ---------------------- | ------------ |
| `"x".slow(2)`          | `"x/2"`      |
| `"x".fast(2)`          | `"x*2"`      |
| `"x".euclid(3,8)`      | `"x(3,8)"`   |
| `"x".euclidRot(3,8,1)` | `"x(3,8,1)"` |

## slow

Slow down a pattern over the given number of cycles. Like the "/" operator in mini notation.

**Parameters:**

- **factor** _(number|Pattern)_: slow down factor

```javascript
s("bd hh sd hh").slow(2); // s("[bd hh sd hh]/2")
```

## fast

Speed up a pattern by the given factor. Used by "\*" in mini notation.

**Parameters:**

- **factor** _(number|Pattern)_: speed up factor

```javascript
s("bd hh sd hh").fast(2); // s("[bd hh sd hh]*2")
```

## early

Nudge a pattern to start earlier in time. Equivalent of Tidal's <~ operator

**Parameters:**

- **cycles** _(number|Pattern)_: number of cycles to nudge left

```javascript
"bd ~".stack("hh ~".early(0.1)).s();
```

## late

Nudge a pattern to start later in time. Equivalent of Tidal's ~> operator

**Parameters:**

- **cycles** _(number|Pattern)_: number of cycles to nudge right

```javascript
"bd ~".stack("hh ~".late(0.1)).s();
```

## clip / legato

Multiplies the duration with the given number. Also cuts samples off at the end if they exceed the duration.

**Parameters:**

- **factor** _(number|Pattern)_: <blockquote>
  = 0

</blockquote>

```javascript
note("c a f e").s("piano").clip("<.5 1 2>");
```

## euclid

Changes the structure of the pattern to form an Euclidean rhythm.
Euclidean rhythms are rhythms obtained using the greatest common
divisor of two numbers. They were described in 2004 by Godfried
Toussaint, a Canadian computer scientist. Euclidean rhythms are
really useful for computer/algorithmic music because they can
describe a large number of rhythms with a couple of numbers.

**Parameters:**

- **pulses** _(number)_: the number of onsets/beats
- **steps** _(number)_: the number of steps to fill

```javascript
// The Cuban tresillo pattern.
note("c3").euclid(3, 8);
```

### euclidRot

Like `euclid`, but has an additional parameter for 'rotating' the resulting sequence.

**Parameters:**

- **pulses** _(number)_: the number of onsets/beats
- **steps** _(number)_: the number of steps to fill
- **rotation** _(number)_: offset in steps

```javascript
// A Samba rhythm necklace from Brazil
note("c3").euclidRot(3, 16, 14);
```

### euclidLegato

Similar to `euclid`, but each pulse is held until the next pulse,
so there will be no gaps.

**Parameters:**

- **pulses** _(number)_: the number of onsets/beats
- **steps** _(number)_: the number of steps to fill
- **rotation** : offset in steps
- **pat**

```javascript
note("c3").euclidLegato(3, 8);
```

## rev

Reverse all cycles in a pattern. See also `revv` for reversing a whole pattern.

```javascript
note("c d e g").rev();
```

## palindrome

Applies `rev` to a pattern every other cycle, so that the pattern alternates between forwards and backwards.

```javascript
note("c d e g").palindrome();
```

## iter

Divides a pattern into a given number of subdivisions, plays the subdivisions in order, but increments the starting subdivision each cycle. The pattern wraps to the first subdivision after the last subdivision is played.

```javascript
note("0 1 2 3".scale("A minor")).iter(4);
```

### iterBack

Like `iter`, but plays the subdivisions in reverse order. Known as iter' in tidalcycles

```javascript
note("0 1 2 3".scale("A minor")).iterBack(4);
```

## ply

The ply function repeats each event the given number of times.

```javascript
s("bd ~ sd cp").ply("<1 2 3>");
```

## segment

Samples the pattern at a rate of n events per cycle. Useful for turning a continuous pattern into a discrete one.

**Parameters:**

- **segments** _(number)_: number of segments per cycle

```javascript
note(saw.range(40, 52).segment(24));
```

## compress

Compress each cycle into the given timespan, leaving a gap

```javascript
cat(s("bd sd").compress(0.25, 0.75), s("~ bd sd ~"));
```

## zoom

Plays a portion of a pattern, specified by the beginning and end of a time span. The new resulting pattern is played over the time period of the original pattern:

```javascript
s("bd*2 hh*3 [sd bd]*2 perc").zoom(0.25, 0.75);
// s("hh*3 [sd bd]*2") // equivalent
```

## linger

Selects the given fraction of the pattern and repeats that part to fill the remainder of the cycle.

**Parameters:**

- **fraction** _(number)_: fraction to select

```javascript
s("lt ht mt cp, [hh oh]*2").linger("<1 .5 .25 .125>");
```

## fastGap

speeds up a pattern like fast, but rather than it playing multiple times as fast would it instead leaves a gap in the remaining space of the cycle. For example, the following will play the sound pattern "bd sn" only once but compressed into the first half of the cycle, i.e. twice as fast.

```javascript
s("bd sd").fastGap(2);
```

## inside

Carries out an operation 'inside' a cycle.

```javascript
"0 1 2 3 4 3 2 1".inside(4, rev).scale("C major").note();
// "0 1 2 3 4 3 2 1".slow(4).rev().fast(4).scale('C major').note()
```

## outside

Carries out an operation 'outside' a cycle.

```javascript
"<[0 1] 2 [3 4] 5>".outside(4, rev).scale("C major").note();
// "<[0 1] 2 [3 4] 5>".fast(4).rev().slow(4).scale('C major').note()
```

## cpm

Plays the pattern at the given cycles per minute.

```javascript
s("<bd sd>,hh*2").cpm(90); // = 90 bpm
```

## ribbon

Loops the pattern inside an `offset` for `cycles`.
If you think of the entire span of time in cycles as a ribbon, you can cut a single piece and loop it.

**Parameters:**

- **offset** _(number)_: start point of loop in cycles
- **cycles** _(number)_: loop length in cycles

```javascript
note("<c d e f>").ribbon(1, 2);
```

```javascript
// Looping a portion of randomness
n(irand(8).segment(4)).scale("c:pentatonic").ribbon(1337, 2);
```

```javascript
// rhythm generator
s("bd!16?").ribbon(29, 0.5);
```

## swingBy

The function `swingBy x n` breaks each cycle into `n` slices, and then delays events in the second half of each slice by the amount `x`, which is relative to the size of the (half) slice. So if `x` is 0 it does nothing, `0.5` delays for half the note duration, and 1 will wrap around to doing nothing again. The end result is a shuffle or swing-like rhythm

**Parameters:**

- **subdivision** _(number)_
- **offset** _(number)_

```javascript
s("hh*8").swingBy(1 / 3, 4);
```

## swing

Shorthand for swingBy with 1/3:

**Parameters:**

- **subdivision** _(number)_

```javascript
s("hh*8").swing(4);
// s("hh*8").swingBy(1/3, 4)
```

---

---

## title: Control Parameters

# Control Parameters

Besides functions that control time, we saw earlier that functions like `note` and `cutoff` control different parameters (short params) of an event.
Let's now look more closely at how these `param(eter) functions` work.

# Parameter Functions

A very powerful feature of tidal patterns is that each parameter can be controlled independently:

```javascript
note("c a f e")
  .cutoff("<500 1000 2000 [4000 8000]>")
  .gain(0.8)
  .s("sawtooth")
  .log();
```

In this example, the parameters `note`, `cutoff`, `gain` and `s` are controlled independently by either patterns or plain values (numbers / text).
After pressing play, we can observe the time and parameter values of each event (hap) in the output created by `.log()`.

## Plain vs Parameterized Values

Patterns that are not wrapped inside a param function will contain unlabeled `plain values`:

```javascript
"<c e g>".log();
```

This will not generate any sound output, because Strudel could only guess which param is meant by these letters.

Now compare that to the version wrapped in `note`:

```javascript
note("<c e g>").log();
```

Now it is clear that these letters are meant to be played as notes.
Under the hood, the `note` function (as well as all other param functions)
will wrap each plain value in an object. If the note function did not exist, we would need to write:

```javascript
cat({ note: "c" }, { note: "e" }, { note: "g" }).log();
```

This will have the same output, though it is rather unwieldy to read and write.

## Wrapping Parameter Functions

To avoid too much nesting, param functions can also be chained like this:

```javascript
cat("c", "e", "g").note().log();
```

This is equivalent to `note(cat('c','e','g')).log()`.

You can use this with any function that declares a type (like `n`, `s`, `note`, `freq` etc), just make sure to leave the parens empty!

## Plain Value Modification

Patterns of plain values can be modified with any of the following operators:

```javascript
"50 60 70".add("<0 1 2>").log();
```

Here, the add function modifies the numbers on the left.
Again, there is no output because these numbers have no meaning without a param.

## Param Value Modification

To modify a parameter value, you can either:

- Use the operator on the plain value pattern, inside the param function:

```javascript
note("50 60 70".add("<0 1 2>")).room(0.1).log();
```

- Similarly, use the operator on the plain value pattern and wrap it later:

```javascript
"50 60 70".add("<0 1 2>").note().room(0.1).log();
```

- Specify which param should be modified inside the operator function:

```javascript
note("50 60 70").room(0.1).add(note("<0 1 2>")).log();
```

Remember the execution of the chained functions goes from left to right.

# Operators

This group of functions allows to modify the value of events.

## add

Assumes a pattern of numbers. Adds the given number to each item in the pattern.

```javascript
// Here, the triad 0, 2, 4 is shifted by different amounts
n("0 2 4".add("<0 3 4 0>")).scale("C:major");
// Without add, the equivalent would be:
// n("<[0 2 4] [3 5 7] [4 6 8] [0 2 4]>").scale("C:major")
```

```javascript
// You can also use add with notes:
note("c3 e3 g3".add("<0 5 7 0>"));
// Behind the scenes, the notes are converted to midi numbers:
// note("48 52 55".add("<0 5 7 0>"))
```

## sub

Like add, but the given numbers are subtracted.

```javascript
n("0 2 4".sub("<0 1 2 3>")).scale("C4:minor");
// See add for more information.
```

## mul

Multiplies each number by the given factor.

```javascript
"<1 1.5 [1.66, <2 2.33>]>*4".mul(150).freq();
```

## div

Divides each number by the given factor.

## round

Assumes a numerical pattern. Returns a new pattern with all values rounded
to the nearest integer.

```javascript
n("0.5 1.5 2.5".round()).scale("C:major");
```

## floor

Assumes a numerical pattern. Returns a new pattern with all values set to
their mathematical floor. E.g. `3.7` replaced with to `3`, and `-4.2`
replaced with `-5`.

```javascript
note("42 42.1 42.5 43".floor());
```

## ceil

Assumes a numerical pattern. Returns a new pattern with all values set to
their mathematical ceiling. E.g. `3.2` replaced with `4`, and `-4.2`
replaced with `-4`.

```javascript
note("42 42.1 42.5 43".ceil());
```

## range

Assumes a numerical pattern, containing unipolar values in the range 0 .. 1.
Returns a new pattern with values scaled to the given min/max range.
Most useful in combination with continuous patterns.

```javascript
s("[bd sd]*2,hh*8").cutoff(sine.range(500, 4000));
```

## rangex

Assumes a numerical pattern, containing unipolar values in the range 0 .. 1
Returns a new pattern with values scaled to the given min/max range,
following an exponential curve.

```javascript
s("[bd sd]*2,hh*8").cutoff(sine.rangex(500, 4000));
```

## range2

Assumes a numerical pattern, containing bipolar values in the range -1 .. 1
Returns a new pattern with values scaled to the given min/max range.

```javascript
s("[bd sd]*2,hh*8").cutoff(sine2.range2(500, 4000));
```

## ratio

Allows dividing numbers via list notation using ":".
Returns a new pattern with just numbers.

```javascript
ratio("1, 5:4, 3:2").mul(110).freq().s("piano");
```

## as

Sets properties in a batch.

**Parameters:**

- **mapping** _(String|Array)_: the control names that are set

```javascript
"c:.5 a:1 f:.25 e:.8".as("note:clip");
```

```javascript
"{0@2 0.25 0 0.5 .3 .5}%8".as("begin").s("sax_vib").clip(1);
```

# Custom Parameters

You can also create your own parameters:

```javascript
let x = createParam("x");
x(sine.range(0, 200));
```

Multiple params can also be created in a more consice way, using `createParams`:

```javascript
let { x, y } = createParams("x", "y");
x(sine.range(0, 200)).y(cosine.range(0, 200));
```

Note that these params will not do anything until you give them meaning in your custom output!

---

---

## title: Signals

# Continuous Signals

Signals are patterns with continuous values, meaning they have theoretically infinite steps.
They can provide streams of numbers that can be sampled at discrete points in time.

## saw

A sawtooth signal between 0 and 1.

```javascript
note("<c3 [eb3,g3] g2 [g3,bb3]>*8").clip(saw.slow(2));
```

```javascript
n(saw.range(0, 8).segment(8)).scale("C major");
```

## sine

A sine signal between 0 and 1.

```javascript
n(sine.segment(16).range(0, 15)).scale("C:minor");
```

## cosine

A cosine signal between 0 and 1.

```javascript
n(stack(sine, cosine).segment(16).range(0, 15)).scale("C:minor");
```

## tri

A triangle signal between 0 and 1.

```javascript
n(tri.segment(8).range(0, 7)).scale("C:minor");
```

## square

A square signal between 0 and 1.

```javascript
n(square.segment(4).range(0, 7)).scale("C:minor");
```

## rand

A continuous pattern of random numbers, between 0 and 1.

```javascript
// randomly change the cutoff
s("bd*4,hh*8").cutoff(rand.range(500, 8000));
```

## Ranges from -1 to 1

There is also `saw2`, `sine2`, `cosine2`, `tri2`, `square2` and `rand2` which have a range from -1 to 1!

## perlin

Generates a continuous pattern of <a href="https://en.wikipedia.org/wiki/Perlin_noise">perlin noise</a>, in the range 0..1.

```javascript
// randomly change the cutoff
s("bd*4,hh*8").cutoff(perlin.range(500, 8000));
```

## irand

A continuous pattern of random integers, between 0 and n-1.

**Parameters:**

- **n** _(number)_: max value (exclusive)

```javascript
// randomly select scale notes from 0 - 7 (= C to C)
n(irand(8)).struct("x x*2 x x*3").scale("C:minor");
```

## brand

A continuous pattern of 0 or 1 (binary random)

```javascript
s("hh*10").pan(brand);
```

## brandBy

A continuous pattern of 0 or 1 (binary random), with a probability for the value being 1

**Parameters:**

- **probability** _(number)_: a number between 0 and 1

```javascript
s("hh*10").pan(brandBy(0.2));
```

## mouseX

The mouse's x position value ranges from 0 to 1.

```javascript
n(mousex.segment(4).range(0, 7)).scale("C:minor");
```

## mouseY

The mouse's y position value ranges from 0 to 1.

```javascript
n(mousey.segment(4).range(0, 7)).scale("C:minor");
```

---

---

## title: Random Modifiers

# Random Modifiers

These methods add random behavior to your Patterns.

## choose

Chooses randomly from the given list of elements.

**Parameters:**

- **xs** _(any)_: values / patterns to choose from.

```javascript
note("c2 g2!2 d2 f1").s(choose("sine", "triangle", "bd:6"));
```

## wchoose

Chooses randomly from the given list of elements by giving a probability to each element

**Parameters:**

- **pairs** _(any)_: arrays of value and weight

```javascript
note("c2 g2!2 d2 f1").s(wchoose(["sine", 10], ["triangle", 1], ["bd:6", 1]));
```

## chooseCycles

Picks one of the elements at random each cycle.

```javascript
chooseCycles("bd", "hh", "sd").s().fast(8);
```

```javascript
s("bd | hh | sd").fast(8);
```

## wchooseCycles

Picks one of the elements at random each cycle by giving a probability to each element

```javascript
wchooseCycles(["bd", 10], ["hh", 1], ["sd", 1]).s().fast(8);
```

```javascript
wchooseCycles(["c c c", 5], ["a a a", 3], ["f f f", 1]).fast(4).note();
```

```javascript
// The probability can itself be a pattern
wchooseCycles(["bd(3,8)", "<5 0>"], ["hh hh hh", 3]).fast(4).s();
```

## degradeBy

Randomly removes events from the pattern by a given amount.
0 = 0% chance of removal
1 = 100% chance of removal

**Parameters:**

- **amount** _(number)_: a number between 0 and 1

```javascript
s("hh*8").degradeBy(0.2);
```

```javascript
s("[hh?0.2]*8");
```

```javascript
//beat generator
s("bd").segment(16).degradeBy(0.5).ribbon(16, 1);
```

## degrade

Randomly removes 50% of events from the pattern. Shorthand for `.degradeBy(0.5)`

```javascript
s("hh*8").degrade();
```

```javascript
s("[hh?]*8");
```

## undegradeBy

Inverse of `degradeBy`: Randomly removes events from the pattern by a given amount.
0 = 100% chance of removal
1 = 0% chance of removal
Events that would be removed by degradeBy are let through by undegradeBy and vice versa (see second example).

**Parameters:**

- **amount** _(number)_: a number between 0 and 1

```javascript
s("hh*8").undegradeBy(0.2);
```

```javascript
s("hh*10").layer(
  (x) => x.degradeBy(0.2).pan(0),
  (x) => x.undegradeBy(0.8).pan(1),
);
```

## undegrade

Inverse of `degrade`: Randomly removes 50% of events from the pattern. Shorthand for `.undegradeBy(0.5)`
Events that would be removed by degrade are let through by undegrade and vice versa (see second example).

```javascript
s("hh*8").undegrade();
```

```javascript
s("hh*10").layer(
  (x) => x.degrade().pan(0),
  (x) => x.undegrade().pan(1),
);
```

## sometimesBy

Randomly applies the given function by the given probability.
Similar to `someCyclesBy`

**Parameters:**

- **probability** _(number|Pattern)_: a number between 0 and 1
- **function** _(function)_: the transformation to apply

```javascript
s("hh*8").sometimesBy(0.4, (x) => x.speed("0.5"));
```

## sometimes

Applies the given function with a 50% chance

**Parameters:**

- **function** _(function)_: the transformation to apply

```javascript
s("hh*8").sometimes((x) => x.speed("0.5"));
```

## someCyclesBy

Randomly applies the given function by the given probability on a cycle by cycle basis.
Similar to `sometimesBy`

**Parameters:**

- **probability** _(number|Pattern)_: a number between 0 and 1
- **function** _(function)_: the transformation to apply

```javascript
s("bd,hh*8").someCyclesBy(0.3, (x) => x.speed("0.5"));
```

## someCycles

Shorthand for `.someCyclesBy(0.5, fn)`

```javascript
s("bd,hh*8").someCycles((x) => x.speed("0.5"));
```

## often

Shorthand for `.sometimesBy(0.75, fn)`

```javascript
s("hh*8").often((x) => x.speed("0.5"));
```

## rarely

Shorthand for `.sometimesBy(0.25, fn)`

```javascript
s("hh*8").rarely((x) => x.speed("0.5"));
```

## almostNever

Shorthand for `.sometimesBy(0.1, fn)`

```javascript
s("hh*8").almostNever((x) => x.speed("0.5"));
```

## almostAlways

Shorthand for `.sometimesBy(0.9, fn)`

```javascript
s("hh*8").almostAlways((x) => x.speed("0.5"));
```

## never

Shorthand for `.sometimesBy(0, fn)` (never calls fn)

```javascript
s("hh*8").never((x) => x.speed("0.5"));
```

## always

Shorthand for `.sometimesBy(1, fn)` (always calls fn)

```javascript
s("hh*8").always((x) => x.speed("0.5"));
```

---

---

## title: Conditional Modifiers

# Conditional Modifiers

## lastOf

Applies the given function every n cycles, starting from the last cycle.

**Parameters:**

- **n** _(number)_: how many cycles
- **func** _(function)_: function to apply

```javascript
note("c3 d3 e3 g3").lastOf(4, (x) => x.rev());
```

## firstOf

Applies the given function every n cycles, starting from the first cycle.

**Parameters:**

- **n** _(number)_: how many cycles
- **func** _(function)_: function to apply

```javascript
note("c3 d3 e3 g3").firstOf(4, (x) => x.rev());
```

## when

Applies the given function whenever the given pattern is in a true state.

**Parameters:**

- **binary_pat** _(Pattern)_
- **func** _(function)_

```javascript
"c3 eb3 g3".when("<0 1>/2", (x) => x.sub("5")).note();
```

## chunk

Divides a pattern into a given number of parts, then cycles through those parts in turn, applying the given function to each part in turn (one part per cycle).

```javascript
"0 1 2 3"
  .chunk(4, (x) => x.add(7))
  .scale("A:minor")
  .note();
```

### chunkBack

Like `chunk`, but cycles through the parts in reverse order. Known as chunk' in tidalcycles

```javascript
"0 1 2 3"
  .chunkBack(4, (x) => x.add(7))
  .scale("A:minor")
  .note();
```

### fastChunk

Like `chunk`, but the cycles of the source pattern aren't repeated
for each set of chunks.

```javascript
"<0 8> 1 2 3 4 5 6 7"
  .scale("C2:major")
  .note()
  .fastChunk(4, (x) => x.color("red"))
  .slow(2);
```

## arp

Selects indices in in stacked notes.

```javascript
note("<[c,eb,g]!2 [c,f,ab] [d,f,ab]>").arp("0 [0,2] 1 [0,2]");
```

## arpWith 🧪

Selects indices in in stacked notes.

```javascript
note("<[c,eb,g]!2 [c,f,ab] [d,f,ab]>").arpWith((haps) => haps[2]);
```

## struct

Applies the given structure to the pattern:

```javascript
note("c,eb,g").struct("x ~ x ~ ~ x ~ x ~ ~ ~ x ~ x ~ ~").slow(2);
```

## mask

Returns silence when mask is 0 or "~"

```javascript
note("c [eb,g] d [eb,g]").mask("<1 [0 1]>");
```

## reset

Resets the pattern to the start of the cycle for each onset of the reset pattern.

```javascript
s("[<bd lt> sd]*2, hh*8").reset("<x@3 x(5,8)>");
```

## restart

Restarts the pattern for each onset of the restart pattern.
While reset will only reset the current cycle, restart will start from cycle 0.

```javascript
s("[<bd lt> sd]*2, hh*8").restart("<x@3 x(5,8)>");
```

## hush

Silences a pattern.

```javascript
stack(s("bd").hush(), s("hh*3"));
```

## invert

Swaps 1s and 0s in a binary pattern.

```javascript
s("bd").struct("1 0 0 1 0 0 1 0".lastOf(4, invert));
```

## pick

Picks patterns (or plain values) either from a list (by index) or a lookup table (by name).
Similar to `inhabit`, but maintains the structure of the original patterns.

**Parameters:**

- **pat** _(Pattern)_
- **xs** _(_)\*

```javascript
note("<0 1 2!2 3>".pick(["g a", "e f", "f g f g", "g c d"]));
```

```javascript
sound("<0 1 [2,0]>".pick(["bd sd", "cp cp", "hh hh"]));
```

```javascript
sound("<0!2 [0,1] 1>".pick(["bd(3,8)", "sd sd"]));
```

```javascript
s("<a!2 [a,b] b>".pick({ a: "bd(3,8)", b: "sd sd" }));
```

## pickmod

The same as `pick`, but if you pick a number greater than the size of the list,
it wraps around, rather than sticking at the maximum value.
For example, if you pick the fifth pattern of a list of three, you'll get the
second one.

**Parameters:**

- **pat** _(Pattern)_
- **xs** _(_)\*

## pickF

pickF lets you use a pattern of numbers to pick which function to apply to another pattern.

**Parameters:**

- **pat** _(Pattern)_
- **lookup** _(Pattern)_: a pattern of indices or names
- **lookup** _(Array.<function()>|object)_: the array or lookup object of functions from which to pull

```javascript
s("bd [rim hh]").pickF("<0 1 2>", [rev, jux(rev), fast(2)]);
```

```javascript
note("<c2 d2>(3,8)")
  .s("square")
  .pickF("<0 2> 1", [jux(rev), fast(2), (x) => x.lpf(800)]);
```

```javascript
note("<c2 d2>(3,8)")
  .s("square")
  .pickF("<jr l> f", { jr: jux(rev), f: fast(2), l: (x) => x.lpf(800) });
```

## pickmodF

The same as `pickF`, but if you pick a number greater than the size of the functions list,
it wraps around, rather than sticking at the maximum value.

**Parameters:**

- **pat** _(Pattern)_
- **lookup** _(Pattern)_: a pattern of indices or names
- **lookup** _(Array.<function()>|object)_: the array or lookup object of functions from which to pull

## pickRestart

Similar to `pick`, but the choosen pattern is restarted when its index is triggered.

**Parameters:**

- **pat** _(Pattern)_
- **xs** _(_)\*

## pickmodRestart

The same as `pickRestart`, but if you pick a number greater than the size of the list,
it wraps around, rather than sticking at the maximum value.

**Parameters:**

- **pat** _(Pattern)_
- **xs** _(_)\*

```javascript
"<a@2 b@2 c@2 d@2>"
  .pickRestart({
    a: n("0 1 2 0"),
    b: n("2 3 4 ~"),
    c: n("[4 5] [4 3] 2 0"),
    d: n("0 -3 0 ~"),
  })
  .scale("C:major")
  .s("piano");
```

## pickReset

Similar to `pick`, but the choosen pattern is reset when its index is triggered.

**Parameters:**

- **pat** _(Pattern)_
- **xs** _(_)\*

## pickmodReset

The same as `pickReset`, but if you pick a number greater than the size of the list,
it wraps around, rather than sticking at the maximum value.

**Parameters:**

- **pat** _(Pattern)_
- **xs** _(_)\*

## inhabit

Picks patterns (or plain values) either from a list (by index) or a lookup table (by name).
Similar to `pick`, but cycles are squeezed into the target ('inhabited') pattern.

**Parameters:**

- **pat** _(Pattern)_
- **xs** _(_)\*

```javascript
let a = s("bd(3,8)");
let b = s("cp sd");
"<a b [a,b]>".inhabit({ a, b });
```

```javascript
s("a@2 [a b] a".inhabit({ a: "bd(3,8)", b: "sd sd" })).slow(4);
```

## inhabitmod

The same as `inhabit`, but if you pick a number greater than the size of the list,
it wraps around, rather than sticking at the maximum value.
For example, if you pick the fifth pattern of a list of three, you'll get the
second one.

**Parameters:**

- **pat** _(Pattern)_
- **xs** _(_)\*

## squeeze

Pick from the list of values (or patterns of values) via the index using the given
pattern of integers. The selected pattern will be compressed to fit the duration of the selecting event

**Parameters:**

- **pat** _(Pattern)_
- **xs** _(_)\*

```javascript
note(squeeze("<0@2 [1!2] 2>", ["g a", "f g f g", "g a c d"]));
```

---

---

## title: Accumulation Modifiers

# Accumulation Modifiers

## superimpose

Superimposes the result of the given function(s) on top of the original pattern:

```javascript
"<0 2 4 6 ~ 4 ~ 2 0!3 ~!5>*8"
  .superimpose((x) => x.add(2))
  .scale("C minor")
  .note();
```

## layer

Layers the result of the given function(s). Like `superimpose`, but without the original pattern:

```javascript
"<0 2 4 6 ~ 4 ~ 2 0!3 ~!5>*8"
  .layer((x) => x.add("0,2"))
  .scale("C minor")
  .note();
```

## off

Superimposes the function result on top of the original pattern, delayed by the given time.

**Parameters:**

- **time** _(Pattern|number)_: offset time
- **func** _(function)_: function to apply

```javascript
"c3 eb3 g3".off(1 / 8, (x) => x.add(7)).note();
```

## echo

Superimpose and offset multiple times, gradually decreasing the velocity

**Parameters:**

- **times** _(number)_: how many times to repeat
- **time** _(number)_: cycle offset between iterations
- **feedback** _(number)_: velocity multiplicator for each iteration

```javascript
s("bd sd").echo(3, 1 / 6, 0.8);
```

## echoWith

Superimpose and offset multiple times, applying the given function each time.

**Parameters:**

- **times** _(number)_: how many times to repeat
- **time** _(number)_: cycle offset between iterations
- **func** _(function)_: function to apply, given the pattern and the iteration index

```javascript
"<0 [2 4]>"
  .echoWith(4, 1 / 8, (p, n) => p.add(n * 2))
  .scale("C:minor")
  .note();
```

## stut

Deprecated. Like echo, but the last 2 parameters are flipped.

**Parameters:**

- **times** _(number)_: how many times to repeat
- **feedback** _(number)_: velocity multiplicator for each iteration
- **time** _(number)_: cycle offset between iterations

```javascript
s("bd sd").stut(3, 0.8, 1 / 6);
```

---

---

## title: Tonal Functions

# Tonal Functions

These functions use [tonaljs](https://github.com/tonaljs/tonal) to provide helpers for musical operations.

### voicing()

Turns chord symbols into voicings. You can use the following control params:

<ul>
<li>`chord`: Note, followed by chord symbol, e.g. C Am G7 Bb^7</li>
<li>`dict`: voicing dictionary to use, falls back to default dictionary</li>
<li>`anchor`: the note that is used to align the chord</li>
<li>`mode`: how the voicing is aligned to the anchor
<ul>
<li>`below`: top note <= anchor</li>
<li>`duck`: top note <= anchor, anchor excluded</li>
<li>`above`: bottom note >= anchor</li>
</ul>
</li>
<li>`offset`: whole number that shifts the voicing up or down to the next voicing</li>
<li>`n`: if set, the voicing is played like a scale. Overshooting numbers will be octaved</li>
</ul>
All of the above controls are optional, except `chord`.
If you pass a pattern of strings to voicing, they will be interpreted as chords.

```javascript
n("0 1 2 3").chord("<C Am F G>").voicing();
```

Here's an example of how you can play chords and a bassline:

```javascript
chord("<C^7 A7b13 Dm7 G7>*2")
  .dict("ireal")
  .layer(
    (x) => x.struct("[~ x]*2").voicing(),
    (x) =>
      n("0*4").set(x).mode("root:g2").voicing().s("sawtooth").cutoff("800:4:2"),
  );
```

### scale(name)

Turns numbers into notes in the scale (zero indexed) or quantizes notes to a scale.

When describing notes via numbers, note that negative numbers can be used to wrap backwards
in the scale as well as sharps or flats to produce notes outside of the scale.

Also sets scale for other scale operations, like {@link Pattern#scaleTranspose}.

A scale consists of a root note (e.g. `c4`, `c`, `f#`, `bb4`) followed by semicolon (':') and then a <a href="https://github.com/tonaljs/tonal/blob/main/packages/scale-type/data.ts">scale type</a>.

The scale name must be written without spaces (because it would be interpreted as a multi-step pattern otherwise).
If your scale name includes spaces, replace them with colons.

The root note defaults to octave 3, if no octave number is given.

**Parameters:**

- **scale** _(string)_: Name of scale

```javascript
n("0 2 4 6 4 2").scale("C:major");
```

```javascript
n("[0,7] 4 [2,7] 4").scale("C:<major minor>/2").s("piano");
```

```javascript
n(rand.range(0, 12).segment(8)).scale("C:ritusen").s("piano");
```

```javascript
n("<[0,7b] [-4# -4] [-2,7##] 4 [0,7] [-4# -4b] [-2,7###] 4b>*4")
  .scale("C:<major minor>/2")
  .s("piano");
```

```javascript
note("C1*16").transpose(irand(36)).scale("Cb2 major").scaleTranspose(3);
```

```javascript
n("[0 0] [1 2] [3 4] [5 6]").scale("C:major:blues");
```

### transpose(semitones)

Transposes all notes to the given number of semitones:

```javascript
"[c2 c3]*4".transpose("<0 -2 5 3>").note();
```

This method gets really exciting when we use it with a pattern as above.

Instead of numbers, scientific interval notation can be used as well:

```javascript
"[c2 c3]*4".transpose("<1P -2M 4P 3m>").note();
```

### scaleTranspose(steps)

Transposes notes inside the scale by the number of steps:

```javascript
"[-8 [2,4,6]]*2"
  .scale("C4 bebop major")
  .scaleTranspose("<0 -1 -2 -3 -4 -5 -6 -4>*2")
  .note();
```

### rootNotes(octave = 2)

Turns chord symbols into root notes of chords in given octave.

```javascript
"<C^7 A7b13 Dm7 G7>*2".rootNotes(3).note();
```

Together with layer, struct and voicings, this can be used to create a basic backing track:

```javascript
"<C^7 A7b13 Dm7 G7>*2".layer(
  (x) => x.voicings("lefthand").struct("[~ x]*2").note(),
  (x) => x.rootNotes(2).note().s("sawtooth").cutoff(800),
);
```

---

---

## title: Stepwise patterning

# Stepwise patterning (experimental)

This is a developing area of strudel, and behaviour might change or be renamed in future versions. Feedback and ideas are welcome!

## Introduction

Usually in strudel, the only reference point for most pattern transformations is the _cycle_. Now it is possible to also work with _steps_, via a growing range of functions.

For example usually when you `fastcat` two patterns together, the cycles will be squashed into half a cycle each:

```javascript
fastcat("bd hh hh", "bd hh hh cp hh").sound();
```

With the new stepwise `stepcat` function, the steps of the two patterns will be evenly distributed across the cycle:

```javascript
stepcat("bd hh hh", "bd hh hh cp hh").sound();
```

By default, steps are counted according to the 'top level' in mini-notation. For example `"a [b c] d e"` has five events in it per cycle, but is counted as four steps, where `[b c]` is counted as a single step.

However, you can mark a different metrical level to count steps relative to, using a `^` at the start of a sub-pattern. If we do this to the subpattern in our example: `"a [^b c] d e"`, then the pattern is now counted as having _eight_ steps. This is because 'b' and 'c' are each counted as single steps, and the events in the pattern are twice as long, and so counted as two steps each.

## Pacing the steps

Some stepwise functions don't appear to do very much on their own, for example these two examples of the `expand` function sound exactly the same despite being expanded by different amounts:

```javascript
"c a f e".expand(2).note().sound("folkharp");
```

```javascript
"c a f e".expand(4).note().sound("folkharp");
```

The number of steps per cycle is being changed behind the scenes, but on its own, that doesn't do anything. You will hear a difference however, once you use another stepwise function with it, for example `stepcat`:

```javascript
stepcat("c a f e".expand(2), "g d").note().sound("folkharp");
```

```javascript
stepcat("c a f e".expand(4), "g d").note().sound("folkharp");
```

You should be able to hear that `expand` increases the duration of the steps of the first subpattern, proportionally to the second one.

You can also change the speed of a pattern to match a given number of steps per cycle, with the `pace` function:

```javascript
stepcat("c a f e".expand(2), "g d").note().sound("folkharp").pace(8);
```

```javascript
stepcat("c a f e".expand(4), "g d").note().sound("folkharp").pace(8);
```

The first example has ten steps, and the second example has 18 steps, but are then both played a rate of 8 steps per cycle.

The argument to `expand` can also be patterned, and will be treated in a stepwise fashion. This means that the patterns from the changing values in the argument will be `stepcat`ted together:

```javascript
note("c a f e").sound("folkharp").expand("3 2 1 1 2 3");
```

This results in a dense pattern, because the different expanded versions are squashed into a single cycle. `pace` is again handy here for slowing down the pattern to a particular number of steps per cycle:

```javascript
note("c a f e").sound("folkharp").expand("3 2 1 1 2 3").pace(8);
```

Earlier versions of many of these functions had `s_` prefixes, and the `pace` function was previously known as `steps`. These still exist as aliases, but may have changed behaviour and will soon be removed. Please update your patterns!

## Stepwise functions

### pace

<em>Experimental</em>

Speeds a pattern up or down, to fit to the given number of steps per cycle.

```javascript
sound("bd sd cp").pace(4);
// The same as sound("{bd sd cp}%4") or sound("<bd sd cp>*4")
```

### stepcat

'Concatenates' patterns like `fastcat`, but proportional to a number of steps per cycle.
The steps can either be inferred from the pattern, or provided as a [length, pattern] pair.
Has the alias `timecat`.

```javascript
stepcat([3, "e3"], [1, "g3"]).note();
// the same as "e3@3 g3".note()
```

```javascript
stepcat("bd sd cp", "hh hh").sound();
// the same as "bd sd cp hh hh".sound()
```

### stepalt

<em>Experimental</em>

Concatenates patterns stepwise, according to an inferred 'steps per cycle'.
Similar to `stepcat`, but if an argument is a list, the whole pattern will alternate between the elements in the list.

```javascript
stepalt(["bd cp", "mt"], "bd").sound();
// The same as "bd cp bd mt bd".sound()
```

### expand

<em>Experimental</em>

Expands the step size of the pattern by the given factor.

```javascript
sound("tha dhi thom nam").bank("mridangam").expand("3 2 1 1 2 3").pace(8);
```

### contract

<em>Experimental</em>

Contracts the step size of the pattern by the given factor. See also `expand`.

```javascript
sound("tha dhi thom nam").bank("mridangam").contract("3 2 1 1 2 3").pace(8);
```

### extend

<em>Experimental</em>

`extend` is similar to `fast` in that it increases its density, but it also increases the step count
accordingly. So `stepcat("a b".extend(2), "c d")` would be the same as `"a b a b c d"`, whereas
`stepcat("a b".fast(2), "c d")` would be the same as `"[a b] [a b] c d"`.

```javascript
stepcat(sound("bd bd - cp").extend(2), sound("bd - sd -")).pace(8);
```

### take

<em>Experimental</em>

Takes the given number of steps from a pattern (dropping the rest).
A positive number will take steps from the start of a pattern, and a negative number from the end.

```javascript
"bd cp ht mt".take("2").sound();
// The same as "bd cp".sound()
```

```javascript
"bd cp ht mt".take("1 2 3").sound();
// The same as "bd bd cp bd cp ht".sound()
```

```javascript
"bd cp ht mt".take("-1 -2 -3").sound();
// The same as "mt ht mt cp ht mt".sound()
```

### drop

<em>Experimental</em>

Drops the given number of steps from a pattern.
A positive number will drop steps from the start of a pattern, and a negative number from the end.

```javascript
"tha dhi thom nam".drop("1").sound().bank("mridangam");
```

```javascript
"tha dhi thom nam".drop("-1").sound().bank("mridangam");
```

```javascript
"tha dhi thom nam".drop("0 1 2 3").sound().bank("mridangam");
```

```javascript
"tha dhi thom nam".drop("0 -1 -2 -3").sound().bank("mridangam");
```

### polymeter

<em>Experimental</em>

Aligns the steps of the patterns, creating polymeters. The patterns are repeated until they all fit the cycle. For example, in the below the first pattern is repeated twice, and the second is repeated three times, to fit the lowest common multiple of six steps.

```javascript
// The same as note("{c eb g, c2 g2}%6")
polymeter("c eb g", "c2 g2").note();
```

### shrink

<em>Experimental</em>

Progressively shrinks the pattern by 'n' steps until there's nothing left, or if a second value is given (using mininotation list syntax with `:`),
that number of times.
A positive number will progressively drop steps from the start of a pattern, and a negative number from the end.

```javascript
"tha dhi thom nam".shrink("1").sound().bank("mridangam");
```

```javascript
"tha dhi thom nam".shrink("-1").sound().bank("mridangam");
```

```javascript
"tha dhi thom nam".shrink("1 -1").sound().bank("mridangam").pace(4);
```

```javascript
note("0 1 2 3 4 5 6 7".scale("C:ritusen"))
  .sound("folkharp")
  .shrink("1 -1")
  .pace(8);
```

### grow

<em>Experimental</em>

Progressively grows the pattern by 'n' steps until the full pattern is played, or if a second value is given (using mininotation list syntax with `:`),
that number of times.
A positive number will progressively grow steps from the start of a pattern, and a negative number from the end.

```javascript
"tha dhi thom nam".grow("1").sound().bank("mridangam");
```

```javascript
"tha dhi thom nam".grow("-1").sound().bank("mridangam");
```

```javascript
"tha dhi thom nam".grow("1 -1").sound().bank("mridangam").pace(4);
```

```javascript
note("0 1 2 3 4 5 6 7".scale("C:ritusen"))
  .sound("folkharp")
  .grow("1 -1")
  .pace(8);
```

### tour

<em>Experimental</em>

Inserts a pattern into a list of patterns. On the first repetition it will be inserted at the end of the list, then moved backwards through the list
on successive repetitions. The patterns are added together stepwise, with all repetitions taking place over a single cycle. Using `pace` to set the
number of steps per cycle is therefore usually recommended.

```javascript
"[c g]".tour("e f", "e f g", "g f e c").note().sound("folkharp").pace(8);
```

### zip

<em>Experimental</em>

'zips' together the steps of the provided patterns. This can create a long repetition, taking place over a single, dense cycle.
Using `pace` to set the number of steps per cycle is therefore usually recommended.

```javascript
zip("e f", "e f g", "g [f e] a f4 c").note().sound("folkharp").pace(8);
```

---

---

## title: Coding syntax

# Coding Syntax

Let's take a step back and understand how the syntax in Strudel works.

Take a look at this simple example:

```javascript
note("c a f e").s("piano");
```

- We have a word `note` which is followed by some brackets `()` with some words/letters/numbers inside, surrounded by quotes `"c a f e"`
- Then we have a dot `.` followed by another similar piece of code `s("piano")`.
- We can also see these texts are _highlighted_ using colours: word `note` is purple, the brackets `()` are grey, and the content inside the `""` are green. (The colors could be different if you've changed the default theme)

What happens if we try to 'break' this pattern in different ways?

```javascript
note(c a f e).s(piano)
```

```javascript
note("c a f e")s("piano")
```

```javascript
note["c a f e"].s{"piano"}
```

Ok, none of these seem to work...

```javascript
s("piano").note("c a f e");
```

This one does work, but now we only hear the first note...

So what is going on here?

# Functions, arguments and chaining

So far, we've seen the following syntax:

```
xxx("foo").yyy("bar")
```

Generally, `xxx` and `yyy` are called [_functions_](<https://en.wikipedia.org/wiki/Function_(computer_programming)>), while `foo` and `bar` are called function [_arguments_ or _parameters_](<https://en.wikipedia.org/wiki/Parameter_(computer_programming)>).
So far, we've used the functions to declare which aspect of the sound we want to control, and their arguments for the actual data.
The `yyy` function is called a [_chained_ function](https://en.wikipedia.org/wiki/Method_chaining), because it is preceded with a dot (`.`).

Generally, the idea with chaining is that code such as `a("this").b("that").c("other")` allows `a`, `b` and `c` functions to happen in a specified order, without needing to write them as three separate lines of code.
You can think of this as being similar to chaining audio effects together using guitar pedals or digital audio effects.

Strudel makes heavy use of chained functions. Here is a more sophisticated example:

```javascript
note("a3 c#4 e4 a4")
  .s("sawtooth")
  .cutoff(500)
  //.delay(0.5)
  .room(0.5);
```

## Write your own chained function

You can write your own chained function using `register`. Here's the above chain but registered as a reusable, chained function.

```javascript
const effectChain = register("effectChain", (pat) =>
  pat
    .s("sawtooth")
    .cutoff(500)
    //.delay(0.5)
    .room(0.5),
);
note("a3 c#4 e4 a4").effectChain();
```

Try adding `.rev()` after `effectChain()` to hear further effects added.

# Comments

The `//` in the example above is a line comment, resulting in the `delay` function being ignored.
It is a handy way to quickly turn code on and off.
Try uncommenting this line by deleting `//` and refreshing the pattern.
You can also use the keyboard shortcut `cmd-/` to toggle comments on and off.

You might noticed that some comments in the REPL samples include some words starting with a "@", like `@by` or `@license`.
Those are just a convention to define some information about the music. We will talk about it in the [Music metadata](/learn/metadata) section.

# Strings

Ok, so what about the content inside the quotes (e.g. `"c a f e"`)?
In JavaScript, as in most programming languages, this content is referred to as being a [_string_](<https://en.wikipedia.org/wiki/String_(computer_science)>).
A string is simply a sequence of individual characters.
In TidalCycles, double quoted strings are used to write _patterns_ using the mini-notation, and you may hear the phrase _pattern string_ from time to time.
If you want to create a regular string and not a pattern, you can use single quotes, e.g. `'C minor'` will not be parsed as Mini Notation.

The good news is, that this covers most of the JavaScript syntax needed for Strudel!

---

---

## title: Understanding Pitch

import { PitchSlider } from '../../components/PitchSlider';

# Understanding Pitch

Let's learn how pitch works! The slider below controls the <span style="color:#3b82f6;">frequency</span> of an oscillator, producing a pitch:

{/_ <PitchSlider client:load showFrequencySlider plot /> _/}

<PitchSlider client:load showFrequencySlider min={20} max={20000} />

- Drag the slider to hear a pitch
- Move the slider to change the pitch
- Observe how the Hz number changes
- <span className="text-red-300">Caution</span>: The higher frequencies could be disturbing for children or animals!

The Hz number is the frequency of the pitch you're hearing.
The higher the frequency, the higher the pitch and vice versa.
A pitch occurs whenever something is vibrating / oscillating at a frequency, in this case it's your speaker.
The unit **Hz** describes how many times that oscillation happens per second.
Our eyes are too slow to actually see the oscillation on the speaker, but we can <a href="https://www.youtube.com/watch?v=CDMBWw7OuJQ" target="_blank">see it in slow motion</a>.

<Box>

The hearing range of a newborn is said to be between 20Hz and 20000Hz.
The upper limit decreases with age. What's your upper limit?

</Box>

In Strudel, we can play frequencies directly with the `freq` control:

```javascript
freq("<200 [300,500] 400 [500,<600 670 712 670>]>*8");
```

## Frequency vs Pitch Perception

Maybe you have already noticed that the <span style="color:#3b82f6;">frequency slider</span> is "lopsided",
meaning the pitch changes more in the left region and less in the right region.<br/>
To make that more obvious, let's add a <span style="color:#eab308">pitch slider</span>
that controls the frequency on a different scale:

<PitchSlider animatable plot showFrequencySlider showPitchSlider client:load />

Try out the buttons above to sweep through the frequency range in 2 different ways:

- Frequency Sweep: <span style="color:#3b82f6;">frequency rises linear</span> , <span style="color:#eab308">pitch rises logarithmic</span>
- Pitch Sweep: <span style="color:#3b82f6;">frequency rises exponential</span> , <span style="color:#eab308">pitch rises linear</span>

<Box>

Don't be scared of these mathematical terms:

- "logarithmic" is just a fancy way of saying "it starts fast and slows down"
- "exponential" is just a fancy way of saying "it starts slow and gets faster"

</Box>

Most of the time, we might want to control pitch in a way that matches our perception,
which is what the <span style="color:#eab308">pitch slider</span> does.

## From Hz to Semitones

Because Hz does not match our perception, let's try to find a unit for pitch that matches.
To approach that unit of pitch, let's look at how frequency behaves when it is doubled:

<PitchSlider client:load showPitchSlider showFrequencySlider pitchStep={1 / 7} />

- Use the now stepped pitch slider above
- Can you hear how these pitches seem related to each other?

<Box>

In musical terms, a pitch with double the frequency of another is an `octave` higher.

</Box>

Because octaves are pretty far apart, octaves are typically divided into 12 smaller parts:

<PitchSlider client:load showPitchSlider showFrequencySlider pitchStep={1 / 12} min={440} max={880} initial={440} />

This step is also called a semitone, which is the most common division of pitched music.
For example, the keys on a piano keyboard are also divided into semitones.

In Strudel, we could do that with `freq` like this:

```javascript
freq("0 4 7 12".fmap((n) => 440 * 2 ** (n / 12)));
```

Of course, this can be written shorter with note, as we will see below.

## From Semitones to MIDI numbers

Now we know what the distance of a semitone is.
Above, we used an arbitrary base frequency of 440Hz, which means the exponent 0 is equal to 440Hz.
Typically, 440Hz is standardized to the number 69, which leads to this calculation:

<PitchSlider
client:load
showPitchSlider
showFrequencySlider
baseFrequency={440}
zeroOffset={69}
pitchStep={1 / 12 / 7}
min={440 / 8}
max={7040}
initial={440}
/>

The yellow number is now a MIDI number, covering more than the whole human hearing range with numbers from 0 to 127.
In Strudel, we can use MIDI numbers inside `note`:

```javascript
note("69 73 76 81");
```

## From MIDI numbers to notes

In western music theory, notes are used instead of numbers.
For each midi number, there is at least one note label:

<PitchSlider
client:load
showPitchSlider
showFrequencySlider
baseFrequency={440}
zeroOffset={69}
pitchStep={1 / 48}
min={440 / 8}
max={880}
initial={440}
claviature
/>

A full note label consists of a letter (A-G), 0 or more accidentals (b | #) and an octave number.
This system is also known as [Scientific Pitch Notation](https://en.wikipedia.org/wiki/Scientific_pitch_notation).
In Strudel, these note labels can also be used inside `note` as an alternative to midi numbers:

```javascript
note("A4 C#5 E5 A5").piano();
```

## Open Questions

Now that we have learned about different representations of pitch, there are still open questions:

- Why 12 notes? What about different divisions of the octave?
- Why are notes labeled as they are? Why only 7 letters?
- Are there other labeling systems?
- What about Just Intonation Systems?
- What about Timbre?

All those questions are important to ask and will be answered in another article.

## Definition

At first, I wanted to start this article with a definition, but then thought it might be a good idea to focus on intuitive exploration.
Maybe you now understand this definition much better:

<Box>

From [wikipedia](<https://en.wikipedia.org/wiki/Pitch_(music)>): "Pitch is a perceptual property of sounds that allows their ordering on a frequency-related scale, or more commonly, pitch is the quality that makes it possible to judge sounds as "higher" and "lower" in the sense associated with musical melodies."

</Box>

---

---

## title: Xenharmonic Functions

# Xenharmonic Functions (experimental)

These functions allow the use of scales other than your typical chromatic 12 based ones.

### tune(scale)

Assumes a numerical pattern of EDO steps. Accepts a scale name or list of frequencies (see all available names at the link on the reference). Returns a new pattern with all values mapped to a frequency ratio. Similar to `xen`.

**Parameters:**

- **scale** _(string|Array.<number>)_

```javascript
"0 1 2 3 4 5".tune("hexany15").mul("220").freq();
```

```javascript
// You can set your root to be a
// particular note with getFreq:
"4 8 9 10 - - 5 7 9 11 - -"
  .tune("tranh3")
  .mul(getFreq("c3"))
  .freq()
  .clip(0.5)
  .room(1);
```

```javascript
// You can also give tune a list of
// frequencies to use as the scale:
"0 1 2 3 4"
  .tune([
    261.6255653006, 302.72962012827, 350.29154279212, 405.32593044476,
    469.00678383895, 523.2511306012,
  ])
  .mul(220)
  .freq();
```

Here's an example of how to configure a basic hexany scale:

```javascript
"0 1 2 3 4 5".tune("hexany15").mul("220").freq();
```

Try other scales like `hexany1`, `iraq`, `gumbeng`, `gunkali`, or `tranh3`

For a full list of available scales from tunejs, see http://abbernie.github.io/tune/scales.html

You can set your root to be a particular note with `getFreq`

```javascript
"4 8 9 10 - - 5 7 9 11 - -"
  .tune("tranh3")
  .mul(getFreq("c3"))
  .freq()
  .clip(0.5)
  .room(1);
```

Some tunings become more pronounced with a longer reverb decay:

```javascript
"<[5 6 8 10] - [5 7 9 12] -> -"
  .tune("gumbeng")
  .mul(getFreq("c3"))
  .freq()
  .clip(0.8)
  .room("3:10")
  .rdim(10000)
  .rfade(5);
```

Additionally, you can combo this with `fmap` so that the base note changes:

```javascript
"9 11 12 10 - - -"
  .tune("gunkali")
  .mul("<c3 c3 a3 d#3>".fmap(getFreq))
  .freq()
  .legato("2 .7")
  .room("1:15")
  .rdim(8500)
  .rlp(14000)
  .rfade(8);
```

Combining this with various polyrhythm tricks can become very evocative:

```javascript
"<[0 3 1 -] [-1 4 2 8]> ~ ~,<-4 -5>"
  .transpose(4)
  .tune("iraq")
  .mul("<c3 d3 c#3>".fmap(getFreq))
  .freq()
  .clip(0.5)
  .room(1)
  .rfade(9);
```

Another helpful trick when exploring new tunings is to strum them.
Many have a much more enchanting sound that was chosen over many generations of musicians for being strummed.

Take the `sanza` tuning:

```javascript
"4 5 6 7 8 9".tune("sanza").mul(getFreq("c3")).freq();
```

Notes 7 and 9 will clash quite a bit if you arp them normally. Many tunings will have this sort of sound, and it can feel distracting on its own.
See how close they are on the pitch wheel?

```javascript
"[7 9]!3".tune("sanza").mul(getFreq("c3")).freq()._pitchwheel();
```

This quality is often due to how the tunings were formed with instruments that were played differently than a piano.
As such, some tunings are much better strummed, with the subtle clash of the detuned notes actually making the sound much more magical:

```javascript
"[0 1 2 3 4 5 6]@0.3 -"
  .transpose("<2 5 8 1>")
  .tune("sanza")
  .mul(getFreq("c3"))
  .freq()
  .legato("3")
  .room(1)
  .rfade(5);
```

Note the legato and reverb effects make sure the sound of the strumming gets to wash together. Alternating the direction of the strum can make the
tones sound even more alive, too.

The `tranh3` tuning has a similar set of notes, with two clashing. You might trying plugging that in above and see if you find a favorite strumming pattern.

You can also give tune a list of frequencies to use as the scale:

```javascript
"0 1 2 3 4"
  .tune([
    261.6255653006, 302.72962012827, 350.29154279212, 405.32593044476,
    469.00678383895, 523.2511306012,
  ])
  .mul(220)
  .freq();
```

### xen(scaleOrRatios)

Assumes a numerical pattern of scale steps, and a scale. Scales accepted are all preset scale names of `tune`, arbitrary edos such as 31edo, or an array of frequency ratios. Assumes scales repeat at octave (2/1). Returns a new pattern with all values mapped to their associated frequency, assuming a base frequency of 220hz.

**Parameters:**

- **scaleNameOrRatios** _(string|Array.<number>)_

```javascript
// A major triad in 31edo:
"0 8 18".xen("31edo").freq().piano();
```

```javascript
// You can also use xen with frequency ratios.
// This is equivalent to the above:
"0 1 2"
  .xen([Math.pow(2, 0 / 31), Math.pow(2, 8 / 31), Math.pow(2, 18 / 31)])
  .freq()
  .piano();
```

```javascript
// xen also supports all scale names that
// tune does:
"0 1 2 3 4 5".xen("hexany15").freq();
// equiv to:
// "0 1 2 3 4 5".tune("hexany15").mul("220").freq()
```

---

---

## title: Understanding Cycles

import { PitchSlider } from '../../components/PitchSlider';

# Understanding Cycles

The concept of cycles is very central to be able to understand how Strudel works.
Strudel's mother language, TidalCycles, even has it in its name.

## Cycles and BPM

In most music software, the unit BPM (beats per minute) is used to set the tempo.
Strudel expresses tempo as CPS (cycles per second), with a default of 0.5 CPS:

```javascript
s("bd");
```

Here we can hear the 0.5CPS in action: The kick repeats once every two seconds.
Let's make it 4 kicks:

```javascript
s("bd bd bd bd");
```

Now we have 4 kicks per cycle, but the whole pattern still plays at 0.5CPS.
In terms of BPM, most musicians would tell you this is playing at 120bpm.
What about this one:

```javascript
s("bd hh bd hh");
```

Because the second sound is now a hihat, the tempo feels slower again.
This brings us to an important realization:

<Box>

Tempo is based on perception.
The choice of sounds also has an impact on the tempo feel.
This is why the same CPS can produce different perceived tempos.

</Box>

## Setting CPM

If you're familiar with BPM, you can use the `setcpm` method to set the global tempo in cycles per minute:

```javascript
setcpm(110);
s("bd hh");
```

If you want to add more beats per cycle, you might want to divide the cpm:

```javascript
setcpm(110 / 4);
s("bd sd bd rim, hh*8");
```

Or using 2 beats per cycle:

```javascript
setcpm(110 / 2);
s("bd sd, hh*4");
```

You can use the `setcps` method to set the global tempo in cycles per second. `setcpm(x)` is the same as `setcps(x / 60)`.

<Box>

To set a specific bpm, use `setcpm(bpm/bpc)`

- bpm: the target beats per minute
- bpc: the number of perceived beats per cycle

</Box>

## Cycles and Bars

Also in most music software, multiple beats form a bar (or measure).
The so called time signature specifies how many beats are in each bar.
In many types of music, it is common to use 4 beats per bar, also known as 4/4 time.
Many music programs use it as a default.

Strudel does not a have concept of bars or measures, there are only cycles.
How you use them is up to you. Above, we've had this example:

```javascript
setcpm(110 / 4);
s("bd sd bd rim, hh*8");
```

This could be interpreted as 4/4 time with a tempo of 110bpm.
We could write out multiple bars like this:

```javascript
setcpm(110 / 4);
s(`<
[bd sd bd rim, hh*8] 
[bd sd bd rim*2, hh*8]
>`);
```

Instead of writing out each bar separately, we could express this much shorter:

```javascript
setcpm(110 / 2);
s("bd <sd rim*<1 2>>,hh*4");
```

Here we can see that thinking in cycles rather than bars simplifies things a lot!
These types of simplifications work because of the repetitive nature of rhythm.
In computational terms, you could say the former notation has a lot of redundancy.

## Time Signatures

To get a time signature, just change the number of elements per bar. Here is a rhythm with 7 beats:

```javascript
s("bd ~ rim bd bd rim ~");
```

or with 5:

```javascript
s("bd hh hh bd hh hh bd rim bd hh");
```

We could also write multiple bars with different time signatures:

```javascript
setcpm(110 * 2);
s(`<
[bd hh rim]@3
[bd hh rim sd]@4
>`);
```

Here we switch between 3/4 and 4/4, keeping the same tempo.

If we don't specify the length, we get what's called a metric modulation:

```javascript
setcpm(110 / 2);
s(`<
[bd hh rim]
[bd hh rim sd]
>`);
```

Now the 3 elements get the same time as the 4 elements, which is why the tempo changes.

---

---

## title: Understanding Chord Voicings

import { PitchSlider } from '../../components/PitchSlider';

# Understanding Chords and Voicings

Let's dig deeper into how chords and voicings work in strudel.
I'll try to keep theory jargon to a minimum, so hopefully this is approachable for anyone interested.

## What is a chord

Playing more than one note at a time is generally called a `chord`. Here's an example:

```javascript
note("<[c3,eb3,g3] [f3,a3,c4]>").room(0.5);
```

Here's the same with midi numbers:

```javascript
note("<[48,51,55] [53,57,60]>").room(0.5);
```

Here, we have two 3-note chords played in a loop.
You could already stop here and write chords in this style, which is totally fine and gives you control over individual notes.
One downside is that it can be difficult to find good sounding chords and maybe you're yearning for a way to organize chords in some other way.

## Labeling Chords

Chords are typically given different labels depending on the relationship of the notes within.
In the number example above, we have `48,51,55` and `53,57,60`.

To analyze the relationship of those notes, they are typically compared to some `root`, which is often the lowest note.
In our case, the `roots` would be `48` (= `c3`) and `53` (= `f3`).
We can express the same chords relative to those `roots` like this:

```javascript
note("<[0,3,7] [0,4,7]>".add("<48 53>")).room(0.5);
```

Now within each chord, each number represents the distance from the root.
A distance between pitches is typically called `interval`, but let's stick to distance for now.

Now we can see that our 2 chords are actually quite similar, as the only difference is the middle note (and the root of course).
They are part of a group of chords called `triads` which are chords with 3 notes.

### Triads

These 4 shapes are the most common types of `triads` you will encounter:

| shape | label      |
| ----- | ---------- |
| 0,4,7 | major      |
| 0,3,7 | minor      |
| 0,3,6 | diminished |
| 0,4,8 | augmented  |

Here they are in succession:

```javascript
note("<[0,4,7] [0,3,7] [0,3,6] [0,4,8]>".add("60")).room(0.5)._pitchwheel();
```

Many types of music often only use minor and major chords, so we already have the knowledge to accompany songs. Here's one:

```javascript
note(
  `<
[0,3,7] [0,4,7] [0,4,7] [0,4,7]
[0,3,7] [0,4,7] [0,3,7] [0,4,7]
>`.add(`<
a c d f
a e a e
>`),
).room(0.5);
```

These are the chords for "The House of the Rising Sun" by The Animals.
So far, it doesn't sound too exciting, but at least it's recognizable.

## Voicings

A `voicing` is one of many ways a certain chord shape can be arranged.
The term comes from choral music, where chords can be sung in different ways by assigning different notes to each voice.
For example we could add 12 semitones to one or more notes in the chord:

```javascript
note("<[0,3,7] [12,3,7] [12,15,7] [12,15,19]>".add("48")).room(0.5);
```

Notes that are 12 semitone steps apart (= 1 `octave`) are considered to be equal in a harmonic sense, which is why they get the same note letter.
Here's the same example with note letters:

```javascript
note("<[c3,eb3,g3] [c4,eb3,g3] [c4,eb4,g3] [c4,eb4,g4]>").room(0.5);
```

These types of voicings are also called `inversions`. There are many other ways we could `voice` this minor chord:

```javascript
note("<[0,3,7,12] [0,15,24] [0,3,12]>".add("48")).room(0.5);
```

Here we are changing the flavour of the chord slightly by

1. doubling notes 12 steps higher,
2. using very wide distances
3. omitting notes

## Voice Leading

When we want to meaningfully connect chords in a sequence, the chosen voicings affect the way each chord transitions to the next.
Let's revisit "The House of the Rising Sun", this time using our newly acquired voicing techniques:

```javascript
note(
  `<
[0,3,7] [7,12,16] [0,7,16] [4,7,12]
[0,3,7] [4,7,12] [0,3,7] [4,7,12]
>`.add(`<
a c d f
a e a e
>`),
).room(0.5);
```

These voicings make the chords sound more connected and less jumpy, compared to the earlier version, which didn't focus on voicing.
The way chords interact is also called `voice leading`, reminiscent of how an
individual choir voice would move through a sequence of chords.

For example, try singing the top voice in the above example. Then try the same
on the example not focusing on voice leading. Which one's easier?

Naturally, there are many ways a progression of chords could be voiced and there is no definitive right or wrong.

## Chord Symbols

Musicians playing chord-based music often use a `lead sheet`, which is a simplified notation for a piece of music.
These sheets condense the essential elements, such as chords, into symbols that make the music easy to read and follow.
For example, a lead sheet for "The House of the Rising Sun" might include chords written like this:

```
Am | C | D  | F
Am | E | Am | E
```

Here, each symbol consists of the `root` of the chord and optionally an `m` to signal it's a minor chord (just the root note means it's major).
We could mirror that notation in strudel using the `pick` function:

```javascript
"<Am C D F Am E Am E>"
  .pick({
    Am: "57,60,64",
    C: "55,60,64",
    D: "50,57,66",
    F: "57,60,65",
    E: "56,59,64",
  })
  .note()
  .room(0.5);
```

## The voicing function

Coming up with good sounding voicings that connect well can be a difficult and time consuming process.
The `chord` and `voicing` functions can be used to automate that:

```javascript
chord("<Am C D F Am E Am E>").voicing().room(0.5);
```

Here we're also using chord symbols but the voicings will be automatically generated with smooth `voice leading`, minimizing jumps.
It is inspired by the way a piano or guitar player would pick chords to accompany a song.

## Voicing Dictionaries

The voicing function internally uses so called `voicing dictionaries`, which can also be customized:

```javascript
addVoicings("house", {
  "": ["7 12 16", "0 7 16", "4 7 12"],
  m: ["0 3 7"],
});
chord("<Am C D F Am E Am E>").dict("house").anchor(66).voicing().room(0.5);
```

In a `voicing dictionary`, each chord symbol is assigned one or more voicings.
The `voicing` function then picks the voicing that is closest to the `anchor` (defaults to `c5`).

The handy thing about this approach is that a `voicing dictionary` can be used to play any chord progression with automated voice leading!

## The default dictionary

When using the default dictionary, you can use these chord symbols:

```
2 5 6 7 9 11 13 69 add9
o h sus ^ - ^7 -7 7sus
h7 o7 ^9 ^13 ^7#11 ^9#11
^7#5 -6 -69 -^7 -^9 -9
-add9 -11 -7b5 h9 -b6 -#5
7b9 7#9 7#11 7b5 7#5 9#11
9b5 9#5 7b13 7#9#5 7#9b5
7#9#11 7b9#11 7b9b5 7b9#5
7b9#9 7b9b13 7alt 13#11
13b9 13#9 7b9sus 7susadd3
9sus 13sus 7b13sus
aug M m M7 m7 M9 M13
M7#11 M9#11 M7#5 m6 m69
m^7 -M7 m^9 -M9 m9 madd9
m11 m7b5 mb6 m#5 mM7 mM9
```

The available chords and the format is very much inspired by [ireal pro chords](https://technimo.helpshift.com/hc/en/3-ireal-pro/faq/88-chord-symbols-used-in-ireal-pro/).
Some symbols are synonymous:

- "-" is the same as "m", for example C-7 = Cm7
- "^" is the same as "M", for example C^7 = CM7
- "+" is the same as "aug"

You can decide which ones you prefer. There is no international standard for these symbols.
To get a full chord, the symbols have to be prefixed with a root pitch, e.g. D7#11 is the 7#11 chord relative to the pitch D.

Here are all possible chords with root C:

```javascript
chord(`<
C2 C5 C6 C7 C9 C11 C13 C69
Cadd9 Co Ch Csus C^ C- C^7 
C-7 C7sus Ch7 Co7 C^9 C^13 
C^7#11 C^9#11 C^7#5 C-6 C-69 
C-^7 C-^9 C-9 C-add9 C-11 
C-7b5 Ch9 C-b6 C-#5 C7b9 
C7#9 C7#11 C7b5 C7#5 C9#11 
C9b5 C9#5 C7b13 C7#9#5 C7#9b5 
C7#9#11 C7b9#11 C7b9b5 C7b9#5 
C7b9#9 C7b9b13 C7alt C13#11 
C13b9 C13#9 C7b9sus C7susadd3 
C9sus C13sus C7b13sus C Caug 
CM Cm CM7 Cm7 CM9 CM13 CM7#11 
CM9#11 CM7#5 Cm6 Cm69 Cm^7 
C-M7 Cm^9 C-M9 Cm9 Cmadd9 
Cm11 Cm7b5 Cmb6 Cm#5
>`)
  .voicing()
  .room(0.5);
```

Note that the default dictionary contains multiple ways (= `voicings`) to play each chord symbol.
By default, the `voicing` function tries to minimize jumps.
You can alter the picked voicings in various ways, which are now explained in further detail:

## anchor

The `anchor` is a note that is used to align the voicings to:

```javascript
anchor("<c4 g4 c5 g5>").chord("C").voicing().room(0.5);
```

By default, the anchor is the highest possible note the voicing can contain.
When deciding which voicing of the dictionary to pick for a certain chord, the voicing with a top note closest to the anchor wins.

Note that the anchors in the above example match up with the top notes in the pianoroll.
Like `note`, anchor accepts either midi numbers or note names.

## mode

With `mode`, you can change the way the voicing relates to the `anchor`:

```javascript
mode("<below above duck root>").chord("C").anchor("c5").voicing().room(0.5);
```

The modes are:

- `below`: the top note of the voicing is lower than or equal to the anchor (default)
- `above`: the bottom note of the voicing is higher than or equal to the anchor
- `duck`: the top note of the voicing is lower than the anchor
- `root`: the bottom note of the voicing is always the root note closest to the anchor

The `anchor` can also be set from within the `mode` function:

```javascript
mode("<below above duck root>:c5").chord("C").voicing().room(0.5);
```

## n

The `n` control can be used with `voicing` to select individual notes:

```javascript
n("0 3 1 2").chord("<C <Fm Db>>").voicing().clip("4 3 2 1").room(0.5);
```

## Example

Here's an example of a Jazz Blues in F:

```javascript
let chords = chord(`<
F7 Bb7 F7 [Cm7 F7]
Bb7 Bo F7 [Am7 D7]
Gm7 C7 [F7 D7] [Gm7 C7]
>`);
$: n("7 8 [10 9] 8").set(chords).voicing().dec(0.2);
$: chords.struct("- x - x").voicing().room(0.5);
$: n("0 - 1 -").set(chords).mode("root:g2").voicing();
```

The chords are reused for melody, chords and bassline of the tune.

---

---

## title: Pattern Aligment

# Pattern Aligment & Combination

One core aspect of Strudel, inherited from Tidal, is the flexible way that patterns can be combined, irrespective of their structure. Its declarative approach means a live coder does not have to think about the details of _how_ this is done, only _what_ is to be done.

As a simple example, consider two number patterns `"0 [1 2] 3"`, and `"10 20"`. The first has three contiguous steps of equal lengths, with the second step broken down into two substeps, giving four events in total. There are a very large number of ways in which the structure of these two patterns could be combined, but the default method in both Strudel and Tidal is to line up the cycles of the two patterns, and then take events from the first pattern and match them with those in the second pattern. Therefore, the following two lines are equivalent:

```js
"0 [1 2] 3".add("10 20");
("10 [11 22] 23");
```

Where the events only partially overlap, they are treated as fragments
of the event in the first pattern. This is a little difficult to
conceptualise, but lets start by comparing the two patterns in the
following example:

```js
"0 1 2".add("10 20");
("10 [11 21] 22");
```

They are similar to the previous example in that the number `1` is split in two, with its two halves added to `10` and `20` respectively. However, the `11` 'remembers' that it is a fragment of that original `1` event, and so is treated as having a duration of a third of a cycle, despite only being active for a sixth of a cycle. Likewise, the `21` is also a fragment of that original `1` event, but a fragment of its second half. Because the start of its event is missing, it wouldn't actually trigger a sound (unless it underwent further pattern transformations/combinations).

In practice, the effect of this default, implicit method for combining two patterns is that the second pattern is added _in_ to the first one, and indeed this can be made explicit:

```js
"0 1 2".add.in("10 20");
```

This makes way for other ways to align the pattern, and several are already defined, in particular:

- `in` - as explained above, aligns cycles, and applies values from the pattern on the right _in_ to the pattern on the left.
- `out` - as with `in`, but values are applied _out_ of the pattern on the left (i.e. _in_ to the one on the right).
- `mix` - structures from both patterns are combined, so that the new events are not fragments but are created at intersections of events from both sides.
- `squeeze` - cycles from the pattern on the right are squeezed into events on the left. So that e.g. `"0 1 2".add.squeeze("10 20")` is equivalent to `"[10 20] [11 21] [12 22]"`.
- `squeezeout` - as with `squeeze`, but cycles from the left are squeezed into events on the right. So, `"0 1 2".add.squeezeout("10 20")` is equivalent to `[10 11 12] [20 21 22]`.
- `reset` is similar to `squeezeout` in that cycles from the right are aligned with events on the left. However those cycles are not 'squeezed', rather they are truncated to fit the event. So `"0 1 2 3 4 5 6 7".add.reset("10 [20 30]")` would be equivalent to `10 11 12 13 20 21 30 31`. In effect, events on the right 'reset' cycles on the left.
- `restart` is similar to `reset`, but the pattern is 'restarted' from its very first cycle, rather than from the current cycle. `reset` and `restart` therefore only give different results where the leftmost pattern differs from one cycle to the next.

We will save going deeper into the background, design and practicalities of these alignment functions for future publications. However in the next section, we take them as a case study for looking at the different design affordances offered by Haskell to Tidal, and JavaScript to Strudel.
