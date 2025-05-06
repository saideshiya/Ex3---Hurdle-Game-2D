# Ex3---Hurdle-Game-2D

## AIM:
To develop a 2D game using C# program in Unity.

## ALGORITHM:
# STEP 1: 
Create a 2D project in Unity.

# STEP 2: 
Add player, hurdles, coins, track in the frame and add the valid collider2D component.

# STEP 3: 
Click Assets -> Create -> # Script.

# STEP 4: 
Create player.cs and coinmanger.cs script and add C# code.

# STEP 5: 
Click canvas -> Gamemanager -> add Score and value.

# STEP 6: 
Drag the script to player and coin.

# STEP 7: 
Run the scene and display the output.
## PROGRAM:
# Player
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using System.Threading;

public class player : MonoBehaviour
{
    public float speed;
    public float jumpforce;
    private Rigidbody2D rb;
    public CoinManager cc;
    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    // Update is called once per frame
    void Update()
    {
        float moveinp = Input.GetAxisRaw("Horizontal");
        transform.position += new Vector3(moveinp, 0, 0) * speed * Time.deltaTime;

        if (Input.GetKeyDown(KeyCode.Space) && Mathf.Abs(rb.velocity.y) < 0.001f)
        {
            rb.AddForce(new Vector2(0, jumpforce), ForceMode2D.Impulse);
        }
    }
    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.CompareTag("Destroy"))
        {
            cc.coincount++;
            Destroy(collision.gameObject);
        }
    }
}

```
# CoinManager
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class CoinManager : MonoBehaviour
{
    public int coincount;
    public Text value;
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        value.text = coincount.ToString(); 
    }
}

```

   

## OUTPUT:

![image](https://github.com/user-attachments/assets/438bdc27-0118-47fd-8cc8-388156a6029c)


![image](https://github.com/user-attachments/assets/50f1ecca-89a7-46b7-9242-bac509550b35)

![image](https://github.com/user-attachments/assets/2d9731c7-fe52-42eb-b56f-1716ffb5f5b0)





## RESULT:
2D game using C# program in Unity is successfully developed....
