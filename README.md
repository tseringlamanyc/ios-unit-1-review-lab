                                                                                                                                                                                                                                                                                                                            # Unit 1 Review Lab

Before completing any of the review questions below, ensure that you have answered each question in the previous labs.

## Question 1

Given the following excerpt from the Declaration of Independence, find the most frequent word that is longer than 5 characters.

 - use components(separatedBy:) to break up the string into an array.
 - use CharacterSet.punctuationCharacters in union with any other characters you don't want in your array, like spaces and new lines.

```swift
let declarationOfIndependence =

"""
When in the Course of human events, it becomes necessary for one people to dissolve the
political bands which have connected them with another, and to assume among the powers of the
earth, the separate and equal station to which the Laws of Nature and of Nature's God entitle
them, a decent respect to the opinions of mankind requires that they should declare the causes
which impel them to the separation.
We hold these truths to be self-evident, that all men are created equal, that they are endowed by
their Creator with certain unalienable Rights, that among these are Life, Liberty and the pursuit
of Happiness. That to secure these rights, Governments are instituted among Men, deriving
their just powers from the consent of the governed, That whenever any Form of Government
becomes destructive of these ends, it is the Right of the People to alter or to abolish it, and to
institute new Government, laying its foundation on such principles and organizing its powers in
such form, as to them shall seem most likely to effect their Safety and Happiness. Prudence,
indeed, will dictate that Governments long established should not be changed for light and
transient causes; and accordingly all experience hath shewn, that mankind are more disposed to
suffer, while evils are sufferable, than to right themselves by abolishing the forms to which they
are accustomed. But when a long train of abuses and usurpations, pursuing invariably the same
Object evinces a design to reduce them under absolute Despotism, it is their right, it is their duty,
to throw off such Government, and to provide new Guards for their future security. Such has
been the patient sufferance of these Colonies; and such is now the necessity which constrains
them to alter their former Systems of Government. The history of the present King of Great
Britain is a history of repeated injuries and usurpations, all having in direct object the
establishment of an absolute Tyranny over these States. To prove this, let Facts be submitted to a
candid world.
"""

func noPunc(old: String) -> String {
    var new = ""
    for char in old {
        if char.isPunctuation {
            continue
        } else if char == "\n" {
            new += " "
        } else {
            new += String(char)
        }
}
    return new
}
var myString = noPunc(old: declarationOfIndependence)

var myStringArr = myString.components(separatedBy: " ")
print(myStringArr)

var fiveWords = [String]()
var freqWord: [String : Int] = [:]
var largestValue = 0
var mostWord = String()
var fiveWordsImproved = [String]()

for word in myStringArr {
    if word.count > 5 {
        fiveWords.append(word)
    }
}

for word in fiveWords {
    if let count = freqWord[String(word)] {
        freqWord[String(word)] = count + 1
    } else {
        freqWord[String(word)] = 1
    }
}

for (key, value) in freqWord {
    if value > largestValue {
        largestValue = value
        mostWord = key
    }
}

print(mostWord)

```

## Question 2

Make an array that contains all elements that appear more than twice in someRepeatsAgain.


```swift
var someRepeatsAgain = [25,11,30,31,50,28,4,37,13,20,24,38,28,14,44,33,7,43,39,35,36,42,1,40,7,14,23,46,21,39,11,42,12,38,41,48,20,23,29,24,50,41,38,23,11,30,50,13,13,16,10,8,3,43,10,20,28,39,24,36,21,13,40,25,37,39,31,4,46,20,38,2,7,11,11,41,45,9,49,31,38,23,41,16,49,29,14,6,6,11,5,39,13,17,43,1,1,15,25]

var emptyDict = [Int: Int]()
var emptyArr = [Int]()

for num in someRepeatsAgain {
    if let count = emptyDict[num] {
        emptyDict[num] = count + 1
    } else {
        emptyDict[num] = 1
    }
}

for (key, value) in emptyDict {
    if value >= 2 {
        emptyArr.append(key)
    }
}

print(emptyArr)

```

## Question 3

Identify if there are 3 integers in the following array that sum to 10. If so, print them. If there are multiple triplets, print all possible triplets.

