#include <GL/glut.h>
#include <math.h>

#define WIN_W 1000
#define WIN_H 1000

float busTopX = -250;
float busBottomX = 1000;

// Bird animation
float birdOffset = 0;
bool birdUp = true;

// Sun animation (ease-out)
float sunRadius = 5;

// ---------- BASIC SHAPES ----------
void drawRect(float x1,float y1,float x2,float y2){
    glBegin(GL_POLYGON);
    glVertex2f(x1,y1);
    glVertex2f(x2,y1);
    glVertex2f(x2,y2);
    glVertex2f(x1,y2);
    glEnd();
}

void drawCircle(float cx,float cy,float r){
    glBegin(GL_POLYGON);
    for(int i=0;i<60;i++){
        float a = 2*3.1416*i/60;
        glVertex2f(cx+cos(a)*r, cy+sin(a)*r);
    }
    glEnd();
}

// ---------- OBJECTS ----------
void drawBus(float x, float y, float r, float g, float b, int dir){
    float w = 180;
    float h = 55;
    float slant = 20;
    float cabinW = 35;

    if(dir == 1){
        glColor3f(r,g,b);
        glBegin(GL_POLYGON);
        glVertex2f(x,           y);
        glVertex2f(x+w,         y);
        glVertex2f(x+w,         y+h-slant);
        glVertex2f(x+w-slant,   y+h);
        glVertex2f(x,           y+h);
        glEnd();

        glColor3f(r*0.5f, g*0.5f, b*0.5f);
        glBegin(GL_POLYGON);
        glVertex2f(x+w-cabinW-slant, y);
        glVertex2f(x+w,              y);
        glVertex2f(x+w,              y+h-slant);
        glVertex2f(x+w-slant,        y+h);
        glVertex2f(x+w-cabinW-slant, y+h);
        glEnd();

        glColor3f(0.9f, 0.95f, 1.0f);
        int numWin = 3;
        float winStart = x + 10;
        float winAreaW = w - cabinW - slant - 20;
        float winW = 30, winH = 25;
        float gap = (winAreaW - numWin * winW) / (numWin + 1);
        for(int i = 0; i < numWin; i++){
            float wx = winStart + gap + i*(winW + gap);
            drawRect(wx, y+h-winH-8, wx+winW, y+h-8);
        }

    } else {
        glColor3f(r,g,b);
        glBegin(GL_POLYGON);
        glVertex2f(x,        y);
        glVertex2f(x+w,      y);
        glVertex2f(x+w,      y+h);
        glVertex2f(x+slant,  y+h);
        glVertex2f(x,        y+h-slant);
        glEnd();

        glColor3f(r*0.5f, g*0.5f, b*0.5f);
        glBegin(GL_POLYGON);
        glVertex2f(x,              y);
        glVertex2f(x+cabinW+slant, y);
        glVertex2f(x+cabinW+slant, y+h);
        glVertex2f(x+slant,        y+h);
        glVertex2f(x,              y+h-slant);
        glEnd();

        glColor3f(0.9f, 0.95f, 1.0f);
        int numWin = 3;
        float winStart = x + cabinW + slant + 10;
        float winAreaW = w - cabinW - slant - 20;
        float winW = 30, winH = 25;
        float gap = (winAreaW - numWin * winW) / (numWin + 1);
        for(int i = 0; i < numWin; i++){
            float wx = winStart + gap + i*(winW + gap);
            drawRect(wx, y+h-winH-8, wx+winW, y+h-8);
        }
    }

    glColor3f(0.05f, 0.05f, 0.05f);
    drawCircle(x+40,  y-5, 12);
    drawCircle(x+140, y-5, 12);
}

void drawCloud(float x,float y){
    glColor3f(1,1,1);
    drawCircle(x,y,25);
    drawCircle(x+25,y+10,30);
    drawCircle(x+50,y,25);
}

void drawBird(float x,float y){
    glColor3f(0,0,0);
    glLineWidth(2);
    float offset = birdOffset;
    glBegin(GL_LINES);
        glVertex2f(x,y);
        glVertex2f(x+10,y+offset);
        glVertex2f(x+10,y+offset);
        glVertex2f(x+20,y);
    glEnd();
}

void drawTree(float x, float y){
    glColor3f(0.45f,0.25f,0.06f);
    drawRect(x-6,y,x+6,y+30);
    glColor3f(0.0f,0.5f,0.0f);
    glBegin(GL_TRIANGLES);
    glVertex2f(x-30,y+30); glVertex2f(x+30,y+30); glVertex2f(x,y+80);
    glEnd();
    glBegin(GL_TRIANGLES);
    glVertex2f(x-22,y+55); glVertex2f(x+22,y+55); glVertex2f(x,y+100);
    glEnd();
    glBegin(GL_TRIANGLES);
    glVertex2f(x-14,y+75); glVertex2f(x+14,y+75); glVertex2f(x,y+115);
    glEnd();
}

