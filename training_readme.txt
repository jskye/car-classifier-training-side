================
Training Params
================
positives = 1200
negatives = 4000
samples 


coderobin used 40 negs, 600 negs to produce 1500 samples through transformations.
http://coding-robin.de/2013/07/22/train-your-own-opencv-haar-classifier.html
This is generally cited as a good tutorial.
40x600 = 1500x
x = 16

1200 x 4000 = 16x
x = 300,000
So technically we could generate this amount of samples if we needed more and still be ok
(according to code robin).
But we already have enough. We try 4 times our positive samples = 4800 samples.


without applying distortions
opencv_createsamples -info positives.txt negatives.txt -vec samples.vec -w 24 -h 24

================
createsamples
================


perl src/createsamples.pl positives.txt negatives.txt samples 4800\
  "opencv_createsamples -bgcolor 0 -bgthresh 0 -maxxangle 0.01\
  -maxyangle 0.03 -maxzangle 0.03 -maxidev 40 -w 24 -h 24"

================
check samples
================

opencv_createsamples -vec samples/samples.vec -w 24 -h 24