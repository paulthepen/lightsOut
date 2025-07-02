# Lights Out - Vue.js Game

A simple implementation of the classic **Lights Out** puzzle game built with Vue.js. Tap the grid lights to toggle them and their neighbors. The goal is to turn **all lights off**.

![screenshot](./screenshot.jpg)

## 🎮 How to Play

- You are presented with a 3x3 grid of lights (on or off).
- Clicking (or tapping) a light toggles it and any adjacent lights (up, down, left, right).
- Your objective is to turn **all the lights off**.
- You win if all lights are off, and lose if all are on again.

## 🧠 Game Logic

The grid is represented as a flat array of 9 elements (`lightStatus`).
Each index has a predefined relationship mapping to its neighbors:

```js
relations = {
  0: [1,3],
  1: [0,2,4],
  2: [1,5],
  ...
}
```
## Running the Program
This app was created with Vue CLI. Make sure you have Vue CLI installed globally:
```
npm install -g @vue/cli
```
Then install dependencies and start the dev server:
```
npm install       # install dependencies
npm run serve     # start the local dev server
```
To build for production:
```
npm run build
```