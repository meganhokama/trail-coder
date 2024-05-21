#Trail Coder
How to create a game like “Trail Coder"?

Trail Coder was created in Twine. Trail Coder is based on the video game classic The Oregon Trail, but is intended to teach players some of the basic mechanics of coding in python. 

Twine is a free software that is available for download and can be used to create choose-your-own adventure-type stories, which makes it an ideal platform for developing a choice-based video game. Since The Oregon Trail works on basic mechanics of player choice, we thought Twine would be an ideal platform to develop Trail Coder.

We are creating this toolkit and basic walk-through to help others create their very own educationally enhanced video games like Trail Coder.

Part 1 – Install the software

To build a game like Trail Coder you need to either download the application Twine or open up the browser application of Twine.  Twine is a free and open-source tool built for making interactive stories or games using hypertext in the form of web pages.
You can download Twine on your computer using this site: https://twinery.org/ 
Twine has multiple languages you can write your file in. We used Harlowe to make Trail Coder. If you would like to use our game as a template you can download the .html file. Then, in Twine, you will see a menu item called library. Click on that, and then click on import. Find the.html file and import it.

How the game works

The game itself functions similarly to the Oregon Trail with twist. The player is a character that has the goal of heading out west. However, due to new laws that have been passed any time the player interacts with a robot they must speak to the robot in Python. The player needs to navigate the trip out west while also abiding by this new law forcing the player to learn how to do some basic coding in order to communicate with others while on your trip west. If the player doesn’t communicate properly with the right robots they might find themselves in prison rather than on the West Coast. 
 
Getting to pick your name

We decided that one of the pieces of control that we wanted the player to have was being able to input their name. To do that we just used:
(set: $name to (prompt: "What is your name?", ""))
And then any time that we were going to use the player's name you use the variable $name and it have a pop-up box that allows players to type in the name of their choosing. 
Question Prompts 

We wanted to have players exercise what they have learned by allowing them to input answers rather than simply identifying the answer. We did this by implementing the code below:

(set: $items to (prompt: "What would you like to purchase? Hint: You are craving food, so be sure to print properly 'I want bread'", ""))

(if: $items is "print('I want bread')"or $items is "print(\"I want bread\")")[[[The robot signals a green blinking light indicating that it understands you. -> Y2]]]

(else:)[[[The robot signals a red blinking light indicating that it does not understand you. -> N2]]]

By storing the question into an item, you are able to prompt a question requiring certain answers. We wanted to allow two acceptable answers so we used “or” as a way to allow players to submit either double or single quoted print answers. Any other answer links to a different passage that signals that the player inputted an incorrect answer. 

Variable counters

Throughout the game each choice you make has a variable counter associated with it. Each decision influences three category counters: health, strength, and knowledge. We wanted to replicate the stats similar to the Oregon Trail so choices do affect your stats. 
Depending on their choice of occupation and state in the customization passage, the player gains either +5 knowledge, strength, or health points. Another instance where player’s decisions affect their points is whether they select their item: med kits (+5 health), clothing (+5 knowledge), and bread (+5 strength). Additionally, a player will lose -10 points from their health bar if they answer a question incorrectly. 
You are able to see your stats in a floating box in the upper left corner throughout the game. 
(float-box: "X====", "Y====")[knowledge: $knowledge
strength: $strength]
By putting 4 equal signs after the X and Y, it allows you to space where the float box should be placed. 

Health bar

This was honestly a very tricky process, however, this involved going into the stylesheet that allowed you to create a bar. You access the stylesheet by clicking the up arrow on the bottom left of your opened twine file and shown in the picture below. Once in the story stylesheet, a screen will appear where you can type in code which allows you to adjust the size and style of the bar. The code we used specifically is this:
#health-bar {
	-webkit-box-sizing: border-box;
	-moz-box-sizing: border-box;
	box-sizing: border-box;
	width: 200px;
	height: 20px;
	padding: 5px;
	background: #ddd;
	-webkit-border-radius: 5px;
	-moz-border-radius: 5px;
	border-radius: 5px;
	position: relative;
}
.bar {
	background: #c54;
	width: 100%;
	height: 10px;
	position: relative;
	transition: width .5s linear;
}

tw-include[title="Update Health Bar"] {
	display: none;
}

We set the max health in the game to 100 before the start of the game and depending on the player’s choices, the health bar can go either up or down. This was quite a tedious process as you had to put the display code in each passage after setting the points in each passage. 

<div id="health-bar">\
	<div class="bar"></div>\
</div>\
(print: "<script>GE.updateHeathBar(" + (text: $maxHealth) + "," + (text: $health) + ");")


Using Pictures:

Pictures can be added to the game as well to help with immersion. An image can be place in the game by using this code:  <center><img src= YOUR URL HERE ></center> 
It is important to note that the URL does need to lead to a direct jpg image, just leading to a general website will not get the image to show up. In order to fix this and also ensure licensing we found out images for Trail Coder using Google’s creative commons license tool. To find this go to google images, once there click the tools button below and to the right of the search bar. This will bring up more options. Click ‘Usage Rights” and then choose “Creative Commons licenses”. This should bring you to pictures that can easily be licensed for creative uses. We only used pictures from Wikimedia website. We also found that in order for the image to load properly you need to not just click the image to get to the website, but then click it again just so you are seeing the URL of just the image itself. Below is an example code of a picture that is centered on the screen with a set width. 
<center><img src= https://upload.wikimedia.org/wikipedia/commons/e/e7/Wild_west_(5882792440).jpg width='600'></center> 

Changing Font: 

The general font of the game can also be edited using the story stylesheet. You access the stylesheet by clicking the up arrow on the bottom left of your opened twine file and shown in the picture below. Once in the story stylesheet a screen will appear where you can type in code which changes your font type. The code we used specifically is this:

@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

tw-story {
    font-family: "Press Start 2P", system-ui;
      color: #39FF14;
}


This code created an Oregon Trail-like feel in our game.
Additional Twine Resources: 

There are many Twine concepts we did not use in Trail Coder, however, that doesn’t mean that providing more resources wouldn't be helpful. Below are some concepts that could be included into Twine games, but were not implemented in Trail Coder. Dr. Meaghan Wetherell had students create a game called SciCombat and some of the below sections were written by Dr. Wetherell to describe issues she was having with building that game, but could be very applicable to any game written in Twine..
 
References
We pretty exclusively used a Harlowe reference vignettes page. Harlowe is the language that we wrote this game in: https://twine2.neocities.org/
There is a little bit of CSS code in this game as well which you can see if you open up the story stylesheet.This allowed me to center different graphics. The CSS information on W3 schools was pretty useful: https://www.w3schools.com/css/css_align.asp
We didn't end up using much of this for this particular game but I have in the past and this is a great resource for CSS as well in twine: https://www.adamhammond.com/wp-content/uploads/2017/03/2_css_twineguide2-1_hammond.pdf
 For the health bar, we referenced a twine post that implemented a moving health bar: https://twinery.org/questions/351/how-can-i-implement-a-visual-health-bar-in-harlowe-2-0-1
