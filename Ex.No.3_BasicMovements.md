# Ex.No: 3  Basic movements in Unity 
### DATE: 30/04/26                                                                            
### REGISTER NUMBER : 212223240127
### AIM: 
 To learn the basic movements translation,scaling and rotation of game objects through code.
### Procedure:
1. Setup the Scene
2. Open Unity and create a 3D Scene.
3. Add three objects:Cube → Rename to Object1 (for movement),Sphere → Rename to Object2 (for rotation).Capsule → Rename to Object3 (for scaling).
4. Add the Script,Create a C# Script → Name it TransformOperations.cs.
5. Write the code for translation,scaling and rotation,save and close the script
6. Save the script
7. Select any empty GameObject (or create one: GameObject → Create Empty).
8. Attach the TransformOperations script to it.
9. In the Inspector, assign Object1 → Drag the Cube,Object2 → Drag the Sphere.Object3 → Drag the Capsule.
10. Run the Scene Press Play ▶️ in Unity
11. Stop the program.
### Program 
```
using UnityEngine;

public class TransformOperations : MonoBehaviour
{
    public Transform object1;
    public Transform object2;
    public Transform object3;

    public float moveSpeed = 2f;
    public float rotateSpeed = 50f;
    public float scaleSpeed = 0.5f;

    void Update()
    {
        // Movement
        if (object1 != null)
        {
            object1.position += Vector3.right * moveSpeed * Time.deltaTime;
        }

        // Rotation
        if (object2 != null)
        {
            object2.Rotate(Vector3.up * rotateSpeed * Time.deltaTime);
        }

        // Scaling
        if (object3 != null)
        {
            float scaleChange =
                Mathf.PingPong(Time.time * scaleSpeed, 1f) + 0.5f;

            object3.localScale =
                new Vector3(scaleChange, scaleChange, scaleChange);
        }
    }
}
```
### Output:

<img width="1919" height="1084" alt="image" src="https://github.com/user-attachments/assets/0e6f12a9-81f7-489c-9105-05b80794d456" />

### Result:
Thus the basic movement is learned through scripting


