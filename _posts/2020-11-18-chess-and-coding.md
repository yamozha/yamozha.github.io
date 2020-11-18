---
layout: post
title:  "Chess and Coding"
date:   2020-11-18
excerpt: "All things computer chess, chess replays/logging, mathematical concepts and more."
feature: https://yamozha.xyz/assets/img/posts/chess_coding.png
tag:
- coding
- chess
- AI
- Neural-Networks
- blog

comments: true
---
## Introduction  
Chess is an amazingly addictive and fun game, and I have been playing it nonstop for around 2 months now. I got the amazing idea to think about chess mathematically, so I decided to do a little bit of research to find out what people have already thought about.  

`SPOILER ALERT` the first part is really technical and boring, so if you're a guy who likes instant gratification and more simple applications of knowledge, skip to [this part](#human-analysis-and-logging-pgns).

## What is chess?  

Chess is a two-player strategy board game played on a checkered board with 64 squares arranged in an 8×8 square grid. It's basically as old as time itself[^1] and is and has been played around 10 million million times[^2] already.  
The game is commonly associated with intelligence and critical thinking.

## Rules
By convention, chess game pieces are divided into white and black sets. Each set consists of 16 pieces: one king, one queen, two rooks, two bishops, two knights, and eight pawns. The pieces are set out as shown in the diagram and photo. The players of the sets are referred to as White and Black, respectively.

The game is played on a square board of eight rows (called ranks, denoted 1 to 8 from bottom to top according to White's perspective) and eight columns (called files, denoted a to h from left to right according to White's perspective). The 64 squares alternate in color and are referred to as light and dark squares. The chessboard is placed with a light square at the right-hand corner nearest to each player. Thus, each queen starts on a square of its own color (the white queen on a light square; the black queen on a dark square).

