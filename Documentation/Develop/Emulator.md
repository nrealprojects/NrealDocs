
# Emulator: Testing your app

The **Emulator** lets you test mixed reality applications on your PC without a real Nreal Light glasses and computing unit. With Emulator, you can speed up app development by testing, iterating and debug without having to build and deploy the app to Nreal device. You could simply **use Unity to test your app by importing an Emulator Prefab.**

Controlling the Emulator is very similar to common 3D video games. You can use keyboard and mouse to control the head pose movement, controller rotation, trackable planes or images in 3D space.

**In this section, you will learn:**

- How to enable Unity to debug MR apps as an Emulator

- How to simulate input events that are usually read by Nreal Light glasses and controller sensors by using your keyboard and mouse when debugging


## Prerequisites

- Understanding NRSDK concept and working flow

- [Import NRSDK into Unity ](https://developer.nreal.ai/develop/discover/introduction-nrsdk)

- Have the code and resources of your app ready


## Find Emulator in NRSDK package

 NRSDK > Emulator
 
![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_0e5c309a7486b2ddaf3ddc9677e25ed2.png)


## Emulator Structure

**Emulator** folder contains all the code and resources of Emulator, here is a brief introduction for you to lookup. 
  - **Editor** contains the script used for modifying Unity Editor  
  - **Image** contains the UI image resources to show controller state
  - **Material** contains the materials for TrackableImage and TrackablePlane in Emulator
  - **Model** contains the room model used in the sample scene.
  - **Prefabs** 
    - ```NRTrackableImageTarget.prefab``` used for simluating the detection of images.
    - ```NRTrackablePlaneTarget.prefab ```  used for simulating the detection of planes. 
  - **Resources** used for dynamic loading resource 
  - **Scene** contains two demos for testing TrackableImage and TrackablePlane
  - **Script** 
    - ```NativeEmulator.cs```  used for calling low-level API
    - ```NREmulatorManager.cs``` is the script  for managing the life cycle of Emulator 
    - ```NREmulatorController.cs``` simulates the input of controller
    - ```NREmulatorHeadPose.cs``` simulates the headpose movement
    - ```NRTrackableImageBehaviour.cs``` is the script to simulate the trackable images
    - ```NRTrackablePlaneBehaviour.cs``` is the script to simulate the trackable planes 
    - ```NRTrackableObserver.cs``` is the observer of trackable target
    - ```TrackableFoundTest.cs```  is a testing script that 


## Simulating the 6DoF Head Pose

- Use WSAD on the keyboard to simulate the movement of the position of the head

    W -> move forward.
    S -> move backward.
    A -> move left.
    D -> move right.

- Press Space key and Use the Mouse to simulate the rotation of the head
- Sample Code
   ```c#
   
        void UpdateHeadPosByInput()
        {
            float mouse_x = Input.GetAxis("Mouse X") * HeadRotateSpeed;
            float mouse_y = Input.GetAxis("Mouse Y") * HeadRotateSpeed;
            Vector3 mouseMove = new Vector3(m_CameraTarget.transform.eulerAngles.x - mouse_y, m_CameraTarget.transform.eulerAngles.y + mouse_x, 0);
            Quaternion q = Quaternion.Euler(mouseMove);
            m_CameraTarget.transform.rotation = q;

            Vector3 p = GetBaseInput();
            p = p * HeadMoveSpeed * Time.deltaTime;
            Vector3 pos = p + m_CameraTarget.transform.position;
            m_CameraTarget.transform.position = pos;

            // Call api to simulate the headpose movement
            NREmulatorManager.Instance.NativeEmulatorApi.SetHeadTrackingPose(pos, q);
        }
    ```

## Simulating Controller Input

There is also a controller UI showing the emulator controller state, including touch movement and button event, at the lower-right corner of the Game window.

  ![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_c0232e9223f8ea9634270abb5003223e.png)

- Simulating Controller Rotation
      Press Shift + Move Mouse

- Simulating Controller Button 
    Mouse left button -> Select Button
    ![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_155bd39143602da20a4f2ebd8a83cf55.png)

      
     Mouse right button -> Home Button
     ![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_0b45bd2369aaedc23ffab788d4481df3.png)

     Mouse middle button -> App Button
![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_40a1283c258330c5fbdcdd7820a7ded9.png)


- Simulating Controller Touch (Swipe Gesture)
Keyboard Left/ Right/ Up/ Down Arrow -> Swipe Left/ Right/ Up/ Down
 ![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_793078aa63033455557ec35b89b8e990.png)
 ![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_e8b99f81268cb1d1e85ad6856e479f65.png)
 ![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_726694d6e5197214f802b439855b5fda.png)
 ![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_3fd83045e08ad6e02fab106d3e85eda9.png)


- Sample Code:  ```NREmulatorController.cs```

   ```c#
        // Control the rotation of controller
        void UpdateControllerRotateByInput()
        {
            float mouse_x = Input.GetAxis("Mouse X") * HeadRotateSpeed;
            float mouse_y = Input.GetAxis("Mouse Y") * HeadRotateSpeed;

            Vector3 mouseMove = new Vector3(m_Target.transform.eulerAngles.x - mouse_y, m_Target.transform.eulerAngles.y + mouse_x, 0);
            Quaternion q = Quaternion.Euler(mouseMove);
            m_Target.transform.rotation = q;
            NREmulatorManager.Instance.NativeEmulatorApi.SetControllerRotation(new Quaternion(q.x, q.y, q.z, q.w));
    
        }

## Tutorial: Simulating Headpose, Controller & Trackable Object

### Run the Sample
First , ```Assets/NRSDk/Emulator/Scenes/TrackableImageEmulator.unity``` and ```Assets/NRSDk/Emulator/Scenes/TrackablePlaneEmulator.unity``` are two samples for the Emulator. Developers could directly play the scene in Unity Editor or build them into apk and run on an Nreal Device.

### Create your own 

1. Make sure you have ```Assets/NRSDK/Prefabs/NRCamreaRig.prefab``` and ```NRSDK/Prefabs/NRInput.prefab``` in the scene. 
- When Unity Editor under runtime, the ```NREmulatorHeadPose.prefab``` will be automatically loaded by ```NRCameraRig.prefab``` into the scene for simulating the head pose data.

- When Unity Editor under runtime, the```EmualatorController.Prefab``` will be automatically loaded by ```NRInput.prefab``` into the scene for simulating the controller input data. 

2. Place ```Assets/NRSDK/Emulator/Prefabs/NRTrackableImageTarget.prefab``` or ```Assets/NRSDK/Emulator/Prefabs/NRTrackablePlaneTarget.prefab``` to simulate the trackalbe images and planes.

- ```TrackableObserver.cs``` is attached to every```NRTrackableImageTarget.prefab``` and ```NRTrackablePlaneTarget.prefab```. You need to register your own logic of Trackable found and lost into TrackableObserver.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_167103f212169827528d76c9fd4af01d.png)


3. In ```/Assets/NRSDK/Emulator/Scripts/TrackableFoundTest.cs``` , you could find the sample for the register event.

- Sample Code: ``` TrackableFoundTest.cs```
 ```
 public class TrackableFoundTest : MonoBehaviour {

    // Observer of the registed event
    public TrackableObserver Observer;
    // Showing GameObject on the detected Trackable object
    public GameObject Obj;
    
	void Start () 
    {
        Obj.SetActive(false);
        Observer.FoundEvent += Found;
        Observer.LostEent += Lost;
	}
	
	private void Found(Vector3 pos, Quaternion qua)
    {
        Obj.transform.position = pos;
        Obj.transform.rotation = qua;
        Obj.SetActive(true);
    }
    private void Lost()
    {
        Obj.SetActive(false);
    }
}
```
 
  

    
4. If you want to use your image as a detection target, you could switch the image database in ``` NRTrackableImageTarget.prefab```  
 ![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_9ca0612e36dae1fd672c11ff28982542.png)
- In NRSDK, we provided you with three default images for image detection. If you would like to add your own, please find ```NRCameraRig.prefab```
    - Find```NRKernalSessionConfig.asset``` under the ```NRSessionBehaviour.cs```

 ![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_199c0d82d46243c2bc3aae913fb02a96.png)

    
- Find TrackingImageDatabase in the ```NRKernalSessionConfig.asset```, and drag your own database.asset into it. 

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_b7cbd49bf553a7e16ca95353f5d80910.png)

- Read about [how to add your image into the Image Tracking Database](https://developer.nreal.ai/develop/unity/image-tracking)
    
![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_c5a6208b308a76905ff8ef9938f8cb2c.png)


    



