# Physics-based Player Controller

## Overall goal

Create a framework for Unity developers to easily integrate into their projects to have a base for player movement.

The user should be free to expand and add to the functionality.

## Priority 1

The first priority is to get the player object moving.

### Attributes

1. terminalVelocity: a floating point number which is used to limit the magnitude of a player's velocity

2. acceleration: a floating point number that is added to the player's velocity magnitude component every physics update

### Behaviors

1. GetInput(): a private void method to capture input from player and translate into a unit vector which describes a desired direction

2. Move(): a private void method which uses the constructed desired direction, applying the defined acceleration, to controll which direction and how much force to put behind the player object for that physics update
  - Move() will also use the ClampMagnitude method of the Vector3 class to clamp the player's velocity magnitude.

## Priority 2

### Arising Problem

An arising problem is that the player object, while is able to stop relatively smoothly and abruptly - this is compared to when the object is percieved to stop moving and when the player has stopped giving input - still ends up having quite a bit of force behind the object to still make unwanted sliding apparent. This will be preserved in the finished project; however, being able to still have very snappy stopping when playing something like a First Person Shooter (FPS) is very desirable because it reinforces the idea the player is a human, and therefore stops quite abruptly when not walking. This sliding could also be detrimental to the rest of the experience given the fact that a player may slide further than the anticipated, or wanted, which would contribute to unplanned demise. This unplanned demised can be very annoying when doing anything, unless learning to deal with this is part of the intended gameplay.

### Basis For A Solution

The solution would be to control the force that will be applied to the player object before applying the force. This would mean taking into account the potential velocity the player could reach - the terminalVelocity - and the current velocity. Then we can use this insight to limit how much force to put behind the player object for this frame. The idea is to have a movement system that will, initially, let the player reach terminal velocity rather quickly, and subsequently slow down to a velocity of 0 when the player has ceased giving input. This will also be the basis for the user to begin customizing the movement calculations to caiter the movement to the game's overall experience it will provide to the player.
