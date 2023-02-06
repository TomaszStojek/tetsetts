# High-level comments

This midterm was the most useful and informative midterm I've delivered to date. I hope you can get the same value out of it that I intend by using the questions to diagnose your misunderstandings. Broadly, there seem to be three categories of mistakes:

1) Mistakes due to relying extensively on copy-pasting code and having no idea what the code means.
2) Mistakes due to lack of practice, but not due to misunderstanding the general concept.
3) Mistakes due to lack of time, but not due to misunderstanding or lack of practice.

If you're in the first category, you must immediately sign up for peer tutoring. Also consider your lab partners carefully: if you want to be successful, surround yourself with successful people. I am genuinely quite worried about this group of people and, if I could, I would suggest reviewing the previous class extensively. There's still time to recover, but you'll need to put in many hours of practice.

If you're in the second category, you're probably fine by just completing the class exercises and getting more practice.

If you're in the third category, I don't need to give you advice, you're learning fine on your own and already know what your mistakes are and how to fix them.

In general, these are study tips:

ALWAYS RETYPE. If you're ever trying to understand code, DON'T copy-paste. Instead, type it carefully, line-by-line, commenting each line. There's a reason why we teach this in the first semester: it works and there really isn't another way. If you MUST copy-paste, then ALSO retype it line-by-line. Seriously. It's like doing piano practice, nobody expects to get better without actually practicing.

MAKE A PLAYGROUND. If the code is too complicated, set up your own, seperate test environment where you can cut out the complicated stuff. Make smaller versions of the code you're trying to understand. Run those.

MAKE YOUR OWN CHALLENGES. I've given you many, many example of code you can use and there are literally thousands of Java coding examples online. E.g., with iterators, make your own iterator. Challenge yourself to think of a case where an iterator would be helpful. Google until you find the case you want. Ground yourself in these examples.

GROUND YOURSELF. Learning only works if you know why you're doing something. Nobody can motivate you for you. Write out a mission statement for why you're at BCIT. Do a pro-con list for studying a topic (and take it seriously: if there are more cons than pros, don't do the thing and accept the consequences because you know why you've decided to ignore something).

# Question by question notes

## Basic_01
### Criteria
- B.01.1 All three globals are declared and named correctly
- B.01.2 Constructor assignment is correct
- B.01.3 Move method is correct

### Common mistakes
- `dx = this.x` in `move()`
- mislabeled local or global variables

### Notes
Use the marking criteria to target your misunderstanding. 
- For B.01.1: You likely need to work creating classes with globally scoped variables. Practice simply creating classes that are stateful.

- For B.01.2: You likely need to work on constructors. Practice creating classes that take variables.

- For B.02.3: You likely need to work on mutating global state. Practice creating classes with methods that update global state.

### Example correct implementation
```java
public class Basic_01 {
  private int x;
  private int y;
  private int size;
  
  public Basic_01(int x, int y, int size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }

  public void move(int dx, int dy) {
      this.x = this.x + dx;
      this.y = this.y + dy;
  }
```

### Example incorrect implementations
```java
  public void move(int dx, int dy) {
    dx += x;
    dy = this.Ypos;
  }
```

```java
public class Basic_01 {
    int x = 0;
    int y = 0;
    int size = 0;
    
  public Basic_01(int x, int y, int size) {
    this.x = x;
    this.y = y;
    this.size = size;
  }
```

## Basic_02
### Criteria
- B.02.1 Constructor and private members correctly implemented in part class (1)
- B.02.2 Getters and setters correctly implemented in part class (2)
- B.02.3 Add correctly adds the two vectors and is reasonably written in part class (1)
- B.02.4 Move correctly resets the whole class position and is reasonably written (1)

### Common mistakes
- Not creating a part class for composition (inner classes accepted)
- `move` was created but no `add`
- `add` had no content apart from returning the given variable
- missing constructor in main class

### Notes
- For B.02.1: You likely need to work on creating new classes which are referenced by other classes. Practice by creating classes that are referenced by other classes.

- For B.02.2: You likely need to learn how to write getters and setters. Look at getters and setters in labs and retype them. Also, use your IDE to autocomplete getters and setters for new classes.

- For B.02.3: You likely need to work on creating methods that have specified inputs and outputs. Practice method design by writing methods by hand on paper.

