# react-native-swipe-gestures-plus

React Native component for handling swipe gestures in up, down, left and right direction with Press and Long Press Events.

## Installation

`npm i -S react-native-swipe-gestures-plus`

# License
This is an updated version by [arunahuja94](https://github.com/arunahuja94). <br/>
Original author [glepur](https://github.com/glepur/react-native-swipe-gestures),

## Usage

```javascript
'use strict';

import React, {Component} from 'react';
import {View, Text} from 'react-native';
import GestureRecognizer, {swipeDirections} from 'react-native-swipe-gestures-plus';

export default function App(){
    const [myText, setMyText] = React.useState('I\'m ready to get swiped!');
    const [gestureName, setGestureName] = React.useState('none');
    const [backgroundColor, setBackgroundColor] = React.useState('#fff');
 
  const onSwipeUp = (gestureState) => {
    setMyText('You swiped up!');
  }
 
  const onSwipeDown = (gestureState) => {
    setMyText('You swiped down!');
  }
 
  const onSwipeLeft = (gestureState) => {
    setMyText('You swiped left!');
  }
 
  const onSwipeRight = (gestureState) => {
    setMyText('You swiped right!');
  }
  
  const onPress = (gestureState) => {
    setMyText('You Clicked!');
  }
  
  const onLongPress = (gestureState) => {
    setMyText('You Long Pressed!');
  }
 
  const onSwipe = (gestureName, gestureState) => {
    const {SWIPE_UP, SWIPE_DOWN, SWIPE_LEFT, SWIPE_RIGHT,ON_PRESS, ON_LONGPRESS} = swipeDirections;
    setGestureName(gestureName);
    switch (gestureName) {
      case SWIPE_UP:
        setBackgroundColor('red');
        break;
      case SWIPE_DOWN:
        setBackgroundColor('green');
        break;
      case SWIPE_LEFT:
        setBackgroundColor('blue');
        break;
      case SWIPE_RIGHT:
        setBackgroundColor('yellow');
        break;
      case ON_PRESS:
        setBackgroundColor('black');
        break;
      case ON_LONGPRESS:
        setBackgroundColor('pink');
        break;
    }
    
  }
 
  const config = {
    velocityThreshold: 0.3,
    directionalOffsetThreshold: 80
  };

  return (
    <GestureRecognizer
      onSwipe={(direction, state) => onSwipe(direction, state)}
      onSwipeUp={(state) => onSwipeUp(state)}
      onSwipeDown={(state) => onSwipeDown(state)}
      onSwipeLeft={(state) => onSwipeLeft(state)}
      onSwipeRight={(state) => onSwipeRight(state)}
      onPress={(state) => onPress(state)}
      onLongPress={(state) => onLongPress(state)}
      config={config}
      style={{
        flex: 1,
        backgroundColor: backgroundColor,
      }}
      >
      <Text>{myText}</Text>
      <Text>onSwipe callback received gesture: {gestureName}</Text>

    </GestureRecognizer>
  );
}
```

## Config

Can be passed within optional `config` property.

| Params                     | Type          | Default | Description  |
| -------------------------- |:-------------:| ------- | ------------ |
| velocityThreshold          | Number        | 0.3     | Velocity that has to be breached in order for swipe to be triggered (`vx` and `vy` properties of `gestureState`) |
| directionalOffsetThreshold | Number        | 80      | Absolute offset that shouldn't be breached for swipe to be triggered (`dy` for horizontal swipe, `dx` for vertical swipe) |
| gestureIsClickThreshold    | Number        | 5       | Absolute distance that should be breached for the gesture to not be considered a click (`dx` or `dy` properties of `gestureState`) |

## Methods

#### onSwipe(gestureName, gestureState)

| Params        | Type          | Description  |
| ------------- |:-------------:| ------------ |
| gestureName   | String        | Name of the gesture (look example above) |
| gestureState  | Object        | gestureState received from PanResponder  |


#### onSwipeUp(gestureState)

| Params        | Type          | Description  |
| ------------- |:-------------:| ------------ |
| gestureState  | Object        | gestureState received from PanResponder  |

#### onSwipeDown(gestureState)

| Params        | Type          | Description  |
| ------------- |:-------------:| ------------ |
| gestureState  | Object        | gestureState received from PanResponder  |

#### onSwipeLeft(gestureState)

| Params        | Type          | Description  |
| ------------- |:-------------:| ------------ |
| gestureState  | Object        | gestureState received from PanResponder  |

#### onSwipeRight(gestureState)

| Params        | Type          | Description  |
| ------------- |:-------------:| ------------ |
| gestureState  | Object        | gestureState received from PanResponder  |