```swift
var tripleSumArr = [-20,-14, -8,-5,-3,-2,1,2,3,4,9,15,20,30]

func triplets (arr: [Int]) -> [[Int]] {
    var ansArr = [[Int]]()
    for num in arr {
        for num2 in arr {
            for num3 in arr {
                if num + num2 + num3 == 10 {
                    var ansInt = [Int]()
                    ansInt.append(num)
                    ansInt.append(num2)
                    ansInt.append(num3)
                    ansArr.append(ansInt)
                }
            }
        }
    }
     return ansArr
}
    
print(triplets(arr: tripleSumArr))
```


## Question 3

```swift
let letterValues = [
"a" : 54,
"b" : 24,
"c" : 42,
"d" : 31,
"e" : 35,
"f" : 14,
"g" : 15,
"h" : 311,
"i" : 312,
"j" : 32,
"k" : 93,
"l" : 203,
"m" : 212,
"n" : 41,
"o" : 102,
"p" : 999,
"q" : 1044,
"r" : 404,
"s" : 649,
"t" : 414,
"u" : 121,
"v" : 838,
"w" : 555,
"x" : 1001,
"y" : 123,
"z" : 432
]
```

a. Sort the string below in descending order according the dictionary letterValues
var codeString = "aldfjaekwjnfaekjnf"
```
var codeString = "aldfjaekwjnfaekjnf"
var ansStr = String()
var sortedValues = letterValues.sorted(by: {$0.value > $1.value})

func answer (str: String) -> String {
    for (key, value) in sortedValues {
        for char in str {
            if key == String(char) {
                ansStr += key
            }
        }
    }
    return ansStr
}

answer(str: codeString)
```


b. Sort the string below in ascending order according the dictionary letterValues
var codeStringTwo = "znwemnrfewpiqn"
```
var codeStringTwo = "znwemnrfewpiqn"
var ansStr = String()
var sortedValues = letterValues.sorted(by: {$0.value < $1.value})

func answer (str: String) -> String {
    for (key, value) in sortedValues {
        for char in str {
            if key == String(char) {
                ansStr += key
            }
        }
    }
    return ansStr
}

answer(str: codeString)
```


## Question 4

Given an Array of Arrays of Ints, write a function that returns the Array of Ints with the largest sum:


```swift
Input: [[2,4,1],[3,0],[9,3]]
var largestsum = 0
var sum = 0
var ansInt = [Int]()


func largestInt( arr: [[Int]]) -> [Int] {
    for thing in arr {
        largestsum = thing.reduce(0,+)
        if sum < largestsum {
            largestsum = sum
            ansInt = thing
        }
    }
    return ansInt
}

largestInt(arr: arr1)

Output: [9,3]
```

## Question 5

```swift
struct Receipt {
  let storeName: String
  let items: [ReceiptItem]
}

struct ReceiptItem {
  let name: String
  let price: Double
}
```

a. Given the structs above, add a method to `Receipt` that returns the total cost of all items
```
struct Receipt {
  let storeName: String
  let items: [ReceiptItem]
    
    func totalCost() -> Double {
        var total = Double()
        for item in items {
            total += item.price
        }
        return total
    }
}
```

b. Write a function that takes in an array of `Receipts` and returns an array of `Receipts` that match a given store name

c. Write a function that takes in an array of `Receipts` and returns an array of those receipts sorted by price

## Question 6

a. The code below doesn't compile.  Why?  Fix it so that it does compile.

```swift
class Giant {
    var name: String
    var weight: Double
    let homePlanet: String

    init(name: String, weight: Double, homePlanet: String) {
        self.name = name
        self.weight = weight
        self.homePlanet = homePlanet
    }
}

let fred = Giant(name: "Fred", weight: 340.0, homePlanet: "Earth")

fred.name = "Brick"
fred.weight = 999.2
fred.homePlanet = "Mars"

class Giant {
    var name: String
    var weight: Double
    var homePlanet: String

    init(name: String, weight: Double, homePlanet: String) {
        self.name = name
        self.weight = weight
        self.homePlanet = homePlanet
    }
}

let fred = Giant(name: "Fred", weight: 340.0, homePlanet: "Earth")
fred.name = "Brick"
fred.weight = 999.2
fred.homePlanet = "Mars"

```
It didnt compile because fred.homePlanet was a constant , it needs to be a var 

b. Using the Giant class. What will the value of `edgar.name` be after the code below runs? How about `jason.name`? Explain why.

