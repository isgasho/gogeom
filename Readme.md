<p align="center"><img src="https://github.com/MindorksOpenSource/gogeom/blob/master/example/gogeom.svg"></p>

# Gogeom - A Geometrical library for the Go programming language.
<!-- #### Refer [Wiki](https://github.com/MindorksOpenSource/gogeom/wiki/Circle) for detailed documentation -->
[![Mindorks](https://img.shields.io/badge/mindorks-opensource-blue.svg)](https://mindorks.com/open-source-projects) [![Mindorks Community](https://img.shields.io/badge/join-community-blue.svg)](https://mindorks.com/join-community) [![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

```
This is a Geometrical library for Go Language.
Which includes multiple Geometrical calculations like Circle, Lines etc in different forms.
```
## Installation

Installation is done using `go get`.
```
go get -u github.com/MindorksOpenSource/gogeom
```



#### These are following shape calculation which is supported by gogeom.
- [x]  **Circle**
- [x]  **Line**
- [x]  **Ellipse**
- [x]  **Parabola**
- [x]  **Triangle**
- [x]  **Quadrilaterals**
- [x]  **N-agons(polygons)**
- [ ] more to come..

# Circle
gogeom can handle two form of Circle.
- **Radius Form** 
  ``` 
  (x-a)^2 + (y-b)^2 = r^2 
  where,
  (a,b) is the center and "r" is the radius of the circle
  ``` 
- **General Form**
  ```
  x2 + y2 + Ax + By+ C = 0
  where,
  A,B and C are real numbers
  ```
#### Step to follow :


- import `shape "github.com/MindorksOpenSource/gogeom"`
- Initalize two circles as (in Radius Form),
```
import geometry "github.com/MindorksOpenSource/gogeom"

func main() {
    // (x-a)^2 + (y-b)^2 = r^2 and (x-c)^2 + (y-d)^2 = s^2  are circle equation
    // r, s are radius of two circles
r := shape.RadiusFormCircle{
        // a, b , r , c, d, s
        2, 3, 4, 5, 6, 7,
	}
}
```
-  Initalize two circles as (in General Form),
```
import `shape "github.com/MindorksOpenSource/gogeom"

func main() {
// x2 + y2 + Ax + By+ C = 0 and  x2 + y2 + Dx + Ey + F = 0 are circle equation
g := shape.GeneralFormOfCircle{
        // a, b , r , c, d, s
        2, 3, 4, 5, 6, 7,
	}
}

```
## Calculations for Circles
| Working                                   | Radius Form                               | General Form        |
| :-------------                         |:-------------                           | :-----            |
| **Distance** between two centers of circles| r.DistanceBetweenTwoCenters()    | g.DistanceBetweenTwoCenters()               |
| **Line  Equation** Connecting Two Centers| <small>r.LineEquationConnectingTwoCenters()</small>|   <small>g.LineEquationConnectingTwoCenters()</small>    |
| Check if both Circles **Intersect**| r.DoesCircleIntersect()||
| Check if both  Circles does not **Intersect**| r.AreTwoNonIntersectingCircle()||
|**Area** of Circle-1 and Circle-2 |r.AreaOfCircles()||
|**Circumference** of Circle-1 and Circle-2|r.CircumferenceOfCircles()||
|**∂** is the area of the triangle formed by the two circle centers and one of the intersection point. The sides of this triangle are S, r0 and R0 , the area is calculated by **Heron' s formula**.|r.CalculateDelta()||
|Calculates  **x1,y1,x2,y2**|r.CalculateXY()||
|Calculates **x1,y1**|r.CalculateAB()||
|Calculates  **x2,y2**|r.CalculateCD()||
|Calculates  **x1,x2**|r.CalculateXs()||
|Calculates  **y1,y2**|r.CalculateYs()||
|Calculates the **Line Equation** connecting both intersection points|<small>r.LineEquationConnectingTwoIntersectionPoint()</small>|<small>g.LineEquationConnectingTwoIntersectionPoint()</small>|
|Check if Both Circles Touch Each other as **tangent**|r.IsTangent()|g.IsTangent()|
|Check if two circles has **Outer Circle Tangency**|r.IsOuterCircleTangency()||
|Check if two circle has **Inner Circle Tangency**|r.IsInnerCircleTangency()||
|Tangential Points|r.TangentPoint()|g.TangentPoint()|
|Slope of Line of **Intersection Point**|<small>r.SlopeOfConnectingLineOfTwoIntersectionPoint()</small>|<small>g.SlopeOfConnectingLineOfTwoIntersectionPoint()</small>|
|Radius of Both Circls **R1,R2**||g.RadiusOfTwoCircle()|

# Line
gogeom can handle two form of Line.
- **General Form** 
  ``` 
  Ax+By+C =0
  where A, B and C are any real number and A and B are not both zero.``` 
- **Two Point Form**
  ```
  (x1,y1) and (x2,y2) form two lines passing through it
  ```

  #### Step to follow :


- import `shape "github.com/MindorksOpenSource/gogeom"`
- Initalize two lines as (in **General** Form),
```
// initialise one line 
l := shape.GeneralLine{
        // a, b, c
        2, 3, 4,
	}
}

---- or if you have to initialise multiple line ----
l := shape.GeneralLines{
        // a, b, c, d, e, f
        2, 3, 4, 5, 6, 7,
	}
}
---- or if you have two point line ----
l := shape.GeneralLines{
        // a, b, c, d, e, f
        2, 3, 4, 5, 
	}
}

