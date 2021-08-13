# pongball
# Pong game created with python with a twist of football! Have uploaded the code here you can add sfx.

#Code
import turtle 
import os
#Window
wn = turtle.Screen()
wn.title("Pong Ball")
wn.bgcolor("Green")
wn.setup(width=800, height=600)
wn.tracer(0)




# Score
score_a = 0
score_b = 0

#Paddle A
paddle_a = turtle.Turtle()
paddle_a.speed(5)
paddle_a.shape("square")
paddle_a.color("white")
paddle_a.shapesize(stretch_wid=5, stretch_len=1)
paddle_a.penup()
paddle_a.goto(-350, 0)

#Paddle B
paddle_b = turtle.Turtle()
paddle_b.speed(5)
paddle_b.shape("square")
paddle_b.color("white")
paddle_b.shapesize(stretch_wid=5, stretch_len=1)
paddle_b.penup()
paddle_b.goto(350, 0)

#Ball
ball = turtle.Turtle()
ball.speed(5)
ball.shape("circle")
ball.color("orange")
ball.penup()
ball.goto(0, 0)
ball.dx = 2
ball.dy = -2


#Pen
pen= turtle.Turtle()
pen.speed(0)
pen.color("White")
pen.penup()
pen.hideturtle()
pen.goto(0, 260)
pen.write("Barcelona:0 RealMadrid:0", align="center", font=("Courier", 24,"normal"))





#Function
def paddle_a_up():
    y = paddle_a.ycor()
    
    y += 20
    if y<300:
        paddle_a.sety(y)

def paddle_a_down():
    y = paddle_a.ycor()
    y -= 20
    if y>-300:
        paddle_a.sety(y)

def paddle_b_up():
    y = paddle_b.ycor()
    y += 20
    if y<300:
        paddle_b.sety(y)

def paddle_b_down():
    y = paddle_b.ycor()
    y -= 20
    if y>-300:
        paddle_b.sety(y)

wn.listen()
wn.onkeypress(paddle_a_up, "w")
wn.onkeypress(paddle_a_down, "s")
wn.onkeypress(paddle_b_up, "Up")
wn.onkeypress(paddle_b_down, "Down")

#Line In Centre 
T=turtle.Turtle()
T.speed(0)
T.up()
T.setposition(0, -250)
T.down()
T.color ("white")
T.pensize(2)
T.left(90)
T.forward(500)

#Circle
t = turtle.Turtle()
t.pensize(2)
t.color("white")
t.circle(50)



#Main Loop
while True:
    wn.update()


    #Move The Ball

    ball.setx(ball.xcor() + ball.dx)

    ball.sety(ball.ycor() + ball.dy)

    #Border
    if ball.ycor() > 290:
        ball.sety(290)
        ball.dy *= -1
        os.system("afplay bounce.wav")


    if ball.ycor() < -290:
        ball.sety(-290)
        ball.dy *= -1

    if ball.xcor() > 390:
        ball.goto(0,0)
        ball.dx *= -1
        score_a +=1
        pen.clear()
        pen.write("Barcelona: {} Real Madrid: {}".format(score_a, score_b), align="center", font=("Courier", 24,"normal"))
    


    if ball.xcor() < -390:
        ball.goto(0,0)
        ball.dx *= -1
        score_b +=1
        pen.clear()
        pen.write("Barcelona: {} Real Madrid: {}".format(score_a, score_b), align="center", font=("Courier", 24,"normal"))

    # Paddle And Ball Collison
    if (ball.xcor() > 340 and ball.xcor() < 350) and (ball.ycor() < paddle_b.ycor() + 40 and ball.ycor() > paddle_b.ycor() -50):
        ball.setx(340)
        ball.dx *= -1
    if (ball.xcor() < -340 and ball.xcor() > -350) and (ball.ycor() < paddle_a.ycor() + 40 and ball.ycor() > paddle_a.ycor() -50):
        ball.setx(-340)
        ball.dx *= -1


