```swift
let edgar = Giant(name: "Edgar", weight: 520.0, homePlanet: "Earth")
let jason = edgar
jason.name = "Jason"
```
both would have the name jason since classes are reference type and point to the same object

## Question 7

```
struct BankAccount {
    var owner: String
    var balance: Double

    func deposit(_ amount: Double) {
        balance += amount
    }

    func withdraw(_ amount: Double) {
        balance -= amount
    }
}
```

a. Explain why the code above doesn't compile, then fix it.
It doesnt compile because deposit and withdraw can change over time. The way it is written initially makes it a constant property especailly inside a struct. 
```
struct BankAccount {
    var owner: String
    var balance: Double

    mutating func deposit(_ amount: Double) {
        balance += amount
    }

    mutating func withdraw(_ amount: Double) {
        balance -= amount
    }
}

```

b. Add a property called `deposits` of type `[Double]` that stores all of the deposits made to the bank account

c. Add a property called `withdraws` of type `[Double]` that stores all of the withdraws made to the bank account

d. Add a property called `startingBalance`.  Have this property be set to the original balance, and don't allow anyone to change it

e. Add a method called `totalGrowth` that returns a double representing the change in the balance from the starting balance to the current balance
```
struct BankAccount {
    var owner: String
    var balance: Double
    var deposits: [Double]
    var withdrawl: [Double]
    let staringBalance: [Double]

    mutating func deposit(_ amount: Double) {
        balance += amount
    }

    mutating func withdraw(_ amount: Double) {
        balance -= amount
    }
    
    mutating func totalGrowth(_ takeout: Double, _ putin: Double) -> Double {
       return balance = putin - takeout
        }
}

```

## Question 8

```swift
enum GameOfThronesHouse: String {
    case stark, lannister, targaryen, baratheon
}
```

a. Write a function that takes an instance of GameOfThronesHouse as input and, using a switch statement, returns the correct house words.

```
House Baratheon - Ours is the Fury

House Stark - Winter is coming

House Targaryen - Fire and Blood

House Lannister - A Lannister always pays his debts

func houseWords() {
    switch self {
    case .baratheon:
        print("Ours is the Fury")
    case .stark:
        print("Winter is Coming")
    case .targaryen:
        print("Fire and Blood")
    case .lannister:
        print("Hear Me Roar")
}

```

b. Move that function to inside the enum as a method
```
enum GameOfThronesHouse: String {
    case stark, lannister, targaryen, baratheon
    
    func houseWords() {
        switch self {
        case .baratheon:
            print("Ours is the Fury")
        case .stark:
            print("Winter is Coming")
        case .targaryen:
            print("Fire and Blood")
        case .lannister:
            print("Hear Me Roar")
    }
    }
}
let houseStark = GameOfThronesHouse.stark
houseStark.houseWords()
```

## Question 9

What are the contents of `library1` and `library2`? Explain why.

```swift
class MusicLibrary {
    var tracks: [String]

    init() {
        tracks = []
    }

    func add(track: String) {
        tracks.append(track)
    }
}

let library1 = MusicLibrary()
library1.add(track: "Michelle")
library1.add(track: "Voodoo Child")
let library2 = library
library2.add(track: "Come As You Are")


```
library 1 has = "Michelle", "Voodoo Child"a
library 2 has none because there is no identifier as library 


## Question 10

Make a function that takes in an array of strings and returns an array of strings. The function should determine if the string can be typed out using just one row on the keyboard. If the string can be typed out using just one row, that string should be in the returned array.  

```
Input: ["Hello", "Alaska", "Dad", "Peace", "Power"]
var line1: Set<Character> = ["q","w","e","r","t","u","i","o","p"]
var line2: Set<Character> = ["a","s","d","f","g","h","j","k","l"]
var line3: Set<Character> = ["z","x","c","v","b","n","m"]
var inputAnswer = [String]()

func sameLine (words: [String]) -> [String] {
    for word in words {
    if Set(word).lowercased()).isSubset(of: line1) || Set(word).lowercased()).isSubset(of: line1) || Set(word).lowercased()).isSubset(of: line1) {
            inputAnswer.append(word)
        }
    }
    return inputAnswer
}

Output: ["Alaska", "Dad", "Power"]
```
