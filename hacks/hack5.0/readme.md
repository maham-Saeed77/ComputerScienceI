#include <stdio.h>
#include <math.h>

double degreesToRadians(double degrees);

double airDistance(double lat_ori, double lat_des, double lon_ori, double lon_des);

double degreesToRadians(double degrees){
    const double pi = 3.141;
    const double earthRadius = 6371.0;
    return (degrees *pi) / 180.0;
}
 double airDistance(double lat_ori, double lat_des, double lon_ori, double lon_des){
    const double pi = 3.14;
    const double earthRadius = 6371.0;

    double a = degreesToRadians(lat_ori);
    double b = degreesToRadians(lat_des);
    double c = degreesToRadians(lon_ori);
    double d = degreesToRadians(lon_des);
 
 double distance = acos(sin(a) * sin(b) + cos(a) * cos(b) * cos(d - c)) * earthRadius;

    return distance;
}

int main() {

    double distance = airDistance(40.7128, 34.0522, -74.0060, -118.2437);
    printf("Air distance: %f km\n", distance);

    return 0;
}