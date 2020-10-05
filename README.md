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
Due to the Lockdowns and Covid-19, BJJ gyms were shut down and then opened back up in June/July.
To represent that experience, I implemented a Covid-19 Toggle button, that is located on the help desk, with the appropriate texts above it describing what Covid-19 mode the user is in.
### Covid-19 Toggle Button
There are three modes that represent the stages(Modes) that BJJ gyms went through: Mode 1(Normal), Mode 2(Lockdowns), and Mode 3(Current Situtation).
* Picture of the Covid-19 Button that we will use to toggle Covid mode. The Covid button is controlled by an event that is handled in three.JS.
When the button changes mode, certain objects either turn invisible/visible, change animation clips, or change positions. These will be later explained in the headers below.

![Covid-19 Button Pic](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/CovidButtonPic.PNG)
### Mode 1: Normal
Mode 1: Normal. This is what BJJ gyms where like in January/February. This is also the default setting that the User spawns in the environment with.
There are some objects in this default scene that potrays the theme of what BJJ was before the lockdowns. 
#### The BJJ Fighter Models
* I made one fighting character model in blender using low poly items like cubes and spheres.

![Fighter with no armature](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/FighterPic2.PNG)
* To make this fighter animate, I made an armature, wihch is like bones, for the character and then later made animation clips/sequences so the model can fight/move.

![Fighter with armature](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/FighterPic1.PNG)
* This is what the animation clips looked like in Blender and as you can see, in the middle of the frames (119), the fighters are in fact in middle of their animations.

![Fighters with their animations](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/FighterFightingSequence.PNG)
* I imported these fighters in AFrame and activated their animations. 
The fight sequences for both of the fights were done independently in blender and I had to go through a lot of trail and error to make the animations correspond with one another.

