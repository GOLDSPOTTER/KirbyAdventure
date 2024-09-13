using System.Collections;
using System.Collections.Generic;
using Unity.VisualScripting;
using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    Rigidbody rb;
    public float movementSpeed = 6f;
    public float jumppower = 9f;
    public Transform groundCheck;
    public LayerMask ground;

    // Start is called before the first frame update
    void Start()
    {
        rb = GetComponent<Rigidbody>();
        
    }
    
    // Update is called once per frame
    void Update()
    {
        //Horizontal and vertical are swapped because the angle is on the side
        float horizontalInput = Input.GetAxis("Vertical"); 
        float verticalInput = Input.GetAxis("Horizontal"); 
        

            

        rb.velocity = new Vector3(horizontalInput * movementSpeed, rb.velocity.y, verticalInput * movementSpeed);


        if (Input.GetButtonDown("Jump") && IsGrounded()) 
        {
            rb.velocity = new Vector3(rb.velocity.x, jumppower , rb.velocity.z);
        }
           
    }

    
    bool IsGrounded()
    {
        return Physics.CheckSphere(groundCheck.position, 0.1f, ground);
    }
    
    
}

# KirbyAdventure
