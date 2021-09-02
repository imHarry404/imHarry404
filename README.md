![head.png](https://github.com/imHarry404/my_django/blob/master/my%20django%20study/banner.png)

Hi there, thanks for stopping by, this is **Hariom Kumar**.

<img align='right' src="https://raw.githubusercontent.com/iCharlesZ/FigureBed/master/img/octocat.gif" width="230">

```javascript
const Harry = {
    pronouns: "He" | "Him",
    askMeAbout: ["AI","ML, "Web-Dev", "Tech"],
    technologies: {
        frontEnd: {
            python:["Pandas","Numpy","Matplotlib","OpenCv","TenserFlow","Keras"],
            js: ["Node","Express","React", "Angular"],
            css: ["CSS3","SCSS", "Tailwind"]
            
        },
        backEnd: ["Python", "Node"],
        databases: ["MONGODB", "MYSQL"],
        framework:["Django"], 
        editor:["Jupyter","Vs Code"]
     },
};
```
![bottom.png](https://raw.githubusercontent.com/iCharlesZ/FigureBed/master/img/readme-bottom.png)

---

⭐️ From [@imHarry404](https://github.com/imHarry404)


textContents = "Hello, I’m Nicolas Goutay, a web developer who specializes in application development, but dabbles in all things creative."

canvasWidth = 800
canvasHeight = 500
padding = 20
fontSize = 56

function setup() {
  createCanvas(canvasWidth, canvasHeight);
  // create a p5.Graphic acting as mask.
  pg = createGraphics(canvasWidth,canvasHeight);
  img = createImage(canvasWidth,canvasHeight);
  
  // create a p5.Graphics containing the image that will be masked
  pg2 = createGraphics(canvasWidth,canvasHeight);
  // draw some stuff.
  pg2.background(178, 217, 194);
  pg2.fill('#FFF');
  pg2.textSize(fontSize);
  pg2.text(textContents, padding, padding, canvasWidth - padding, canvasHeight - padding);
}

function draw() {
  background(228, 107, 42);
  pg.background(255);
  pg.fill(0);
  pg.ellipse(mouseX,mouseY,200);
  fill(165, 60, 103, 255);
  textSize(fontSize);
  text(textContents, padding, padding, canvasWidth - padding, canvasHeight - padding);
  text('Nice to meet you!', 250, canvasHeight - 80, canvasWidth - padding, canvasHeight - padding);
  var maskedImage1 = pgMask(pg2, pg);
  image(maskedImage1, 0, 0);
}

function pgMask(_content,_mask){
  //Create the mask as image
  var img = createImage(_mask.width,_mask.height);
  img.copy(_mask, 0, 0, _mask.width, _mask.height, 0, 0, _mask.width, _mask.height);
  //load pixels
  img.loadPixels();
  for (var i = 0; i < img.pixels.length; i += 4) {
    // 0 red, 1 green, 2 blue, 3 alpha
    // Assuming that the mask image is in grayscale,
    // the red channel is used for the alpha mask.
    // the color is set to black (rgb => 0) and the
    // alpha is set according to the pixel brightness.
    var v = img.pixels[i];
    img.pixels[i] = 0;
    img.pixels[i+1] = 0;
    img.pixels[i+2] = 0;
    img.pixels[i+3] = v;
  }
  img.updatePixels();
  
  //convert _content from pg to image
  var contentImg = createImage(_content.width,_content.height);
  contentImg.copy(_content, 0, 0, _content.width, _content.height, 0, 0, _content.width, _content.height);
  // create the mask
  contentImg.mask(img)
  // return the masked image
  return contentImg;
}