- For B.03.4: You likely need to work on stepping through code that calls other code. Practice by using your debugger, taking note of how the values change by writing them on paper step by step.

### Example correct implementations
```java
public class Basic_02_vector {
  private int x;
  private int y;
  
  public Basic_02_vector(int x, int y){
    this.x = x;
    this.y = y;
  }
  
  public int getX() {
    return x;
  }

  public void setX(int x) {
    this.x = x;
  }

  public int getY() {
    return y;
  }

  public void setY(int y) {
    this.y = y;
  }
  
  public Basic_02_vector add(Basic_02_vector other){
    this.x += other.getX();
    this.y += other.getY();
    return this;
  }
}
```

### Example incorrect implementations
```java
public int add(int d) {
    int r;
    r = this.x + this.y + d;
    return r;
}
```
```java
public Basic_02_vector add(Basic_02_vector direction) {
    this.direction += this.direction + direction;
}
```
```java
public Basic_02_vector add(Basic_02_vector direction) {
  this.position.x == this.position.x + this.direction.x;
  this.position.y == this.position.y + this.direction.y;
}
```

## Basic_03
### Criteria
- B.03.1 Constructor and members
- B.03.2 Add deals with z appropriately
- B.03.3 Add deals with x,y in super

### Common mistakes
- Not throwing to super
- Not passing parameters into super
- Adding this.x/y and then passing to super
- Not using the superclass's attributes/members correctly
- Modifying the superclass rather than extending it
- Not addressing class variables

### Notes
- For B.03.1: You are likely unclear on how to make super and subclasses and what the relationship between them are. You may also be unsure of what super() does. Practice making super and subclasses where the subclasses rely on the superclasses attributes/members and methods. Use the debugger to step through calls to the subclass which also call super.

- For B.03.2: You are likely unclear on class attributes and how they work. Practice by declaring subclasses and using your IDE's popup suggestion boxes to see candidate variables. Then, trace the code using your debugger.

- For B.03.3: You likely do not understand how super works (or missed that instruction). Practice is the same as - B.03.1 but for methods rather than constructors.

### Example correct implementations
```java
public class Basic_03_Sub extends Basic_03 {
  public float z;
  
  @Override
  public void add(Basic_03 vec){
    if (vec instanceof Basic_03_Sub){
      this.z += ((Basic_03_Sub) vec).z;
    }
    super.add(vec);
  }
}
```

### Example incorrect implementations
```java
public void add(Basic_03 vec) {
    super.add(z);
}
```
```java
public void add(Basic_03 vec) {
    this.z += vec.z;
}
```

## Basic_04
### Criteria
- B.04.1 Defined ITimtable with methods and implemented with current class
- B.04.2 Correctly defined start
- B.04.3 Correctly defined lap
- B.04.4 Correctly defined print

### Common mistakes
- Not using the implements keyword or adding methods to interface
- Not using parameters for draw or lap
- Not updating now
- Not clearing laps
- Defining methods in the interface rather than leaving them declared but undefined
- Adding return values to interface 

### Notes
- For B.04.1: You may not understand the definition of interfaces. Practice by declaring interfaces and working through the IDE bugs one-by-one.

- For B.04.2: You may not understand the Date class, how initializing variables works, or the lifecycle of Java variables. Practice by using your debugger to step through the variable values. Write them down on a piece of paper step-by-step.

- For B.04.3: Same as - B.04.2.

- For B.04.4: You may not understand how arrays, loops, or printing works. Practice by drawing your arrays by hand and stepping through with the debugger.

### Example correct implementations
```java
public interface Basic_04_ITimeable {

  void start();
  void lap();
  void print();

}


public class Basic_04 implements Basic_04_ITimeable{
  private Date start;
  private Date now;
  private ArrayList<Date> laps;

  public Basic_04() {
    this.start = new Date();
    this.now = new Date();
    this.laps = new ArrayList<Date>();
  }
  
  public void start() {
    this.start = new Date();
    laps.clear();
  }

  public void lap() {
    Date now = new Date();
    laps.add(now);
    this.now = now;
  }

  public void print() {
    lap();
    for (Date lap : laps) {
      System.out.println(lap);
    }
  }
}
```

