# Closest-pair-algorithm-parallelization

Step 1- Sort the points on x-coordinate and on y-coordinate.

Step 2- Divide them into two halves
    2.1) Let the value of the median(when sorted on x-coordnates) be x_mid.
    2.2) Split x into x_left and x_right. Points in x_left have the value when x-coordinate <=x_mid and x_right contains the rest of the coordinates.
    2.3) Split y into y_left and y_right. Points in y_left have the value when y-coordinate <=x_mid and y_right contains the rest of the coordinates.
    2.4) Let min1 and min2 be the two pairs of the form (x1,y1) and (x2,y2) containing the closest pair of points.

Step 3- Recursive calls
    3.1) Let d1= distance of the closest pair on input (x_left,x_right) and d2=distance of the closest pair on input (y_left,y_right).
    3.2) Compute d=min(d1,d2) and similarly the closest pairs min1 and min2.
    3.3) Around x_mid we will consider a band of length d on both sides. Anything outside of the band will have a distance >d.

Step 4- Combine step
    4.1) From the vector sorted on the basics of y-coordinate extract all the points for which point.x > x_mid – d and put in a separate vector called band.
    4.2) Scan band from top to bottom, comparing each point against a finite number of points(7 points) and computing the distance between them. 
         And if we get a distance smaller than the current distance then update both the distance and the closest pairs. This step will take O(n) time.
