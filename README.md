# EX 6 : Two-Dimensional Transformations

## AIM

To write a c program to implement 2D transformation of image.


## ALGORITHM

Step 1:Start the program.

Step 2:Draw the image with default parameters.

Step 3 : Get the choice from the user.

Step 4: Get the parameters for transformation.

Step 5 : Perform the transformation.

Step 6 : Draw the image.

Step 7 : Stop the program.


## Program :
~~~
#include<stdio.h>
#include<graphics.h> 
#include<process.h>
void main() 
{
int gd=DETECT, gm; 
float i,xmax,ymax,xmin,ymin,x11,y11,x22,y22,m; 
float a[4],b[4],c[4],x1,y1; 
clrscr(); 
initgraph(&gd,&gm,"c:\\turboc3\\bgi"); 
printf("\nEnter the bottom-left coordinate of viewport: "); 
scanf("%f %f",&xmin,&ymin); 
printf("\nEnter the top-right coordinate of viewport: "); 
scanf("%f %f",&xmax,&ymax); 
rectangle(xmin,ymin,xmax,ymax); 
printf("\nEnter the coordinates of 1st end point of line: "); 
scanf("%f %f",&x11,&y11); 
printf("\nEnter the coordinates of 2nd endpoint of line: "); 
scanf("%f %f",&x22,&y22); 
line(x11,y11,x22,y22); 
for(i=0;i<4;i++) 
{ 
a[i]=0; 
b[i]=0; 
} 
m=(y22-y11)/(x22-x11); 
if(x11<xmin) a[3]=1; 
if(x11>xmax) a[2]=1; 
if(y11<ymin) a[1]=1; 
if(y11>ymax) a[0]=1; 
if(x22<xmin) b[3]=1; 
if(x22>xmax) b[2]=1; 
if(y22<ymin) b[1]=1; 
if(y22>ymax) b[0]=1; 
printf("\nRegion code of 1st pt "); 
for(i=0;i<4;i++) 
{ 
printf("%f",a[i]); 
} 
printf("\nRegion code of 2nd pt "); 
for(i=0;i<4;i++) 
{ 
printf("%f",b[i]); 
} 
printf("\nAnding : "); 
 for(i=0;i<4;i++) 
{ 
c[i]=a[i]&&b[i]; 
} 
 for(i=0;i<4;i++) 
   printf("%f",c[i]); 
 getch(); 
  if((c[0]==0)&&(c[1]==0)&&(c[2]==0)&&(c[3]==0)) 
   { 
     if((a[0]==0)&&(a[1]==0)&&(a[2]==0)&&(a[3]==0)&& 
    (b[0]==0)&&(b[1]==0)&&(b[2]==0)&&(b[3]==0)) 
      { 
        clrscr(); 
        clearviewport(); 
        printf("\nThe line is totally visible\nand not a clipping candidate"); 
        rectangle(xmin,ymin,xmax,ymax); 
        line(x11,y11,x22,y22); 
        getch(); 
      } 
     else 
      { 
       clrscr(); 
        clearviewport(); 
        printf("\nLine is partially visible"); 
        rectangle(xmin,ymin,xmax,ymax); 
        line(x11,y11,x22,y22); 
        getch(); 
        if((a[0]==0)&&(a[1]==1)) 
        { 
    x1=x11+(ymin-y11)/m; 
    x11=x1; 
    y11=ymin; 
       } 
        else if((b[0]==0)&&(b[1]==1)) 
        { 
   x1=x22+(ymin-y22)/m; 
   x22=x1; 
   y22=ymin; 
        } 
        if((a[0]==1)&&(a[1]==0)) 
        { 
   x1=x11+(ymax-y11)/m; 
    x11=x1; y11=ymax; 
        } 
else if((b[0]==1)&&(b[1]==0)) 
        { 
   x1=x22+(ymax-y22)/m; 
   x22=x1; y22=ymax; 
       } 
        if((a[2]==0)&&(a[3]==1)) 
        { 
    y1=y11+m*(xmin-x11); 
    y11=y1; x11=xmin; 
        } 
        else if((b[2]==0)&&(b[3]==1)) 
        { 
      y1=y22+m*(xmin-x22); 
    y22=y1; 
    x22=xmin; 
        } 
        if((a[2]==1)&&(a[3]==0)) 
        { 
    y1=y11+m*(xmax-x11); 
    y11=y1; x11=xmax; 
        } 
        else if((b[2]==1)&&(b[3]==0)) 
        { 
   y1=y22+m*(xmax-x22); 
    y22=y1; 
    x22=xmax; 
        } 
       clrscr(); 
        clearviewport(); 
        printf("\nAfter clippling:"); 
        rectangle(xmin,ymin,xmax,ymax); 
        line(x11,y11,x22,y22); 
        getch(); 
      } 
   } 
  else 
  {  
clrscr(); 
     clearviewport(); 
     printf("\nLine is invisible"); 
     rectangle(xmin,ymin,xmax,ymax); 
    getch(); 
   } 
   closegraph(); 
   getch(); 
 }
~~~
## Output :
![Screenshot 2025-05-02 113228](https://github.com/user-attachments/assets/cef91f47-3957-49ea-82e4-113bab2fbc9e)
![Screenshot 2025-05-02 113305](https://github.com/user-attachments/assets/4be51baf-d8b8-4f2b-8e1e-6337478c117f)
![Screenshot 2025-05-02 113312](https://github.com/user-attachments/assets/a79354db-dc43-434b-8e57-8e45cdf4d581)

## Result :
Thus to write a c program to implement 2D transformation of image is implemented successfully.

