Below is a single Markdown document you can drop straight into Obsidian (or any Markdown editor). The first half is structured “notes” on each concept; the second half (“Flashcards”) gives you quick Q&A cards you can review or import into a flash-card plugin.

---

## Java Core Concepts

### JVM (Java Virtual Machine)
- **What it is**: An abstract virtual computer that runs Java bytecode on any hardware/OS.  
- **Main steps**:
  1. **Class loading** (bootstrap, extension, application loaders)  
  2. **Linking** (verify, prepare, resolve)  
  3. **Initialization** (run `<clinit>` static initializers)  
  4. **Execution** (interpret + JIT compile, thread stacks, heap GC)  
  5. **Termination** (when `main` returns and non-daemon threads finish)

---

### Data Types

#### Primitives
| Type    | Size        | Usage                                         |
|---------|-------------|-----------------------------------------------|
| `byte`  | 8 bits      | I/O buffers, networking, compact arrays       |
| `short` | 16 bits     | when you need a bit more than byte            |
| `int`   | 32 bits     | default integer type                          |
| `long`  | 64 bits     | large integer values                          |
| `float` | 32 bits     | single-precision floating point                |
| `double`| 64 bits     | default floating point                        |
| `char`  | 16 bits     | UTF-16 code unit                              |
| `boolean`| JVM-dependent| true/false (usually 1 byte or packed bit)    |

#### Reference Types
- **Classes** (`String`, `Dog`, your own types)  
- **Interfaces** (define contracts, no state)  
- **Arrays** (`int[]`, `String[]`)  
- **Enums** (fixed set of constants, can have fields/methods)  
- **Annotations**, **Records**, etc.

---

### `static` vs. Instance

- **Instance**:  
  - Created via `new ClassName()`.  
  - Holds its own copy of instance fields.  
  - Instance methods operate on that object’s state.
- **`static` members**:  
  - Belong to the **class** itself—one shared copy.  
  - Can be accessed via `ClassName.member` without an object.  
  - Good for utilities or shared constants.

---

### `toString()`
- Defined on `java.lang.Object`.  
- Default: `ClassName@hashcodeHex`.  
- Automatically called by `println`, string concatenation, logging.  
- **Override** in your classes to return meaningful state info.

---

### Java Program Lifecycle

1. **Edit**: Write `MyApp.java`  
2. **Compile**: `javac MyApp.java` → `MyApp.class`  
3. **Run**: `java MyApp`  
   - JVM startup  
   - Class loading → linking → initialization  
   - Invoke `public static void main(String[] args)`  
4. **Execute**: Bytecode runs (interpret + JIT); objects on heap; threads on stacks  
5. **GC**: Automatic garbage collection reclaims unused objects  
6. **Exit**: `main` returns & non-daemon threads finish → JVM shutdown

---

## Flashcards

- **Q: What is the JVM?**  
  A: The Java Virtual Machine is an abstract platform that loads, verifies, links, initializes, and executes Java bytecode on any host system.

- **Q: Name the five main phases of JVM operation.**  
  A: Class Loading, Linking (verify/prepare/resolve), Initialization, Execution (interpret + JIT), Termination.

- **Q: What’s the size of a Java `int`?**  
  A: 32 bits (4 bytes).

- **Q: How many bits does a `char` use and why?**  
  A: 16 bits, because Java uses UTF-16 for characters.

- **Q: What is a reference type? Give two examples.**  
  A: A variable holding an address to an object on the heap. Examples: `String`, `int[]`, an `enum`, or any class.

- **Q: How do `static` and instance members differ?**  
  A: `static` belongs to the class (one shared copy, callable without an instance); instance belongs to each object (requires `new` and a reference to call).

- **Q: What does `toString()` do by default?**  
  A: Returns `ClassName@hexHashCode`. It’s invoked automatically in string contexts and by `println`.

- **Q: Outline the lifecycle of a Java program from source to exit.**  
  A: Edit → Compile → Run (JVM startup, load, link, init) → Execute (interpret + JIT, GC) → Exit.

- **Q: Why override `toString()`?**  
  A: To provide meaningful, human-readable object descriptions for debugging and logging.

- **Q: How can a static method be invoked?**  
  A: Directly via the class, e.g. `Math.abs(-5)` or `MyClass.myStaticMethod()`.

---

You can import this whole file into Obsidian as one note, and if you use a flashcard plugin (e.g. “Obsidian to Review”), it will pick up the Q/A pairs automatically. Enjoy your reviews!