### Example incorrect implementations
```java
public class Basic_04 implements Basic_04_ITimeable {
  private Date start;
  private Date now;
  private ArrayList<Date> laps;

  public Basic_04_Answer() {
    this.start = new Date();
    this.now = new Date();
    this.laps = new ArrayList<Date>();
  }
  
  public void start(){
    this.start = now;
    this.laps.clear();
  }
  
  public void lap() {
    this.laps.add(now);
  }
}

```

## Basic_05
### Criteria
- B.05.1 Made exception class
- B.05.2 Made useful error message
- B.05.3 Try/catch block 1
- B.05.4 Try/catch block 2

### Common mistakes
- No try/catch blocks or error handling
- Error messages that did not use passed values
- Exception never thrown
- Throwing exceptions while handling exceptions

### Notes
- For B.05.1: Practice making exception classes.
- For B.05.2: Practice writing good error messages by using the passed variables in your exception as part of the error string.
- For B.05.3: Wrap methods that throw exceptions in try/catch blocks. Practice by using exceptions and following the IDE warnings.
- For B.05.4: Same as - B.05.3.

### Example correct implementation
```java
public class Basic_05_exception extends Exception {
  public Basic_05_exception(int a, int b) {
    super(String.format("A: %d B: %d. Negative values not allowed.", a, b));
  }
}

public int addPositive(int a, int b) throws Basic_05_exception {
  if (a < 0 || b < 0) {
    throw new Basic_05_exception(a, b);
  } else {
    return a + b;
  }
}
  
```

## Basic_06
### Criteria
- B.06.1: Test case for x-position correct
- B.06.2: Test case for y-position correct
- B.06.3: Move method implemented

### Common mistakes
- Few mistakes were common except not finishing

### Notes
- For B.06.1: You may not understand how to create or use JUnit tests. Pratice by using the IDE's context actions to automatically generate tests. Review the test lab and practice creating tests.
- For B.06.2: Same as - B.06.1.
- For B.06.3: Same as any above method writing suggestions.

### Example correct implementation
```java
Basic_06_myClass b = new Basic_06_myClass();

@Test
void moveTest(){
  b.move(1, 1);
  assertEquals(1, b.x);
  assertEquals(1, b.y);
}
```

## Basic_07
### Criteria
- B.07.1: Calls are in correct order, -1 for each missing or out of order call

### Common mistakes
- Incorrect order.

### Notes
- For B.07.1: Trace code using the stepper or through clicking. Use communication or sequence diagrams to help.

## Basic_08
### Criteria
- B.08.01: Correctly adding attributes.
- B.08.02: Correctly adding methods.
- B.08.03: No obvious errors.

### Common mistakes
- No earnest answer had a mistake beyond possible access modifiers which I ignored.

### Notes
None.

## Basic_09
### Criteria
- B.09.1 Correct attributes and types
- B.09.2 Correct methods and types

### Common mistakes
- Incorrect syntax/missing types

### Notes
For both: I would suggest looking at examples of code -> single UML classes online and redrawing on paper. Highlight the things that are the same with the same colour pen. Print out your code and draw lines between the keywords in the code and the keywords in the UML diagram.

## Intermediate_01
### Criteria
- I.01.1: 6 correct test cases.
- I.01.2: Setup and values reasonable and correct.

### Common mistakes
- Missing test cases.
- Not splitting asserts into separate tests.
- Not creating seperate test classes.
- Not using JUnit/using system.out.println

### Notes
- For I.01.1: Tests need to cover all boundaries/edge cases/conditions. Easiest method is to make sure there's at least one test per condition, and a test for each side of a value boundary. Best practice is to write out a table of expected inputs and outputs.

- For I.01.2: Best practice involves declaring and intializing variables in @Before setup method, but OK to change state per test. Goal is readability. Practice by using the automatic test creation offerred by the IDE as a template, then expanding to all edge cases.

### Example correct implementation
```java
class Intermediate_01_Test extends Intermediate_01 {

  Intermediate_01 i01;

  @BeforeEach
  void setUp() {
    i01 = new Intermediate_01();
    i01.setX(40);
    i01.setY(40);
  }

  @Test
  void moveLeft() {
    i01.move("LEFT", 5);
    assertEquals(35, i01.getX());
  }

  @Test
  void moveUp() {
    i01.move("UP", 5);
    assertEquals(45, i01.getY());
  }

  @Test
  void moveRight() {
    i01.move("RIGHT", 5);
    assertEquals(45, i01.getX());
  }

  @Test
  void moveDown() {
    i01.move("DOWN", 5);
    assertEquals(35, i01.getY());
  }

  @Test
  void outOfBounds() {
    i01.move("LEFT",40);
    assertEquals(0, i01.getX());

    i01.move("DOWN", 50);
    assertEquals(0, i01.getY());
  }
}
```

