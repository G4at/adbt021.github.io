import processing.sound.*;
SoundFile blop;

int balls = 20;

float[] x = new float[balls];
float[] y = new float[balls];
float[] xSpeed = new float[balls];
float[] ySpeed = new float[balls];
float[] size = new float[balls];
float[] r = new float[balls];
float[] g = new float[balls];
float[] b = new float[balls];

void setup() {
 blop = new SoundFile(this, "blop.wav");
  size(700, 700);
  for (int i = 0; i < balls; i++) {
    x[i] = random(width);
    y[i] = random(height);
    xSpeed[i] = random(-3, 3);
    ySpeed[i] = random(-3, 3);
    size[i] = random(50, 125);
    r[i] = random(256);
    g[i] = random(256);
    b[i] = random(256);
  }
}

void draw() {

  background(#EDAFAF);

  for (int i = 0; i < balls; i++) {

    x[i] += xSpeed[i];
    if (x[i] < 0 || x[i] > width) {
      xSpeed[i] *= -1; blop.play();
    }

    y[i] += ySpeed[i];
    if (y[i] < 0 || y[i] > height) {
      ySpeed[i] *= -1; blop.play();
    }

    fill(r[i], g[i], b[i]);
    ellipse(x[i], y[i], size[i], size[i]);
  }
}
