#  Kuchi Flash Cards

Kuchi Flash Cards is a simple flash card app for learning languages whilst traveling. It allows the user to add new words, phrases, and characters to decks, then later test themselves from the set decks, or quickly access phrases for common situations, such as eating, socializing, or working.

The app will have a landing scene where they can select to test themselves or access a pre-made deck (for editing or viewing). Decks and the contents of decks can be listed (for editing or viewing).


## Swift UI 

### what is a view modifier on swift ui ?

A modifier is a view instance method that creates a copy of the view, does something to the view copy (such as changing the font size or the color), and returns the modified view.

<b>Example</b>

```
Text("Hola serotes")
  .font(.system(size: 60))
```

To change the look of a Text instance, you use modifiers. But beyond that, more generally, any view can be altered using modifiers.

<b>There are two categories of modifiers that SwiftUI offers:</b>

- Modifiers bundled with the View protocol, available to any view.
- Modifiers specific to a type, available only to instances of that type.

 