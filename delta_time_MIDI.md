A MIDI file is a sequence of events (note on, note off, etc.). Instead of storing absolute timestamps, it stores:

delta time = number of ticks since the previous event

So each event starts with a VLQ that tells how long to wait before executing it.

VLQ encoding is basically:

“Split number into 7-bit chunks, then chain them with continuation bits.”

Why MIDI uses VLQ
Saves space (very important in old MIDI systems)
Most delta times are small → often 1 byte only
Allows efficient streaming playback


ticks=(((B1​&0x7F)≪7)+(B2​&0x7F))(for 2 bytes)



value = 0
for byte in VLQ:
    value = (value << 7) + (byte & 0x7F)