```
- Initalize two lines as (in **Two Point Form Line** Form),

## Calculations for Line
| Working                                   | General Form (Single Line)  | General Form (Multiple Lines)                              | Two Point Form        |
| :-------------                         |:-------------                         | :-----              | :-----              |
|Slope of Line| l.SlopeOfLine()||l.SlopeOfLine()|
|Y-Intercept|l.YIntercept()|||
|X-Intercept|l.XIntercept()||
|Mid-Point of the line|||l.MidPoints()|
|Intersection of two lines **Ax + By + C = 0** and **Dx + Ey + F = 0**||l.IntersectionOfLines()||
|Point **(x, y)** which divides the line connecting two points **(x1 , y1)** and **(x2 , y2)** in the ratio **p:q**|||l.DividingPoints(p,q)|
|Point **(x, y)** which divides the line connecting two points **(x1 , y1)** and **(x2 , y2)** **externally** in the ratio **p:q**|||l.ExternalDividingPoints(p,q)|
|**Angle** Between Two Lines||l.AngleBetweenTwoLines()||
|**Line Eqn** passing two points|||l.LineThroughTwoPoint()|
|**EquiDistant Parallel Line**|l.EquiDistantParallelLine()|||
|Distance Between Two Points|||l.DistanceBetweenTwoPoints()|
|Distance Between Intercepts|||l.DistanceBetweenInterecepts()|
 
# Ellipse
Ellipse Equation,
```
x^2/a^2 + y^2/b^2 = 1,
(center at   x = 0   y = 0)
```       
 #### Step to follow :


- import `shape "github.com/MindorksOpenSource/gogeom"`
- Initalize ellipse,
```
e := shape.Ellipse {
        // a, b
        1,2
}
```
| Working                                   | General Form (Single Line) | Result
| :-------------                |:-------------    | :-----         
|Eccentricity of Ellipse|e.GetEccentricity()|float64|
|Shape Of Locus|e.GetShapeOfLocus()| Circle/Ellipse/Parabola/Hyerbola|
|Slope Of Tangent Line at **x1,y1**|e.GetSlopeOfTangentLine(x1,y1)| float64|
|Tangent Line Equation at **x1,y1**|e.GetTangentLineEquation(x1,y1)| string|
|Ramanujan Approx Circumference of ellipse|e.RamanujanApproxCircumference()| float64|

# Parabola 
Gogeom can support two form 
- **Equation of Parabola** 
``` 
  y^2 = 4ax
  or 
  x^2 = 4ay
  or 
  (y - k)^2 = 4a(x - h)
  where, (h,k) are vertex
  or
  (x - h)^2 = 4a(y - k)
  where, (h,k) are vertex