## Intermediate_02
### Criteria
- I.02.1: Classes created with appropriate methods
- I.02.2: Implements is correct
- I.02.3: Interfaces created with methods
- I.02.4: Compiles correctly

### Common mistakes
- Using abstract classes instead of interfaces
- Not implementing interface methods

### Notes
- For I.02.1: Look into the definition of interfaces vs. abstract methods. 
- For I.02.2: Look into labs on polymorphism.
- For I.02.3: Almost no mistakes here.
- For I.02.4: Use the IDE to give you hints about what needs to be fixed.

### Example correct implementation
```java
public interface Liftable {
  void lift();
}

public interface Drivable {
  void drive();
}

public interface Loadable {
  void load();
}

public class Bike implements Drivable, Liftable {
  public Bike() {}
  public void drive() {}
  public void lift() {}
}

public class Car implements Drivable, Loadable {
  public Car() {};
  public void drive() {};
  public void load() {};
}

public class Truck implements Drivable, Loadable {
  public Truck() {};
  public void drive() {};
  public void load() {};
}
```

## Intermediate_03
### Criteria
- I.03.1 Abstract class is declared with reasonable attributes and methods
- I.03.2 Composition is used where parts are included in wholes
- I.03.3 Inheritance is used where multiple classes inherit from other classes
- I.03.4 Aggregation is used where a whole class includes multiples of the same part in an array
- I.03.5 Reasonable overall structure, readable, illustrates the concept clearly

### Common mistakes
- Declaring empty abstract classes.
- Using unclear names or names that imply a different function than how the class is being used.
- Using extends/implements inappropriately, i.e., extends from a part class rather than a super class.
- Using methods rather than objects to model composition, inheritance and aggregation.
- Unclear hierarchy
- No member attributes to indicate composition or aggregation
- No arrays or other collections used for aggregation

### Notes
- For I.03.1: You likely need practice with modeling similarities between classes of objects. Focus particulaly on reducing code duplication. 
- For I.03.2: You likely need practice with the parts-whole relationship of composition. Focus particularly on creating classes that use other classes without extension. Practice by decomposing objects in the world into parts-whole relationships and modeling them with code.
- For I.03.3: You likely need practice with using inheritance to reduce code duplication. Or, you may need to use inheritance to indicate type-of relationships. Practice is similar to - I.03.1.
- For I.03.4: Most mistakes that I saw either just didn't use aggregation or used composition instead of aggregation, which is a pretty reasonable mistake with a simple fix: use collections such as ArrayLists, etc.
- For I.03.5: You likely need practice with communicating via code, i.e., naming variables reasonably, using comments, structuring your code. Practice involves editing your code, i.e., reading it from the perspective of another person reading it.

### Example correct implementation
```java
public abstract class Automobile {
  protected Engine engine;
  protected ArrayList<Wheel> wheels;
}

public class Car extends Automobile {}

public class Engine {}

public class Truck extends Automobile {}

public class Wheel {}
```

## Intermediate_04
### Criteria
- Each class was correctly implemented.

### Common mistakes
- Technically, constructors should call super, but since I didn't ask for constructors, I didn't mark this down
- Also technically, you don't need to reimplement methods from a superclass that you aren't overriding, but I decided not to take marks off for this
- Use of implements rather than extends
- Extending incorrectly
- Creating the abstract class without any abstract methods
- Small errors were ignored for this question

## Notes
See above mistakes.

### Example correct implementation
```java
public abstract class Book {
  private int length;
  private int position;
  private ArrayList<Page> pages;
  public abstract Page getPage();
}

public class Page {
  private ArrayList<Paragraph> content;
  public Paragraph getParagraph(int p) {
    return content.get(p);
  }
}

public class Paragraph {
  private ArrayList<String> sentences;
  public String getSentence(int s) {
    return sentences.get(s);
  }
}

public class Textbook extends Book {}
```

## Intermediate_05
### Criteria
- I.05.1 Since this was relative to your own work and therefore highly variable between submissions, all reasonable attempts given full marks.

