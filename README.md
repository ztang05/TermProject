# Next?

## Update

* May 7: a few bugs fixed in NextViewController.swift and SearchViewController.swift.

## Synopsis

* “Next?” is an IOS mobile app developed with Swift 3.0. 
* The app is focused on providing information of TV shows 
* The app will recommend TV shows to users based on their interests, therefore different users will get different response from the app; 
* Users can search for TV shows they like and see brief information about this show including title, crews and plot; 
* Users can add TV shows to their favorites and track the next episode dates of those shows.


## Code Example
---
```
// Section of compute recommendations
// **********************************
var xList = [String]()
var yList = [Int]()
for x in newRecList
{
if resultSet.intersection(x.genre.components(separatedBy: ", ")).count > 0
{
xList.append(x.title)
yList.append(resultSet.intersection(x.genre.components(separatedBy: ", ")).count)
}
}
if xList.count>1
{
let sortedxy = zip(xList, yList).sorted { $0.1 > $1.1 }
xList = sortedxy.map { $0.0 }
yList = sortedxy.map { $0.1 }
}

print("**********************")
for (x,y) in zip(xList, yList)
{
print ("Show \(x) has \(y) intersections")
}

var favListTitle = [String]()
for x in favoriteList
{
favListTitle.append(x.title)
}

var firstList = [String]()
var secondList = [String]()
var lastList = [String]()

for (x,y) in zip(xList, yList)
{
if y == 3
{
firstList.append(x)
}
if y == 2
{
secondList.append(x)
}
if y == 1
{
lastList.append(x)
}
}

while (!firstList.isEmpty)
{
for x in favListTitle
{
firstList = firstList.filter { $0 != x }
}
let index = Int(arc4random_uniform(UInt32(firstList.count)))
print ("count \(firstList.count)")
if firstList.isEmpty
{
break
}
print("1")
return firstList[index]
}
while (!secondList.isEmpty)
{
for x in favListTitle
{
secondList = secondList.filter { $0 != x }
}
let index = Int(arc4random_uniform(UInt32(secondList.count)))
if secondList.isEmpty
{
break
}
print("2")
return secondList[index]

}
while (!lastList.isEmpty)
{
for x in favListTitle
{
lastList = lastList.filter { $0 != x }
}
let index = Int(arc4random_uniform(UInt32(lastList.count)))
if lastList.isEmpty
{
break
}
print("3")
return lastList[index]
}

let index = Int(arc4random_uniform(UInt32(copyList.count)))
print("copylist")
return copyList[index].title
}
```
---

## Installation

You need to have Xcode to use my project, and iPhone7 simulator is recommmeded. My App is not available in App Store yet.
Unzip the TVshows.zip, and run TVshows.xcodeproj. Then you are good to go!

## API Reference

Two Main APIs

* TVMaze: http://www.tvmaze.com/api

* OMDB: http://www.omdbapi.com/


## Contributors

Please don't modify my project. Thank you.