```
  - import `shape "github.com/MindorksOpenSource/gogeom"`
  - Initalize Parabola,
```
p := shape.Parabola {
        1,
        true // where this boolean value indicates if the parabola is on Y-Axis or not.
}
---- or ----

p :=shape.Parabola {
        1,
        true // where this boolean value indicates if the parabola is on Y-Axis or not.
}
```
#### Step to follow :
| Working          | Parabola With Origin | Parabola |Result
| :-------------           |:-------------              | :-----   | :-----   
|Lenght Of Latus Ration|p.LenghtOfLatusRation()|p.LenghtOfLatusRation()|float64| 
|Focus|p.FocusOfParabola()|p.FocusOfParabola()|float64,float64|
|Directrix Equation|p.DirectrixEquation()|p.DirectrixEquation()|string|
|Axis Equation|p.AxisEquation()|p.AxisEquation()|string|
|Vertex|p.Vertex()||string|
|Position Of Point - **x,y**||p.PositionOfPoint(x,y)|string|
|Point Of Interesction - **y = mx + c**||p.PointOfInteresction(m,c)|string|
|Tangent Equation - **x,y**||p.TangentEquation(x,y)|string|
|Normal Equation - **x,y**||p.NormalEquation(x,y)|string|
|Chord Of Contact Equation - **x,y**||p.ChordOfContactEquation(x,y)|string|
|Polar Of Point - **x,y**||p.PolarOfPoint(x,y)|string|
|Pole Of line - **lx + my + x = 0** ||p.PoleOfline(l,m)|float64, float64|

# Triangle
Gogeom supports the following types of triangle and their respective calculations
- Right Angled Triangle
- Isosceles Triangle
- Equilateral Triangle
- Scalene Triangle

#### Step to follow :


- import `shape "github.com/MindorksOpenSource/gogeom"`
- Initialize triangles
```
//Right Triangle
rt := shape.RightTriangleSides {
	//base, height, hypotenuse
	4, 3, 5,
}

//Isosceles Triangle
it := shape.IsoscelesTriangleSides {
	//base, slants
	6,8,
}

//Equilateral Triangle
et := shape.EquilateralTriangleSides {
	//side
	6,
}

//Scalene Triangle
st := shape.ScaleneTriangleSides {
	//side1, side2, side3
	3,4,5,
}
```

## Calculations for Triangles
| Triangle | Input values | Working | Calculation | Result|
| :--- | :--- | :--- | :--- | :--- |
| Right Triangle | base, height, hypotenuse | Perimeter | rt.PerimeterOfRightTriangle() | float64|
||| Area | rt.AreaOfRightTriangle() | float64|
||| Altitude | rt.AltitudeOfRightTriangleBase()  rt.AltitudeOfRightTriangleHeight()  rt.AltitudeOfRightTriangleHypotenuse() | float64 |
|Isosceles Triangle|base,slants|Perimeter|it.PerimeterOfIsoscelesTriangle()|float64|
|||Area|it.AreaOfIsoscelesTriangle()|float64|
|||Altitude|it.AltitudeOfIsoscelesTriangle()|float64|
|Equilateral Triangle|side|Perimeter|et.PerimeterOfEquilateralTriangle()|float64|
|||Area|et.AreaOfEquilateralTriangle()|float64 |
|||Altitude|et.AltitudeOfEquilateralTriangle()|float64|
|Scalene Triangle|side1, side2, side3|Perimeter  Area|st.PerimeterOfScaleneTriangle()  st.AreaOfScaleneTriangle()|float64|

# Quadrilaterals
Gogeom supports the following types of quadrilaterals and their respective calculations
- Square
- Rectangle
- Parallelogram
- Trapezium/Trapezoid
- Rhombus
- Scalene Quadrilaterals

#### Step to follow :
- import `shape "github.com/MindorksOpenSource/gogeom"`
- Initialize quadrilaterals
```
//when Square sides are known
sqs := shape.SquareSides {
	//side
	4,
}

