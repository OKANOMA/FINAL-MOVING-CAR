# FINAL-MOVING-CAR
from OpenGL.GL import *
from OpenGL.GLU import *
from OpenGL.GLUT import *


def myinit ():
    glMatrixMode(GL_PROJECTION)
    glLoadIdentity()
    gluPerspective(60, 1, 0.1, 50)
    gluLookAt(8,9,10,
              0,0,0,
              0,1,0)
    glClearColor(0,0,0,0)
    glClear(GL_COLOR_BUFFER_BIT)


def path (): #STREET
    glLoadIdentity()
    glColor(0.4,0.4,0.4)
    glRotate(90,0,1,0)
    glBegin(GL_POLYGON)
    glVertex(61, 0, -3)
    glVertex(61, 0, 4)
    glVertex(-22, 0, 4)
    glVertex(-22, 0, -3)
    glEnd()


    glLoadIdentity()
    glColor(0,0.5,0.1)
    glRotate(90, 0, 1, 0)
    glBegin(GL_POLYGON)#RIGHT STREET SIDE
    glVertex(61, 0, -4.2)
    glVertex(61, 0, -50)
    glVertex(-22, 0, -50)
    glVertex(-22, 0, -4.2)
    glEnd()

    glLoadIdentity()
    glColor(0,0.5,0.1)
    glRotate(90, 0, 1, 0)
    glBegin(GL_POLYGON)#LEFT STREET SIDE
    glVertex(61, 0, 4.5)
    glVertex(61, 0, 50)
    glVertex(-22, 0, 50)
    glVertex(-22, 0, 4.5)
    glEnd()


    #STREET LINES#
    glLoadIdentity()
    glColor(1, 1, 1)
    glRotate(90, 0, 1, 0)
    glBegin(GL_POLYGON)
    glVertex(25, 0, 0)
    glVertex(25, 0, 1)
    glVertex(33, 0, 1)
    glVertex(33, 0, 0)
    glEnd()

    glLoadIdentity()
    glColor(1, 1, 1)
    glRotate(90, 0, 1, 0)
    glBegin(GL_POLYGON)
    glVertex(19, 0, 0)
    glVertex(19, 0, 1)
    glVertex(26, 0, 1)
    glVertex(26, 0, 0)
    glEnd()

    glLoadIdentity()
    glColor(1, 1, 1)
    glRotate(90, 0, 1, 0)
    glBegin(GL_POLYGON)
    glVertex(9, 0, 0)
    glVertex(9, 0, 1)
    glVertex(17, 0, 1)
    glVertex(17, 0, 0)
    glEnd()


    glLoadIdentity()
    glColor(1,1,1)
    glRotate(90,0,1,0)
    glBegin(GL_POLYGON)
    glVertex(0,0,0)
    glVertex(0,0,1)
    glVertex(8,0,1)
    glVertex(8,0,0)
    glEnd()

    glLoadIdentity()
    glColor(1, 1, 1)
    glRotate(90, 0, 1, 0)
    glBegin(GL_POLYGON)
    glVertex(-9, 0, 0)
    glVertex(-9, 0, 1)
    glVertex(-1, 0, 1)
    glVertex(-1, 0, 0)
    glEnd()
    #####################END OF STREET LINES



#def streetTrees ():
    glLoadIdentity()
    glRotate(90, 0, 1, 0)
    glTranslate(0,-1,0)
    glColor3f(0,0.5,0.1)
    glBegin(GL_POLYGON)
    glVertex(35, 3.5, 0)
    glVertex(35, 10, 0)
    glVertex(-25, 10, 0)
    glEnd()
    ######################

##########################################

CAR = 0
RETURN = True

def sphere ():

    global RETURN
    global CAR
    glLoadIdentity()
    glRotate(90, 0, 1, 0)
    glTranslate(CAR , 0, 0)
    glColor3f(0, 0, 0)
    glutWireSphere(0.5, 30, 30)


    if RETURN:
        CAR -= 0.05
        if CAR < -10:
            RETURN = False
    else :
        CAR += 0.05
        if CAR > 20 :
            RETURN= True




