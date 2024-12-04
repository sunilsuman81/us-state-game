# us-state-game
Building a U.S. States Guessing Game in Python

Let’s walk through the code to build an interactive game that quizzes a user on naming U.S. states. This is a nice beginner Python project that combines data analysis using pandas, GUI programming, and game logic.

Project Overview
The game will:

Load a CSV dataset of U.S. states data
Extract state names and positions
Display blank US map image
Allow guessing state by clicking position
Track correct guesses in a list
Show state name on map when guessed
Allow guessing all states to win
Save unguessed states to new CSV

mporting Modules
We import Pandas for data work and Turtle for graphics:
        import turtle 
        import pandas

Loading State Data
We use Pandas to load the CSV of state data and extract the state names to a list:

        data = pandas.read_csv("50_states.csv")
        all_states = data.state.to_list()

Setting Up Screen
We configure the Turtle screen, set the US map image shape, and set a game title:

          screen = turtle.Screen()
          screen.title("U.S. States Game")  
          screen.addshape("blank_states_img.gif")
          turtle.shape("blank_states_img.gif")


State Guessing Loop
We use a loop to prompt for guessing states. Correct guesses get appended to guessed_states:

        guessed_states = []
        
        while len(guessed_states) < 50:
          answer_state = screen.textinput(prompt="Guess a state").title()
         
          if answer_state in all_states:  
            guessed_states.append(answer_state)
          
            # Get state coordinates to write name
            state_data = data[data.state == answer_state]   
            t.goto(state_data.x, state_data.y)
            t.write(answer_state)


Saving Unguessed States
If the user exits early, we can save the states they didn’t guess to a new CSV:

missing_states = [state for state in all_states if state not in guessed_states]
pandas.DataFrame(missing_states).to_csv("states_to_learn.csv")


This game is a great way to learn geography and Python fundamentals! Let me know if you need any part explained further.
