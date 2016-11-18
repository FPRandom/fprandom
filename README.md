#FPRandom

Welcome to the official repository of FPRandom, a modified browser
whose goal is to counter advanced fingerprinting techniques!

### The browser
FPRandom is a modified version of Firefox 53, the latest Nightly version
from Mozilla. FPRandom's primary goal is to break the stability and determinism
of very specific fingerprinting techniques while preserving the best user experience possible.
By introducing enough noise during the fingerprinting process, trackers are fooled and cannot bound 
a freshly collected fingerprint with an old one, thus rendering the tracking across
multiple sessions impossible.

###The patch
The **fprandom.patch** file contains the complete list of modifications brought
to Firefox. The patch is structured as follows:
* [From line 1 to 249](https://github.com/fprandom/fprandom/blob/master/fprandom.patch#L1) -
addition of an entry in the **Privacy** section of Firefox preferences to chose
when the protection is activated ("Always", "Only in private windows" or "Never")
* [From line 250 to 348](https://github.com/fprandom/fprandom/blob/master/fprandom.patch#L250) -
modification of the **Canvas API** to change the browser's fallback font and add imperceptible
variations to selected colors
* [From line 349 to 578](https://github.com/fprandom/fprandom/blob/master/fprandom.patch#L349) -
modification of the **AudioContext API** to reduce the volume of random parts of
processed audio by a very small factor inaudible by the user
* [From line 579 to 641](https://github.com/fprandom/fprandom/blob/master/fprandom.patch#L579) -
modification of the iterator of JavaScript objects to change the **enumeration order** of properties
and to prevent browser's unmasking


###The Linux prototype
You can find a fully-compiled prototype of FPRandom for x64 Linux systems 
in the _Release_ section of this repository 
[HERE](https://github.com/fprandom/fprandom/releases).
After downloading the archive, extract it and execute the following command:

    ./firefox

If you want to launch FPRandom alongside your main instance of Firefox with a different
profile, you can execute the following command:

    ./firefox -no-remote -P "New profile"
    
    
###Demo
You can use the demo page at
[https://fprandom.github.io/fprandom/](https://fprandom.github.io/fprandom/)
to compare the impact of FPRandom with a vanilla version of Firefox or Chrome.
By running the tests several times, you can see that FPRandom produces new values at every
execution while a standard browser keeps the same stable ones.