def marks ():
    glBegin(GL_LINES)
    glColor3f(1, 0, 0)
    glVertex(0, 0, 0)
    glVertex(10, 0, 0)
    glEnd()

    glBegin(GL_LINES)
    glColor3f(0, 1, 0)
    glVertex(0, 0, 0)
    glVertex(0, 10, 0)
    glEnd()

    glBegin(GL_LINES)
    glColor3f(0, 0, 1)
    glVertex(0, 0, 0)
    glVertex(0, 0, 10)
    glEnd()

angle = 0
x = 0
goForward = True
switch = 0

def move(button, x, y):
    global switch
    if button == GLUT_KEY_RIGHT:
        switch += 3
    elif button == GLUT_KEY_LEFT:
        switch -= 3


    display()

def display ():
    global angle
    global x
    global goForward
    global switch
    glClear(GL_COLOR_BUFFER_BIT)
    glMatrixMode(GL_MODELVIEW)






    glLoadIdentity()
    path()

    #glLoadIdentity()
    #streetTrees()

    glLoadIdentity()
    sphere()

    #glLoadIdentity()
    #marks()
    glLoadIdentity()
    glRotate(90, 0, 1, 0)
    glTranslate(2.5 + x, -2.5 * 0.25, -2.5 * 0.5 + switch)
    glRotate(angle, 0, 0, 1)
    glutWireTorus(0.2, 0.5, 12, 8)

    glLoadIdentity()
    glRotate(90, 0, 1, 0)
    glTranslate(-2.5 + x, -2.5 * 0.25, -2.5 * 0.5 + switch)
    glRotate(angle, 0, 0, 1)
    glutWireTorus(0.2, 0.5, 12, 8)

    glLoadIdentity()
    glRotate(90, 0, 1, 0)
    glTranslate(x,0,0 + switch)
    glColor3f(1,0,0)
    glScale(1,0.25,0.5)
    glutSolidCube(5)

    glLoadIdentity()
    glColor(0,0.6,0.8)
    glRotate(90, 0, 1, 0)
    glTranslate(x,5*0.25,0 + switch)
    glScale(0.5, 0.25, 0.5)
    glutSolidCube(5)


    glColor3f(0,0,0)
    glLoadIdentity()
    glRotate(90,0,1,0)
    glTranslate(2.5 + x ,-2.5*0.25,2.5*0.5 + switch)
    glRotate(angle, 0, 0, 1)
    glutWireTorus(0.2,0.5,12,8)

    glLoadIdentity()
    glRotate(90,0,1,0)
    glTranslate(-2.5 + x , -2.5 * 0.25, 2.5 * 0.5 + switch )
    glRotate(angle, 0, 0, 1)
    glutWireTorus(0.2, 0.5, 12, 8)


    glLoadIdentity()
    glRotate(90,0,1,0)
    glTranslate(-2.8 + x ,0,-0.5 + switch)
    glColor3f(1,1,0)
    glutWireSphere(0.2,100,100)

    glLoadIdentity()
    glRotate(90,0,1,0)
    glTranslate(-2.8 + x , 0, 0.5 + switch)
    glColor3f(1, 1, 0)
    glutWireSphere(0.2, 100, 100)


    if goForward:
        angle -= 0.9
        x += 0.05
        if x > 20:
            goForward = False
    else :
        x -= 0.05
        angle += 0.9
        if x < -7 :
            goForward = True



    glutSwapBuffers()



glutInit()
glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB)
glutInitWindowSize(900, 900)
glutCreateWindow(b"Moving Car")
glutDisplayFunc(display)
glutIdleFunc(display)
glutSpecialFunc(move)
myinit()
glutMainLoop()
