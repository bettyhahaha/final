# final
let img;
let img2;
let img3;
let img4;
let img5;
let img6;
let INIT = 0;
let WON = 1;
let LOST = 2;

let state = INIT;

function preload() {
  img = loadImage("road.jpg");
  img2 = loadImage("padestrian1.png");
  img3 = loadImage("padestrian2.png");
  img4 = loadImage("padestrian3.png");
  img5 = loadImage("banana.png");
  img6 = loadImage("can.png");
}

function setup() {
  createCanvas(400, 400);
}

var img2a = -150;
var img2speed = 3;
var img3a = -250;
var img3speed = 2;
var img4a = 400;
var img4speed = 4;
var img5a = 10;
var img5speed = 5;
var img6a = -300;
var img6speed = 4;

var images = [img2a, img3a, img4a, img5a, img6a];
var range = 120;

function inRect(x, y, l, t, range) {
  
  return (x >= l && x <= l + range) && ( y >= t && y <= t + range);
}

function mousePressed() {
  image(img5, img2a + 3, img5a);
  image(img6, img3a + 2, img6a);
  if (inRect(mouseX, mouseY, img2a + 3 + 20, img2a + 20, range )) {
    console.log("a");
    state = LOST;
  }
  if (inRect(mouseX, mouseY, img4a + 6 + 50, img3a + 100 ,range)) {
    console.log("a");
    state = LOST;
  }
  if (inRect(mouseX, mouseY, img6a + 2 + 30, img4a +40,range)) {
    console.log("a");
    state = LOST;
  }
  if (inRect(mouseX, mouseY, img2a + 3 + 70, img5a + 220,range)) {
    console.log("a");
    state = WON;
  }
  if (inRect(mouseX, mouseY, img3a + 2, img6a + 240,range)) {
    console.log("a");
    state = WON
  }
}

function draw() {
  background(220);
  image(img, 0, 55);
  text("State: " + state, 10, 10);
  
  if (state === INIT) {
  if (mouseIsPressed) {
    fill(50, 50, 100);
    ellipse(mouseX, mouseY, 20, 20);
  } else {
    fill(0, 150, 0);
    ellipse(mouseX, mouseY, 20, 20);
  }
    
  // these are for the green rectangles, you can remove this
 // rect(img2a + 3 + 20, img2a + 20, range, range);
  //rect(img4a + 6 + 50, img3a + 100 ,range, range) 
  //rect(img6a + 2 + 30, img4a +40,range, range) 
 // rect(img2a + 3 + 70, img5a + 220,range, range) 
 // rect(img3a + 2, img6a + 240,range, range) 
    
    
  image(img2, img2a + 3, img2a);
  image(img3, img4a + 6, img3a);
  image(img4, img6a + 2, img4a);
  image(img5, img2a + 3, img5a);
  image(img6, img3a + 2, img6a);
  img2a = img2a + img2speed;
  img3a = img3a + img3speed;
  img4a = img4a - img4speed;
  img5a = img5a + img5speed;
  img6a = img6a + img6speed;
  if (img2a >= 430) {
    img2speed = -3;
  }

  if (img5a >= 450) {
    img5speed = -6;
  }

  if (img5a <= -250) {
    img5speed = 6;
  }

  if (img3a >= 400) {
    img3speed = -2;
  }

  if (img4a <= -10) {
    img4speed = -4;
  }

  if (img2a <= -30) {
    img2speed = 3;
  }

  if (img3a <= -30) {
    img3speed = 2;
  }

  if (img4a >= 450) {
    img4speed = 4;
  }

  if (img6a >= 500) {
    img6speed = -4;
  }

  if (img6a <= -300) {
    img6speed = 4;
  }
  
  }
  
  if (state === WON) {
    text("Y0ou won", 20, 30);
  }
  
  if (state === LOST) {
    text("Y0ou Lost", 20, 30);
  
  }
  
  

  // ellipse(mouseX, mouseY, 20, 20);
}
