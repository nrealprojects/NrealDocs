## Navigating

This section covers basic operations that helps the user navigate through Nreal's mixed reality system, like how to get from menus to menus, apps to apps. 

### Select

The default method for selecting any interactable object is by first targeting it and then performing some kind of action to select.

| Means of Targeting | Selecting Action                                             |
| ------------------ | ------------------------------------------------------------ |
| Ray and/or Cursor  | Tapping or clicking                                          |
| Vision center      | Dwell for n seconds, Tapping or clicking, Voice commands*    |
| Hands (hand mode)  | Mimicking pointing gesture and pressing, Mimicking grabbing gesture |

### Back

By default, single clicking the **home (bottom) button** is dedicated for returning to the app's previous view (back) on every hands-on method of controlling. This allows quick navigation in and out of different views within an app. However, for apps that are intended to be compatible with hands-free methods like the gaze and dwell, there should be an interactable object or app tray to satisfy the back function.

### Closing an App
Closing an app is performed by long-pressing the **home button**. With the current SDK version which doesn't support multi app, this will also bring the user directly back to the launcher. 

#### Adjusting Ray Origins for 3DoF Controllers

The ray origin is the beginning point of a ray which is stationary when rotating the controller.

Since there are no absolute positions for a 3DoF controller, one can only assume that at the moment a ray is first casted (presumably on the start of an app), the user is pointing their controller towards the center of their field of view (a natural thing to do). However, that might be wrong: the users could be pointing their controller far off from center on the moment of ray cast. In this case the ray will be misaligned, making content targeting much more difficult.

When this happens, you will have to provide a means for the user to consciously readjust the direction their controller is pointing and refresh the ray cast to their vision center. By default, this is done by clicking the **app button** once.

#### Switching Between Left and Right (3DoF Only)

Since ray origin for 3DoF controlling methods is relative to the absolute position of the user's head, it is unknown if the controller is in the user's left or right hand. Therefore, if the ray origin is offset to the wrong side, targeting would feel very awkward: almost as if the user was using a mirrored laptop!

By default, ray origin is switched to the opposite side by double clicking the **app button**.

### Next Step
Read the [Developer Guide](/develop/unity/android-quickstart) to learn more about how to develop  a mixed reality app on Nreal Light. 