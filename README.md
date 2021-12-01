# Physics-based Player Controller

## Overall goal

Create a framework for Unity developers to easily integrate into their projects to have a base for player movement.

The user should be free to expand and add to the functionality.

## Priority 1

The first priority is to get the player object moving.

### Attributes

1. terminalVelocity: a floating point number which is used to limit the magnitude of a player's velocity

2. acceleration: a floating point number that is added to the player's velocity magnitude component every physics update

# Behaviors

1. GetInput(): a private void method to capture input from player and translate into a unit vector which describes a desired direction

2. Move(): a private void method which uses the constructed desired direction to 
