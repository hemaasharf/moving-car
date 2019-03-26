# moving-car
from OpenGL.GL import *
from OpenGL.GLU import *
from OpenGL.GLUT import *

def draw_XYZ():
    glBegin(GL_LINES)
    # x_axis
    glColor3f(0, 0, 0)
    glVertex(0, 0, 0)
    glVertex(10, 0, 0)

    glVertex(0, 0, 0)
    glVertex(-30, 0, 0)

    glVertex(10, 0, 10)
    glVertex(-30, 0, 10)
    # y_axis
    glColor3f(0, 0, 0)
    glVertex(0, 0, 0)
    glVertex(0, 10, 0)

    # z_axis
    glColor3f(0, 0, 0)
    glVertex(0, 0, 0)
    glVertex(0, 0, 10)
    glEnd()


def myInit():
    glMatrixMode(GL_PROJECTION)
    glLoadIdentity()
    gluPerspective(60, 1, 1, 30)
    gluLookAt(8, 9, 10,
              0, 0, 0,
              0, 1, 0)

    glClearColor(.1,.3,.4,.5)
    glClear(GL_COLOR_BUFFER_BIT)


angle = 0
x = 0
forward = True
def cube(a,b):
    glLoadIdentity()
    glColor3f(a, a, a)
    glScale(.8, .2, .2)
    glTranslate(-b, -5, -25)
    glutSolidCube(5)
def cube_left(a,b):
    glLoadIdentity()
    glColor3f(a, a, a)
    glTranslate(-b, 0, 5.5)
    glScale(0.8, 0.2, 0.22)
    glutSolidCube(5)

def draw():
    global angle
    global x
    global forward

    glMatrixMode(GL_MODELVIEW)
    glLoadIdentity()
    glClear(GL_COLOR_BUFFER_BIT)
    # road
    glLoadIdentity()

    glBegin(GL_QUADS)
    glColor3f(.2, .2, .2)
    glVertex(10, -.5, -3.2)
    glVertex(-19, -.5, -3.2)
    glVertex(-19, -.5, 6)
    glVertex(10, -.5, 6)

    glColor3f(1, 1, 1)
    glVertex(10, 0, -.5)
    glVertex(-17, 0, -.5)
    glVertex(-17, 0, 0)
    glVertex(10, 0, 0)

    glVertex(10, 0, 3)
    glVertex(-17, 0, 3)
    glVertex(-17, 0, 3.5)
    glVertex(10, 0, 3.5)

    #middle
    glVertex(5,0,2)
    glVertex(0,0,2)
    glVertex(0,0,1)
    glVertex(5,0,1)

    glVertex(-3,0,2)
    glVertex(-8,0,2)
    glVertex(-8,0,1)
    glVertex(-3,0,1)

    glEnd()

    glBegin(GL_QUADS)
    glColor3f(0.7, 0.7, .1)
    glVertex(-30, -1, -6 )
    glVertex(-30, -1, -15)
    glVertex(15, -1, -15 )
    glVertex(15, -1, -6)
    glEnd()
    glBegin(GL_POLYGON)
    glColor3f(0.7, 0.7, .1)
    glVertex(-25, -1, 5)
    glVertex(-30, -1, 14)
    glVertex(15, -1, 15)
    glVertex(15, -1, 5)
    glEnd()

    #draw_XYZ()

    # first_cube

    glColor3f(0, 0, 0)
    glTranslate(x, 0, 1.5)
    glScale(1, 0.25, 0.5)
    glutSolidCube(5)
    # second_cube
    glLoadIdentity()
    glColor3f(.4, 0.5, 0.5)
    glTranslate(x, .25*5, 1.5)
    glScale(.5, .25, .5)
    glutSolidCube(5)
    # right_front_torus
    glColor3f(0, 0, 0)
    glLoadIdentity()
    glTranslate(.5*5+x, -.5*.25*5, 5*.5*.5+1.5)
    glRotate(angle, 0, 0, 1)
    glutSolidTorus(.125, .5, 10, 10)

    # left_front_torus
    glLoadIdentity()
    glTranslate(-.5 * 5+x, -.5 * .25 * 5, 5 * .5 * .5+1.5)
    glRotate(angle, 0, 0, 1)
    glutSolidTorus(.125, .5, 10, 10)


    # right_behind_torus
    glLoadIdentity()
    glTranslate(x+.5 * 5, -.5 * .35 * 5, -5 * .5 * .5+1.5)
    glRotate(angle, 0, 0, 1)
    glutSolidTorus(.125, .5, 10, 10)

    glLoadIdentity()
    glColor(0, 0, 1)
    glTranslate(x+2.4, 0, 0.5+1.5)
    glutSolidSphere(.2, 100, 100)

    glColor3f(0, 0, 1)
    glLoadIdentity()
    glTranslate(x + 2.4, 0, -0.8+1.5)
    glutSolidSphere(0.2, 100, 100)

    # pavement left
    cube(0,25)
    cube(1,20)
    cube(0,15)
    cube(1,10)
    cube(0, 5)
    cube(1, 0)
    cube(0,-5)
    cube(1,-10)
    ##

    # pavement right
    cube_left(0,5)
    cube_left(1, 3)
    cube_left(0, 1)
    cube_left(1, -1)
    cube_left(0, -3)
    cube_left(1, -5)
    cube_left(0, -7)

    glutSwapBuffers()

    if forward:
        angle -= 0.1
        x += 0.02
        if x > 10:
            forward = False
    else:
        angle += 0.1
        x -= 0.02
        if x < -10:
            forward = True


glutInit()
glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB)
glutInitWindowSize(600, 600)
glutCreateWindow(b"Moving Car")
myInit()
glutDisplayFunc(draw)
glutIdleFunc(draw)
glutMainLoop()
