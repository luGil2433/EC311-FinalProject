# Pong 2.0 Bounce Beyond

Contributors: Lucia Gil, Noel Madyag, Phyo Kyaw

Inspired by https://github.com/chmo2019/EC311_Final_Project

Video Demonstration

If you'd like to check out our game, here's the link: 

Project Overview

Our final project for EC311 at Boston University is a version of the classic Atari game, Pong. Our version has three different ways of playing: Sigle player, Multi player and, Impossible. The single player consits of the paddle in the bottom and the ball bouncing around. The paddle works by pressing the "A" and "D" keys on the keyboard.To increase difficulty we added speed with each collision, and to add our own spin on the classic several decoy balls as the game progresses. The objective of the game is to catch the ball with the paddle before it hits the bottom of the scree. The second mode is multiplayer wich consist of two paddles, one on the top and one on the bottom. The top paddle works with the keys "L" and "J" and the bottom with the keys "A" and "D". The goal of the game is to maintain the ball between the two paddles for the longest time possible. The last mode is the impossible, and as the name says it is impossible. The mode contains the regular bottom paddle and the square, but it also has a square in the middle of the screen. If the ball touches the square the game will be over. The impossible contols are the same as the single player mode.

# How run our project

Download the zip file and modify the constraints as needed (the constraints used as for the Nexys-A7 100T FPGA board). Open the '.xpr' file with Vivado 2020.1. Then, either run the synthesis, implementation, then bitstream or program the device. Turn the FPGA on and connect the VGA and you will see the main menu screen. To begin playing press the center button (or button corresponding to your constraints file) in order to prompt the game to run. As the game is running, use two buttons (again, left or right button or corresponding buttons in your constraints file) on the FPGA board to move the paddle left and right and catch the ball. The longer you play the more challenging it gets. As you play your score will be available on the 7-segment display. Once you lose the screen will say GAME OVER, and then press the start button again to return to the home screen that says PONG 

# Code Overview



We Organized all our code into a top module call 'system_Top.v'. The top module manages the game modes (using a case block) and takes user input as well as feeding visual output to the user. The visual handling tasks are done by 'bg_gen.v', partially by the 'game.v', 'menu_screen.v', as well as 'score_to_7seg.v'. While the first three of those modules have VGA components, the 'score_to_7seg.v' module and 'clock_divider.v' module are responsible for converting raw numbers at appropriate timings into appropriate digits to be displayed on the 7-segment display in decimal format. Within that module, the 'dec_bcd' and 'num_hex.v' modules decode counters, fed by 'game.v', into readable, 7-segment digits on the FPGA. For the VGA displaying modules, the 'vga640x480' acts as the primary driver to create appropriate synchronization signals to animate moving pixels properly. These synchronization signal are then fed into the different game objects ('square.v', 'start_square.v', 'paddle.v') as well as the memory reading modules ('sram.v') in order to generate displayable pixels on the VGA display.The modes are saved in files named 'pong.v 'for the single player, 'pong_multi.v'for the multi player, and 'pong_impossible.v' for the impossible.
