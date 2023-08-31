---
title: TextAlive API
---
The [TextAlive API](https://developer.textalive.jp) provides information about the timing of a song's lyrics. The tutorials are in Japanese, but the [code samples](https://github.com/TextAliveJp) are enough to get the gist of how it works.

## Timing Info
Let `p` be an instance of the `Player` class.

- `p.getBeats()` returns an array of the song's beats
	- Given a timestamp in ms, `p.findBeat` will return the beat that's ongoing at that time.
	- These also form a doubly-linked list: `IBeat` has `previous` and `next` properties
	- Beats need not have a constant duration: `IBeat` has a `duration` property, as well as a `startTime` and `endTime`
- Lyrics information is contained in `p.video`
	- Lyrics are split up in 3 different ways: individual characters, words, or whole phrases.
	- A list of all phrases is available as the property `p.video.phrases`, but analogous properties don't exist for characters or words.
	- All of these also form linked lists: given an instance, they have `previous` and `next` properties.
	- Given a timestamp, `findWord` will return the word that appears at the given time. Analogous methods for characters and phrases exist.
	- These all also have `startTime`, `endTime`, and `duration` properties.

The effect of this is that whichever division type you choose to work with, you'll have two parallel linked lists to deal with. The timing boundaries of the lyrics don't necessarily align with those of the beats, so you'll be advancing your position in them at different times.

## Listener Methods
`onVideoReady`

This is called once the lyrics information is loaded. Initialization that relies on having the lyrics can go here.

`onTimeUpdate`

This is the main frame update method, it gets constantly called while the song is playing and provides the timestamp of the current position. 

`onSeekComplete`

If a seek is requested, this method is called once all the adjustment in the player is done.  
This is *supposed* to provide the timestamp that the song ends up at, but in practice the player will jump a little after this gets called.  
It's best to just use this to flag that a seek has happened, and then handle it in `onTimeUpdate` when that gets the real timestamp.