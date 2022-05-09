#  Kuchi Flash Cards

Kuchi Flash Cards is a simple flash card app for learning languages whilst traveling. It allows the user to add new words, phrases, and characters to decks, then later test themselves from the set decks, or quickly access phrases for common situations, such as eating, socializing, or working.

The app will have a landing scene where they can select to test themselves or access a pre-made deck (for editing or viewing). Decks and the contents of decks can be listed (for editing or viewing).


## Swift UI 
_These are some notes I took from swift ui book_
### **what is a view modifier on swift ui ?**

A modifier is a view instance method that creates a copy of the view, does something to the view copy (such as changing the font size or the color), and returns the modified view.

**Example**

```
Text("Hola serotes")
  .font(.system(size: 60))
```

To change the look of a Text instance, you use modifiers. But beyond that, more generally, any view can be altered using modifiers.

**There are two categories of modifiers that SwiftUI offers:**

- Modifiers bundled with the View protocol, available to any view.
- Modifiers specific to a type, available only to instances of that type.

### Custom modifiers

_In this example I'll be using a Texfield_

At this moment I found out that there are two ways, you can either `textFieldStyle()` modifier and pass an instance of an object that conforms to `TextFieldStyle` :

```
TextField("Enter some text", text: $text)
 .textFieldStyle(KuchiTextStyle())
```

```
struct KuchiTextStyle: TextFieldStyle {
    public func _body(
        configuration: TextField<Self._Label>) -> some View {
            return configuration
                .padding(EdgeInsets(top: 8, leading: 16, bottom: 8, trailing: 16))
                .overlay(RoundedRectangle(cornerRadius: 8)
                    .stroke(lineWidth: 2)
                    .foregroundColor(.blue)
                )
                .shadow(color: Color.gray.opacity(0.4), radius: 3, x: 1, y: 2)
          
      }
}
```

Or you can create a custom modifier, in this and apply to any view instance that conforms to `View` protocol, this is better than creating a text field since you can use this view modifier on any view like a `Button`. 


```
struct BorderedViewModifier: ViewModifier {
    func body(content: Content) -> some View {
        return content
            .padding(
              EdgeInsets(top: 8, leading: 16, bottom: 8, trailing: 16))
            .background(Color.white)
            .overlay(
              RoundedRectangle(cornerRadius: 8)
                .stroke(lineWidth: 2)
                .foregroundColor(.blue)
            )
            .shadow(color: Color.gray.opacity(0.4),
                    radius: 3, x: 1, y: 2)
            .cornerRadius(8)
    }
}

extension View {
    func bordered() -> some View {
        ModifiedContent(content: self, modifier: BorderedViewModifier())
    }
}
```
 