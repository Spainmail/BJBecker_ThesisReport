<br>
<h1>How do I achieve seamless level streaming similar to Alan Wake II?</h1>
<br>
<i>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b>Thesis Project by Billy Becker</i></b><br>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Yrgo 2026</p>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img width="613" height="460" alt="AssetStreaming-crop" src="https://github.com/user-attachments/assets/a265ee91-dbe8-4da1-b049-82fbd963d952" />
<br><br><br>

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

Through this project I want to research and understand how level and asset streaming affect frame times, and how that effect can be minimized or even completely avoided.<br>
I specifically chose Alan Wake II as reference game due to having it fresh in memory the times in that game where the player enter a room through a door, only to seconds later exit through the same door and ending up somewhere different than where they came from. My assumption was that this was a very smooth level streaming happening as the player entered the second room.<br>
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

The chosen context for my tests is Unity. Both because it's an environment I'm familiar with and because that's where I've previously encountered this topic.<br>
The product of my thesis project is intended to be a scene which streams in other ones additively, with UI elements to control which streaming techniques is being used. Data should then be possible to collect and record, both for loading times and most importantly for frame time data which is how effectiveness of each streaming method will be measured.<br>
The player character will be possible to control manually, but also possible to set to automatic movement to some degree.<br>
It will also contain a section for asset streaming, which is a secondary objective but one that should integrate well with Unity's Addressables system which I'll be implementing for scenes.<br>
<br>
<img width="843" height="527" alt="sceneOverview0" src="https://github.com/user-attachments/assets/ecbf769f-385a-4b6c-a038-450339c048da" />
<br><br>
&nbsp;&nbsp;&nbsp;&nbsp; - The north scene is a balanced terrain scene.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - The south scene contains approximately 28.000 rock prefabs of the same kind.<br>
&nbsp;&nbsp;&nbsp;&nbsp; - The inner scene is for testing GameObject streaming speficically.<br>
<br><br>

