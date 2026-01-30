# image-to-ascii-
ASCII Art Generation in Python

This project explores two different techniques for generating ASCII art using Python.
The purpose was not only to produce visual output but also to understand image processing basics, loops, indexing, and conditional logic.

**Approach 1** — BMP Image to ASCII (Binary Image Processing)
Overview
In this approach, an actual BMP image file is read in binary mode, pixel data is extracted, converted to grayscale, and then mapped to ASCII characters based on brightness levels.
This method focuses on image processing fundamentals and data interpretation rather than manual drawing.
Step-by-Step Explanation
**1. Read BMP Image Data**
Open the BMP file in binary mode.
Extract key header values:
Width → Byte Offset 18
Height → Byte Offset 22
Pixel Data Offset → Byte Offset 10
BMP stores pixels in BGR format (Blue, Green, Red).
Each pixel = 3 bytes.
BMP rows are padded so every row size is a multiple of 4 bytes.

**2. Convert RGB to Grayscale**
Human vision perceives green as brighter than red or blue.
So instead of simple averaging, we use weighted conversion:
Gray = 0.299 * R + 0.587 * G + 0.114 * B
This produces more visually accurate brightness values.

**3. Resize the Image**
ASCII characters are taller than they are wide.
To maintain aspect ratio, the image is resized vertically (usually height ÷ 2).

**4. Map Brightness to ASCII Characters**
Each grayscale value (0–255) is mapped to a character set, for example:
" .:-=+*#%@"
Dark pixels → dense characters (@, #)
Bright pixels → light characters (., space)

**5. Print ASCII Line by Line**
Characters are printed row by row to recreate the image visually in text form.
**Pros**
Real image input
Teaches binary file handling
Introduces grayscale conversion
Praitical image-processing knowledge
**Cons**
More complex implementation
Requires understanding file headers
Slower compared to manual patterns

**Approach 2 — Manual Pattern Generation (Loops + If-Else)
Overview**
Instead of reading an image, ASCII patterns are generated manually using loops and conditional logic.
Each character is printed based on its position index.
Core Concept
Define a fixed column width.
Use a loop (while or for) from 0 → cols.
Use if-elif-else to determine which symbol prints at each index.
Repeat per line.
Example Logic Idea
if i < 20 → print(":")
elif i == 20 → print("=")
elif i < 30 → print("%")
else → print(":")
Each condition represents a character count segment.
**Pros**
Strengthens logical thinking
Full control over spacing & alignment
No external files required
Great for learning loops and conditions
**Cons**
Time-consuming for large patterns
Hard to maintain long designs
Requires precise counting

**Trade-off between automation vs logic building.**
