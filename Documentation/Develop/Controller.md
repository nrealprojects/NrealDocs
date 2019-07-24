# Controller

This guide will show you how to use the **Nreal Light controller** and **Nreal phone controller**. The tutorial will demonstrate how to create apps using **Nreal Light controller** as an interaction model. 

## Introduction

Controllers provide a simple way for users to navigate in mixed reality. In the latest version, NRSDK supports two types of controlling methods: **Nreal Light controller** and **Nreal phone controller**. The Nreal Light controller can be paired with a Nreal Light computing unit or a mobile phone through Bluetooth. The Nreal phone controller is only available when using the phone as Nreal Light's computing unit.

Currently, only the **Nreal Light controller** (available in the Nreal Developer Kit) is available to developers. The **Nreal phone controller** will serve as a second input choice for users in the future.

## How to Use the Nreal Light Controller


![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_6e663670e0fca3c1cebeae76da88f51a.png)



### The Nreal Light Controller

**On the front**

| Controller Features | Description | 
| -------- | -------- |
| 3Dof Tracking | 3 degrees of freedom | 
| Touchpad | **Press** = Tigger Button. Can detect touching, swiping and clicking. Customizable for your app, e.g. scrolling. | 
| App Button | **Press** to recenter your controller. **Press and hold** can be customized for your app, e.g. opening an in-app menu or performing a special action. | 
| Home Button | **Press and hold** to open Nreal launcher. **Press** can be customized for in-app action, e.g. return to the previous step. | 
| LED Light | Display controller status | 

**On the back** 

| Controller Features | Description |
| -------- | -------- |
| Charging pins | The three bottom-facing charging pins connect the controller with the computing unit. It is also used to send data from the computing unit to the controller. |
| Power Switch | The Nreal Light controller  on/off switch is below the charging spots. Green means the power is on, and red means the power is off. |


#### Nreal Light Controller LED Guide
See **LED demo** below:


![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_c5bf85a4c0f4fbcb3dd4c97e3ba5a2b3.gif)



#### Connecting the Nreal Light Controller 

1. Make sure the Bluetooth on your Neal Light computing unit/or Android mobile phone is on. (The Bluetooth on Nreal Light computing unit is on as default.) 

2. Turn the Nreal Light controller power switch on. Long press the touchpad until the green light starts blinking.

3. Put the Nreal Light controller on the computing unit, and they will be paired automatically. 

4. If pairing is successful, the LED will stop blinking and become solid green. If you cannot complete this step, remove all other controllers in the Bluetooth record list and try again.

#### Charging the Nreal Light Controller

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_4b2bd5c37818c64112049dc35e6ada6f.jpg)


Magnetically attach to the Nreal Light computing unit. Battery power will be shared between the two whether the controller is on or off.


*The lithium battery in the controller is not removable. Please do not attempt to open the controller. Damage caused this way cannot be fixed.*


## How to Use Your Phone as a Controller

 
![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_3113db8a723c0e6483734ef73b76aa91.png)


 
| Controller Features | Description | 
| -------- | -------- |
| 3Dof Tracking | 3 degrees of freedom | 
| Touchpad | **Press** = Trigger Button. Can detect touching, swiping and clicking. Customizable for your app, e.g. scrolling. | 
| App Button | **Press** to recenter your controller. **Press and hold** can be customized for your app, e.g. opening an in-app menu or performing a special action. | 
| Home Button | **Press and hold** to open Nreal launcher.  **Press** can be customized for in-app action, e.g. return to the previous step.|  


# Tutorial： Nreal Light Controller

## Input in Unity

These following points will help you better understand the Input from NRSDK in Unity.

**ControllerProvider:** This provides various controller state information to NRInput, including rotation, button press, button up, battery, and gyro. There is a default provider for Nreal controllers. You can also write a custom controller provider.

**EventSystem:** Integration with Unity's standard EventSystem supports user interaction with GUI and other physical objects. NRIput will automatically generate an EventSystem when the application runs.

**Visualizations:** Default visualizations, such as controller visual, ray visual, and reticle visual, are already included. There is also an interface for you to reskin visualizations.

### Enabling NRInput

1. To enable NRInput, simply drag the ++NRInput++ prefab into your scene hierarchy.
2. If you already have a Main Camera set up, drag it onto ++Override Camera Center++ in the NRInput prefab. Otherwise, the prefab will find the Main Camera.
3. Users can now interact in the app using Nreal Light controllers.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_17d15069bf0418652f8c4650f6a656e3.png)

### Raycast Modes in NRInput

There are two raycasting modes included in the NRInput: the <u>Gaze Mode</u> and the <u>Ray Mode</u>. 

The <u>Ray Mode</u> is the default raycasting mode most apps will be based on. In this mode, the ray will start from the center of the controller.

When in <u>Gaze Mode</u>, the raycast will start from the center of the user's forehead and emanate in a forward direction. Thus, the ray will be invisible. 

### Current Controller Features

Since NRSDK supports multiple types of controllers, a method was scripted to help you understand the features your current controller supports.

**Sample Use Case:**
~~~c#
    bool supportsPosition = NRInput.GetControllerAvailableFeature(ControllerAvailableFeature.CONTROLLER_AVAILABLE_FEATURE_POSITION);
    bool supportsGyro = NRInput.GetControllerAvailableFeature(ControllerAvailableFeature.CONTROLLER_AVAILABLE_FEATURE_GYRO);
~~~

### Some Common Usage of NRInput

