# Awesome Unity
A community driven resources for Unity development.

## Code Examples
<details>
  <summary>Player Movement</summary>
  
  ```csharp
using UnityEngine;
using System.Collections;

public class PlayerController : MonoBehaviour {

    public float speed;

    private Rigidbody rb;

    void Start ()
    {
        rb = GetComponent<Rigidbody>();
    }

    void FixedUpdate ()
    {
        float moveHorizontal = Input.GetAxis ("Horizontal");
        float moveVertical = Input.GetAxis ("Vertical");

        Vector3 movement = new Vector3 (moveHorizontal, 0.0f, moveVertical);

        rb.AddForce (movement * speed);
    }
}
  ```
</details>
<details>
  <summary>Moving Camera</summary>
  
  ```csharp
using UnityEngine;
using System.Collections;

public class CameraController : MonoBehaviour {

    public GameObject player;

    private Vector3 offset;

    void Start ()
    {
        offset = transform.position - player.transform.position;
    }

    void LateUpdate ()
    {
        transform.position = player.transform.position + offset;
    }
}
  ```
</details>
<details>
  <summary>Collectable Objects</summary>
  
  ```csharp
using UnityEngine;
using System.Collections;

public class PlayerController : MonoBehaviour {

    void OnTriggerEnter(Collider other) 
    {
        if (other.gameObject.CompareTag ("Pick Up"))
        {
            other.gameObject.SetActive (false);
        }
    }
}
  ```
</details>
<details>
  <summary>Score Display</summary>
  
  ```csharp
using UnityEngine;
using UnityEngine.UI;
using System.Collections;

public class PlayerController : MonoBehaviour {

    public Text countText;
    public Text winText;
    private int count;

    void Start ()
    {
        count = 0;
        SetCountText();
        winText.text = "";
    }

    void OnTriggerEnter(Collider other) 
    {
        if (other.gameObject.CompareTag ( "Pick Up"))
        {
            count = count + 1;
            SetCountText ();
        }
    }

    void SetCountText ()
    {
        countText.text = "Count: " + count.ToString ();
        if (count >= 12)
        {
            winText.text = "You Win!";
        }
    }
}
  ```
</details>
<details>
  <summary>Behaviour Components</summary>
  
  ```csharp
using UnityEngine;
using System.Collections;

public class ExampleBehaviourScript : MonoBehaviour
{
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.R))
        {
            GetComponent<Renderer> ().material.color = Color.red;
        }
    }
}
  ```
</details>
<details>
  <summary>Check State</summary>
  
  ```csharp
using UnityEngine;
using System.Collections;

public class CheckState : MonoBehaviour
{
    public GameObject myObject;

    void Start ()
    {
        Debug.Log("Active Self: " + myObject.activeSelf);
        Debug.Log("Active in Hierarchy" + myObject.activeInHierarchy);
    }
}
  ```
</details>
<details>
  <summary>Translate and Rotate</summary>
  
  ```csharp
using UnityEngine;
using System.Collections;

public class TransformFunctions : MonoBehaviour
{
    public float moveSpeed = 10f;
    public float turnSpeed = 50f;
    
    void Update ()
    {
        if(Input.GetKey(KeyCode.UpArrow))
            transform.Translate(Vector3.forward * moveSpeed * Time.deltaTime);
        
        if(Input.GetKey(KeyCode.DownArrow))
            transform.Translate(-Vector3.forward * moveSpeed * Time.deltaTime);
        
        if(Input.GetKey(KeyCode.LeftArrow))
            transform.Rotate(Vector3.up, -turnSpeed * Time.deltaTime);
        
        if(Input.GetKey(KeyCode.RightArrow))
            transform.Rotate(Vector3.up, turnSpeed * Time.deltaTime);
    }
}
  ```
