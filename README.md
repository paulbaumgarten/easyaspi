# EasyAsPi

This project aims to remove a lot of the complexity of dealing with the GPIO and PiCamera for beginner level programmers working with the Raspberry Pi.

This project has been initially developed for use within my own classes that I teach but I hope it might find use for others too.

## Getting started

This assumes you have a Raspberry Pi (and a PiCamera to use that functionality). All code tested on Raspberry Pi model 3, PiCamera model 2, running Raspbian 2018-06-29.

## Install

```
pip install easyaspi
```

## Usage

At present, the project supports LEDs, buttons, ultrasonics and the PiCamera. This list of tools is expected to grow as need arises.

**Note: This library will set the default GPIO pin layout mode to BCM.**

### LEDs

* Create the LED object

```python
import easyaspi
led = easyaspi.LED( pin_number )
```

* Turn an LED on

```python
led.set(True)
```

* Turn an LED off

```python
led.set(False)
```

### Buttons

* Create the Button object

```python
import easyaspi
button = easyaspi.Button( pin_number )
```

* Retrieve if the button is being pressed

```python
button_state = button.get()
```

* Set an event callback for button presses

```python
# Note: The function definition for the callback requires the state parameter even though it should always be set to True to indicate the button is currently pressed.

def was_pressed(state):
   print("Button was pressed!")

button.on_press(was_pressed)
```

* Remove an event callback

```python
button.remove_on_press()            # Remove any event listener for this button
```

### Ultrasonic

* Create the Ultrasonic variable

```python
import easyaspi
ultra = easyaspi.Ultrasonic( trigger_pin_number, echo_pin_number )
```

* Retrieve the distance in centimeters

```python
distance = ultra.get_distance()
```

### Pi Camera

* Create the Camera object

```python
import easyaspi
camera = easyaspi.Camera()
```

* Take a photo (without a message)

```python
camera.photo("myphoto.png")
```

* Take a photo (with a message)

```python
camera.photo("myphoto.png", "my message")
```

* Start video recording

```python
camera.record("myvideo.h264", "my message")
```

* Check to see if camera is recording video

```python
recording_state = camera.recording      # Returns True or False
```

* Stop video recording

```python
camera.stop()
```

* Close the camera preview window when finished

```python
camera.preview(False)
```

## Author

* [Paul Baumgarten](https://pbaumgarten.com/)

## License

MIT License (C) 2018 Paul Baumgarten

