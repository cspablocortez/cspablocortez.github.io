---
title: Refactoring Conditional Statements in Unity
date: 2024-07-20
layout: post
published: true
tags: [devlog, "Little Alchemy"]
---
In our `CollisionScript.cs` we currently have a chain of conditional statements (if-statements) that check the tag of two components to yield a new tag, which is the product of the two elements colliding.

This is what it looks like: 

```cs
private void OnCollisionEnter2D(Collision2D collision)
    {
        Debug.Log("OnCollisionEnter in CollisionScript.cs has activated");

        if (gameObject.tag == "fire" && collision.gameObject.tag == "water" ||
            gameObject.tag == "water" && collision.gameObject.tag == "fire")
        {
            uiManager.EnableButtonByTag("water vapor");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "fire" && collision.gameObject.tag == "earth" ||
        gameObject.tag == "earth" && collision.gameObject.tag == "fire")
        {
            uiManager.EnableButtonByTag("lava");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "water" && collision.gameObject.tag == "earth" ||
      gameObject.tag == "earth" && collision.gameObject.tag == "water")
        {
            uiManager.EnableButtonByTag("mud");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "lava" && collision.gameObject.tag == "water" ||
    gameObject.tag == "water" && collision.gameObject.tag == "lava")
        {    
            uiManager.EnableButtonByTag("rock");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "mud" && collision.gameObject.tag == "rock" ||
gameObject.tag == "rock" && collision.gameObject.tag == "mud")
        {  
            uiManager.EnableButtonByTag("clay");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "air" && collision.gameObject.tag == "rock" ||
gameObject.tag == "rock" && collision.gameObject.tag == "air")
        {
            uiManager.EnableButtonByTag("sand");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "fire" && collision.gameObject.tag == "air" ||
gameObject.tag == "air" && collision.gameObject.tag == "fire")
        {
            uiManager.EnableButtonByTag("smoke");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "water vapor" && collision.gameObject.tag == "water vapor")
        {
            uiManager.EnableButtonByTag("cloud");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "fire" && collision.gameObject.tag == "clay" ||
gameObject.tag == "clay" && collision.gameObject.tag == "fire")
        {
            uiManager.EnableButtonByTag("brick");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "fire" && collision.gameObject.tag == "clay" ||
gameObject.tag == "clay" && collision.gameObject.tag == "fire")
        {
            uiManager.EnableButtonByTag("brick");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "fire" && collision.gameObject.tag == "smoke" ||
gameObject.tag == "smoke" && collision.gameObject.tag == "fire")
        {
            uiManager.EnableButtonByTag("electric");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "electric" && collision.gameObject.tag == "cloud" ||
gameObject.tag == "cloud" && collision.gameObject.tag == "electric")
        {
            uiManager.EnableButtonByTag("thunder cloud");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "electric" && collision.gameObject.tag == "smoke" ||
gameObject.tag == "smoke" && collision.gameObject.tag == "electric")
        {
            uiManager.EnableButtonByTag("steam generator");
            Destroy(this.gameObject);
        }


        if (gameObject.tag == "brick" && collision.gameObject.tag == "rock" ||
gameObject.tag == "rock" && collision.gameObject.tag == "brick")
        {
            uiManager.EnableButtonByTag("castle");
            Destroy(this.gameObject);
        }
    }
```

To reduce the code in this method, we will use a data structure called a [dictionary](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2?view=net-8.0#definition). 

> **dictionary**: A special kind of list where each item has two parts: a key and a value.

The key is like a label, and the value is the information or thing that the key refers to. In the example we saw last time we used countries and their capitals. In C# we could make a dictionary for this example like this:

```cs

// First we create the dictionary:

Dictionary<string, string> capitalCities = new Dictionary<string, string>();

// Then we add its values:

capitalCities.Add("USA", "Washington, D.C.");
capitalCities.Add("Canada", "Ottawa");
capitalCities.Add("Mexico", "Mexico City");
capitalCities.Add("France", "Paris");
capitalCities.Add("Japan", "Tokyo");

// Then we can see the output:
Console.WriteLine(cities["Japan"]); // This will return "Tokyo"
```

Now that we know what dictionaries look like and how we can create them, we will begin *refactoring* our code. To refactor code means to maintain the same functionality while changing its form, namely to improve readability and modularity.

# Step 1 -  Update `OnCollisionEnter2d`

The dictionary containing the set of elements and the new element they produce when combined will be moved to the `Start()` method. This way our `OnCollisionEnter2D` will remain as minimal as possible. Here is what the updated `OnCollisionEnter2D` method will look like:

```cs
private void OnCollisionEnter2D(Collision2D collision)
    {
        Debug.Log("OnCollisionEnter in CollisionScript.cs has activated");

        string tag1 = gameObject.tag;
        string tag2 = collision.gameObject.tag;

        if (collisionResults.TryGetValue((tag1, tag2), out string result) ||
            collisionResults.TryGetValue((tag2, tag1), out result))
        {
            uiManager.EnableButtonByTag(result);
            Destroy(this.gameObject);
        }
    }
```

With this change, our method will the dictionary for the tags involved in the collision, and if a result is found, then it will enable the corresponding button while destroying the GameObject.

The heavy lifting is done here by the `TryGetValue` method, which accepts two parameters: the name of the key(s) we are looking for and a variable name for the result if it finds one. The variable name comes after the `out` keyword. In our case, we called this `result`, but you can rename it to `newElementTag` or whatever you prefer. 

Here is what the actual dictionary looks like. Remember that we have moved the tag checking to our `Start()` method.

# Step 2 - Defining the dictionary

First we define the variable `collisionResults` above our methods like so:

```cs
public class CollisionScript : MonoBehaviour
{
    private UIManager uiManager;
    private Dictionary<(string, string), string> collisionResults;
...
}
```

# Step 3 - Populating the dictionary

```cs
void Start()
    {
        uiManager = FindObjectOfType<UIManager>();
        Debug.Log(uiManager);

        collisionResults = new Dictionary<(string, string), string>
        {
            { ("fire", "water"), "water vapor" },
            { ("water", "fire"), "water vapor" },
            { ("fire", "earth"), "lava" },
            { ("earth", "fire"), "lava" },
            { ("water", "earth"), "mud" },
            { ("earth", "water"), "mud" },
            { ("lava", "water"), "rock" },
            { ("water", "lava"), "rock" },
            { ("mud", "rock"), "clay" },
            { ("rock", "mud"), "clay" },
            { ("air", "rock"), "sand" },
            { ("rock", "air"), "sand" },
            { ("fire", "air"), "smoke" },
            { ("air", "fire"), "smoke" },
            { ("water vapor", "water vapor"), "cloud" },
            { ("fire", "clay"), "brick" },
            { ("clay", "fire"), "brick" },
            { ("fire", "smoke"), "electric" },
            { ("smoke", "fire"), "electric" },
            { ("electric", "cloud"), "thunder cloud" },
            { ("cloud", "electric"), "thunder cloud" },
            { ("electric", "smoke"), "steam generator" },
            { ("smoke", "electric"), "steam generator" },
            { ("brick", "rock"), "castle" },
            { ("rock", "brick"), "castle" }
        };
}
```


