# NotesToSystemBeepMelody
Script that will convert notes into a melody and play them using `[System.Console]::Beep`

This is the result in me, itroducing an idea to my friend ChatGPT. Zero alcohol involved (true story).

It needed _some_ guidance
1. Feeding it with a frequency lookup-table. The suggested frequencies was off to begin with.
2. The need for a BPM parameter, It wanted to use generic delays "for simplicity"
3. Providing the desired formula to calculate durations
4. Telling it to bake/pre-calulate the melody for increased playback performance, rather than doing it live in playback function (probably unnessasary, but fun)
5. Telling it to use an ORDERED hashtable for storing the melody (😂 LOL)


My idea was to take the MusicXML-format as input, but all the examples was paywalled so...


# Example

The script needs a BMP and a melody, specified like this, the rest is taken care of by lookup-tables and math:

```PowerShell
# Set BPM for the melody. This is used to calculate note and delay durations.
$BPM = 125

# Melody - each line defines note, duration and delay. This example is "Happy birthday":
$melody = @(

    #Happy bithday to you
    @("G4", "quarter", "eighth"),
    @("G4", "quarter", "sixteenth"),
    @("A4", "quarter", "sixteenth"),
    @("G4", "quarter", "sixteenth"),
    @("C5", "quarter", "sixteenth"),
    @("B4", "quarter", "eighth"),

    #Happy bithday to you
    @("G4", "quarter", "eighth"),
    @("G4", "quarter", "sixteenth"),
    @("A4", "quarter", "sixteenth"),
    @("G4", "quarter", "sixteenth"),
    @("D5", "quarter", "sixteenth"),
    @("C5", "quarter", "eighth"),

    #Happy bithday dear [whoami]
    @("G4", "quarter", "eighth"),
    @("G4", "quarter", "sixteenth"),
    @("G5", "quarter", "sixteenth"),
    @("E5", "quarter", "sixteenth"),
    @("C5", "quarter", "sixteenth"),
    @("B4", "quarter", "sixteenth"),
    @("A4", "quarter", "eighth"),

    #Happy bithday to you
    @("F5", "quarter", "eighth"),
    @("F5", "quarter", "sixteenth"),
    @("E5", "quarter", "sixteenth"),
    @("C5", "quarter", "sixteenth"),
    @("D5", "quarter", "sixteenth"),
    @("C5", "quarter", "eighth")
)
```
