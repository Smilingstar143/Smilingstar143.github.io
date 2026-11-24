#include <graphics.h>
#include <stdio.h>
#include <conio.h>
#include <math.h>
#include <iostream.h>

void bresenham(int x1, int y1, int x2, int y2)
{
    int dx, dy, sx, sy, x, y, p;

    dx = abs(x2 - x1);
    dy = abs(y2 - y1);

    sx = (x2 > x1) ? 1 : -1;
    sy = (y2 > y1) ? 1 : -1;

    x = x1;
    y = y1;

    if (dx > dy)
    {
        p = 2 * dy - dx;
        for (int i = 0; i <= dx; i++)
        {
            putpixel(x, y, WHITE);
            x += sx;
            if (p >= 0)
            {
                y += sy;
                p -= 2 * dx;
            }
            p += 2 * dy;
        }
    }
    else
    {
        p = 2 * dx - dy;
        for (int i = 0; i <= dy; i++)
        {
            putpixel(x, y, WHITE);
            y += sy;
            if (p >= 0)
            {
                x += sx;
                p -= 2 * dy;
            }
            p += 2 * dx;
        }
    }
}

void main()
{
    int gd = DETECT, gm;
    int x1, y1, x2, y2;

    cout<<"Enter starting point (x1 y1)";
    cin>>x1>>y1;
    cout<<"Enter ending point (x2 y2)";
    cin>>x2>>y2;

    initgraph(&gd, &gm, "C:\\Turboc3\\BGI");   

    bresenham(x1, y1, x2, y2);

    getch();
    closegraph();
}