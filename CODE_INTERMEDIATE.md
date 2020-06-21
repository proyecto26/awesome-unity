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
<details open>
  <summary><b>Dictionaries</b></summary>

  ```csharp
  using UnityEngine;
  using System.Collections;
  using System.Collections.Generic;

  public class SceneController: MonoBehaviour {
      public Dictionary<string, Shape> shapeDictionary;

      void Start()
      {
          shapeDictionary = new Dictionary<string, Shape>();
          var shapeName = "Circle";
          var circle = new Shape { Name = shapeName };

          shapeDictionary.Add(shapeName, circle);
      }

      private void SetColorByName(string shapeName, Color color)
      {
          shapeDictionary[shapeName].SetColor(color);
      }

      void Update()
      {
          if (Input.GetKeyDown(KeyCode.C))
          {
              SetColorByName("Circle", Color.red);
          }
      }
  }
  ```
</details>
