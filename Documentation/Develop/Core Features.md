# Core Features

Let’s get started with NRSDK's five core features. They are **Spacial Computing**, **Optimized Rendering**, **Multi-modal Interactions**, **Developer Tools** and **Third-party Integration**.

## Spatial Computing

Nreal glasses use a variety of sensors and cameras to build a sophisticated understanding of both the surrounding environment and the users themselves, creating immersive experiences that seamlessly blend the digital world with the real world.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_e61fce6136378a2737e75139604b0cec.gif)

* **6Dof Tracking** technology uses the two SLAM cameras located on both sides of the Nreal glasses to identify feature points, tracking how these points move over time. Combining the movement of these points with readings from the glasses' IMU sensors, NRSDK accurately tracks both the position and orientation of the glasses as it moves through space. 6Dof tracking also provides developers with real-time mapping constructions and 3D point clouds, giving the applications information on the physical structures of the environment.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_f46fcc33121a7d1e695c7cc2229b8602.gif)


* **Plane Detection** enables Nreal glasses to detect flat surfaces (both horizontal and vertical) in the environment, such as a table or a wall (in NRSDK 1.0.0 beta, only horizontal plane detection is available). The transformation of the plane is continuously updated. When the glasses move around, the plane can be extended, and multiple planes can merge into one when they overlap.

![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_63c6113a61cfef49aec8d0793866db63.gif)

* **Image Tracking** allows apps to recognize physical images and build augmented reality experiences around them. By adding multiple reference images to the image database, more than one pre-trained image can be detected in a session.

## Optimized Rendering

NRSDK optimizes the rendering performance in the backend to minimize the latency of the entire system and to reduce judder. It provides a smooth and comfortable user experience devoid of dizziness and sickness. You do not need to enable or tune rendering features as they are automatically applied. 

* **Warping**
Instead of polling tracking data at the very beginning of each frame to render the image, NRSDK uses the last predicted position of the Nreal glasses to warp the rendered image, reproject, and send to display before every VSync.


## Multi-modal Interactions


![](https://codimd.s3.shivering-isles.com/demo/uploads/upload_b8f79fcf89892747aab3920dd26d03fd.png)



* **Nreal Light Controller (3Dof)**
A light 3Dof controller to interact with the virtual objects in a natural and intuitive way. 

* **Nreal Phone Controller (3Dof)** (Currently is not available for you to develop apps)
An Android mobile phone can serve as a 3Dof controller when connected to Nreal glasses. The touchscreen supports gestures and all interactions mirror interactions on the Nreal controller. 


For more interaction models,  please refer to the [Design Guide](/design/interacting).

## Developer Tools

Developer Tools, such as  **Testing Tool** and **Observer View**, are something we designed especially for you. 

* The **Testing Tool** (will be available in next NRSDK version) is like an emulator running under the Unity Editor play mode. Inputs that would usually be read by the sensors on Nreal glasses are instead simulated using the keyboard, mouse, or smartphone. It comes with NRSDK and allows you to test applications without having real Nreal devices.

* **Observer View** allows you to share your creations with others by allowing them to see a Nreal Light user's world on a 2D phone or tablet screen, which is synchronized by a marker. 


## Third-party Integration

NRSDK is designed as an open platform and can be integrated with third-party SDKs as plug-ins. For example, data from the RGB camera is available for third-party SDKs to run face detection algorithms.

## Next Steps
Read [Quickstart for Android Unity](/develop/unity/android-quickstart) to learn how to build your first mixed reality application on Nreal glasses.