</details>
<details>
  <summary>Look At</summary>
  
  ```csharp
using UnityEngine;
using System.Collections;

public class CameraLookAt : MonoBehaviour
{
    public Transform target;
    
    void Update ()
    {
        transform.LookAt(target);
    }
}
  ```
</details>
<details>
  <summary>Linear Interpolation</summary>
  
  ```csharp
// In this case, result = 4
float result = Mathf.Lerp (3f, 5f, 0.5f);
// The Mathf.Lerp function takes 3 float parameters: one representing the value to interpolate from; another representing the value to interpolate to and a final float representing how far to interpolate

Vector3 from = new Vector3 (1f, 2f, 3f);
Vector3 to = new Vector3 (5f, 6f, 7f);

// Here result = (4, 5, 6)
Vector3 result = Vector3.Lerp (from, to, 0.75f);

// The same principle is applied when using Color.Lerp.
// In the Color struct, colours are represented by 4 floats representing red, blue, green and alpha.
// When using Lerp, these floats are interpolated just as with Mathf.Lerp and Vector3.Lerp.

void Update ()
{
    light.intensity = Mathf.Lerp(light.intensity, 8f, 0.5f * Time.deltaTime);
    // With deltaTime, the change to intensity would happen per second instead of per frame.
}
  ```
</details>
<details>
  <summary>GetAxis Horizontal and Vertical</summary>
  
  ```csharp
using UnityEngine;
using System.Collections;

public class DualAxisExample : MonoBehaviour 
{
    public float range;
    public GUIText textOutput;

    void Update () 
    {
        float h = Input.GetAxis("Horizontal");
        float v = Input.GetAxis("Vertical");
        float xPos = h * range;
        float yPos = v * range;
        
        transform.position = new Vector3(xPos, yPos, 0);
        textOutput.text = "Horizontal Value Returned: "+h.ToString("F2")+"\nVertical Value Returned: "+v.ToString("F2");    
    }
}
  ```
</details>

