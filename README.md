# CS4331 VR Project 1: Covid-19 Martial Arts
## Project Description and Theme

Welocome to my Brazilian Jiu-Jitsu Gym, where I will be showing you how Covid-19 and the lockdown affected me.
Covid-19 affected all of us in different ways and some aspects of our lifestyles started to change.
One of those changes, for me, was the closing down of Martial Arts gyms.
6 weeks before lockdown happened in March 2020, I started doing Brazilian Jiu-Jitsu(BJJ) at the Texas Tech Rec Center. 
During the lockdowns, the Jiu-Jitsu club at Tech and all Martial Arts gyms around the world shut down. 
Therefore, through a Virtual Environment setting, I would like to show everyone how Covid-19 affect Martial Arts gyms. 

## The Environment
### Walls, Floor, and Roof
I started by building the walls of my Martial Arts Gym and incorporated BJJ wall papers. 
The floor is a simple plane object and the roof is an a 3d model that I found online.
* Here is a picture of the outside of what my building looks like.
![Outside Building Pic](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/OutsideBuildingPic.PNG)

I made the walls using 3 different Cubes so each wall is different cubes. That allowed me to give each vertical part of the wall a different texture.
Doing different textures with so many pictures on each wall did come with a downside, which is the decrease in performance and occasionally causing lag. I will later explaing what I did to increase performance in the performance header.
* Here is a picture of the inside of my building and what are the different wallpapers I used to make it seem like a BJJ gym.
![Inside Building Pic](https://github.com/RahilPatel04/MartialArts_VR_Project1/raw/master/ReportDocuments/Images/InsideBuilding.PNG)

### Lights and Doors
The building contains doors for access and multiple lights that give the environment lighting.
I imported all the closet doors and main door 3d models from online as well. 

However, I did make the lights in blender.
To give the effect that there the light models are emmitting light, I only used one point light positioned in the middle. 
I also used an ambient light to give just a little bit of light when the light switch is toggled and the point light turns off.
* The light models I made in Blender and they can be toggled ON/OFF by the light switch near the help desk.
![Light Model in Blender](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/LightModel.PNG)

The doors are interactable and open/close when the user clicks on them. To help out the user, there are texts about each door indicating this function.
I implemented this by changing the rotation parameters of the doors when clicked through an event.
The lights were set to turn visible/invisible when clicked through an event as well.
```js
function toggleLights(){
 <!-- Toggle lights -->
 <!-- Change the visible light state to what its not. This acts like a toggle of the lights -->
  light_1_Actual.setAttribute('visible', !light_1_Actual.getAttribute('visible'));
}
function toggleMainDoor(){
 <!-- toggles the main door to open/close -->
 if(MainDoorOpen == false){
    MainDoorVar.setAttribute('position', {x: 22.115, y: 4.511, z: 39.89});
    MainDoorVar.setAttribute('rotation', {x: 0, y: -90, z: 0});
    MainDoorOpen = true;
  }
  else{
    MainDoorVar.setAttribute('position', {x: 24.325, y: 4.511, z: 37.874});
    MainDoorVar.setAttribute('rotation', {x: 0, y: 0, z: 0});
    MainDoorOpen = false;
  }
}
```

* Here is a demo of changing the lights and the doors.
![Lights and Door Gif](https://media.giphy.com/media/Xxizchdx3kLfF0IeqM/giphy.gif)

## Navigating the Room
To help the User navigate the room, I incorporated teleportion, for VR use without keyboard, and the WASD keys.
To use teleportation, the user has to click on the purple spheres presented across the room. The position of the camera changes to the sphere upon clicking.
* There are total three purple spheres, presented in the gif, in the VR environment to help the user navigate.
I choose to implement these spheres to help out the mobile users and also to limit lag, caused by the user moving with WASD keys.
![Teleporting Spheres Gif](https://media.giphy.com/media/Dw9CWzdzYlUowPE7Mj/giphy.gif)

## Texts to Help Understand the VR Environment
In order for users to get the full immersive experience from my VR environment, I have incorporated texts to display the functionalities.
These texts are display everywhere where the user can interact with the environment.
* One important function that I wanted to add was that the text should always be facing the User. 
I acccomplished this by adding the Aframe-look-at-billboard-component registry which added to my script. Then I used the look-at="" tag on my text object and pointed that to my camera object: look-at="#camera". 
```html
<script src="https://rawgit.com/blairmacintyre/aframe-look-at-billboard-component/master/dist/aframe-look-at-billboard-component.min.js"></script>

<a-text value="Click The Punching Bags" font="https://cdn.aframe.io/fonts/mozillavr.fnt" color="#55dff7" align="center" scale="4 4 4" position="-0.061 11.9 29.529" look-at="src: #camera"></a-text>
```
* Here is a gif of one of the texts presented in the environment. As I am moving, you can see that the texts rotate and are always facing the user.
I think this functionality will help the user and encourage them to click on the items.
![Texts Gif](https://media.giphy.com/media/SXisWH9ihPiS0YQXO6/giphy.gif)

## BJJ and Covid-19


## Increasing Performance