![Initial Position](https://cdn1.ichess.net/wp-content/uploads/2017/02/Chess-Opening-Strategy-Center.jpg)

Moving is compulsory; it is illegal to skip a turn, even when having to move is detrimental. A player may not make any move that would put or leave the player's own king in check. If the player to move has no legal move, the game is over; the result is either checkmate (a loss for the player with no legal move) if the king is in check, or stalemate (a draw) if the king is not.

[Read More](https://en.wikipedia.org/wiki/Chess#Setup)

## Mathematical Simplicity
The game structure and nature of chess are related to several branches of mathematics. Many combinatorical and topological problems connected to chess have been known for hundreds of years.
The number of legal positions in chess is estimated to be about 10<sup>43</sup>, and has been proved to be fewer than 10<sup>47</sup>, with a game-tree complexity of approximately 10123. The game-tree complexity of chess was first calculated by Claude Shannon as 10<sup>120</sup>, a number known as the Shannon number. An average position typically has thirty to forty possible moves, but there may be as few as zero (in the case of checkmate or stalemate) or (in a constructed position) as many as 218.

Mathematical analysis of chess has been a thing for a while and a lot of people studied chess with a mathematical purpose. For example we have the `Knight's tour`, studied by mathematicians Euler, Legendre, de Moivre, and Vandermonde to name a few.  

A `knight's tour` is a sequence of moves of a knight on a chessboard such that the knight visits every square exactly once. If the knight ends on a square that is one knight's move from the beginning square (so that it could tour the board again immediately, following the same path), the tour is closed; otherwise, it is open.  

![Knight's Tour](https://new.uschess.org/sites/default/files/wp-thumbnails/Math1.jpg)  

On an 8 × 8 board, there are exactly 26,534,728,821,064 directed closed tours (i.e. two tours along the same path that travel in opposite directions are counted separately, as are rotations and reflections).

And right here we're going to the next point which is

## Neural Networks and Chess

The knight's tour problem also lends itself to being solved by a neural network implementation. The network is set up such that every legal knight's move is represented by a neuron, and each neuron is initialized randomly to be either "active" or "inactive" (output of 1 or 0), with 1 implying that the neuron is part of the solution. Each neuron also has a state function (described below) which is initialized to 0.

When the network is allowed to run, each neuron can change its state and output based on the states and outputs of its neighbors (those exactly one knight's move away) according to the following transition rules:

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/09152a84b0cb9db0b0ca5870ef379e1dc5d765d0)  

Neural Networks that play chess have also been made, as you have a big number of past games that they can analyze and make accurate predictions and mind-boggling plays based on them.

But before neural networks were even thought of, people used pure brute-force methods to make chess-playing bots - generating every possible move and deciding which one to take, based on checks, good trades or even checkmates.

The Association for Computing Machinery (ACM) held the first major chess tournament for computers, the North American Computer Chess Championship, in September 1970. CHESS 3.0, a chess program from Northwestern University, won the championship. Nowadays, chess programs compete in the World Computer Chess Championship, held annually since 1974.

## Human analysis and logging, PGNs
When I first started playing chess(online) I noticed that chess websites have a certain button - `Save as PGN`.  
At first I thought it was just a misspelled PNG, but it turned out to be a very different, amazing thing.

I'll give you the beginning of a PGN file, try to figure out how it's structured.

```
[Date "2020.11.15"]
[White "Player1"]
[Black "Player2"]
[Result "0-1"]
[EndTime "16:02:31 PST"]
[Termination "Player2 won by resignation"]

1. e4 e5 2. c4 Nf6 3. d3 c5 4. b4 d6 5. bxc5 dxc5 6. Nc3 Qa5 7. Qa4+ Nc6 8. Bd2
Qb6...
```

I think you are already starting to get why I find it as amazing as I say. In this example we have all sorts of information. You have first of all the date the game is played on, you have the usernames of both players, you have the end result, the time at which the game ended and how the player won/drew/lost.  

I like to think of that as a header in the PGN file. After that you have the body or the real interesting part.   
In that part we have a number - `1.`, and you have a set of letters and numbers - `e4 e5`, which translates into `The first move by white is pawn at e4, followed by black, playing pawn at e5`, which looks like this:  

![e4 e5](/assets/img/posts/e4e5.png)

So to translate the whole entire pgn body syntax to you, it goes like this:

- just the number and letter combination that describes space on the board means that a pawn has moved at it. - `e4 e5`

- uppercase letter, number and letter combination - other figure has moved - N being knight, B - bishop, Q - queen R- rook, K - king e.g `Nf6`, which looks like this:  

![Nf6](/assets/img/posts/nf6.png)

- captures are marked with x - `bxc5` (When a pawn makes a capture, the file from which the pawn departed is used to identify the pawn.)

![bxc5](/assets/img/posts/bxc5.png)

and more details [here](https://en.wikipedia.org/wiki/Algebraic_notation_(chess)#Notation_for_moves).

And this syntax is not only in the computer world and PGNs, people have used this way of typing in chess games ever since chess is made into the modern game we know today.  
For example, this is a game that Einstein and Oppenheimer played in 1933:

`1. e4 e5 2. Nf3 Nc6 3. Bb5 a6 4. Ba4 b5 5. Bb3 Nf6 6. O-O Nxe4 7. Re1 d5 8. a4 b4 9. d3 Nc5 10. Nxe5 Ne7 11. Qf3 f6 12. Qh5 g6 13. Nxg6 hxg6 14. Qxh8 Nxb3 15. cxb3 Qd6 16. Bh6 Kd7 17. Bxf8 Bb7 18. Qg7 Re8 19. Nd2 c5 20. Rad1 a5 21. Nc4 dxc4 22. dxc4 Qxd1 23. Rxd1 Kc8 24. Bxe7 1-0`

So of course you can make replays and studies of what is the most common moves in chess games, for example this graph of chess openings up until 2010

![Graph](https://i.insider.com/5385db3eecad04877313aa52?width=1100&format=jpeg&auto=webp)

I made a PGN to gif script a couple of weeks ago as seen here:

<script src="https://gist.github.com/yamozha/d1e7e89764fc2a556e450e1b59a4039f.js"></script>

and using it on the game between Einstein and Oppenheimer mentioned above, we get:

![GeniusGame](/assets/img/posts/einsteinoppenheimer.gif)


## Conclusion
The possibilities to use chess in your mathematical/coding projects are endless - from a protocol and server like [FICS](https://www.freechess.org/) all the way to a chess neural network like [AlphaZero](https://www.chess.com/blog/the_real_greco/understanding-alphazero-a-basic-chess-neural-network). Chess is a mathematical and logical masterpiece of a game, and playing it and thinking and developing your own concepts and theories is a surprisingly entertaining thing to do.
Thanks for reading!



[^1]: Predecessors - 280-550, Modern Game - 1200-1700, [Source](https://en.wikipedia.org/wiki/Chess#History)  
[^2]: [Source](https://www.sciencefocus.com/science/has-every-possible-chess-game-been-played/)
