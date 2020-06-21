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
<details open>
  <summary><b>Queues</b></summary>

  ```csharp
  using UnityEngine;
  using System.Collections;
  using System.Collections.Generic;

  public class EnemiesController: MonoBehaviour {
      public Queue<Enemy> enemyQueue;

      void Start()
      {
          enemyQueue = new Queue<Enemy>();
          enemyQueue.Enqueue(new Enemy { Name = "Boss1" });
          enemyQueue.Enqueue(new Enemy { Name = "Boss2" });
          enemyQueue.Enqueue(new Enemy { Name = "Boss3" });
      }

      public Enemy GetFirstEnemy()
      {
          if (enemyQueue.Count > 0) {
              var enemy = enemyQueue.Dequeue();
              // Call any method if you want
              enemy.Animate();
              return enemy;
          }
          Debug.Log("Enemy queue is empty");
          return null;
      }
  }
  ```
</details>
<details open>
  <summary><b>Stacks</b></summary>

  ```csharp
  using UnityEngine;
  using System.Collections;
  using System.Collections.Generic;

  public class EnemiesController: MonoBehaviour {
      public Stack<Enemy> enemyStack;

      void Start()
      {
          enemyStack = new Stack<Enemy>();
          enemyStack.Push(new Enemy { Name = "Final boss" });
          enemyStack.Push(new Enemy { Name = "Superboss" });
          enemyStack.Push(new Enemy { Name = "Miniboss" });
      }

      public Enemy GetNextBoss()
      {
          if (enemyStack.Count > 0) {
              var enemy = enemyStack.Pop();
              // Call any method if you want
              enemy.Animate();
              return enemy;
          }
          Debug.Log("Final boss was killed");
          return null;
      }
  }
  ```
</details>
