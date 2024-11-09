# WDC-A2
Project: Working with Data and Code: Code Prototype

Software used: p5.js

Outline of project: create a 2-3 second looped animation for company "Fitness Co"

Code:
//setting up of the canvas, text, and ball
let textY, ballY;
let textSpeed = 4; 
let ballSpeed = 4; 
let textDirection = -1; 
let ballDirection = 1; 
let message = "Fitness Co";
let circleRadius = 60; 
let textBounced = false; 
let ballBounced = false;

function setup() {
  createCanvas(400, 400);
  textSize(32);
  textAlign(CENTER, CENTER);
  
  textY = height / 2;
  ballY = height / 2;
}

function draw() {
  background(103, 157, 245);

  //motion of the ball and text: how I wanted them to move

  // wanted text to move upwards, bounce off top of screen and then finish in the centre
  if (!textBounced || textY !== height / 2) {
    textY += textSpeed * textDirection;
    
    if (textY < textAscent() / 2 && !textBounced) {
      textDirection *= -1; 
      textBounced = true; 
    }
    
    if (textBounced && abs(textY - height / 2) < textSpeed) {
      textY = height / 2; 
    }
  }

  // same for ball, bounce at the bottom of the screen and finish in the middle
  
  if (!ballBounced || ballY !== height / 2) {
    ballY += ballSpeed * ballDirection;
    
  
    if (ballY > height - circleRadius && !ballBounced) {
      ballDirection *= -1; 
      ballBounced = true; 
    }
    
  
    if (ballBounced && abs(ballY - height / 2) < ballSpeed) {
      ballY = height / 2; 
    }
  }
  

  fill(255, 165, 0); 
  ellipse(width / 2, ballY, circleRadius * 2, circleRadius * 2);
  
  fill(0); 
  text(message, width / 2, textY);
}
