# How Patterns Are Organized

---

### Intro

Patterns are organized in a nested folder structure under ./src/patterns/

```php
[patternType]/[patternSubtype]/[patternName].[patternExtension]
```
Here are the parts:

* patternType denotes the overall pattern type. If using Atomic Design this will be 
  something like “atoms” or “molecules” but it can be anything you want. For example, 
  “components” or “elements.”
* patternSubtype denotes the sub-type of pattern and is optional. This helps to organize 
  patterns under an overall pattern type. For example, a 
  “blocks” pattern subtype under the “molecules” pattern type.
* patternName is the name of the pattern.
* patternExtension is the file extension.


### Initial Structure
* Base
  * This is the place to store helpers, meta elements and stuff to make the rest work
* Atoms
  * are UI elements that can’t be broken down any further and serve as the elemental building blocks of an interface.
* Molecules
  * are collections of atoms that form relatively simple UI components.
* Organisms 
  * are relatively complex components that form discrete sections of an interface.
* Templates 
  * place components within a layout and demonstrate the design’s underlying content structure.
* Pages
  * apply real content to templates and articulate variations to demonstrate the final UI and test the resilience of the design system.
```php
- src/
  - patterns/
    - 00-base
    - 01-atomx/
    - 02-molecules/
    - 03-organisms/
    - 04-templates/
    - 05-pages/
   ```

### Deeper Nesting
PHP support nesting of folders under patternSubtype. For example, you may want to organize your pattern documentation, pattern, Sass files and pseudo-patterns in one directory like so:
```php
- 02-molecules/
  - blocks/
    - media-block/
      - media-block.md
      - media-block.twig
      - media-block.less
      - media-block~variant1.json
      - media-block~variant2.json
   ```
   
   
