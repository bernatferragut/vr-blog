---
layout: post
title: "FW - Future Web:  A-Frame for WebVR"
description: "A web framework for building virtual reality experiences"
date: 2017-03-08
tags: [design, future web, webvr, angular]
comments: true
share: true
---

# A-frame

![aframe360](https://cloud.githubusercontent.com/assets/17754060/23701921/b7103940-03d7-11e7-853a-823dce17c88b.png)

### What is A-frame

A-Frame is a web framework for building virtual reality experiences. It was started by Mozilla VR to make WebVR content creation easier, faster, and more accessible.

### HTML

HTML is one of the easiest languages to understand, and many of us are already familiar with it. There are no build steps or boilerplate required nor anything to install; all we need is an HTML file:

```html
<html>
  <head>
    <script src="https://aframe.io/releases/0.5.0/aframe.min.js"></script>
  </head>
  <body>
    <a-scene>
      <a-box color="#6173F4" opacity="0.8" depth="2"></a-box>
      <a-sphere radius="2" src="texture.png" position="1 1 0"></a-sphere>
      <a-sky color="#ECECEC"></a-sky>
    </a-scene>
  </body>
</html>
```
### A-scene
(a-scene) contains all of the objects in our 3D scene. It also handles all of the setup that is traditionally required for 3D: setting up WebGL, the canvas, camera, lights, renderer, render loop as well as out of the box VR support on platforms such as HTC Vive, Oculus Rift, Samsung GearVR, and smartphones (Google Cardboard). Tons of repeated code eliminated with one clean line of HTML.

Then we can place objects within our scene using assorted primitive elements that come with A-Frame such as (a-box) or (a-sphere). This is extremely readable, and we could copy and paste this HTML to any other scene and it would behave the same. And we can use the browser’s DOM Inspector just as we would with for any other web site.

### Javascript 
We can use traditional JavaScript DOM APIs to manipulate A-Frame scenes to add logic, behavior, and functionality:

We do this in the same way we would with Unity:
1- We get the Attributes we want
2- We modify them

```js
var box = document.querySelector('a-box');
box.getAttribute('position');
box.addEventListener('click', function () {
  box.setAttribute('color', 'red');
});
```

### Entity-Component-System

Object-oriented and hierarchical patterns have well-suited the 2D web, where we lay out elements and components that have fixed behavior on a web page. 3D and VR is different; there are infinite types of objects with endless complexity. We need an easy way to build up different kinds of objects without having to create a special class for each one.

In A-Frame, an entity is simply:

> <a-entity></a-entity>

A-Frame components (not to be confused with Web Components) are reusable modules that can be plugged into any entity. They are allowed to do anything and have full access to JavaScript, three.js, and Web APIs. The structure of a basic component may look like:

```js
AFRAME.registerComponent('foo', {
  schema: {
    bar: {type: 'number'},
    baz: {type: 'string'}
  },
  init: function () {
    // Do something when component is plugged in.
  },
  update: function () {
    // Do something when component's data is updated.
  }
});
```

Then once defined, we can plug this bundle of appearance, behavior, or functionality into an entity straight from an HTML attribute.

> <a-entity foo="bar: 5; baz: qux"></a-entity>

![a-frame](https://cloud.githubusercontent.com/assets/17754060/23701920/b6fe0810-03d7-11e7-8934-252b804307e3.png)

### Component Ecosystem

A-Frame ships with several components, but since A-Frame is fully extensible at its core, the community has filled the ecosystem with tons of components such as physics, particle systems, audio visualizations, and Leap Motion controls. This ecosystem is the lifeblood of A-Frame. A developer can build a component and publish it, and then someone else can take that component and use it straight from HTML without even having to know any JavaScript.

These components are curated and collected into the A-Frame Registry. This is similar to the collection of components and modules on the Unity Asset Store, but free and open source. We make sure they work well and from there they are easily searchable and installable through multiple channels. One of which is through the A-Frame Inspector.

### A-Frame Inspector

The A-Frame Inspector is a visual tool for inspecting and editing A-Frame scenes. Similar to the browser’s DOM Inspector, you can go to any A-Frame scene, local or on the Web, and hit <ctrl> + <alt> + i on your keyboard.

This will open the visual Inspector where you can make changes and return to the scene with the reflected changes. You can visually move and place objects, poke around with properties of the components, or pan the camera around to see a different view of the scene. It’s like viewing the source in an interactive way.

### Summary

After having started to play with a-frame for few days I have to admit that is by far the easiest and more comprehensive way to start in VR today. You just need an Internet connection and some knowledge of basic Html to start playiing with. The results are relatively fast and it makes easy something that actually is far more complex than it seems like connecting to the right input device and setting up the stereo camera. VR, is like entering into the Matrix, it's deep and highly complex, but with a-frame I do think that more and more people will be able to start playin and experimenting with this exciting new world. Thumbs up for the Mozilla team in creating this beautiful piece of online software ! 

### Links

>[A-Frame](https://aframe.io/)

