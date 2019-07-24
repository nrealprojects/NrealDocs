# Design Guide

A quick and simple guide aimed at providing fundamental design knowledge as well as establishing some common standards for user interaction in Nreal mixed-reality apps. 
The guide is broken down into four principle sections: [Displaying](/design/displaying), [Controlling](/design/Controlling), [Interacting](design/interacting) and [Navigating](design/navigating).

<br />

## Displaying

This section explores ways of conveying visual information within the mixed-reality world, which can be less obvious compared to traditional screen based app designs.

### Sizing

Object sizing can also be complicated in MR. A good way to think about this is by thinking about objects in real life. When working with objects in MR, always keep a reference on their size and distance from the camera with real life objects. For example, an apple is on average 8 centimeters in diameter and your hand resting on a table is usually around 40 centimeters away. 

### Colors

In mixed reality, **Whiter = Occludes more of the background (user's environment)** and **Black = Transparent**. Therefore, if you want the users to see the object, make it brighter. On the contrary, if you want to hide something, you can play with shadows and black. An easy way to visualize this is by trying out the "lighten" overlaying effect on adobe photoshop or by picturing how ghosts are usually depicted in films like the Harry Potter series.

Vibrant colors look great in the Nreal Light. However, for higher quality visual effects, it is recommended to stay away from an overuse of gradients.

### Text

Due to the higher brightness and pixel density, text displayed with Nreal Light can be significantly easier to read when compared to most other head mounted MR devices. However, text is still tricky business in MR design and should be considered carefully.

#### Text Size

One of the major influences in text readability is font size. A good rule of thumb is to always keep the the size of text above 14px when it is at a distance of two meters away from the user. However larger text sizes are advisable when content is few, as this ensures minimum eye strain for the users.

#### Font

Simple and clear fonts in the family of san-serif is recommended as it requires less pixels for the same readability as the serif type phase.

### Interactable Objects

Most apps are made up of a series of interactable objects that can be summarized with two large categories: **selectable objects** and **movable objects**. When using only a single type from the category, almost any combination of hover and select would be enough to satisfy the needs for visual feedback. However, when considering using both at the same time, more thoughts should be put on picking different feedbacks before and during the target and select process.

#### Selectable Objects

Selectable objects are unmovable objects that can usually be hovered on and selected to execute a command.

| Selectable Effects in 3D      | Exemplar Scenarios                                           |
| ----------------------------- | ------------------------------------------------------------ |
| Enlargement / Pulsing         | Useful for any floating objects that are not in direct contact with another object. |
| Brightening / Change in Color | Functional in almost all situations, hence good for standardized feedbacks. Can however be viewed as unnatural or boring in some circumstances. |
| Object Animation              | Vivid and lively especially with organic elements like plant, animal and food.|
| Colors and Effects on Ray     | Serious scenes where objects should remain static and realistic. |

| Selectable Effects in 2D      | Exemplar Scenarios                                           |
| ----------------------------- | ------------------------------------------------------------ |
| Brightening / Change in Color | Much of the 2D content will come directly from a native android / windows application, this will remain the most commonly used effect for target and select that users are used to. |
| Bounding box                  | Clear and easy to implement. Can be difficult to make artistic and interesting. |

#### Movable Objects

Movable objects can be held and dragged or double-clicked and attached to the end of ray for more complex manipulation done via the trackpad. This section considers the visual feedbacks on scenarios where both selectable (non-movable) objects and movable ones co-exist. Therefore the movable method should be distinguished from the non-movable ones.

| Movable Effects in 3D                                 | Exemplar Scenarios                                           |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| 3D Bounding box                                       | The 3D bounding box is the most straightforward way to signify movability. As it communicates configurability in many UI. |
| 3D axis arrows, rotation circle and enlargement cube. | This is the best choice when the users are used to 3D modification programs, and when the application features complex object transforming and requires UI examples of what users can and cannot do during their current selection mode(s). |
| Different Animation                                   | Vivid and lively especially with organic elements like plant, animal and food. |

| Movable Effects in 2D                            | Exemplar Scenarios                                           |
| ------------------------------------------------ | ------------------------------------------------------------ |
| Make the Object's UI Pop Out From the Background | The current method for helping users distinguish movable objects from selectables in 2D environments is to make the UI different or by juxtaposing it so it pops out from the "background" of other selectables. |
| Broken Bounding Box                              | The standard method for configurable objects in 2D.          |

### Organizing Objects

#### Plane Table

Organizing objects on planes is typically done in a table-like fashion, grouping objects in horizontal rows and arranging these groups vertically. With this setup, scrolling vertically shuffles through rows of grouped objects, which can be scrolled horizontally to go through each individual object.

There are two main ways to scroll through plane tables: dragging the objects vertically or horizontally in the opposite direction or simply swiping in that direction on the trackpad. For the current version of Nreal Light, the second method is more recommended although both methods can be implemented at the same time.

It is important to give visual cues to unfinished columns and rows where users can still scroll to unveil new objects. These can include faded edges, arrows or other icons indicating unread content.

#### Cylinder Arrangement

By wrapping the plane table horizontally around the user, one essentially ends up with a cylinder. This is an easy way to make the plane table experience more three-dimensional and fun. However, cylinders that are fully enclosed or have a radius that is less than two meters from the user can cause discomfort.

#### Sphere Arrangement

When objects are not necessarily grouped by logic, one can use a 3D ball model for organization. The ball should be around five meters in diameter and two meters away from the user. It can spin freely on the angle the user has last released their ray or finger on. This method of object collection gives the users greater freedom and is more complex three-dimensionally. 

### Clipping Objects

Nothing distracts the user from the MR world like clipping. Although Nreal has a forced clipping distance that is only a few centimeters away from the camera, clipping is still inevitable in some situations. 

There are ways to smooth out the effects of clipping. For example, instead of the sharp clipping lines on the force clipping area, one can use effects like disintegrating pixels that start fading before the clipping lines and disappear steadily.

<br/>


