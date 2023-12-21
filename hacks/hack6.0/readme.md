#include <math.h>
#include <stdlib.h>

int rgbToCMYK(int r, int g, int b, double *c, double *m, double *y, double *k) {
    if (r < 0 || r > 255 || g < 0 || g > 255 || b < 0 || b > 255) 
        return 1; 