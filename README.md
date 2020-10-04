# CS4331 VR Project 1: Covid-19 Martial Arts
## Project Description and Theme

The objective of Project 1 was to make a VR enviornment that showed how Covid-19 and the lockdowns affected you. 
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
![Outside Building Pic](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/OutsideBuildingPicture1.PNG)

I made the walls using 3 different Cubes so each wall is different cubes. That allowed me to give each vertical part of the wall a different texture.
Doing different textures with so many pictures on each wall did come with a downside, which is the decrease in performance and occasionally causing lag.
* Here is a picture of the inside of my building and what are the different wallpapers I used to make it seem like a BJJ gym.
![Inside Building Pic](https://github.com/RahilPatel04/MartialArts_VR_Project1/raw/master/ReportDocuments/Images/InsideBuildingPicture.PNG)

### Lights and Doors
The building contains doors for access and multiple lights that give the environment lighting.
I imported all the closet doors and main door 3d models from online as well. 

However, I did make the lights in blender.
To give the effect that there the light models are emmitting light, I used two point lights for each light model.
One point light was at a higher intensity, giving the effect that the light model was emmitting light while another point light was at a lower intensity but with a greater distance, thus lighitng up the room with a less intensity.
* The light models I made in Blender
![Light Model in Blender](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/LightsBlenderModel.PNG)
![Light Model in Scene](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/Lights.PNG)
* The lights can also be turned ON/OFF by clicking on the Light Switch on the wall
![Light Switch](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/LightSwitch.PNG)

The doors are interactable and open/close when the user clicks on them. To help out the user, there are texts about each door indicating this function.
![MainDoor](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/MainDoor.PNG)

## Navigating the Room
To help the User navigate the room, I incorporated teleportion, for VR use without keyboard, and the WASD keys.
To use teleportation, the user has to click on the purple spheres presented across the room.
* As you can see, there are total three purple spheres, presented in the picture, in the VR environment to help the user navigate.
I choose to implement these spheres to help out the mobile users and also to limit lag, caused by the user moving with WASD keys.
![Teleporting Spheres](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/teleportingSpheres.PNG)

## Texts to Help Understand the VR Environment
In order for users to get the full immersive experience from my VR environment, I have incorporated texts to display the functionalities.
These texts are display everywhere where the user can interact with the environment.
* Here is a picture of the Texts layed out within the room.
![TextPic1](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/TextsPicture1.PNG)
* One important function that I wanted to add was that the text should always be facing the User. 
I acccomplished this by adding the Aframe-look-at-billboard-component registry which added to my script. Then I used the look-at="" tag on my text object and pointed that to my camera object: look-at="#camera". 
```html
<script src="https://rawgit.com/blairmacintyre/aframe-look-at-billboard-component/master/dist/aframe-look-at-billboard-component.min.js"></script>

<a-text value="Click The Punching Bags" font="https://cdn.aframe.io/fonts/mozillavr.fnt" color="#55dff7" align="center" scale="4 4 4" position="-0.061 11.9 29.529" look-at="src: #camera"></a-text>
```
* Here is a picture of the same texts presented in the previous picture above. However, I am standing at a differenct spot looking at them from a different angle and the texts still end up looking at me.
I think this functionality will help the user and encourage them to click on the items.
![TextPic2](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/TextsPicture2.PNG)

## Increasing Performance