## Editor
- [UIWidgets](https://github.com/UnityTech/UIWidgets) - A Unity Package which helps developers to create, debug and deploy efficient, cross-platform Apps.

## Controllers
- [2D-Platformer-Hunter](https://github.com/ta-david-yu/2D-Platformer-Hunter) - A 2D Platformer Controller in Unity.

## Networking
- [RestClient](https://github.com/proyecto26/RestClient) - 🦄 Simple HTTP and REST client for Unity based on Promises, also supports Callbacks! 🎮.

## Platforms
- [Native Toolkit](https://github.com/ryanw3bb/unity-native-toolkit) - Easily integrate native iOS & Android functionality into Unity projects.

## Guides
- [Coding in C# in Unity for beginners](https://unity3d.com/learning-c-sharp-in-unity-for-beginners) - The very basics of coding, like variables, functions and classes, and how to use them.

## Tutorials
- [Introduction to Roll-a-Ball](https://youtu.be/RFlh8pTf4DU) - An introduction to the Roll-a-ball project, showing the final game and describing what will be covered in this tutorials.
- [Setting up the Game](https://youtu.be/W_fAidYRGzs) - Creating a new project and setting up the basic game.
- [Moving the Player](https://youtu.be/7C7WWxUxPZE) - Moving the player object using player input and physics forces.
- [Moving the Camera](https://youtu.be/Xcm5H2J95iI) - Moving the camera relative to the player.
- [Setting up the Play Area](https://youtu.be/dahT0wRVO1Q) - Setting up the play area.
- [Creating Collectable Objects](https://youtu.be/HlDGSStxuHI) - Creating and placing the "Pick Up" collectables.
- [Collecting the Pick Up Objects](https://youtu.be/XtR29MmzuT0) - Collecting the pick-up objects; discussing physics, collisions and triggers.
- [Displaying the Score and Text](https://youtu.be/bFSLI2cmYYo) - Counting, displaying text and ending the game.
- [Building the Game](https://youtu.be/hSg3e1M3hKY) - Building the game as a Standalone application.
- [Scripts as Behaviour Components](https://youtu.be/Z0Z7xc18CcA) - Learn about the behaviour component that is a Unity script, and how to Create and Attach them to objects.
- [Variables And Functions](https://youtu.be/-c1RsydH2nA) - What are Variables and Functions, and how do they store and process information for us?
- [Conventions and Syntax](https://youtu.be/0mks0QaWCNQ) - Learn about some basic conventions and syntax of writing code.
- [If Statements](https://youtu.be/PQihrWCOSic) - How to use IF statements to set conditions in your code.
- [Loops](https://youtu.be/Jefkb3Gm7vE) - How to use the For, While and Do-While Loops as well as the For Each loop to repeat actions in code.
- [Scope and Access Modifiers](https://youtu.be/_0oBLCJcpCs) - Understanding variable & function scope and accessibility.
- [Awake and Start](https://youtu.be/4QdjoV63wjM) - How to use Awake and Start, two of Unity's initialisation functions.
- [Update and FixedUpdate](https://youtu.be/u42aWzAIAqg) - How to effect changes every frame with the Update and FixedUpdate functions, and their differences.
- [Vector Maths](https://youtu.be/e3z91RqZPAk) - A primer on Vector maths - as well as information on the Dot and Cross products.
- [Enabling and Disabling Components](https://youtu.be/PCdg3cnQfZ4) - How to enable and disable components via script during runtime.
- [Activating GameObjects](https://youtu.be/MhPFB-rAdlg) - Learn about the behaviour component that is a Unity script, and how to Create and Attach them to objects.
- [Translate and Rotate](https://youtu.be/32JkMANaMpk) - How to use the two transform functions Translate and Rotate to effect a non-rigidbody object's position and rotation.
- [LookAt](https://youtu.be/cAAqf5J7_9w) - How to make a game object's transform face another's by using the LookAt function.
- [Destroy](https://youtu.be/pRDj3jss5t8) - How to use the **Destroy** function to remove GameObjects and Components at runtime.
- [GetButton and GetKey](https://youtu.be/-A7D5Rcumz4) - How to get button or key for input and how these axes behave / can be modified with the Input manager.
- [GetAxis](https://youtu.be/MK4OmsViqMA) - How to "get axis" based input for your games in Unity and how these axes can be modified with the Input manager.
- [How to Play Test Game Mods (Official Unity Tutorial)](https://youtu.be/kZCJmKVQAPQ) - In the Play Testing In-Editor Tutorial, you will learn how to play and mod your Microgame in Unity.

## Resources
- [GameDev-Resources](https://github.com/Kavex/GameDev-Resources) - A wonderful list of Game Development resources.

## Tools
- [OpenUPM](https://openupm.com) - Open Source Unity Package Registry.

## YouTube Channels
- [Brackeys](https://www.youtube.com/user/Brackeys/videos) - Game Dev Tutorials

## Other Awesome Lists
- [awesome-unity3d](https://github.com/insthync/awesome-unity3d) - A categorized collection of awesome opensource unity3d repos.
- [Awesome Unity Open Source on GitHub (800+)](https://github.com/baba-s/awesome-unity-open-source-on-github) - A categorized collection of awesome Unity open source on GitHub.
- [Awesome Unity FREE](https://github.com/netpyoung/awesome-unity-free) - A community driven list of useful Unity Game Engine "FREE" packages, libraries and others.
- [Awesome Unity Community](https://github.com/UnityCommunity/AwesomeUnityCommunity) - A categorized community-driven collection of high-quality awesome Unity assets, projects, and resources.

## Supporting 🍻
I believe in Unicorns 🦄
Support [me](http://www.paypal.me/jdnichollsc/2), if you do too.

## Happy coding 💯
Made with ❤️

<img width="150px" src="https://avatars0.githubusercontent.com/u/28855608?s=200&v=4" align="right">
