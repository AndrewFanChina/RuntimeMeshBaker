﻿﻿﻿﻿# Runtime Mesh Baker v1.2.0 #
![](RMB_1200_630.png)

##Introduction:([中文版本](Manual_zh.md)):

Help you to combine meshes 、 materials and textures to reduce draw calls in runtime！
Got less draw calls than static and dynamic batching.
Got more resource saving than non-runtime baking.

- ★ support baking at runtime
- ★ Support baking for multi-times (re-baking)  
- ★ support the merging of multiple sub-meshes and multiple materials
- ★ Very simple to use, learn in 1 minutes
- ★ Works with any material and shader
- ★ The most effective solution of combination
- ★ Automaticly chek and configure the shaders
- ★ Runtime combine quickly
- ★ Runtime auto garbage recyling
- ★ Undo Supported, friendly UIs

Warning:  this tool cannot combine meshes which vertext count are above 64k, because it is the limit of unity.



Home Page:[https://github.com/AndrewFanChina/RuntimeMeshBaker](https://github.com/AndrewFanChina/RuntimeMeshBaker)
Support Mail: [mailoflonelywalker@qq.com](mailoflonelywalker@qq.com)
##Version Changes:

Version 1.2.0 2019.10.26
- new feature：Support baking for multi-times (re-baking) 
- new feature：support baking for seperated regions,bring some support for big world optimization
- obsolete feature：deep baking&SkinnedMesh Baking,for they are not real need at runtime for mobile deivices

Version 1.1.3 2017.11.15

- new feature: upgrade the effective of MildBaker
- Fixed bug: error combination of mesh for skinned-meshes
- Fixed bug: error combination of sub-meshes for MildBaker
- Add Example: unitychan for SkinnedMeshBaker
- Add Example: unitytank for MildBaker


Version 1.1.2 2017.9.18

- Support merging skinned-meshes of same material

Version 1.1.1 2017.9.10

- support add baking script at runtime
- support the merging of multiple sub-meshes and multiple materials


##Download URL:

[Runtime Mesh Baker Of AssetStore](https://www.assetstore.unity3d.com/#!/content/90510)

##Usage:

1. Get your GameObjects ready for baking, just put them into one tree hierarchy, all GameObjects have the same top parent.(not include GameObjects with movement)

2. Select the top parent,then select the menu "Window/Rumtime Mesh Baker/Add MeshBaker" 
At runtime,you can do it in you code:

		gameObject.AddComponent<BAT_MeshBaker>();
	
	
3. It's ok. let's run it. Auto baking should be working.

##Mild Baking of meshes:
![](mild_bake.png)

- Auto Bake: wheter do baking automatically,you can call the StartBake() function by your script.
- Seperate Shadow: sepretate the shadow casting, it will combine a shadow casting GameObject from the multi-group baked showing objects, and set the showing objects not casting shadows.
- Region Size: You can use the value to seperate the baking group by diffrent region (same by diffrent material) ,if it's not needed ,set the value with a big number.
- Show Region Gizmo: show the grid of diffrent regions.

##Baking Process:

1. Search the target gameobject, check all MeshFilters and MeshRenderers.
2. Find out all meshes and materials, and seperate the meshes into diffrent groups by materials(and regions)
3. Baking progress will just use the original materials and textures.it does not create new materials or textures.
4. Create a new baking node and start mesh baking by groups,if group's mesh vertex count is overflow, then bake to new one mesh.
5. Set the MeshFilters by new created mesh,and set MeshRenderers by the material of current group,the whole group share the same material.
6. Do clearing and hiding,it would hide the original MMeshRenderers because the new multi-group showing objects are created.







