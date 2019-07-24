## Interacting

Mixed reality apps are meant to be interactive. This section discusses the fundamentals of interactive apps like targeting and manipulating objects.

### Targeting

#### Ray

The ray is the default method of selection designed for Nreal Light. It is a clear and 3D method of selection and is supported by all controlling devices currently compatible with Nreal Light.

The concept of the ray is a straight line projecting forwards from the ray origin which is often close to the user's controller holding hand. For the 3DoF controller and phone, the ray origin is by default 50 cm below the user's headphones and slightly offset to the right or left depending on the user's habitual hand. For the 6DoF controller however, the point of projection should ideally be overlapping with the user's controlling hand.

#### Cursor

A cursor is the point of contact of the ray with the content object and can be used with or without the ray. When used in conjunction with the ray, the cursor provides a clearer point of action and can display other visual feedbacks like hover and swiping. Using the cursor alone can also be a good way for visualizing selection in 2D applications as it removes the sometimes distracting ray in the foreground. 

The cursor can have different states like "hovering", "pressed" and "swiping". It can also be used to differentiate non-selectable, selectable and movable objects when applications contain a large amount of  objects with different properties.

#### Gaze and dwell

Gaze alone as a selection method can still be used for less interactive applications like video-streaming or book-reading. The gaze and dwell method requires users to focus their gaze center on a selectable object for a given period of time. This means that the users, while using gaze and dwell as a selection method, can free up both hands for activities like dining or work.

### Manipulation

Moving and turning objects around in 3D space is one of the most complicated interaction in MR and requires some degree of learning no matter the controlling method. It is therefore strongly advised to follow this guide for a standardized manipulation logic.

#### Simple Grab and Place

Simple grab and place allows users to quickly grab an object or window with the ray or cursor by holding the trackpad. In this mode, users can move the object in a spherical path around its ray origin with the object always facing the front of the user (simulating a fixed ray length). Users are also unable to change the ray length during simple grab and place. Therefore, in order to move an object forward, the user must move physically with his headphones and ray origin. For more complicated manipulations such as rotation, scaling and ray length, it is recommended to incorporate them in hover and fixed to ray modes.

| Object follows ray/cursor | Change object distance | Scale object | Rotate object (ground plane) | Rotate object (side plane) |
| ------------------------- | ---------------------- | ------------ | ---------------------------- | -------------------------- |
| √                         | ×                      | ×            | ×                            | ×                          |

#### Fixed to Ray

To fix the object to the end of the ray or cursor, double click on the object instead of holding onto it. By fixing the object to the end of ray, users can release their finger to more freely perform trackpad gestures, which is required for object manipulation beyond simple ray following.

|      | Object follows ray/cursor | Change object distance | Scale object         | Rotate object (ground plane) | Rotate object (side plane) |
| ---- | ------------------------- | ---------------------- | -------------------- | ---------------------------- | -------------------------- |
| 1    | √                         | swipe up and down      | ×                    | swipe left and right         | ×                          |
| 2    | √                         | swipe up and down      | swipe left and right | ×                            | ×                          |

#### Hover Manipulation

Hover manipulation is faster than the fix-to-ray method but provides less control. By aiming the ray at the object and doing gestures directly, objects can be manipulated in a similar or complimentary way with fixing to ray. The object's center however will always remain stationary during hover manipulation.

|      | Object follows ray/cursor | Change object distance | Scale object      | Rotate object (ground plane) | Rotate object (side plane) |
| ---- | ------------------------- | ---------------------- | ----------------- | ---------------------------- | -------------------------- |
| 1    | ×                         | ×                      | swipe up and down | swipe left and right         | ×                          |
| 2    | ×                         | ×                      | ×                 | swipe left and right         | swipe up and down          |
