# Computer as medium
### This is a repo for the Computer As A Medium Fall 2026.
### Group Name: [Jam 12]
### Group Members: [Paul Jones & Kyle Young]
https://youtu.be/fz58lUrVQ3w 
Paul/I worked on the trap/false top code, ranged attack and mana system
using UnityEngine;
using TMPro;

public class PlayerMana : MonoBehaviour
{
    public int mana = 100;
    public TMP_Text manaText;
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        manaText.text = "Mana: " + mana;
    }

    // Update is called once per frame
    void Update()
    {
        manaText.text = "Mana: " + mana;
    }
}

using UnityEngine;
public class Trap : MonoBehaviour
{
    public PlayerHealth playerHealth;
    // Start is called once before the first execution of Update after the
    //MonoBehaviour is created
void Start()
    {

    }
    // Update is called once per frame
    void Update()
    {
    }
    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Player"))
        {
            playerHealth.health -= 11;
        }
    }
}


using UnityEngine;
using UnityEngine.InputSystem;
public class RangedAttack : MonoBehaviour
{
    public PlayerMana playerMana;
    public Animator animator;
    // Start is called once before the first execution of Update after the
    //MonoBehaviour is created
    void Start()
    {
    }
    // Update is called once per frame
    void Update()
    {
        RangedAnimation();
    }
    void RangedAnimation()
    {
        if (Keyboard.current.gKey.wasPressedThisFrame)
        {
            animator.SetBool("ranged attack", true);

            playerMana.mana -= 10;

           
        }
        else
        {
            animator.SetBool("ranged attack", false);

        }
    }
}


using UnityEngine;

public class NewMonoBehaviourScript : MonoBehaviour
{
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        
    }
    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Player"))
        {
            // Handle player entering the trigger

            Destroy(gameObject);
        }
    }
}


Meanwhile Kyle worked on the health pack and helped me with troubleshooting.

using UnityEngine;

public class HealthPack : MonoBehaviour
{
    public PlayerHealth playerHealth;
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {

    }

    // Update is called once per frame
    void Update()
    {

    }

    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Player"))
        {
            if (playerHealth.health < 100)
            {
                playerHealth.health += 10;
            }
            if (other.CompareTag("Player"))
            {
                Destroy(gameObject);
            }


        }
    }
}
