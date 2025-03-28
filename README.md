# Sports Team Generator
This code is designed to create teams and distribute players fairly for your recreational sports activities. By default, it is used for Football (soccer) but it can be used for other sports too. For the ease of implementation it is better to use a google form to get the player ratings from participants. In this code we have the following considerations:

- Players will be rated from best to worst (a sample is available below)
- Average position of each player will be calculated and they will be assigned into skill buckets from 1 to 5 stars. I tried to distributee players fairly and randomly based on their skill bucket. As an example, a 5 star player, is a top player that should not end up in the same team as another 5 star player if possible.
- Goalkeepers are considered, so they do not end up in the same team if possible.
- Absent players are considered.
- You can add guest players to the teams

## How it works
### Create a google form to get the input
create a google form that takes the order of players (see "example-team-ratings.pdf"). You can share this form with your players to get their vote. As an example, if there are 15 players, the output of your form could look like below
```
[
    ["Timestamp", "1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11", "12", "13", "14", "15"],
    ["2025/03/01 1:20:08 PM EST", "Ronaldo", "Ibrahimovic", "Messi", "Iniesta", "Xavi", "Modric", "Marcelo", "Buffon", "Kroos",
     "Casillas", "Carvajal", "Fabregas", "Valdes", "Roberto", "Rudiger"],
    ["2025/03/01 1:22:32 PM EST", "Messi", "Xavi", "Ronaldo", "Iniesta", "Ibrahimovic", "Modric", "Kroos", "Marcelo", "Carvajal",
     "Buffon", "Fabregas", "Casillas", "Rudiger", "Valdes", "Roberto"],
    ["2025/03/01 1:25:45 PM EST", "Xavi", "Messi", "Ronaldo", "Ibrahimovic", "Iniesta", "Modric", "Carvajal", "Kroos", "Marcelo",
     "Fabregas", "Casillas", "Buffon", "Valdes", "Rudiger", "Roberto"]
]
```

### Link your responses to a google sheet
By navigating to responses tab on your google form, you can click on link to sheets which will allow you to create a new google sheet which will always get synced to the updated responses of your form. This way, you can dynamically import the latest results into your code everytime you run it.

### Run the code with google colab
We will utilize google's Colaboratory to run the code. You will need to follow these steps:
 - Copy "team_generator.ipynb" file into your google drive, open it, and run the blocks in order
 - You will be asked to connect your code to your google drive and for a shareable link of your response sheet. The output will be saved on your colab environment as "google_form_team_ratings.csv"
 - You will be asked to enter the name of absent players, comma separated, and without space (you can press enter and skip if no one is missing).
 - You will be asked to enter the number of teams you want to create.
 - You will be asked to enter the name of your goalkeepers for an equal distribution between teams (you can press enter and skip if you have no goalkeepers)
 - You will be asked to enter the number of guest players you want to add to the teams (you can enter 0 and skip if you have no guest players)
 - Finally, your teams will be generated. You can also check your top players in the end based on the responses


#### Code output example
```
Enter absent players separated by commas: Carvajal
Enter the number of teams: 3
Enter goalkeepers separated by commas (up to the number of teams): Valdes,Casillas,Buffon
Enter the number of guest players: 1
Team 1: Ronaldo, Modric, Casillas, Roberto, Marcelo
Team 2: Iniesta, Buffon, Messi, Fabregas, Kroos
Team 3: Xavi, Valdes, Rudiger, Ibrahimovic, Guest Player 1
Enter the number of top players to display: 5

Top Players:
1. Ronaldo: 5
2. Messi: 5
3. Ibrahimovic: 5
4. Xavi: 4
5. Iniesta: 4
```
