<br>
<h1>How do I achieve seamless level streaming similar to Alan Wake II?</h1>
<br>
<i>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b>Thesis Project by Billy Becker</i></b><br>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Yrgo 2026</p>
<br><br><br><br><br><br><br><br><br>

<h2>Introduktion</h2>
<br><br>

I'm Billy, and this is my thesis project as student at YRGO's "Game Creator - Programmer" program in Gothenburg.<br>
I have a background in game design, and have dabbled in many game engines, DAWs, 3D modeling programs, bug tracking software and other tools but my primary experience with completed projects lie in Unity.<br>
That game design background is also where I've encountered the topic I've chosen to tackle for this thesis; seamless level streaming. Even before that I was also interested in how developers achieved (and tried to achieve) this in games.<br>
Like many other optimization fields it's a thankless task: When it's not perfect it can be very noticeable by players, but when it's working flawlessly it should ideally not be something they think about at all.<br>

<br><br>
The goal I want to work towards and hope to achieve with this project is then seamlessly streaming in subscenes into a main scene.<br>
Whether I manage to achieve that goal or not I expect to learn a lot about optimization, mostly within the context of Unity but also methods that are more engine agnostic. 
This is a field that in particular benefit games with larger levels and worlds, the types of games which I subsequently hope to be able to confer smart, studied development insights for.<br>
I also hope this thesis will be of use to anyone hoping to take their first steps toward level and asset streaming optimization.
<br><br><br><br>


<h2>How do I achieve seamless streaming similar to Alan Wake II?</h2>
<br><br>

Through this project I want to research and understand how level and asset streaming affect frame times, and how that effect can be minimized or even completely avoided. I specifically chose Alan Wake II as reference game due to having it fresh in memory the times in that game where the player enter a room through a door, only to seconds later exit through the same door and ending up somewhere different than where they came from. My assumption was that this was a very smooth level streaming happening as the player entered the second room.<br>
The first week of research did reveal that while Alan Wake II definitely uses some fancy level streaming, the particular moments I was impressed by was more a case of seamlessly transport the player WITHIN a level. While this is a really interesting and effectful technique, it's not quite where my interest lies. I chose to retain Alan Wake II as the aspirational target because while the method used isn't what I will be focusing on, the results are still what I hope to achieve from the player perspective.
<br><br><br><br>


<h2>Research</h2>
<br><br>

I started the research by looking for resources specifically on how Remedy handles level streaming, but as mentioned above this was a bit of a wild goose chase. Nazareno Urbano's (Remedy Entertainment) talk ["The Dark Place of 'Alan Wake 2': Crafting an Evolving Nightmare Dimension](https://www.youtube.com/watch?v=vyafiQG6XEU) was the video that made me realize the seamless transitions I experienced in the game was not what I technically aim to research, level and asset streaming.
<br>
I then fell down a design rabbit hole of how developers use level design to better hide the streaming of levels, famously the blast doors of Metroid only opening after the room is loaded and the "squeeze-through-a-tight-gap" technique that was and is still used to intentionally slow down the player so the level or assets can load. This is interesting, and I might look into implementing something like this for my project if there's time, but again is not what my research is about.
<br>
<br>
At this point I decided to start searching for Unity-specific resources on streaming since general resources seemed nigh-on impossible to find, at least as far as programming goes. The absolute majority of results from this new search topic came in the form of Unity's Addressables/AssetBundles system. My initial testing will compare basic, asynchronous and addressable (additive) streaming of scenes. Addressables in particular seems promising both for scenes and asset streaming, but as described in [Asset Streaming in Valheim](https://www.youtube.com/watch?v=Fzu2Das_1FU), a talk by a third-party consulting developer for Iron Gate which implemented asset streaming to Valheim post-launch.
<br>
A lot of the sources I came across also tended to discuss other, more general rendering optimization which goes hand-in-hand with optimizing streaming. Batching draw calls, impostors, LODs, etc. I will be looking into batching draw calls for sure, as I'm curious how it interacts with the AssetBundle and Addressables system.
<br>

<br><br><br><br>
TO DO/Skeleton text:<br>
- Add links to addressables tutorial and batching draw calls tutorial.
