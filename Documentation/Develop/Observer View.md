# Observer View

## Overview
NRSDK's observer view allows users to share their mixed reality experience with others who are holding a phone or tablet running ARCore. These shared experiences can be streamed or recorded.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_1781b8b5624ba6a627c6fbb5cca08a93.jpg)

### Capabilities
* Camera movement supported   
* Third-person view and multi-user experience supported; Viewers can interact
* Can be streamed to screens   
* Android phone (ARCore supported) required  
* Wireless supported / Networking required (UNET scripting); Network server auto-discovery for adding phones to sessions
* A set of synchronized network frames that supports value synchronization and RPC function
* Coordinate system alignment allows everyone to see Nreal applications in the exact same place



### Use Cases

* Record mixed reality in HD: Using Observer View, you can record a mixed reality experience using an Android phone or a tablet.
* Live demonstrations: Stream live mixed reality experiences to a TV directly from your phone or tablet.
* Share your experience with others: Have others share your mixed reality experience on the spot from their phones or tablets.

### Licenses
* Unity ARCore - (Apache 2.0 License)


## Tutorial: How to Set Up Observer View 

### Requirements
* Observer View uses the built-in network for its network discovery and spatial syncing. This means all interactivity during the application needs to be synced between devices.

* Hardware
    * Nreal Light glasses
    * Windows PC running Windows 10
    * [ARCore compatible device](https://developers.google.com/ar/discover/supported-devices) 
 
### Network Synchronization
 All network synchronization is based on NetworkBehaviour.  See `CameraCaptureController.cs` , located in `Assets > NRKernal > Demos > Sharring > Scripts > TestNetBehaviour` for an example on how to realize your NetworkBehaviour. 

Your own NetworkBehaviour class must inherit the NetworkBehaviour base class.

**Data Synchronization**
 The SDK comes with several data types that can be synchronized. They are the following:
 * SynTransform
 * SynInt
 * SynVector2
 * SynVector3
 * SynQuaternion

 **RPC Function**
 You can use RPC functions as below:
 ~~~c#
   this.RPC("Hello");

   public void Hello()
   {
       Debug.Log("Hello world!");
   }
~~~

### Coordinate Alignment

See `UpdateWorldOrigin.cs` , located in `Assets > NRKernal > Scripts > Utility `  You can use UpdateWorldOrigin to align the coordinate of your detected image as below:
 ~~~c#
   UpdateWorldOrigin.ResetWorldOrigin(position, rotation);
~~~

### Setup Application

* Click `NRWindows > Start Sharing Server` menu to initiate a local sharing server.
    
* Start your client applications to search for and connect to local servers. 

* Scan your tracking image to align coordinates. All applications will share the same coordinates. The data will synchronize subsequently. 