**Sample Use Case:**
~~~c#
void Update()
    {
        //returns a int value of how many available controllers currently
        NRInput.GetAvailableControllersCount();

        //returns true if a Trigger button is currently pressed
        NRInput.GetButton(ControllerButton.TRIGGER);

        //returns true if a Trigger button was pressed down this frame
        NRInput.GetButtonDown(ControllerButton.TRIGGER);

        //returns true if a Trigger button was released this frame
        NRInput.GetButtonUp(ControllerButton.TRIGGER);

        //returns Vector3.zero if controller is 3dof, otherwise returns the position of the domain controller
        NRInput.GetPosition();

        //returns the rotation of the domain controller
        NRInput.GetRotation();

        //returns the ControllerType of the domain controller
        ControllerType controllerType = NRInput.GetControllerType();

        //returns a Vector2 value of the touchpad, x(-1f ~ 1f), y(-1f ~ 1f);
        NRInput.GetTouch();

        //returns a Vector3 value of gyro if supports
        NRInput.GetGyro();

        //to get what hand mode is using now, left-hand or right-hand
        ControllerHandEnum domainHand = NRInput.DomainHand;

        //the same as NRInput.GetRotation()
        NRInput.GetRotation(NRInput.DomainHand);

        //returns the rotaion of the left hand controller
        NRInput.GetRotation(ControllerHandEnum.Right);
    }
~~~

### Get Frequently Used Anchors

The NRInput provides an easy way to get frequently used anchors quickly.

**Sample Use Case:**
~~~c#
    Transform gazeAnchor = NRInput.AnchorsHelper.GetAnchor(ControllerAnchorEnum.GazePoseTrackerAnchor);
    Transform leftRayAnchor = NRInput.AnchorsHelper.GetAnchor(ControllerAnchorEnum.LeftRayAnchor);
~~~

### Raycasters in NRInput

Three raycasters are included in the NRInput prefab. One of which for Gaze Mode, and the other two for Ray Mode. The raycaster class inherits from Unity's BaseRaycaster class. A chosen raycaster's farthest raycasting distance can be modified directly from the Inspector window. You can also define which objects are interactable by changing the parameter of its Mask.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_27635ecd14215de1e11c540747f246bf.png)


## Building a Project with User Input

To help you get started with integrating control into your own app, we have prepared a sample case study.

By reading the study you will be able to:

1. Select a range of appropriate inputs to use with the ontroller.
2. Write code in C# to receive user inputs such as the Home, Bumper, Trigger and Touchpad.
3. Activate, rotate, and move a GameObject by using the input.
4. Interact with physical objects and UGUI in the unity environment.

**Objective:**
1. When pointing the controller at the cube, its color will change to green. 
2. The color of the cube will randomly change when you press the trigger button. 
3. The cube will rotate with the controller.
4. Activate or deactivate the cube for rotation by pressing the UGUI button.

**Steps：**
1. Drag NRCameraRig and the NRInput prefab to the scene hierarchy.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_49669dd8fd5aad02bcc2eb757566683e.png)

2. Create a cube. In the Inspector window, set its position to (0, 0.1, 3), and scale to (0.3, 0.3, 0.3).

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_7d09f5d7c2201734d485290146e2375b.png)

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_299a2e234dc96dda65186ac287db0ccf.png)


3. Create a script named <u>CubeInteractiveTest.cs</u> as follows and add it to the cube.
~~~c#
public class CubeInteractiveTest : MonoBehaviour, IPointerClickHandler, IPointerEnterHandler, IPointerExitHandler
{
    private MeshRenderer m_MeshRender;

    void Awake () {
        m_MeshRender = transform.GetComponent<MeshRenderer>();
    }
    
    void Update()
    {
        //get controller rotation, and set the value to the cube transform
        transform.rotation = NRInput.GetRotation();
    }

    //when pointer click, set the cube color to random color
    public void OnPointerClick(PointerEventData eventData)
    {
        m_MeshRender.material.color = new Color(Random.Range(0f, 1f), Random.Range(0f, 1f), Random.Range(0f, 1f));
    }

    //when pointer hover, set the cube color to green
    public void OnPointerEnter(PointerEventData eventData)
    {
        m_MeshRender.material.color = Color.green;
    }

    //when pointer exit hover, set the cube color to white
    public void OnPointerExit(PointerEventData eventData)
    {
        m_MeshRender.material.color = Color.white;
    }
}
~~~
![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_0bc22e7348bfd467694e56322d58a064.png)


4. Add a DirectLight to brighten the cube.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_93da34c0026a9fc195f4c93cc20216c8.png)


5. Add a Canvas and delete the EventSystem.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_18dc419d99337c5e4ea1fd06d2ec5008.png)

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_f887ac7cdeae0763ea3874483602dfa9.png)


6. Set the Canvas RenderMode to WorldSpace, and then set its position and scale to an appropriate value such as that listed below.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_f88c4afbeaa90b2fc1b5d881725f6f45.png)

7. Remove the <u>Graphic Raycaster</u> component from it and add <u>Canvas Raycast Target</u>.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_df7ac49e5812cb8947cb3afb705f1582.png)

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_61d88257b76803096643062461aeb345.png)


8. Add two buttons to the Canvas as its children. Name one button <u>activeBtn</u> and the other <u>deactive</u>. Remember to also change the button text.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_a4dac72a9a3d3553a0b5b4f238759140.png)


9. Set the buttons to an appropriate position and add the <u>SetActive</u> function as their OnClick events.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_e0ee31f07407dc92243f2c8a9e3f2eec.png)

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_06c56d17ddec68a7fe4613e57a58b5a8.png)


10. Finally, compile the app. An interactive mixed reality app utilizing user input with a Nreal Light controller is complete.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_3bfb76ed4209e693d4d2bee776c7cdd0.png)

## Next Steps

Check out the [Design Guide](/design/controlling) to learn more about user experience design with Nreal Controller.






