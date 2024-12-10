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

For this tutorial you will need to have a 2 capsules in the scene, both capsules should have a capsule collider onto them, and with one of the capsules to have a PlayerMovement or [Basic Character Movement](https://github.com/itsducksss/Basic-Character-Movement) script. For this tutorial, the playable character is represented by a green capsule in the scene. You should also have at a plane in the scene with a mesh collider which the player and the AI can walk on. In this scene, the white capsule will represent the AI in the scene. You will also need to download the Navigation AI package in Unity's registry.

![image](https://github.com/user-attachments/assets/dfe1c099-ac93-4528-a606-525cb435ff01)

We will first add the NavMeshAgent onto the capsule we want to follow the player. Which is white for this tutorial. We can then leave it as a humanoid type of AI for the NavMeshAgent.

![image](https://github.com/user-attachments/assets/d4ec2b38-507a-442d-a5a3-d01acede531f)

We will then open the Navigation menu which will bake the maps (create) on which the AI can and cannot go onto. We will mainly use the Navigation (Obsolete) window, however in older Unity versions prior to 2021 may not have this and may instead have these functions on the Navigation window which should have the same functionality.

https://github.com/user-attachments/assets/e50e44e4-0ef4-487d-a0e7-f779212c86ec

This video just shows the Navigation windows as well as how to bake a map in which the AI can walk onto. The video shows how the map adjusts to an obstacle when added into the scene, as well as what to do when the navigation window is closed and how to reopen the window. As seen in the video we open the Naviagtion (Obselete) window and slect the plane in which we want the AI to walk onto. we the bake the mesh usingthe Navigation (Obselete) window.

![image](https://github.com/user-attachments/assets/233a1a12-af68-4cee-b805-fdf44aafc0e2)

This mesh can be adjusted using the Naviagtion window as seen above by adjusting these values.

We then create a script called AiLocomotion, which will use the NavMesh we added onto the Ai capsule to move the capsule towards the playable character capsule (green) using the player's Transform values to  determine the position of the player within the scene. 

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

- bool refers to a value that is either true or false.
- velocity in this script just refers to how the AI is moving which adjusts to the desired velocity of the AI from where the AI currently is.
- desiredVelocity in this script just refers to where the AI wants to go this just means that as the character moves that the line shown to represent the desired velocity will show where it wants to go (the target) almost immediatley as the player moves.
- path this refers to route the AI is planning to take to get towards the traget which would be the player in this tutorial.
- [if()](https://imran-momin.medium.com/if-else-statements-unity-c-3ea7e8bc8eee) is an if statement which is used to help show if a block of code can be exectuted if specified conditions is true. in this case if the player_detection and input is true then the print "-"
- [Gizmos](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/Gizmos.html) this used to help provide visual debugging and setups within a scene when you play. This is not visible in the game view but is visible in the scene view of the unity project.
- [Color](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/Color.html) this just refers to a RGBA colors in Unity.
- Color.green means that the color will be green.
- Gizmos.color this just means that the Gizmos will be x color.
- Gizmos.color = Color.green means that the line that will be shown that represents the velocity of the AI agent will be shown in the color green when youb play the scene.
- [DrawLine](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/Gizmos.DrawLine.html) this just means that a line will be drawn from the AI towards the target (desired velocity).
- transform.position this just means that it uses the Tranform component and the values stated in there to determine the position of a certain GameOvject within a scene.
- agent.velocity this just means that it uses the NavMeshAgent's comonent to create and show the velocity when debugging.
- desiredVelocity means that the Gizmos shown will be where the Ai wants to go within the scene. In the instance of this tutorial the AI is made to follow the player character, which means that the desired path of the AI will be the playable character meaning that the line of the desiredVelocity should follow and adjust to where the player is.
- Color.red means that the color will be red.
- Color.black means that the color used will be black.
- [var](https://docs.unity3d.com/2019.3/Documentation/Manual/bolt-variables.html) is just a shortened term for a variable.
- agentpath this just means that agentpath is a areference to something.
- var agentpath this means that the variable is called agentpath.
- agent.path this means that the variable referenced as agentpath is using the NavMeshAgent component and the oath its taking.
- [Vector3](https://docs.unity3d.com/ScriptReference/Vector3.html) refers to the position using all 3 axis x, y, z which can be represented on a 3d space.
- prevCorner this just means the previous corner Later in teh script prevCorner = corner just means that the prevCorner is the smae as the corner in the scene when drawing the Gizmos.
- [foreach](https://www.reddit.com/r/csharp/comments/kwz815/can_someone_explain_foreach_loops/)
- corner this is in reference to the corner in the baked mesh of where the AI can and cannot go to and show its path of the AI.
- var corner this just means that each of the corners in the agents path.
- in this just means that the corner is in the agentpath.
- agentpath.corners this means that the script will use the corners that are in the agentpath component to function.
- Gizmos.DrawLine(prevCorner, corner) just refers to where the corners of where the AI can go to it will connect the previous corner to the next corner on it's path (towards where it wants to go).
- DrawSphere means that spheres will be drawn/shown on the scene in that area.
- Gizmos.DrawSphere(corner, 0.1f), means that at the corners of the path of the AI, a sphere will be drawn in the scene to represent it.
- prevCorner = corner means thata corner can be refered to as a corner within the script.

This just means that the script will show the desired velocity (desired direction) of the AI shown by the line in the colour of red, the velocity (is where the AI is navigating and how it adjusts to the desiredVelocity as the target moves) of the AI represented by the line in the colour green, and the path of the AI which is shown using lines and spheres in the colour black in the scene. The path in the scene is shown using the spheres which represents the corners, and the lines which connect the corners and the previous corners, of where the AI can and cannot go in the scene, which eventually connect to the target in teh scene which in this tutorial is the player.

![image](https://github.com/user-attachments/assets/665ad54e-486c-4cdf-af9a-094e7480483d)

if you want to create obstacles for the AI, we can add a cube and scale the cube as desired and add the NavMeshObstacle onto it. We then leave it as a box type obstacle for the shape, which just means that the shape of the obstacle is box-like in shape which can affect the way the baked mesh for where the AI can and cannot go to.