## Intermediate_06
### Criteria
- I.06.1 Communication digram has correct number of classes, direction of arrows, and method labels.
- I.06.2 Sequence diagram has correct number of classes, direction of arrows, and method labels.

### Common mistakes
- No method calls along arrows in communication diagram
- Communication diagram shows every instance of class
- Sequence diagram does not show every instance of class

### Notes
- For I.06.1: The common mistakes seemed to be not about conceptual difficulties, rather, they were about syntax details. Practice should include simply refering to communication diagram specifications (widely available on the internet) and using them in the project to track your own code.

- For I.07.1: Mostly syntax errors as well. For those who did not attempt either the communication diagram or the sequence diagram, the best practice will be to spend time with your debugger, stepping through each function call. If you have not spent time with the debugger yet, now is the time.


## Advanced_01
### Criteria
- A.01.1 next() advances the current index, returns the value of next
- A.01.2 hasNext() is a boolean, checks whether there is a next value correctly
- A.01.3 iterator() calls an actual iterator

### Common mistakes
- Using built-in iterator rather than creating your own iterator. This was common and I did not give any marks for it.
- Not constructing the iterator
- Returning "this" rather than constructing a new object

### Notes
For all criteria: most mistakes that I saw were what I would call "coding without knowing why." I know this is particularly difficult for custom iterators, since the obvious retort is "why don't I just use an ArrayList?" The answer is "because you often need to decorate an existing ArrayList with custom functionality and be able to loop through the array," but that sounds very abstract. The point is that you will be able to control the iteration.

E.g., for those of you who used the builtin HashMap iterator, the order of returns may not be what you want. Is it alphabetical? Is it random? A custom iterator will allow you to control this.

### Example correct implementation
```java
class hashMapIterator implements Iterator<String> {
  HashMap<String, String> store;
  ArrayList<String> keys;
  int i = 0;

  public hashMapIterator(HashMap<String, String> store) {
    this.store = store;
    this.keys = store.keySet();
  }

  public boolean hasNext() {
    return i < store.size();
  }

  public String next() {
    String ret = store.get(keys.get(i));
    i++;
    return ret;
  }
}
```

## Advanced_02
### Criteria
- A.02.1 Getter/Setter correctly implemented
- A.02.2 getInstance correctly implemented
- A.02.3 Constructor and attributes correctly imlemented

### Common mistakes
- Not creating a private constructor
- Not calling the constructor from getInstance
- No conditional logic in getInstance
- Circular instantiation

### Notes
- For A.02.1: Often seems to have simply been missed.
- For A.02.1 and - A.02.2: most mistakes here seem to have been related. E.g., the singleton was missing an attribute which held the instance --> no conditional logic was included. Or, the singleton had no private constructor --> getInstance was not the only way to construct the singleton rendering it not a singleton. Best practice would be:

(1) type the singleton BY HAND and comment each line to ensure you understand what you are typing. Very clearly many people simply did a bad job of copy-pasting by not knowing the meaning of each line. There's no value in copy-pasting for learning: discipline yourself to retype until you understand it. 

(2) set up a test case for yourself similar to the midterm question and ensure that you're not able to create multiple instances.

### Example correct implementation
```java
public class Singleton {
  private static Singleton singleton;
  private String label;

  private Singleton() {}

  public static Singleton getInstance() {
    if (singleton == null) {
      singleton = new Singleton();
    }
    return singleton;
  }

  public void setLabel(String label) {
    this.label = label;
  }

  public String getLabel() {
    return this.label;
  }
}
```

## Advanced_03
### Criteria
- A.03.1 Comparison is correct, outputs an integer, compiles
- A.03.2 Exceptions are used reasonably
- A.03.3 Types are correctly used (or casting is reasonable) and style is readable

### Common mistakes
- Casting without any type check
- No exceptions
- Invalid comparisons, e.g., between objects without guaranteed type

### Notes
- For A.03.1: few people got this one very wrong, so not much to say here.
- For A.03.2: Many people did not throw the exceptions as specified in the comment. Those who did, I tended to give full marks to.
- For A.03.3: This is where the majority of the difficulties seemed to be. Casting is "possible" in the sense that this would get away from compiler errors, but it doesn't allow your code to be very extensible and would throw errors as soon as you compared something other than what you casted to. Try to not think about casting as a cure-all to compiler errors. The best solutions here explicitly handled type with an exception (that's why the comment required them). 

