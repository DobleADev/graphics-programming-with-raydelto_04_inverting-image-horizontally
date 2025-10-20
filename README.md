# graphics-programming-with-raydelto_04_inverting-image-horizontally

**DISCLAIMER** Gemini 2.5 Flash was used for the sake of the assignment completion and insight learning.

## Intro

**Goal:** Implement a FlipHorizontally method to this bmp_reader program

So in the starting logic, the program process the image readed, applying a grayscale filter, and flipping it vertically.
So instead of flipping it vertically, we want the image horizontally flipped.

## Development

I begin my journey compiling the starting code, I couldn't! 💀 Because of my incorrectly setted Msys64 libraries, cstdio wasn't recognize. But talking with the AI assistant I got the commands needed to get the job done, so now we compile it successfully. 😅

main.cpp was built on the bin folder and from there can't read the image properly, so I moved it to the root project location. And there I saw the test2.bmp with the starting changes, grayscaled and vertically flipped. 🧐

In this phase, I head to the code script and begin the analysis... 😲🤯 I Couldn't understand a bit of all that stuff. I toyed a bit with the code logic, for example I assumed the std::swap() accepted a (x, y) arguments so I inverted them, watching in the build that the final image isn' even flipped vertically 😬, so then I knew I can't get this done in few minutes without help, here comes Gemini AI. 😉

I asked it for a deep analysis and I understood the important part: for the flipping logic, we just need to operate on half of the image, as std::swap() inverts the pointers, we can give it as parameters the opposite pixels and the function do all the work, from the side to the center, so there's an optimization there, and the pixel channels have to be inverted as well as the pointer get swapped, its inner values get inverted too (BGR instead of RGB). 🙄

But, I was missing an important clue for this quest, the loop was operating on the rows only... And have 2 loops for the inversion could be the beginner approach, we can just do the work on a single array range like IMAGE[columns, -rows], but that's just a mere simplification, but its a good starting point though, so we would get a IMAGE[-columns, rows]. 🤓

With Gemini I got to have 3 versions of the function till the end of the assignment:

1. **3 Loop Logic Approach**: So I knew that I needed to operate on the image's array columns, so that I did, I got a first FOR Loop iterating the pixels vertically, then the WHILE loop operating for update the opposite pixel pointers, and the last FOR loop to invert the pixel channels, we reach the goal! but, could I improve this approach? 🤨

2. **Using std::reverse()**: This really looked like the possible winner, in one FOR loop did the inversion using the function std::reverse(), yeah but we forgot about inverting the pixel channels to normalize them... 😞 I was just trying things with Gemini, I didn't try to make it work with this approach, I wanted to get the logic alike to FlipVertically's logic as much as possible, I thought I could get it so, I tried to archive that, thanks to Gemini. 

3. **Final version**: So... this is really as the first approach, but different, the fields where more alike to the FlipVertically function, I think we really need to operate like this to get to the column pixels, so I let it as it is, but I make some changes and erase some extra variables that we really didn't need, and that's my best humbling attempt. 😌

I don't have the needed algorithm skills to get a better approach in this assignment, but we have it working bois. I'm out. 😋
