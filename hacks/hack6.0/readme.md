#include <math.h>
#include <stdlib.h>

int rgbToCMYK(int r, int g, int b, double *c, double *m, double *y, double *k) {
    if (r < 0 || r > 255 || g < 0 || g > 255 || b < 0 || b > 255) 
        return 1; 

        double r_prime = r / 255.0, g_prime = g / 255.0, b_prime = b / 255.0;
    *k = 1 - fmax(fmax(r_prime, g_prime), b_prime);

    if (*k == 1) {
        *c = *m = *y = 0;
    } else {
        *c = (1 - r_prime - *k) / (1 - *k);
        *m = (1 - g_prime - *k) / (1 - *k);
        *y = (1 - b_prime - *k) / (1 - *k);
    }
     return 0; // No error
}

int cmykToRGB(double c, double m, double y, double k, int *r, int *g, int *b) {
    if (c < 0 || c > 1 || m < 0 || m > 1 || y < 0 || y > 1 || k < 0 || k > 1) 
        return 1; 

    *r = round(255 * (1 - c) * (1 - k));
    *g = round(255 * (1 - m) * (1 - k));
    *b = round(255 * (1 - y) * (1 - k));

    return 0; 
}