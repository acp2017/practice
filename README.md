<!--
Author  : Henry Naoto Ishiyama
Date    : 2019/04/07
Version : 1.0.0
Description :
This program was developed as a part of the assignment project on
"THE ODIN PROJECT".
Project :
ROCK PAPER SCISSORS
Project URL :
https://www.theodinproject.com/courses/web-development-101/lessons/rock-paper-scissors
https://github.com/TheOdinProject/curriculum/blob/master/web_development_101/javascript_basics/project_rock_paper_scissors.md
-->

<!DOCTYPE html>
<html>
    <head>
        <title>THE ODIN PROJECT - Rock Paper Scissors</title>
    </head>
    <body>
        <script>
            "use strict";
            const MAX_PLAY_ROUND = 5;
            const ROCK      = 0;
            const PAPER     = 1;
            const SCISSORS  = 2;
            const SELECTION = ["ROCK", "PAPER", "SCISSORS"];
            const DRAW        = 0;
            const PC_WIN      = 1;
            const HUMAN_WIN   = 2;
            const SCORE_TABLE = [
                                    [DRAW,      PC_WIN,    HUMAN_WIN], // DRAW, PC,   HU
                                    [HUMAN_WIN, DRAW,      PC_WIN],    // HU,   DRAW, PC
                                    [PC_WIN,    HUMAN_WIN, DRAW]       // PC,   HU,   DRAW
                                ];
            function computerPlay()
            {
                let computerSelection = Math.round((Math.random() * 2));
                return computerSelection;
            }
            function humanPlay()
            {
                let humanSelectionStr = prompt("your selection: (ROCK, PAPER, SCISSORS)");
                let humanSelection = SELECTION.indexOf(humanSelectionStr.toUpperCase());
                return humanSelection;
            }
            function playRound(humanSelection, computerSelection)
            {
                const result = SCORE_TABLE[humanSelection][computerSelection];
                return result;
            }
            function game()
            {
                let humanScore = 0;
                let computerScore = 0;
                for (let i = 0; i < MAX_PLAY_ROUND; i++)
                {
                    let humanSelection    = humanPlay();
                    let computerSelection = computerPlay();
                    let result = playRound(humanSelection, computerSelection);
                    switch (result)
                    {
                        case DRAW:
                            console.log("DRAW");
                        break;
                        case PC_WIN:
                            console.log("PC WINS");
                            computerScore++;
                        break;
                        case HUMAN_WIN:
                            console.log("HUMAN WINS");
                            humanScore++;
                        break;
                        default:
                        break;
                    }
                }
                if (humanScore > computerScore)
                {
                    console.log(`HUMAN WINS (${humanScore} Vs ${computerScore})`);
                }
                else if (humanScore < computerScore)
                {
                    console.log(`PC WINS (${computerScore} Vs ${humanScore})`);
                }
                else
                {
                    console.log(`DRAW (${humanScore} Vs ${computerScore})`);
                }
            }
            game();
        </script>
    </body>
</html>
