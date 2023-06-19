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
### Configuring the formatter : 
**RelativeDateTimeFormatter** provides several properties to customize the formatting. The key properties are:

* **dateTimeStyle** : Specifies the level of detail for the formatted string, such as **named** & **numeric** .
* **unitsStyle** : Determines the style of units used, such as **full**, **short** and **spellOut**.
* **formattingContext** : Defines the context in which the string will be used, such as **beginningOfSentence** or **middleOfSentence** .

## Examples: 

### Difference between two dates: 


### Formatting a date for yesterday with dateTimeStyle :

```swift
let formatter = RelativeDateTimeFormatter()
formatter.dateTimeStyle = .named
let now = Date()
let yesterday = Calendar.current.date(byAdding: .day, value: -1, to: now)!
print(formatter.localizedString(for: yesterday, relativeTo: now)) // "yesterday"

formatter.dateTimeStyle = .numeric
print(formatter.localizedString(for: yesterday, relativeTo: now)) // 1 day ago
```
In the above example, we specify a **.dateTimeStyle**. If we specify **.named**, we will get something like **yesterday**, whereas if you specify **.numeric**, you will get **1 day ago**.
  
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
