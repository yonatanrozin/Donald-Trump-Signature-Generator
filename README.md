# Donald Trump Signature Generator

A Python program written in Jupyter Notebook that produces randomly-generated asemic writing modeled after Donald Trump's official presidential signature. Access the Jupyter Notebook [here](https://colab.research.google.com/drive/11KM2JbkzJXKvv3h4X4BxGzJyqZeg3zX6). Go to Runtime->Run all to run all the cells and scroll through the notebook to see the various iterations.

## DJTSig Introduction

DJTSig Generator was created for the midterm of [Allison Parrish](https://www.decontextualize.com/)'s  Materiality of Language course, for which Jupyter Notebook had to be used to create samples of asemic writing.

As the title might suggest, this project is modeled heavily after Donald Trump's official presidential signature, which looks unlike any other signature I've ever seen:

![Donald Trump's official presidential signature, preceeded by the word "Sincerely," and proceeded by the name "Donald J. Trump" in print](https://github.com/yonatanrozin/Donald-Trump-Signature-Generator/blob/main/Images/DJTSig_official.jpeg)

This signature is the perfect inspiration for asemic compositions as it can be reduced down to a series of patterns:
- The entire signature is a zigzag line, where each "peak" is a letter
- Lowercase letters are all uniformly short in height
- Taller/uppercase letters consist of a sharp stroke up and a second stroke down at a random angle, not necessarily resembling the required letter

My goal was to emulate these patterns as accurately as possible, and perhaps extrapolate on them a bit.

The Jupyter Notebook consists of a series of functions that randomly generate zigzag lines. As the functions are expanded and modified, the resulting lines gradually begin to resemble the original signature. The notebook uses the Python Flat library, which allows for graphics to be generated and embedded in the Jupyter Notebook. Additionally, the notebook uses Allison Parrish's Bezmerizing library's polyLine object, which receives a list of coordinate pairs and returns a series of connected lines.

#### makeZigZag1

The first function receives 3 integer arguments, corresponding to the length and height of the total shape in mm and the number of line segments it will contain. The function predictably creates the desired number of line segments in the desired zigzag pattern to fill up the specified space.

#### makeZigZag2

The second function introduces variable, randomly chosen letter heights.

#### makeZigZag3

The third function randomly chooses from a list of 3 possible letter heights (low, medium, tall), with probabilities taken from the model signature (15/20 low, 2/20 medium, 3/20 high).

#### makeZigZag4

The fourth function turns the polyline object into a series of smooth Bezier curves, which much more closely resemble human handwriting. The sharp edges of the letters are also rounded out. Additionally, the function introduces a slight variation in the y-position of the line segments, so they don't start and end at exactly the same height every time.

#### makeZigZag5

By offsetting the x-position of the "valleys" (the space in between the "letter" strokes) slightly, the fifth function creates an Italics effect.

## makeDJTSig

This function is the official DJT signature generator function. It ensures that the first letter is always tall. Additionally, for tall letters, it splits up each line segment (of which there are usually 2 per letter) into 2 randomly-placed smaller segments, creating some more significant variation in the taller letters.

With these modifications in place, the DJTSig generator comes extremely close to the original signature. Here it is again, for reference, next to one particularly successful re-creation:

![Donald Trump's official presidential signature, preceeded by the word "Sincerely," and proceeded by the name "Donald J. Trump" in print](https://github.com/yonatanrozin/Donald-Trump-Signature-Generator/blob/main/Images/DJTSig_official.jpeg)

![A randomly-generated asemic line, made to resemble Donald Trump's official signature](https://github.com/yonatanrozin/Donald-Trump-Signature-Generator/blob/main/Images/DJTSig_close.jpeg)

## extraSig

To extrapolate on these random-yet-predicable patterns seen in DJT's signature, the extraSig function introduces a variable called attOffset, or "attribute offset". All integer variables are incremented by ±attOffset. The one exception to this is the starting and ending y-position of each letter, to maintain any semblance of order.

Setting attOffset to 0 will result in the normal signature generator, while setting it to progressively larger numbers will begin to gradually distort the resulting signature. For comparison, the notebook shows the distorted and original versions side-by-side.

Setting attOffset to a value of 3 has been found to create a randomly-generated signature that more closely resembles Donald Trump's pre-office signature from 2015. For reference, here's a side-by-side comparison of his signature before and after taking office:

![A side-by-side comparison of 2 of Donald Trump's signatures. The first, on the left, is more distorted than his current version, and the words "Donald Trump, September 2015" are printed underneath. The second, on the right, resembles his official signature, and the words "Donald Trump signs Keystone Pipeline executive order January 2017" are written underneath.](https://github.com/yonatanrozin/Donald-Trump-Signature-Generator/blob/main/Images/DJTSig_Chronology.jpeg)

And finally, here's the before/after style replicated in the generator:

![Another side-by-side comparison of 2 procedurally-generated signatures. The one on the left is more distorted than the one on the right, similar to the signatures in the previous photo.](https://github.com/yonatanrozin/Donald-Trump-Signature-Generator/blob/main/Images/DJTSig_extrasig.jpeg)