//when Square diagonals are known
sqd := shape.SquareDiagonals {
	//diagonal
	9,
}

//rectangle
rct := shape.RectangleSides {
	//length, breadth
	6,10,
}

//parallelogram
plg := shape.ParallelogramSides {
	//base, slant, height
	10,6,4.5,
}

//trapezium sides with height
tph := shape.TrapeziumSidesWithHeight {
	//base, top, height
	10,5,4.6,
}

//trapezium sides with slants
tps := shape.TrapeziumSidesWithSlants {
	//base, top, slant1, slant2
	10,5,5.2,5.7,
}

//rhombus with diagonals are known
rmd := shape.RhombusDiagonals {
	//diagonal1, diagonal2
	10,8,
}

//rhombus with sides and height known
rms := shape.RhombusSides {
	//side, height
	8,7,
}

//scalene quadrilateral
scq := shape.ScaleneQuadrilateralSides {
	//side1, side2, side3, side4
	4,8,6,5,
}
```

## Calculations for Quadrilaterals
|Quadrilaterals|Input|Working|Calculation|Result|
|:---|:---|:---|:---|:---|
|Square|side|Perimeter<br/>Area<br/>Diagonal|sqs.PerimeterOfSquare()<br/>sqs.AreaOfSquare()<br/>sqs.DiagonalOfSquare()|float64|
||diagonal|Perimeter<br/>Area<br/>Side|sqd.PerimeterOfSquare()<br/>sqd.AreaOfSquare()<br/>sqd.SideOfSquare()|float64|
|Rectangle|length,breadth|Perimeter<br/>Area<br/>Diagonal|rct.PerimeterOfRectangle()<br/>rct.AreaOfRectangle()<br/>rct.DiagonalOfRectangle()|float64|
|Parallelogram|base,slant,height|Perimeter<br/>Area|plg.PerimeterOfParallelogram()<br/>plg.AreaOfParallelogram()|float64|
|Trapezium|base,top,height|Area|tph.AreaOfTrapezium()|float64|
||base,top,slant1,slant2|Perimeter|tps.PerimeterOfTrapezium()|float64|
|Rhombus|diagonal1,diagonal2|Area<br/>Side length<br/>Perimeter|rmd.AreaOfRhombus()<br/>rmd.LengthOfRhombusSides()<br/>rmd.PerimeterOfRhombus()|float64|
||side,height|Perimeter<br/>Area|rms.PerimeterOfRhombus()<br/>rms.AreaOfRhombus|float64|
|Scalene Quadrilaterals|side1,side2,side3,side4|Perimeter|scq.PerimeterOfScaleneQuadrilateral()|float64|

# N-Agon
Gogeom can handle any polygon with given their *number of sides*, *length of sides* and *apothem of the shape*.
#### Step to follow :
- import `shape "github.com/MindorksOpenSource/gogeom"`
- Initialize n-agon
```
//if polygon
n := shape.CountAndLengthAndApothemOfAgonSide {
	//side_count, side_length, side_apothem
	5,6,4.2,
}

//OR, if hexagon
n := shape.CountAndLengthAndApothemOfAgonSide {
	//side_count, side_length, side_apothem
	6,6,4.6,
}
```

## Calculations for n-agon (polygons)
|Input|Working|Calculations|Result|
|:---|:---|:---|:---|
|side count,side length,apothem|Perimeter<br/>Area|n.PerimeterOfAgon()<br/>n.AreaOfAgon()|float64|

### TODO
* More features related to Geometrical Functions

## If this library helps you in anyway, show your love :heart: by putting a :star: on this project :v:

[Check out Mindorks awesome open source projects here](https://mindorks.com/open-source-projects)


#### Contributor
[Himanshu Singh](https://github.com/hi-manshu)\
[Nishchal Raj](https://github.com/nishchalraj)


### License
```
   Copyright (C) 2018 MINDORKS NEXTGEN PRIVATE LIMITED

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```
