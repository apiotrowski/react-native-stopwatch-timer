## React Native Stopwatch Timer

A React Native component that provides a stopwatch and timer.

### Instructions

```npm install react-native-stopwatch-timer```

```js
import { Stopwatch, Timer } from 'react-native-stopwatch-timer'
```

### Options

#### Stopwatch and Timer Options

|Name|Type|Description|Default|
|----|----|-----------|------|
|start|boolean|starts timer/stopwatch if true, stops if false|false|
|reset|boolean|stops timer/stopwatch, resets|false|
|msecs|boolean|includes milliseconds in render of time|false|
|options|object|describes style of rendered timer/stopwatch|see example|

#### Timer Options

|Name|Type|Description|Default|
|----|----|-----------|------|
|totalDuration|Integer|number of milliseconds to set timer for|0|
|handleFinish|function|function to perform when timer completes|function() { console.log("Timer Finished") }|

### Example

```js
import React, { Component } from 'react';
import { AppRegistry, StyleSheet,Text,View, TouchableHighlight } from 'react-native';
import { Stopwatch, Timer } from 'react-native-stopwatch-timer';

class TestApp extends Component {
  constructor(props) {
    super(props);
    this.state = {
      timerStart: false,
      stopwatchStart: false,
      totalDuration: 90000,
      timerReset: false,
      stopwatchReset: false,
    };
    this.toggleTimer = this.toggleTimer.bind(this);
    this.resetTimer = this.resetTimer.bind(this);
    this.toggleStopwatch = this.toggleStopwatch.bind(this);
    this.resetStopwatch = this.resetStopwatch.bind(this);
  }

  toggleTimer() {
    this.setState({timerStart: !this.state.timerStart, timerReset: false});
  }

  resetTimer() {
    this.setState({timerStart: false, timerReset: true});
  }

  toggleStopwatch() {
    this.setState({stopwatchStart: !this.state.stopwatchStart, stopwatchReset: false});
  }

  resetStopwatch() {
    this.setState({stopwatchStart: false, stopwatchReset: true});
  }


  render() {
    return (
      <View>
        <Stopwatch msecs start={this.state.stopwatchStart}
          reset={this.state.stopwatchReset}
          options={timerStyle}/>
        <TouchableHighlight onPress={this.toggleStopwatch}>
          <Text style={{fontSize: 30}}>{!this.state.stopwatchStart ? "Start" : "Stop"}</Text>
        </TouchableHighlight>
        <TouchableHighlight onPress={this.resetStopwatch}>
          <Text style={{fontSize: 30}}>Reset</Text>
        </TouchableHighlight>
        <Timer totalDuration={this.state.totalDuration} msecs start={this.state.timerStart}
          reset={this.state.timerReset}
          options={stopwatchStyle}
          handleFinish={handleTimerComplete}/>
        <TouchableHighlight onPress={this.toggleTimer}>
          <Text style={{fontSize: 30}}>{!this.state.timerStart ? "Start" : "Stop"}</Text>
        </TouchableHighlight>
        <TouchableHighlight onPress={this.resetTimer}>
          <Text style={{fontSize: 30}}>Reset</Text>
        </TouchableHighlight>
      </View>
    );
  }
}

const handleTimerComplete = () => alert("custom completion function");

const timerStyle = {
  container: {
    backgroundColor: '#000',
    padding: 5,
    borderRadius: 5,
    width: 220,
  },
  timer: {
    fontSize: 30,
    color: '#FFF',
    marginLeft: 7,
  }
};

const stopwatchStyle = {
  container: {
    backgroundColor: '#000',
    padding: 5,
    borderRadius: 5,
    width: 220,
  },
  text: {
    fontSize: 30,
    color: '#FFF',
    marginLeft: 7,
  }
};


AppRegistry.registerComponent('TestApp', () => TestApp);

```


### Future Direction

I would like to add laps to the stopwatch feature.