In general, the idea of a "valid comparision" needs to be reinforced with type checking. Best practice for this is to really solidify the idea of type in your mind by practicing comparisons. E.g., if we wanted to compare two objects, what are the qualities by which we could compare them? Which are orderable, which are not? If they DO have a possible order, what do we need?

E.g., comparing two cups, we could compare by:
- Size
- Weight
- Volume
- Colour
- Use case

Which of these are ordered and which are not? Can we impose an order on some, or are some simply invalid? What would it mean to produce an order on the invalid cases and why would that be bad?

Concretely from the lab, we did comparison on strength of Player vs. Enemy. That was a single number. But what if you had to compare multiple numbers, e.g., strength, dexterity, skill, etc. You would have to develop your own metric. Practice by forcing yourself to make these metrics in your project.

### Example correct implementation
```java
public int compareTo(Object o) throws NullPointerException, ClassCastException {
    if (o == null) {
      throw new NullPointerException();
    }

    if (!(this instanceof o)) {
      throw new ClassCastException();
    }

    if (this.size > ((myClass) o).size) {
      return 1;
    } else if (this.size < ((myClass) o).size) {
      return -1;
    } else {
      return 0;
    }
}
```

## Advanced_04
### Criteria
- A.04.1 Reg/UnRg
- A.04.2 Notify/Update
- A.04.3 Prints correctly
- A.04.4 Constructor and style

### Common mistakes
- Missing register or unregister
- Missing notify or update or the internal logic of either
- Missing the ID part of the TODO
- Never initializing the ArrayList or initializing outside of a constructor

### Notes
For all: most of the lost marks on this one was simply missing code. I don't think there's much of a conceptual difficulty exposed by this midterm question.

### Example correct implementation
```java
public class Observable {
  ArrayList<Observer> observers;
  
  public Observable(){
    this.observers = new ArrayList<>();
  }

  public void registerObserver(Observer observer) {
    this.observers.add(observer);
  }

  public void unregisterObserver(Observer observer) {
    this.observers.remove(observer);
  }

  public void notifyObservers(String msg) {
    for (Observer observer : observers){
      observer.update(msg);
    }
  }
}

public class Observer {
  private String message;
  private int id;

  public Observer(int id) {
    this.id = id;
  }

  public String update(String message) {
    this.message = message;
    return String.format("%d: %s", id, message);
  }
}
```

## Advanced_05
### Criteria
- A.05.1 Classes correctly declared
- A.05.2 Methods correctly declared

### Common mistakes
- Those who earnestly attempted the correct style of diagram generally did well
- A few mistakes in terms of misunderstanding the kind of diagram, i.e., some people implemented a class diagram

### Notes
There were enough issues with directionality that I think it reflects on the quality of my explanation more than the knowledge of the people who attempted it. As such, I gave full marks to anyone who got all of the methods and classes correct, even if they put the methods in different classes.

### Example correct implementation
```java
public class RC_Remote {}

public class RadioReceiver {
  public int sendSignal() {}
  public int poll() {}
}

public class Controller {
  public void setSpeed(int speed) {}
  public void receiveCommand() {}
}

public class MotorController {
  public void setDirection(int direction) {}
  public void setSpeed(int speed) {}
  public void setAngle(int angle) {}
}

public class MotorDriver {
  public void setPower(int power) {}
}
```

## Advanced_06
### Criteria
- A.06.1 Reasonable implementation of diagram.

### Common mistakes
- There were a few problems with methods that did not call the correct other classes, generally the attempt were well-done

### Notes
I took marks off if there was no clear connection between the classes or if the methods were very incorrect. Some people put in more methods than I expected; as long as they were reasonable, I gave full marks.

```java
public class Controller {
  private Engine engine;
  private Brakes brakes;
  public Controller() {}
  public void run() {
    engine.accelerate();
    engine.decelerate();
    brakes.decelerate();
  }
  public void setCurrentGasOutput() {}
  public void setCurrentSpeed() {}
}

public class Engine {
  private Controller controller;
  public Engine() {}
  public void accelerate() {
    controller.setCurrentGasOutput();
  }
  public void decelerate() {
    controller.setCurrentGasOutput();
  }
}

public class Brakes {
  private Controller controller;
  public Brakes() {}
  public void decelerate() {
    controller.setCurrentSpeed();
  }
}
```
