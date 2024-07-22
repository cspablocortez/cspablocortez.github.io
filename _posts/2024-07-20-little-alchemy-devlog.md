---
title: Little Alchemy Devlog
date: 2024-07-20
layout: post
published: false
tags: [devlog]
---

Current bugs:

`NullReferenceException in combination.cs:14`

There is an object `gameManager` that has not been instantiated.

---
Working combinations (with same console output):

- Earth and fire

To begin testing, we disabled `combination.cs` on the earth and fire prefabs to begin activating `CollisionScript.cs`.

This worked after changing the method and parameter names from `OnCollision` to `OnCollision2D`. So far it works for Fire and Water, yielding `Water Vapor` and activating the corresponding button through the following:

```csharp
private void OnCollisionEnter2D(Collision2D collision)
    {
        if (gameObject.tag == "foo" && collision.gameObject.tag == "bar" ||
            gameObject.tag == "bar" && collision.gameObject.tag == "foo")
        {

          Debug.Log("STEP 3: Call UIManager method EnableButtonByTag() after collision.");
          uiManager.EnableButtonByTag("foobar");
        }
    }
```