These are the four (additive) scene loading methods I've decided to implement and compare based on my research:
| Basic | Asynchronous | Addressables (Scenes) | Addressables (GameObjects) |
|----------|-----------------|--------------------------|-------------------------------|
| (SceneManagement.LoadScene() | SceneManagement.LoadSceneAsync() | Addressables.LoadSceneAsync() | Addressables.LoadAssetAsync() |
| The basic way to load scenes in Unity.<br> No frills, just load a scene alongside those already loaded. | Loads a scene while minimizing blockage of other CPU tasks Unity wants to perform. | Loads a scene asynchronously according to user-set groupings of required components. | Loads asset(s) (GameObject, etc.) asynchronously according to user-set groupings of required components. |
<br><br>

The southern scene was purposefully filled with a large amount of items to better test load time differences, though this ultimately proved to have other drawbacks (the main one being the frame time graph clogging up due to poor overall performance, making it harder to parse). For this reason I made another version of the scene where each tree was replaced by a specific rock asset. This made it still take longer to load than the northern scene, which keeping frame times more stable once it does load.<br>
<br>


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img width="435" height="243" alt="fieldofTrees0" src="https://github.com/user-attachments/assets/6dd011a1-6cc5-4801-9000-b0991bf62d8e" />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img width="433" height="243" alt="fieldOfRocks0" src="https://github.com/user-attachments/assets/a7e2f12b-fc95-43b6-a5a0-38841ad3f9a0" />
<br><br>

When it comes to asset streaming, I wanted to compare two methods: Normal instantiation of prefabs versus Addressables asynchronous loading of the same prefabs.<br>
The implementation of this went hand-in-hand with streaming scenes as GameObjects, and as I'll go into more in a later section had a much greater impact for assets even if the implementation was the same.<br>
<br>
I set up an interior space where no extra terrain would need to be rendered, sectioned into 5 distinct zones containing prefabs. These zones were then made into prefabs, and grouped into Addressables groups according to contained assets. The idea was to see the reduction in load times both comparing those load methods, but also whether multiples of already loaded prefabs would allow for faster streaming within this interior scene.<br>
<br>

<img width="425" height="318" alt="sketch" src="https://github.com/user-attachments/assets/c23eb53b-cf61-4c21-be7a-68445d947699" />
&nbsp;&nbsp;&nbsp;&nbsp;
<img width="543" height="303" alt="BillyBeckerThesisProj - Main - Windows, Mac, Linux - Unity 6 6 (6000 6 4f1) _DX12_ 2026-11-26 21_08_01" src="https://github.com/user-attachments/assets/0d243149-3c27-4c26-b45f-5081281a47f7" />
<br><br>

I encountered quite a few difficulties while implementing Addressables specifically. Firstly, while it was easy enough to create basic Addressable Groups and load those at runtime, properly releasing them from memory was a somewhat obtuse process. This was due to how Unity treats AsyncOperationHandles, variables used to keep track of each asynchronous operation to see their status as well as reference back to them on unload.<br>
Secondly, grouping assets together in a way that makes sense is a puzzle in itself; Which asset prefabs do a specific scene need? Which materials, meshes and shaders to those in turn need? I'll go into this further in the reflections section, but Addressables require a lot of attention.<br>
The fourth and final method of streaming I implemented for scenes was based on converting them to prefabs and loading those in. Easy enough to implement after already doing the same for individual GameObjects, but harder to optimize than any of the prior three.<br>
<br>
During the course of the project I came across various tangential optimization techniques that work hand in hand to ease rendering memory use. One of these is "batching draw calls": meshes which share materials can (at runtime) be combined into needing fewer draw calls per frame. This is extremely easy to just toggle on for applicable GameObjects in Unity, as it's just two clicks per prefab. All that's needed is knowledge of the assets themselves so you know whether they're compatible or not. There's also GPU instancing, a shader option which will batch draw calls even further for objects that share both the same mesh AND material.<br> 
For the "Rocks" version of the southern scene in my project, this made a huge difference on frame times after loading the scene! So while not technically a level streaming technique, this will reduce CPU bottlenecks which in turn will help with other CPU tasks (including level streaming).<br>
<br><br>
<img width="1071" height="719" alt="PerformanceLog_20261123_1304 (Async (Rocks)) txt - Notepad 2026-11-26 21_10_10" src="https://github.com/user-attachments/assets/b6e0f6ad-8be5-46d8-884b-50498bfa76c1" />
<br><br>
An important aspect of the Unity project was logging data in order to compare and analyze it. I had two aspects I wanted to record: Load times and, more importantly, frame times. The frame times will help me determine severity of frame time spikes, the main focus of my thesis question.<br>
To record this data, I implemented a log which displays every load time and a graph which shows frame-for-frame how long each take to render. One a button press these can be exported both as a text file and a PNG which displays all time frame data of the session, also calculating and outputting various important data points for that session (average FPS, max MS/frame, etc.). In hindsight they would have been more accurate and easier to read if I excluded the initial startup frame times as they tended to be an unavoidable spike in themselves.<br>
<br><br><br><br>

<h2>Results</h2>
<br>

This is are the latest recorded data sets for each loading type, using the "Rocks" version of the southern scene to make the graphs more readable.<br>
<br>
Basic loading:
<img width="1200" height="600" alt="PerformanceLog_20261123_1303 (Basic (Rocks))_Annotated" src="https://github.com/user-attachments/assets/f7441c28-f510-43cd-a088-42ff4d2553b9" />
<br>
Asynchronous loading:
<img width="1200" height="600" alt="PerformanceLog_20261123_1304 (Async (Rocks))_Annotated" src="https://github.com/user-attachments/assets/60b32288-8f5f-4a92-9225-1f27fb80aa6b" />
<br>
Addressables loading using scenes:
<img width="1200" height="600" alt="PerformanceLog_20261123_1305 (Addressable Scenes (Rocks))_Annotated" src="https://github.com/user-attachments/assets/78c0cab0-51cb-4739-aae7-5d070346463a" />
<br>
Addressables loading using prefabs as scenes:
<img width="1200" height="600" alt="PerformanceLog_20261123_1351 (Addressables (Prefab (Rocks)))_Annotated" src="https://github.com/user-attachments/assets/eb47e2da-fb14-477a-a257-3245b21399ba" />
<br>

<br><br>
Scene loading breakdown:<br>
||<b>Basic</b>|<b>Async</b>|<b>Addressables<br>(Scenes)</b>|<b>Addressables<br>(Prefabs)</b>|
|<b>Highest load time</b>|
|<b>Lowest load time</b>|
|<b>Average FPS</b>|
|<b>Average MS/Frame</b>|
|<b>Highest MS/Frame</b>|
|<b>Lowest MS/Frame</b>|


<br><br>
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
