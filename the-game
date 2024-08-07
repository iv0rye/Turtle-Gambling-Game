import turtle
import random
import time

balance = 1000.00
bets = []
# Set up the screen
print("===========================================================================")
print("""Hello! in this game you are required to gamble your way to $5000 dollars. 
The gameplay rules are:
- You start off with $1000, and are required to reach $5000. If your balance reaches $0 or dips lower than $0, you lose the game.
- You are able to put a certain amount of money on any turtle, sorted by color. 
  If a turtle you bet on wins, you earn back 5x what you put in. You get NOTHING if your turtle DOESN'T come first.""")
time.sleep(5)
def start_race():
    print("==========================")
    print("type 'yes' to begin!")
    open_screen = input()
    if open_screen.capitalize() != 'Yes':
        print("damn ok")
        exit()

    screen = turtle.Screen()
    screen.title("gambling")
    screen.bgcolor("white")
    screen.setup(width=800, height=600)
    # Create the turtle
    global bets
    global winnings
    global balance

    turtles = ['turtle1', 'turtle2', 'turtle3', 'turtle4', 'turtle5']
    colors = ['purple', 'blue', 'red', 'green', 'orange']
    bets = []
    betted_colors = []
    winnings = 0


    def default_turtle(turtle_name, color):
        turtle_name.shape("turtle")
        turtle_name.color(color)
        turtle_name.pensize(5)


    def spawn_location(turtle_name, x_spawn_position):
        turtle_name.hideturtle()
        turtle_name.penup()
        turtle_name.goto(x_spawn_position, -250)
        turtle_name.pendown()
        turtle_name.left(90)
        turtle_name.showturtle()


    # establish turtles spawning
    for x in range(len(turtles)):
        turtles[x] = turtle.Turtle()
        default_turtle(turtles[x], colors[x])
        spawn_location(turtles[x], -300 + (x * 150))

    finsh_line = turtle.Turtle(visible= False)
    finsh_line.penup()
    finsh_line.pensize(3)
    finsh_line.goto(-450, 250)
    for x in range(55):
        finsh_line.forward(10)
        finsh_line.penup()
        finsh_line.forward(10)
        finsh_line.pendown()

    print(f"you currently have ${balance}. How much are you willing to bet for: \n(note: 0 for none, only input numbers no dollar sign)")

    check = True
    while check:
        try:
            for i in range(5):
                capitalized_color = colors[i]
                bet = input(f"{capitalized_color.capitalize()}:")
                if int(bet) < 0:
                    print("you have bet negative money!! try again.")
                    bets.clear()
                else:
                    bets.append(int(bet))
            if sum(bets) > balance:
                print("you have bet more than you own!! try again.")
                bets.clear()
            else:
                check = False
        except ValueError:
            print("enter a number!")
            bets.clear()
    print(f"You have bet ${sum(bets):.2f}.")

    for i in range(len(bets)):
        if bets[i] > 0:
            betted_colors.append(colors[i])
        else:
            betted_colors.append(False)

    # countdown
    i = 3
    while i > 0:
        print(f'{i}...')
        i -= 1
        time.sleep(1)
    print("go!")


    # function to randomize turtles movement
    def move_turtle(turtle_name):
        choice = random.randint(1,5)
        if choice >= 2:
            turtle_name.forward(random.randint(1, 5))
        else:
            choice2 = random.randint(1,10)
            if choice2 >= 2:
                turtle_name.forward(random.randint(10, 15))
            else:
                turtle_name.forward(random.randint(40, 50))


    # turtle racing
    run = True
    while run:
        for t in turtles:
            move_turtle(t)
            if t.ycor() >= 250:
                run = False
                winner = t.color()
                # revealing winner
                print(f"the winner was the {winner[0]} turtle")
                time.sleep(1)
                win = False
                for i in range(len(betted_colors)):
                    if betted_colors[i] == winner[0]:
                        print(f"congratulations! you predicted that {winner[0]} would win the race, and they did!")
                        winnings = bets[i] * 5
                        print(f"for winning the race, you have won {winnings}")
                        win = True
                if win is False:
                    print(f"the {winner[0]} turtle won... better luck next time bud")

        screen.update()

    screen.clearscreen()
    return True


while start_race():
    time.sleep(1)
    balance = balance + winnings - sum(bets)
    print(f"your balance is now ${balance:.2f}")
    if balance > 5000:
        time.sleep(1)
        print("congratulations! you have earnt more than enough to win! good luck on your future gambling journey!")
        break
    if balance <= 0:
        print("unfortunately you have gone bankrupt and lost the game. try your hands on real gambling and see how that goes!")
        break
