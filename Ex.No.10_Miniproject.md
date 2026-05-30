# Ex.No: 10  Implementation of 2D/3D game -------------------
### DATE: 30/05/26                                                                            
### REGISTER NUMBER : 212223240127
### AIM: 
To develop a game a simple 3D Maze Game in Unity 
### Algorithm:
```
1. Start a new 3D Unity project and create a plane as the maze base.
2. Add cube walls and design the maze layout.
3. Create a Player capsule and attach PlayerController.cs for movement.
4. Position the Main Camera and attach CameraFollow.cs to smoothly track the player.
5. Create a Goal object with a WinTrigger.cs script to detect when the player reaches it.
6. Add lights, textures, and build for testing.
```  
### Program:
```
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    public float speed = 5f;

    void Update()
    {
        float moveHorizontal = Input.GetAxis("Horizontal");
        float moveVertical = Input.GetAxis("Vertical");

        Vector3 movement = new Vector3(moveHorizontal, 0.0f, moveVertical);
        transform.Translate(movement * speed * Time.deltaTime, Space.World);
    }
}

using UnityEngine;

public class CameraFollow : MonoBehaviour
{
    [SerializeField] Transform player;  // Assign player object in Inspector
    [SerializeField] float distance = 5f;
    [SerializeField] float height = 3f;
    [SerializeField] float smoothSpeed = 0.125f;

    void LateUpdate()
    {
        Vector3 desiredPosition = player.position - player.forward * distance + Vector3.up * height;
        Vector3 smoothedPosition = Vector3.Lerp(transform.position, desiredPosition, smoothSpeed);
        transform.position = smoothedPosition;
        transform.LookAt(player);
    }
}

using UnityEngine;
using UnityEngine.SceneManagement;

public class WinTrigger : MonoBehaviour
{
    public GameObject player;

    private void OnTriggerEnter(Collider other)
    {
        if (other.gameObject == player)
        {
            Debug.Log("Maze Completed!");
            // You can load a success screen or restart
            SceneManager.LoadScene(SceneManager.GetActiveScene().name);
        }
    }
}
```
### Output:

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9b9d62d2-2a42-4581-918a-bc96145a8c2f" />

<img width="1915" height="1079" alt="image" src="https://github.com/user-attachments/assets/99344f04-2690-499d-b518-b0fa982ec386" />

### Result:
Hence a functional 3D Maze Game was successfully created using Unity and C# with player movement, camera tracking, and game-end trigger events.
