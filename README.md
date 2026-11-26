<br>
<h1>How do I achieve seamless level streaming similar to Alan Wake II?</h1>
<br>
<i>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b>Thesis Project by Billy Becker</i></b><br>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Yrgo 2026</p>
<br><br><br><br><br><br><br><br><br>

<h2>Introduktion</h2>
<br>

I'm Billy, and this is my thesis project as student at YRGO's "Game Creator - Programmer" program in Gothenburg.<br>
I have a background in game design, and have dabbled in many game engines, DAWs, 3D modeling programs, bug tracking software and other tools but my primary experience with completed projects lie in Unity.<br>
That game design background is also where I've encountered the topic I've chosen to tackle for this thesis; seamless level streaming. Even before that I was also interested in how developers achieved (and tried to achieve) this in games.<br>
Like many other optimization fields it's a thankless task: When it's not perfect it can be very noticeable by players, but when it's working flawlessly it should ideally not be something they think about at all.<br>

<br>
The goal I want to work towards and hope to achieve with this project is then seamlessly streaming in subscenes into a main scene.<br>
Whether I manage to achieve that goal or not I expect to learn a lot about optimization, mostly within the context of Unity but also methods that are more engine agnostic. 
This is a field that in particular benefit games with larger levels and worlds, the types of games which I subsequently hope to be able to confer smart, studied development insights for.<br>
I also hope this thesis will be of use to anyone hoping to take their first steps toward level and asset streaming optimization.
<br><br><br><br>


<h2>How do I achieve seamless streaming similar to Alan Wake II?</h2>
<br>

Through this project I want to research and understand how level and asset streaming affect frame times, and how that effect can be minimized or even completely avoided. I specifically chose Alan Wake II as reference game due to having it fresh in memory the times in that game where the player enter a room through a door, only to seconds later exit through the same door and ending up somewhere different than where they came from. My assumption was that this was a very smooth level streaming happening as the player entered the second room.<br>
The first week of research did reveal that while Alan Wake II definitely uses some fancy level streaming, the particular moments I was impressed by was more a case of seamlessly transport the player WITHIN a level. While this is a really interesting and effectful technique, it's not quite where my interest lies. I chose to retain Alan Wake II as the aspirational target because while the method used isn't what I will be focusing on, the results are still what I hope to achieve from the player perspective.
<br><br><br><br>


<h2>Research</h2>
<br>

I started the research by looking for resources specifically on how Remedy handles level streaming, but as mentioned above this was a bit of a wild goose chase. Nazareno Urbano's (Remedy Entertainment) talk ["The Dark Place of 'Alan Wake 2': Crafting an Evolving Nightmare Dimension](https://www.youtube.com/watch?v=vyafiQG6XEU) was the video that made me realize the seamless transitions I experienced in the game was not what I technically aim to research, level and asset streaming.
<br>
I then fell down a design rabbit hole of how developers use level design to better hide the streaming of levels, famously the blast doors of Metroid only opening after the room is loaded and the "squeeze-through-a-tight-gap" technique that was and is still used to intentionally slow down the player so the level or assets can load. This is interesting, and I might look into implementing something like this for my project if there's time, but again is not what my research is about.
<br>
<br>
At this point I decided to start searching for Unity-specific resources on streaming since general resources seemed nigh-on impossible to find, at least as far as programming goes. The absolute majority of results from this new search topic came in the form of Unity's Addressables/AssetBundles system. My initial testing will compare basic, asynchronous and addressable (additive) streaming of scenes. Addressables in particular seems promising both for scenes and asset streaming, but as described in [Asset Streaming in Valheim](https://www.youtube.com/watch?v=Fzu2Das_1FU), a talk by a third-party consulting developer for Iron Gate which implemented asset streaming to Valheim post-launch.
<br>
A lot of the sources I came across also tended to discuss other, more general rendering optimization which goes hand-in-hand with optimizing streaming. Batching draw calls, impostors, LODs, etc. I will be looking into batching draw calls for sure, as I'm curious how it interacts with the AssetBundle and Addressables system.
<br><br><br><br>

