# pingpong-game-with-Python
Sets of programming code to create an interactive pingpong game with two sets of players (Player A &amp; Player B) 
See programming code below:

print("#Ping Pong Game Created By Bolo \n - This is a personal project \n - Let's Get Started!!! Yaay!")



import turtle
import winsound

wn = turtle.Screen()
wn.title("Ping Pong by Bolo")
wn.bgcolor("black")
wn.setup(width=800, height=600)
wn.tracer(0)

print("#Score")
score_a = 0
score_b = 0

print("Paddle A")
paddle_a = turtle.Turtle()
paddle_a.speed(0)
paddle_a.shape("square")
paddle_a.color("blue")
paddle_a.shapesize(stretch_wid=6, stretch_len=1)
paddle_a.penup()
paddle_a.goto(-350, 0)

print("Paddle B")
paddle_b = turtle.Turtle()
paddle_b.speed(0)
paddle_b.shape("square")
paddle_b.color("blue")
paddle_b.shapesize(stretch_wid=6, stretch_len=1)
paddle_b.penup()
paddle_b.goto(+350, 0)

print("Ball")
ball = turtle.Turtle()
ball.speed(0)
ball.shape("circle")
ball.color("red")
ball.penup()
ball.goto(0, 0)
ball.dx = 2
ball.dy = -2

print("#Pen")
pen = turtle.Turtle()
pen.speed(0)
pen.color("white")
pen.penup()
pen.hideturtle()
pen.goto(0, 260)
pen.write("Player A: 0 Player B: 0", align="center", font=("Comic sans",20, "normal"))

print("# Function")
def paddle_a_up():
    y = paddle_a.ycor()
    y += 20
    paddle_a.sety(y)

def paddle_a_down():
    y = paddle_a.ycor()
    y -= 20
    paddle_a.sety(y)

def paddle_b_up():
    y = paddle_b.ycor()
    y += 20
    paddle_b.sety(y)

def paddle_b_down():
    y = paddle_b.ycor()
    y -= 20
    paddle_b.sety(y)

print("Keyboard binding")
wn.listen()
wn.onkeypress(paddle_a_up, "w")
wn.onkeypress(paddle_a_down, "s")
wn.onkeypress(paddle_b_up, "Up")
wn.onkeypress(paddle_b_down, "Down")

print("#Main game loop")
print("#Setting borders")
while True:
    wn.update()

    ball.setx(ball.xcor() + ball.dx/10)
    ball.sety(ball.ycor() + ball.dy/10)


    if ball.ycor() > 290:
        ball.sety(290)
        ball.dy *= -1
        winsound.PlaySound(r"C:\Users\HP\Desktop\BOLO\Bolo_Files\Bolo Analytics\Python\bounce.wav", winsound.SND_ASYNC)

    elif ball.ycor() < -290:
        ball.sety(-290)
        ball.dy *= -1
        winsound.PlaySound(r"C:\Users\HP\Desktop\BOLO\Bolo_Files\Bolo Analytics\Python\bounce.wav", winsound.SND_ASYNC)

    if ball.xcor() > 390:
        ball.goto(0, 0)
        ball.dx *= -1
        score_a += 1
        pen.clear()
        pen.write("Player A: {} Player B: {}".format(score_a, score_b), align="center", font=("Comic sans", 20, "normal"))

    elif ball.xcor() < -390:
        ball.goto(0, 0)
        ball.dx *= -1
        score_b += 1
        pen.clear()
        pen.write("Player A: {} Player B: {}".format(score_a, score_b), align="center", font=("Comic sans", 20, "normal"))

    if ball.xcor() > 340 and ball.xcor() < 350 and ball.ycor() < paddle_b.ycor() + 40 and ball.ycor() > paddle_b.ycor() -50:
        ball.setx(340)
        ball.dx *= -1
        winsound.PlaySound(r"C:\Users\HP\Desktop\BOLO\Bolo_Files\Bolo Analytics\Python\bounce.wav", winsound.SND_ASYNC)

    if ball.xcor() < -340 and ball.xcor() > -350 and ball.ycor() < paddle_a.ycor() + 40 and ball.ycor() > paddle_b.ycor() -50:
        ball.setx(-340)
        ball.dx *= -1
        winsound.PlaySound(r"C:\Users\HP\Desktop\BOLO\Bolo_Files\Bolo Analytics\Python\bounce.wav", winsound.SND_ASYNC)