// ---------- DISPLAY ----------
void display(){
    glClear(GL_COLOR_BUFFER_BIT);

    glColor3f(0.5,0.75,0.9);
    drawRect(0,480,1000,1000);

    glColor3f(1,1,0);
    drawCircle(900,900,sunRadius);

    drawCloud(150,850);
    drawCloud(450,800);
    drawCloud(700,850);

    drawBird(250,860); drawBird(280,880); drawBird(310,870);
    drawBird(480,820); drawBird(510,840);
    drawBird(700,860); drawBird(730,880); drawBird(760,870);

    int baseY = 480;

    int b1x=100,b1w=180;
    glColor3f(0.4,0.4,0.4);
    drawRect(b1x,baseY,b1x+b1w,baseY+300);
    int cx=b1x+b1w/2;
    glColor3f(1,0,0);
    drawRect(cx-10,baseY+230,cx+10,baseY+280);
    drawRect(cx-30,baseY+250,cx+30,baseY+260);
    glColor3f(1,1,1);
    for(int r=0;r<3;r++)
        for(int c=0;c<3;c++)
            drawRect(b1x+30+c*50,baseY+160-r*50,b1x+60+c*50,baseY+190-r*50);
    glColor3f(0.2,0.2,0.2);
    drawRect(cx-30,baseY,cx+30,baseY+60);

    int b2x=380;
    glColor3f(0.6,0.3,0.3);
    drawRect(b2x,baseY,b2x+200,baseY+220);
    glColor3f(1,1,1);
    for(int r=0;r<2;r++)
        for(int c=0;c<3;c++)
            drawRect(b2x+35+c*55,baseY+140-r*60,b2x+65+c*55,baseY+170-r*60);
    glColor3f(0.2,0.2,0.2);
    drawRect(b2x+70,baseY,b2x+130,baseY+60);

    int b3x=700;
    glColor3f(0.9,0.2,0.5);
    drawRect(b3x,baseY,b3x+240,baseY+260);
    glColor3f(1,0.7,0.4);
    drawRect(b3x+20,baseY+50,b3x+50,baseY+220);
    drawRect(b3x+190,baseY+50,b3x+220,baseY+220);
    glColor3f(0.3,0.3,0.3);
    glBegin(GL_TRIANGLES);
    glVertex2f(b3x-20,baseY+260);
    glVertex2f(b3x+260,baseY+260);
    glVertex2f(b3x+120,baseY+350);
    glEnd();
    glColor3f(1,1,1);
    drawRect(b3x+80,baseY+150,b3x+120,baseY+190);
    drawRect(b3x+140,baseY+150,b3x+180,baseY+190);
    drawRect(b3x+80,baseY+90,b3x+120,baseY+130);
    drawRect(b3x+140,baseY+90,b3x+180,baseY+130);
    glColor3f(0.2,0.2,0.2);
    drawRect(b3x+90,baseY,b3x+150,baseY+70);

    drawTree(320,480);
    drawTree(650,480);
    drawTree(950,480);

    glColor3f(0.8,0.8,0.8);
    drawRect(0,430,1000,480);

    glColor3f(0.2,0.2,0.2);
    drawRect(0,300,1000,420);
    glColor3f(1,1,1);
    for(int i=0;i<1000;i+=120)
        drawRect(i+30,350,i+90,360);

    glColor3f(0.35,0.35,0.35);
    drawRect(0,240,1000,300);
    glColor3f(1,1,0);
    drawRect(0,268,1000,272);

    glColor3f(0.2,0.2,0.2);
    drawRect(0,120,1000,240);
    glColor3f(1,1,1);
    for(int i=0;i<1000;i+=120)
        drawRect(i+30,170,i+90,180);

    drawBus(busTopX,    330, 1.0f, 0.0f, 0.0f,  1);
    drawBus(busBottomX, 150, 0.0f, 0.5f, 1.0f, -1);

    glutSwapBuffers();
}

// ---------- ANIMATION ----------
void update(int){
    busTopX += 3;
    if(busTopX > 1100) busTopX = -250;

    busBottomX -= 3;
    if(busBottomX < -250) busBottomX = 1100;

    if(birdUp){ birdOffset += 0.3; if(birdOffset > 8) birdUp = false; }
    else       { birdOffset -= 0.3; if(birdOffset < -8) birdUp = true; }

    if(sunRadius < 50){
        float speed = (50 - sunRadius) * 0.02f;
        if(speed < 0.01f) speed = 0.01f;
        sunRadius += speed;
    }

    glutPostRedisplay();
    glutTimerFunc(16,update,0);
}

void init(){
    glClearColor(1,1,1,1);
    gluOrtho2D(0,1000,0,1000);
}

int main(int argc,char** argv){
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB);
    glutInitWindowSize(WIN_W,WIN_H);
    glutCreateWindow("City Traffic Scene Simulation");
    init();
    glutDisplayFunc(display);
    glutTimerFunc(0,update,0);
    glutMainLoop();
    return 0;
}