<h2>Knowledge Sharing</h2>
<br>

Unity project as (testing) context.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - Why?<br>
Scene, player and UI (both settings and data collection) structure.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - MEDIA: Scene overview with annotations.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - MEDIA: Overview of level with things loading gif.<br>
Planned methods of streaming a scene (basic, async, addressable, addressable prefab).<br>
&nbsp;&nbsp;&nbsp;&nbsp; - Mention scene update with tripled amount of trees.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - Name the functions.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - MEDIA: Trees vs. rocks scene.<br>
Planned methods of streaming an asset/prefab.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - MEDIA: "Inner" scene overview plus sketch.<br>
Difficulties implementing and gauging effect of addressables.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - MEDIA: Code snippet? AS A PNG?<br>
Difficulties even getting addressables to work for prefabs.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - MEDIA: Code snippet for non-working state? AS A PNG?<br>
Batching draw calls.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - Should this one just have its results presented here since it's tangential to my actual research? Ask Mikael?<br>
&nbsp;&nbsp;&nbsp;&nbsp; - MEDIA: FPS comparison gif?<br>
Data capturing.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - MEDIA: Example shot of load time log and frame time UI elements (with annotations).<br>
<br><br><br><br>

<h2>Results</h2>
<br>

Why loading TIMES cannot be properly compared. (At least not basic loading).<br>
&nbsp;&nbsp;&nbsp;&nbsp; - Before that though, give it one last try with assistance.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - Basic loading (Scenemanagement.LoadScene()) seems to consider the scene completely loaded once it itself is instantiated and present in the scene rather than when it AND all in its heirarchy is loaded (double check).<br>
&nbsp;&nbsp;&nbsp;&nbsp; - MEDIA: Show load times being exactly the same every instance for basic loading.<br>
Frametime data comparisons sectioned by load type and area (north, south, south_rocks).<br>
&nbsp;&nbsp;&nbsp;&nbsp; - MEDIA: Frame time PNGs vertically stacked, and cut/trimmed to line up in terms of when a load occurs.<br>
Analyzing above frametime data (including initial hickups when starting and when FIRST loading a scene).<br>
&nbsp;&nbsp;&nbsp;&nbsp; - Table describing gains, losses?<br>
<br>
Basic (Scenemanagement.LoadScene())	Async (Scenemanagement.LoadSceneAsync())	Addressables (Addressables.LoadSceneAsync())	Addressables Prefab/GameObject (Addressables.LoadAssetAsync())
Frame Time Comparison	High (lowers with subsequent loads?).	Medium (lowers with subsequent loads?).	Low	???
Positives	Simplest to implement.	Lower frame time spikes than basic loading.
Almost as simple to implement as basic scene streaming.		
Negatives	Largest frame time spikes?		Puzzling together addressables groups and structuring scenes around them.	Puzzling together addressables groups and structuring scenes around them.
<br><br>
(FPS comparisons before and after batching draw calls / static batching (remember to mention amount of GOs in scene/visible).) - Maybe not relevant enough to make it into this section?<br>
&nbsp;&nbsp;&nbsp;&nbsp; - MEDIA: If it is though, but that FPS comparison gif here.<br>
Take-aways in terms of frame time spikes, rather than actual time it takes to load a scene.<br>
M&nbsp;&nbsp;&nbsp;&nbsp; - EDIA: PNG of the best frame time graph I had over the course of the project. - Hopefully from the final week of recording!<br>
Take-aways for addressable gameobjects, again in terms of frame time spikes.<br>
<br><br><br><br>

<h2>Reflections</h2>
<br>

Best of the best<br>
Tangentials<br>

<br><br><br><br>
TO DO/Skeleton text:<br>
- Add links to addressables tutorial and batching draw calls tutorial.
