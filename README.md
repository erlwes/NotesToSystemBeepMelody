# NotesToSystemBeepMelody
Script that will convert notes into a melody and play them using `[System.Console]::Beep`

# WHY? 😂

I ran the idea my friend ChatGPT yesterday (zero alcohol involved. true story).

The AI needed _some_ guidance, like
1. A frequency lookup-table I found on Google, because the suggested frequencies was off.
2. The need for a BPM parameter, AI wanted to use generic delays "for simplicity"
3. Providing the desired formula to calculate durations, again it used static values "for simplicity".
4. Telling it to bake/pre-calulate the melody for increased playback performance, rather than doing it live in playback function (probably unnessasary on todays computers, but fun)
5. And finally, telling it to use an ORDERED hashtable for storing the melody! 😂

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
