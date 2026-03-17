Title: Winter Computer Science Final Project: XAGUSD Asia ORB trading bot

Goal: 

The goal of this code was to be able to build a fully functioning trading bot that can execute trades following a simple strategy and proper risk managment.
The bot is going to have to be able to identify a specific set of parameters within the market and make the proper decision based on rules 
that we give to the bot. The bot will also have to properly manage risk based on percentages and be able to calculate risk properly. 
With this bot I will be able to remove emotion and inconsistency from my trading. 

Challenges: 

I started by writing the framework of the strategy and the risk management which went pretty smoothly, especially risk management and executing trades
were some simple loops and essentially true or false statements. However, when actually getting to part where I had to test my code and see if the bot
would actually execute trades given market data, this is where I started to struggle. At first I was trying to figure out an interface that would 
allow me to still write in C++ because that's kind of the whole point of the project. However, I had really no idea how to do so. I found a trading
software called Jforex4 that allows for progammable strategies to be tested over the course of any time frame under any parameters. The only issue 
with this software is that the backtesting bot only accepts Java source code. I ran into a wall here because I am not familiar with Java syntax, however, 
with the help of Claude AI I was able to fully convert my original file from C++ into a Java alternative. The issues were not finished here though, 
After plugging in my Java source when trying to backtest the bot, not a single trade executed. This is because the opening range did not get defined properly. 
For example, the variable bool bullrange was set equal to the current candle close (bar.getclose). As price moved around the midpoint of the range it was causing 
the boolean varibale to flip between true and false on every bar. This meant that the strategy would not execute, because instead of buying the pullback how it was intended, 
it would flip and start looking for a sell. That sell signal wouldn't get triggered either because the selling range was on the other side. The solution to this problem
was to fix the definition of the range by determining the direction based off of how the opening range closed relative to the previous close. Once the range locked, 
the variable bullrange would stay completely fixed for the rest of the session. After this was fixed the bot was properly executing trades with proper risk calculations.

Plans for future implementation:

This bot is definitely a first iteration because it was as unprofitable as can be. When backtested over the course of the previous year the bot lost essentially
all of the capital it had access to. It's suffice to say that the actual trading strategy has a lot of room for improvement because consistently losing capital is not
a viable means of trading the markets. As it stands I would be better off executing trades manually. However, a bright spot to look at is that I was able to get the code 
fully functioning, and the bot was executing trades and properly calculating risk which is the most important thing. This project actually makes me very excited for my future,
this is because now that I have the framework for the code I can start making the strategy more sophisticated for the bot to execute trades. 
