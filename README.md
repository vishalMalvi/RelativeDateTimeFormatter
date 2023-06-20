# Simplifying Date Formatting with RelativeDateTimeFormatter in Swift 

Working with dates and times can be complex, especially when it comes to presenting them in a user-friendly format. Swift's RelativeDateTimeFormatter is a powerful tool that simplifies the process of displaying relative date and time representations, making it easier for developers to convey temporal information accurately. 

In this article, we'll explore the RelativeDateTimeFormatter in Swift, along with several examples to illustrate its usage.

## Understanding RelativeDateTimeFormatter :

**RelativeDateTimeFormatter** is a class introduced in iOS 13.0, macOS 10.15, iPadOS 13.0, watchOS 6.0 and later versions that allow us to format date and time information in a way that is easy for users to understand. It takes into account the current context and provides localized relative descriptions instead of precise timestamps.

## Using RelativeDateTimeFormatter :

To start using RelativeDateTimeFormatter, you'll need an instance of the formatter class. Let's see how to create one and then explore its various formatting options.

### Creating a RelativeDateTimeFormatter instance :

```swift 
let formatter = RelativeDateTimeFormatter()
```
### Using the formatted :
There are four available methods that allow you to format time in different representations to a string :
```swift
func localizedString(for: Date, relativeTo: Date) -> String
func localizedString(from: DateComponents) -> String
func localizedString(fromTimeInterval: TimeInterval) -> String
func string(for: Any?) -> String?
```

### Configuring the formatter : 
**RelativeDateTimeFormatter** provides several properties to customize the formatting. The key properties are:

* **dateTimeStyle** : Specifies the level of detail for the formatted string, such as **named** & **numeric** .
* **unitsStyle** : Determines the style of units used, such as **full**, **short** and **spellOut**.
* **formattingContext** : Defines the context in which the string will be used, such as **beginningOfSentence** or **middleOfSentence** .

## Examples: 

###  Formatting a date with dateTimeStyle **.named** :

```swift
let formatter = RelativeDateTimeFormatter()
formatter.dateTimeStyle = .named
let now = Date()
let yesterday = Calendar.current.date(byAdding: .day, value: -1, to: now)!
print(formatter.localizedString(for: yesterday, relativeTo: now)) // "yesterday"
```
###  Formatting a date with dateTimeStyle **.numeric** :

```swift
let formatter = RelativeDateTimeFormatter()
formatter.dateTimeStyle = .numeric
let now = Date()
let yesterday = Calendar.current.date(byAdding: .day, value: -1, to: now)!
print(formatter.localizedString(for: yesterday, relativeTo: now)) // 1 day ago
```

###  Formatting a date with dateTimeStyle **.numeric** and unitsStyle **.spellOut** :

```swift
let formatter = RelativeDateTimeFormatter()
formatter.dateTimeStyle = .numeric
formatter.unitsStyle = .spellOut
let now = Date()
let yesterday = Calendar.current.date(byAdding: .day, value: -1, to: now)!
print(formatter.localizedString(for: yesterday, relativeTo: now)) // one day ago
```

## Formatting a date in a specific locale : 

**RelativeDateTimeFormatter** automatically adapts to the user's preferred language and region by utilizing the device's locale settings. However, we can explicitly set the locale property to achieve specific localization. 

```swift
let formatter = RelativeDateTimeFormatter()
formatter.dateTimeStyle = .numeric
formatter.locale = Locale(identifier: "fr_FR")
let now = Date()
let yesterday = Calendar.current.date(byAdding: .day, value: -1, to: now)!
print(formatter.localizedString(for: yesterday, relativeTo: now)) // "il y a 1 jour"
```
## Formatting a date Specifying a specific calendar and locale:

```swift
let formatter = RelativeDateTimeFormatter()
formatter.calendar = Calendar(identifier: .gregorian)
formatter.locale = Locale(identifier: "en_US")
let date = Calendar.current.date(byAdding: .hour, value: -1, to: Date())!
let formattedString = formatter.localizedString(for: date, relativeTo: Date())
print(formattedString) // "1 hour ago"
```

## Conclusion :

The RelativeDateTimeFormatter class in Swift simplifies the task of formatting dates and times relative to the current moment. With its localized and customizable output, you can provide a more user-friendly and intuitive date display in your app. In this article, we explored various examples. 
By harnessing the power of RelativeDateTimeFormatter, you can master date formatting in Swift and enhance the overall user experience of your applications.

## Offical Apple document - [Link](https://developer.apple.com/documentation/foundation/relativedatetimeformatter#3737523)  
