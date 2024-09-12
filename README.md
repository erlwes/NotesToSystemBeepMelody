# NotesToSystemBeepMelody
Script that will convert notes into a melody and play them using `[System.Console]::Beep`

# BUT WHYYY? 🤦‍♂️

I had an idea, that one could play music if one provided the correnct frequency, duration and delays.
I quickly discovered that this was already a thing on Reddit, but I wanted to take it one step further, and then asked my friend ChatGPT to help ...

The AI needed _some_ guidance, like:
1. A frequency lookup-table I found on Google, because the suggested frequencies was off.
2. The need for a BPM parameter, AI wanted to use generic delays "for simplicity"
3. Providing the desired formula to calculate durations, again it used static values "for simplicity".
4. Telling it to bake/pre-calulate the melody for increased playback performance, rather than doing it live in playback function (probably unnessasary on todays computers, but fun)
5. And finally, telling it that the hashtable for storing the melody has to be ORDERED! 😂

# Example
The script needs a BMP and notes to make a playable melody. It looks like this:

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
$preCalculatedMelody = Precalculate-Melody -melody $melody -BPM $BPM
Play-Melody -preCalculatedMelody $preCalculatedMelody
```


# Example 2 (Work-in-progress)
```PowerShell
$BPM = 113
$melody = @(
    # Nev-er gon-na
    @("D4", "sixteenth", "sixteenth"),
    @("E4", "sixteenth", "sixteenth"),
    @("G4", "sixteenth", "sixteenth"),
    @("E4", "sixteenth", "sixteenth"),

    # Give you up
    @("B4", "quarter", "sixteenth"),
    @("B4", "quarter", "sixteenth"),
    @("A4", "quarter", "quarter"),

    # Nev-er gon-na
    @("D4", "sixteenth", "sixteenth"),
    @("E4", "sixteenth", "sixteenth"),
    @("G4", "sixteenth", "sixteenth"),
    @("E4", "sixteenth", "sixteenth"),

    # let you down
    @("A4", "quarter", "sixteenth"),
    @("A4", "quarter", "sixteenth"),
    @("G4", "quarter", "quarter"),

    # Nev-er gon-na
    @("D4", "sixteenth", "sixteenth"),
    @("E4", "sixteenth", "sixteenth"),
    @("G4", "sixteenth", "sixteenth"),
    @("E4", "sixteenth", "sixteenth"),
    
    # Run a______ round
    @("G4", "quarter", "sixteenth"),
    @("A4", "quarter", "sixteenth"),
    @("D4", "quarter", "quarter"),

    # and de-serty you
    @("D4", "quarter", "sixteenth"),
    @("D4", "sixteenth", "sixteenth"),
    @("A4", "eighth", "sixteenth"),
    @("G4", "quarter", "quarter")
)
$preCalculatedMelody = Precalculate-Melody -melody $melody -BPM $BPM
Play-Melody -preCalculatedMelody $preCalculatedMelody
```
