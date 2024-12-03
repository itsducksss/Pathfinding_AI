# Pathfinding_AI
This tutorial will showcase how to create a basic pathfinding AI, and show how debugg (add/draw gizmos) that will allow the person to see the path of the AI as it follows an object (in this tutorial the player).

# Prerequisites
Before approaching this tutorial, you will need a current version of Unity and a code editor (such as Microsoft Visual Studio Community) installed and ready to use.

This tutorial was created with Unity 2022.3 LTS and Microsoft Visual Studio Community 2022 versions. It should work with earlier or later versions. But you should check the release notes for other versions as the Editor controls or Scripting API functions may have changed. This is as the changes in the updates can cause errors to occur that may have been fixed or changed within different versions of the Unity and Visual Studio softwares.

If you need help installing Unity you can find many online tutorials such as: https://learn.unity.com/tutorial/install-the-unity-hub-and-editor

You will also need to know how to create an empty project, add primitive objects to your scene, create blank scripts, and run projects from within the editor. If you need help with this, there is a short video demonstrating how to do all of these things here:

https://www.youtube.com/watch?v=eQpWPfP1T6g

In this tutorial we will be importing TextMeshProEssentials Unity Package which will be shown in the tutorial.

# Primary Objectives
The primary objective of this tutorial is to create an GameObject, that will follow the player, and show its path and how it changes d3epending on the where the player is (with factors such as obstacles).

# Preview

https://github.com/user-attachments/assets/83fe753d-f881-4bed-a9dc-b50228bdd021

This video shows how the AI character follows the player and the debugg shows how the AI adjusts its movements depending on where the player is and the obstacles in it's path..

# Getting Started

For this tutorial you will need to have a 2 capsules in the scene. For this tutorial, the playable character is represented by a green capsule in the scene. In this scene, the white capsule will represent the AI in the scene. You will also need to download the Navigation AI package in Unity's registry.

![image](https://github.com/user-attachments/assets/8a32a62c-3201-4cd1-8c03-0553125c88a6)

- using just means that it will use that system e.g. if it said using UnityEngine, that just means that thescript has components that will utilise the Unity Engine system.
- using UnityEngine.AI just means that the script will use the elements that is within the UnityEngine.AI system. This can be seen in the NavMeshAgent which is part of that system.
- [public](https://discussions.unity.com/t/public-or-private/9977) means that anything anywhere has direct access to whatever it is.
- [class](https://medium.com/nerd-for-tech/what-are-classes-in-unity-620e467fd4f) is used to organize items in Unity. it is a datatype that represents something else.
- MonoBehaviour refers to  Unity supplied class that attaches directly to GameObjects, which we base a new class onto.
- [Transform](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Component-transform.html) just refers to the position/location of where a GameObject is within a scene.
- playerTransform will then refer to the player's transform.
- [NavMeshAgent](https://docs.unity3d.com/ScriptReference/AI.NavMeshAgent.html) refers to a component that can be attached onto a mobile (movable) GameObject that causes the GameObject to navigate the scene
- [start](https://docs.unity3d.com/ScriptReference/MonoBehaviour.Start.html) just means that this action will occur at the satrt of the scene and will be called upon
- [GetComponent](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html) just means that whatever GameObject this script is attached onto, it will get the stated component
- agent is what will be used in the code which just refers to the NavMeshAgent component.
- void refers to a function can return normally without the need of a value.
- [OnDrawGizmos](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnDrawGizmos.html) refers to gizmos that are used in debugging in Unity and just means that it will draw these "Gizmos" to show visual aid in the Unity Scene when playing the scene.
- agent.destination, just refers to what the NavMeshAhent is following, which is the player's transform/ position, which will be shown in the scene (not in the game) screen.

![image](https://github.com/user-attachments/assets/ce8f6949-3e19-45ce-9046-b2a0032d1f75)

- bool refers to
- desiredVelocity
- path
- if
- velocity in this script just refers to
- Gizmos
- Color
- Color.green means that the color will be green.
- Gizmos.color
- Gizmos.color = Color.green means that the line that will be shown that represents the velocity of the AI agent will be shown in the color green when youb play the scene.
- DrawLine
- transform.position
- agent.velocity
- desiredVelocity means that the Gizmos shown will be where the Ai wants to go within the scene. In the instance of this tutorial the AI is made to follow the player character, which means that the desired path of the AI will be the playable character meaning that the line of the desiredVelocity should follow and adjust to where the player is.
- Color.red means that the color will be red.
- Color.black means that the color used will be black.
- var
- agentpath
- var agentpath
- agent.path
- [Vector3](https://docs.unity3d.com/ScriptReference/Vector3.html) refers to the position using all 3 axis x, y, z which can be represented on a 3d space.
- preCorner
- foreach
- corner
- var corner
- in
- agentpath.corners
- Gizmos.DrawLine(prevCorner, corner) just refers to where the corners of where the AI can go to it will connect the previous corner to the next corner on it's path (towards where it wants to go).
- DrawSphere means that spheres will be drawn/shown on the scene in that area.
- Gizmos.DrawSphere(corner, 0.1f), means that at the corners of the path of the AI, a sphere will be drawn in the scene to represent it.
- prevCorner = corner means thata corner can be refered to as a corner within the script.

This just means that the script will show the desired velocity (desired direction) of the AI shown by the line in the colour of red, the velocity (is where the AI is navigating and how it adjusts to the desiredVelocity as the target moves) of the AI represented by the line in the colour green, and the path of the AI which is shown using lines and spheres in the colour black in the scene. The path in the scene is shown using the spheres which represents the corners, and the lines which connect the corners and the previous corners, of where the AI can and cannot go in the scene, which eventually connect to the target in teh scene which in this tutorial is the player.

