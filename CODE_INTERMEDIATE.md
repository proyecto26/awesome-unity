# Code Intermediate
A list of intermediate topics working with C# in Unity

<details open>
  <summary><b>Generic Lists</b></summary>

  ```csharp
  using UnityEngine;
  using System.Collections;
  using System.Collections.Generic;

  public class SceneController: MonoBehaviour {

      public List<string> shapes;

      void Start()
      {
        shapes = new List<string> { "circle", "square", "triangle", "octagon" };
        shapes.Add("rectangle");
        shapes.Insert(2, "diamond");

        shapes.Sort();
        var triangleShape = shapes.Find(s => s == "triangle");
      }
  }
  ```
</details>