![Red Mat Fighters](https://media.giphy.com/media/v1sUHMhk1zEo7lY33m/giphy.gif)
![Blue Mat Fighters](https://media.giphy.com/media/El0fy8vw6zAmsi7mJH/giphy.gif)
* My code to activate their animations:
```html
<!-- Fighters -->
<a-entity id = "Fighter1" gltf-model="#FightersLeave" scale = ".65 .65 .65" position="-3.25 -0.268 -8.13" rotation="0 180 0" animation-mixer="clip: ArmatureAction;"></a-entity>      
<a-entity id = "Fighter2" gltf-model="#FightersLeave" scale = ".65 .65 .65" position="-3.25 -0.268 -1.053" rotation="0 0 0" animation-mixer="clip: ArmatureAction;"></a-entity>
<a-entity id = "Fighter3" gltf-model="#FighterMounted_Scene2" scale = ".65 .65 .65" position="33.24 -0.268 -36.95" rotation="0 0 0" animation-mixer="clip: ArmatureAction;"></a-entity>
<a-entity id = "Fighter4" gltf-model="#FighterOnGround_Scene2" scale = ".65 .65 .65" position="33.24 -0.268 -36.95" rotation="0 0 0" animation-mixer="clip: Armature.001Action;"></a-entity>
```
#### The Chairs for Viewership 
Before the Covid-19 lockdowns, many BJJ gyms would have tournaments and people would come watch. To implement this, I got 3d chair models from online.
To add the effect that you are watching the matches as well, if you click on the chair, your camera get teleported to the chair and it feels like you are spectating the match.
As you can see from the gif, you can click on any chair and if feels like you are sitting down and spectating. This functionality is also available on the benches in the locker room.

![ChairSpectating](https://media.giphy.com/media/GQKHvD7ThuqdZ52V9w/giphy.gif)
* Code for this function. This is same code for the chairs as well. The offset parameter helps to decrease the y value of the camera and makes it like you are sitting down.
```js
<!-- register the teleport element with our teleport spheres -->
 AFRAME.registerComponent('teleport', {
  schema:{
    offset:{type:"number", default:0}
  },
  init: function(){  
    var offset = this.data;
    this.el.addEventListener('click', function(evt){
    var camera = document.querySelector('#camera');
    camera.setAttribute('position', {x:this.getAttribute('position').x, y:this.getAttribute('position').y+offset, z:this.getAttribute('position').z});
   });
 }
});
```
#### Boxing
In many BJJ gyms, there are boxing classes available as well. I put in boxing model such as the boxing bags and the boxing bag frame. 
Try clicking on the punching bags and punching sound effects will be heard.

![Boxing](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/BoxingAreaPic.PNG)
### Mode 2: During Lockdown (March)
The user can switch Modes by clicking on the Covid button. The text above the button will help the user with what mode they are on.
Mode 2 is to represent during lockdown mode, where everybody left the gyms and the places were closed.
To express this effect, I made another animation for the two fighters on the blue mat. When Mode 2 is initiazed, the two fighters will start animation 2, which is to leave the BJJ gym.
Additionally, the lights also get turned off and the fighters on the red mat are turn invisible. The chairs that were used for spectators are now placed, by changing their positions, in the closet since they won't be of use now. 

![FightersLeaving](https://media.giphy.com/media/F2ZDDEp51BlN0two1N/giphy.gif)
* Code: this is part of the code that sums up on how I was able to change object/situations in the same scene. As you can see, if we are in mode 1 and the button is clicked, then initiate mode 2.
These coding sequences are very crucial to my VR app since they control the different covid modes. 
This piece of code represents the three ways I used to change the situtaion: turning objects invisible/visible, changing animation clips, and changing positions.
```JS
            <!-- covidMode will toggle off between our scenes. 1 is normal, 2 is during covid, and 3 is after lockdowns(June, July, August)
            if(covidMode == 1){
              <!-- Change fighters 1 and 2 animaiton so they leave the building during lockdown phase -->
              fighter1.setAttribute('rotation', {x: 0, y: 0, z: 0});
              fighter1.setAttribute('animation-mixer', 'clip: Leave');
              fighter2.setAttribute('animation-mixer', 'clip: Leave');
              <!-- Make fighters 3 and 4 invisible -->
              fighter3.setAttribute('visible', !fighter3.getAttribute('visible'));
              fighter4.setAttribute('visible', !fighter4.getAttribute('visible'));
              
              <!-- Put chairs in closet -->
              chair1.setAttribute('position', {x: 60.171, y: 0, z: 2.564});
              chair2.setAttribute('position', {x: 60.171, y: 0.4, z: 2.564});
              chair3.setAttribute('position', {x: 60.171, y: 0.8, z: 2.564});
              chair4.setAttribute('position', {x: 60.171, y: 1.2, z: 2.564});
              chair5.setAttribute('position', {x: 60.171, y: 1.6, z: 2.564});
              <!-- Make ChairText go invisible -->
              ChairTextVar.setAttribute('visible', 'false');
              
              <!-- Turn off lights -->
              light_1_Actual.setAttribute('visible', 'false');
              
              <!-- Change the Covid Mode Text -->
              CovidModeTextVar.setAttribute('value', CovidMode2);
              
              <!-- Open the door so fighters can leave -->
              if(MainDoorOpen == false){
                toggleMainDoor();
              }
              <!-- Open the closet doors so the chairs are seen in the closet -->
              if(ClosetDoorOpen == false){
                toggleClosetDoor();  
              }
              
              covidMode = 2;
            }
```
### Mode 3: After Lockdown(June/July 2020) - Current Situation
Mode 3 is supposes to represent the current situation in which many Martial Arts/BJJ gyms are in now.
During June/July 2020, depending on what state, gyms started to open up and some people went back to their BJJ gyms.
However, there were some gyms that implemented training dummys that their students can train on instead of training with other students.
* This gif shows up the two scenarios that I mentioned and as you can also see that the chairs are still in the closet.
Due to minimizing visitors as much, I assumed that there would be not spectators allowed in the gyms, just people who want to go do BJJ.
The fighters on the red mat became visible and the fighters on the blue mat become invisible. On the blue mats, some training dummy become visible instead.

![Mode 3 gif](https://media.giphy.com/media/FjXt4Ldux85rw5OtSi/giphy.gif)
* I also made the dummy model in blender using low poly objects.

![dummy pic](https://raw.githubusercontent.com/RahilPatel04/MartialArts_VR_Project1/master/ReportDocuments/Images/DummyPic.PNG)
### Feel Free to Play Around the Environment
You can click the covid-19 button as much as you like and also interact with everything that has signage above it.

## Issues Faced: Optimizing Performance
One major issue that I faced was reaching 60 fps in my VR environment. 
Unfortunately, I was only getting 45 fps so I had to reasearch some performance optimization techniques.
I came across this webpage: [AFrame Best Practices Documentation](https://aframe.io/docs/1.0.0/introduction/best-practices.html)
The implementations that I made were:
* Resized my textures to powers of two(512X1024, 256X256, etc)
* Some online 3d models were out-of-date and were causing performance issues. I simply opened them up in my 3D viewer software and save them again.
* The biggest change that I made was to not use a background, such as sky, but just use a default colored background.
These changes ended up fixing the issue and gave me 60 fps.

## Conclusion
I learned a lot about WebVR and really enjoyed working on the project. I focused most of my time on making the 3d character models and its animations.
Covid-19 and the lockdowns affected a lot of people and I hope I was able to make this project a little bit informative about how the Martial Arts/BJJ community was hit by Covid-19/lockdowns.
Thank you for reading my report and I hope you really enjoyed/learned from my VR project.

## Resources Used
### Textures:
* Walls: <https://texturehaven.com/tex/?c=plaster&t=white_plaster_03>
* Top Wall:

<https://wallpapercave.com/bjj-wallpapers>
<https://wallpapercave.com/w/wp1955433>
<https://wallpapercave.com/w/wp1955388>
<https://wallpapercave.com/w/wp1955349>
<https://wallpapercave.com/w/wp1955347>
<https://wallpapercave.com/w/wp1955347>
<https://wallpapercave.com/w/wp1955345>

### Online 3d Models:
* Floor: <https://texturehaven.com/tex/?c=concrete&t=concrete_floor_painted>
* Roof:  <https://sketchfab.com/3d-models/roof-or-floor-98b5ee3f85b34ead9884e87d50c40302>
* Desk: <https://sketchfab.com/3d-models/modern-l-shaped-desk-ea003301e9f945639fc27e880960bcb0>
* Water Fountain: <https://sketchfab.com/3d-models/water-fountain-low-poly-52c818cc6bad4129941378ec2bec34a5>
* Computer: <https://poly.google.com/view/2EHvZLax4Y3>
* Mop: <https://sketchfab.com/3d-models/mop-4f95d61bb5b04dd9b2b543a0c4cbb060>
* Light Switches: <https://poly.google.com/view/1xBl-8de6b0>
* Main Door and Closet Door: <https://poly.google.com/view/2F9VFWWTLs7>
* Lockers: <https://poly.google.com/view/3jGb44V-Ske>
* Benches in Lockers: <https://poly.google.com/view/2EvQDFgG1H3>
* Chairs: <https://poly.google.com/view/7Jl72KgiRl->
* Animated Training Dummy: <https://sketchfab.com/3d-models/animated-training-dummy-46f5711e3ac04900a49732d78f4f64d8>
* Shoe Rack: <https://sketchfab.com/3d-models/ikea-tjusig-shoe-rack-948a2d3130ea40fbbb2dc0a676580a28>
* Punching Bag: <https://poly.google.com/view/aODw_lbKxQP>
* Shoes: <https://poly.google.com/view/0ASn5OTnrkz>

### Sound Bits Used:
* Punching Sound: <https://www.zapsplat.com/music/cartoon-punch-5/>
* Emergency Sound heard when Covid Button hit: <https://www.zapsplat.com/music/cartoon-punch-5/>

### Self Made 3d Models (Located in Assests folder):
* Fighting Character Models (4 Same Models)
* Covid Button
* Training Dummy
* Tech Punching Bag
* Lights on the Roof
* All of the Fighting Animations
* The Blue and the Red Mats
* Walls

