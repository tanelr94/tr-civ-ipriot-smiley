# Evidence and Knowledge

This document includes instructions and knowledge questions that must be completed to receive a *Competent* grade on this portfolio task.

## 1. Required evidence

### 1.1. Answer all questions in this document

- Each answer should be complete, well-articulated, and within the specified word count limits (if added) for each question.
- Please make sure **all** external sources are properly cited.
- You must **use your own words**. Please include your full chat transcripts if you use generative AI in any way.
- Generative AI hallucinates, is not an authoritative source

### 1.2. Make all the required modifications to the code

- Please follow the instructions in this document to make the changes needed to the code.

- When requested to upload evidence, upload all screenshots to `screenshots/` and embed them in this document. For example:

```markdown
![Example Running Code](screenshots/screenshot1.png)
```

![Sample](screenshots/sample.png)
> Note the `!`, and the use of a relative path.

- You must upload the code into your GitHub repository.
- While you can use a branch, your code should be in main when you submit.
- Upload a zip of this repository to Blackboard when you are ready to submit.
- You will be notified of your result via Blackboard
- However, if using GitHub classrooms, you may also receive additional feedback on GitHub directly

### 1.3. Optional: Use of Raspberry Pi and SenseHat

Raspberry Pi or SenseHat is **optional** for this activity. You can use the included `sense_hat.py` file to simulate the SenseHat on your computer.

If you use a Pi, please **delete** the `sense_hat.py` file.

### 1.4. Accessible version of the code

This project relies on visual patterns that appear on an LED matrix. If you have any accessibility requirements, you can use the `udl/accessible` branch to complete the project. This branch provides an accessible code version that uses text-based patterns instead of visual ones.

Please discuss this with your lecturer before using that branch.

## 2. Specific Tasks & Questions

Address the following tasks and questions based on the code provided in this repository.

### 2.1. Set up the project locally

1. Fork this repository (if not using GitHub Classrooms)
2. Clone your repository locally
3. Run the project locally by executing the `main.py` file
4. Evidence this by providing screenshots of the project directory structure and the output of the `main.py` file

![Local Execution (INSERT YOUR SCREENSHOT)](screenshots/CREATE_A_SCREENSHOT_OF_YOUR_local_setup.png)

If you are running on a Raspberry Pi, you can use the following command to run the project and then screenshot the result:

```bash
ls
python3 main.py
```

### 2.2. Fundamental code comprehension

 Answer each of the following questions **as they relate to that code** supplied by in this repository (ignore `sense_hat.py`):

1. Examine the code for the `smiley.py` file and provide  an example of a variable of each of the following types and their corresponding values (`_` should be replaced with the appropriate values):

   | Type                    | name       | value          |
   | ----------              | ---------- | -------------- |
   | built-in primitive type |  dimmed         |  True (or False, a boolean value used in the dim_display method)             |
   | built-in composite type | pixels          |  list of 64 tuples             |
   | user-defined type       | sense_hat          |  An instance of SenseHat class from the sense_hat module             |

2. Fill in (`_`) the following table based on the code in `smiley.py`:

   | Object                   | Type                    |
   | ------------             | ----------------------- |
   | self.pixels              | list                       |
   | A member of self.pixels  | tuple(RGB color, e.g., (255, 255, 0))                   |
   | self                     | object                   |

3. Examine the code for `smiley.py`, `sad.py`, and `happy.py`. Give an example of each of the following control structures using an example from **each** of these files. Include the first line and the line range:

   | Control Flow | File       | First line  | Line range  |
   | ------------ | ---------- | ----------- | ----------- |
   |  sequence    | smiley.py        |self.sense_hat=SenseHat()           | 13-20           |
   |  selection   | sad.py         |if wide_open| 26-28           |
   |  iteration   | happy.py          |for pixel in mouth        | 21-23          |

4. Though everything in Python is an object, it is sometimes said to have four "primitive" types. Examining the three files `smiley.py`, `sad.py`, and `happy.py`, identify which of the following types are used in any of these files, and give an example of each (use an example from the code, if applicable, otherwise provide an example of your own):

   | Type                    | Used? | Example |
   | ----------------------- | ----- | --------|
   | int                     | yes     | 255 (in WHITE = (255, 255, 255) in line 5         |
   | float                   | yes    | 0.25 (in delay=0.25 in happy.py, line 33)|
   | str                     | no   | 'example'(not used in the files)    |    
   | bool                    | yes  |True (in wide_open=True in happy.py, line 24)     |

5. Examining `smiley.py`, provide an example of a class variable and an instance variable (attribute). Explain **why** one is defined as a class variable and the other as an instance variable.

> Class Variable: YELLOW = (255, 255, 0) - The reason that YELLOW is a class variable is that it is declared out in the class Smiley and not in any method. It can be shared on all of the objects of the class. Class variables are normally constants or common values which cannot vary with the instance.
>Instance Variable for example self.pixels = [...] -  This is an instance variable since it is declared within the ___init__ method and also it is prefixed with self. This implies that each of the Smiley class objects may contain a copy of pixels array, which may be manipulated freely, without affecting others.

6. Examine `happy.py`, and identify the constructor (initializer) for the `Happy` class:
   1. What is the purpose of a constructor (in general) and this one (in particular)?

   > Code:
   > def __init__(self):
    super().__init__()
    self.draw_mouth()
    self.draw_eyes()
   >

   2. What statement(s) does it execute (consider the `super` call), and what is the result?

   > super().__init__(): Uses Smiley constructor to initialize both the LED matrix as well as the default smiley face
   > self.draw_mouth(): Blackout some coordinates creating a smiling mouth.
   > self.draw_eyes(): Blanks images in particular pixels to make them open.

   >

### 2.3. Code style

1. What code style is used in the code? Is it likely to be the same as the code style used in the SenseHat? Give to reasons as to why/why not:

> PEP 8: the standard Python style 
> Not likely.The SenseHat library is a product of the Raspberry Pi Foundation which could adhere to more strict or other formatting in order to optimise either hardware libraries, or performance.  This code is clean and PEP 8 compliant as well but it is more level-specific and geared more on application behaviour and not hardware efficiency embedded within it.

2. List three aspects of this convention you see applied in the code.

> Naming , Identation, Docstrings
>

3. Give two examples of organizational documentation in the code.

> Docstring in class Declaration
>Docstring in Method

### 2.4. Identifying and understanding classes

> Note: Ignore the `sense_hat.py` file when answering the questions below

1. List all the classes you identified in the project. Indicate which classes are base classes and which are subclasses. For subclasses, identify all direct base classes.
  
  Use the following table for your answers:

| Class Name | Super or Sub? | Direct parent(s) |
| ---------- | ------------- | ---------------- |
| smiley    | Super           | none    |
| happy      | Sub         |  Smiley,Blinkable         |
| Sad        | Sub          | Smiley    | 
| Blinkable  | Super   | ABC (from abc module) |   

2. Explain the concept of abstraction, giving an example from the project (note "implementing an ABC" is **not** in itself an example of abstraction). (Max 150 words)

> Abstraction reduces the complexity of systems by revealing only the necessary aspects as well as concealing their implementation.
>

3. What is the name of the process of deriving from base classes? What is its purpose in this project? (Max 150 words)

> It is called Inheritance, and in it both Happy and Sad are derived off of Smiley in this project, re-using its pixel grid initialization and functions such as show () and dim_display (). This minimizes duplication and guarantee similar display behavior. Happy is also a child of Blinkable and it incorporates the blink method of Blinkable too, to make the eyes blink. 
>

### 2.5. Compare and contrast classes

Compare and contrast the classes Happy and Sad.

1. What is the key difference between the two classes?
   > The one and only major difference is that Happy inherits both of Blinkable and implements a method call blink() which is used to animate the blinking of its eyes whereas Sad only inherits Smiley and does not have the blinking capability.
   >
2. What are the key similarities?
   > The two classes are derived out of Smiley and share the same pixel grid structure and override draw_mouth() and draw_eyes() to get their own expression.
   >
3. What difference stands out the most to you and why?
   > The blink() method of Happy which is through inheritance of Blinkable. This is striking in the sense that this is a dynamically animated one and thus more interactive and visually interesting than the static one that the Sad entails. The blinking quality works in conjunction with the energetic meaning of a happy expression and improves the usage experience.
   >
4. How does this difference affect the functionality of these classes
   > Happy object can blink, animate its eye movement thanks to the blink() method available in the module. Without this, Sad is immobile and so does not allow much interaction to take place. 
   >

### 2.6. Where is the Sense(Hat) in the code?

1. Which class(es) utilize the functionality of the SenseHat?
   > The Smiley, Happy and Sad classes exploit the capabilities of SenseHat. Direct is the fact that Smiley makes the SenseHat class directly to initialize and manage the LED matrix.
   > Happy and Sad are subclasses of Smiley and so have this method inherited, to express their happy and sad faces.
   >
2. Which of these classes directly interact with the SenseHat functionalities?
   > The Smiley class is the only one that deals directly with the SenseHat functionalities. 
   
3. Discuss the hiding of the SenseHAT in terms of encapsulation (100-200 Words)
   >The encapsulation in the project prevents the exposure of complexity of SenseHat but displays only high level methods to this subclasses and users. 

### 2.7. Sad Smileys Can’t Blink (Or Can They?)

Unlike the `Happy` smiley, the current implementation of the `Sad` smiley does not possess the ability to blink. Let's first explore how blinking has been implemented in the Happy Smiley by examining the blink() method, which takes one argument that determines the duration of the blink.

**Understanding Blink Mechanism:**

1. Does the code's author believe that every `Smiley` should be able to blink? Explain.

> The author does not think that every Smiley needs to blink. The Smiley class in  smiley.py does not have a blink() method and only such subclasses realize it. The happy class in  happy.py is developed to inherit Blinkable (blinkable.py ), which requires a blink() method, but the Sad class from  sad.py does not, and it has no blinking feature. This selective inheritance means that not all the Smileys are obliged to blink but the trait is optional.
>

2. For those smileys that blink, does the author expect them to blink in the same way? Explain.

> The author anticipates a blinking smiley to have the same interface but not similar in the same manner. The abstract base class Blinkable (blinkable.py, line 4) has a hook method blink() which is abstract, meaning that a child of Blinkable (as e.g., Happy) must have a blink(). The details of the implementation however may vary, e.g. pixel change or timing. 
>

3. Referring to the implementation of blink in the Happy and Sad Smiley classes, give a brief explanation of what polymorphism is.

> Polymorphism to foster the same method to be implemented with differences between different classes which have a similar interface. 
>

4. How is inheritance used in the blink method, and why is it important for polymorphism?

> Inheritance also helps the Happy object derive itself off of the Blinkable object within happy.py whereby Happy must also have an implementation of the abstract method blink() at the location of blinkable.py at line 9. Using this common interface one can have polymorphic behavior the code can behave consistently when calling blink() on objects of various classes and allow each class to implement the actual behavior.
>
1. **Implement Blink in Sad Class:**

   - Create a new method called `blink` within the Sad class. Ensure you use the same method signature as in the Happy class:


2. **Code Implementation:** Implement the code that allows the Sad smiley to blink. Use the implementation from the Happy Smiley as a reference. Ensure your new method functions similarly by controlling the blink duration through the `delay` argument.

3. **Testing the Implementation:**

- Test the new blink functionality on your Raspberry Pi or within the Python classes provided. You might need to adjust the `main.py` script to incorporate Sad Smiley's new blinking capability.

Include a screenshot of the sad smiley or the modified `main.py`:

![image](https://github.com/user-attachments/assets/1d9ecb0a-53c5-43fd-a79b-f84fc601d38e)


- Observe and document the Sad smiley as it blinks its eyes. Describe any adjustments or issues encountered during implementation.

  > Your answer here

  ### 2.8. If It Walks Like a Duck…

  Previously, you implemented the blink functionality for the Sad smiley without utilizing the class `Blinkable`. Assuming you did not use `Blinkable` (even if you actually did), consider how the Sad smiley could blink similarly to the Happy smiley without this specific class.

  1. **Class Type Analysis:** What kind of class is `Blinkable`? Inspect its superclass for clues about its classification.

     > The blinkable is an abstract base. It inherits ABC (found in the Location package in blinkable.py:1), and this is used to denote that it aims at defining blueprints of subclasses without implementing concrete versions. 

  2. **Class Implementation:** `Blinkable` is a class intended to be implemented by other classes. What generic term describes this kind of class, which is designed for implementation by others? **Clue**: Notice the lack of any concrete implementation and the naming convention.

  > The interface term is generic. Blinkable is not concrete, and its implementation is abstract (blink()), a contract to be implemented by other classes (e.g. Happy) by implementing the blink() function. According to the naming convention (-able suffix), it specifies a functionality of implementing classes.

  3. **OO Principle Identification:** Regarding your answer to question (2), which Object-Oriented (OO) principle does this represent? Choose from the following and justify your answer in 1-2 sentences: Abstraction, Polymorphism, Inheritance, Encapsulation.

  > Abstraction. Blinkable is an example of abstraction because it creates an abstract method blink() without specifying how it is supposed to be implemented and instead leaves it to the subclasses to define that. This obscures complexity and mandates a homogenous interface on the classes who implement it.

  4. **Implementation Flexibility:** Explain why you could grant the Sad Smiley a blinking feature similar to the Happy Smiley's implementation, even without directly using `Blinkable`.

  > The Sad type can introduce a blink() method without extending Blinkable since the blinking capability is only based on the existing methods (draw_eyes() and show() ) with the current Smiley and the sleep() method of the time module. Sad can do the same by simply observing the way Happy does it.

  5. **Concept and Language Specificity:** In relation to your response to question (4), what is this capability known as, and why is it feasible in Python and many other dynamically typed languages but not in most statically typed programming languages like C#? **Clue** This concept is hinted at in the title of this section.

  > Its is known as duck typing. With a dynamically typed language such as Python, Sad can define a blink() method with the same signature as the one on Happy even though there is no such formal interface such as Blinkable.

  ***

  ## 3. Refactoring

  ### 3.1. Does a Smiley Have to Be Yellow?

  While our current implementation predominantly features yellow smileys, emotional expressions like sickness or anger typically utilize colors like green, red, or orange. We'll explore the feasibility of integrating these colors into our smileys.

  1. **Defined Colors and Their Location:**

     1. Which colors are defined and in which class(s)?
        > White, Green, Red, Yellow, and Blank (black), all in the Smiley class smiley.py at line 4.
     2. What type of variables hold these colors? Are the values expected to change during the program's execution? Explain your answer.
        > These colors are saved as instance attributes (classes are in form of tuples of three numbers which represent RGB color values). 
     3. Add the color blue to the appropriate class using the appropriate format and values.

  2. **Usage of Color Variables:**

     1. In which classes are the color variables used?
        > defined in Smiley and used in Smiley, Happy, and Sad. 

  3. **Simple Method to Change Colors:**
  4. What is the easiest way you can think to change the smileys to green? Easiest, not necessarily the best!
     > To alter __init__ method in smiley.py changing Y = self.YELLOW with Y = self.GREEN. This will shift the base color of the smiley to green in every case of Smiley, Happy and Sad since they all rely on the pixels list which is initialized with

  Here's a revised version of the "Flexible Colors – Step 1" section for the smiley project, incorporating your specifications for formatting and content updates:

  ### 3.2. Flexible Colors – Step 1

  Changing the color of the smileys once is straightforward, but it isn't very flexible. To facilitate various colors for smileys, it is advisable not to hardcode values in any class. This approach was identified earlier as a necessary change. Let's start by removing the built-in assumptions about color in our classes.

  1. **Add a method called `complexion` to the `Smiley` class:** Implement this instance method to return `self.YELLOW`. Using the term "complexion" instead of "color" provides a more abstract terminology that focuses on the meaning rather than implementation.

  2. **Refactor subclasses to use the `complexion` method:** Modify any subclass that directly accesses the color variable to instead utilize the new `complexion` method. This ensures that color handling is centralized and can be easily modified in the future.

  3. **Determine the applicable Object-Oriented principle:** Consider whether Abstraction, Polymorphism, Inheritance, or Encapsulation best applies to the modifications made in this step.

  4. **Verify the implementation:** Ensure that the modifications function as expected. The smileys should still display in yellow, confirming that the new method correctly replaces the direct color references.

  This step is crucial for setting up a more flexible system for color management in the smiley display logic, allowing for easy adjustments and extensions in the future.

  ### 3.3. Flexible Colors – Step 2

  Having removed the hardcoded color values, we now enhance the base class to support dynamic color assignments more effectively.

  1. **Modify the `__init__()` method in the `Smiley` class:** Introduce a default argument named `complexion` and assign `YELLOW` as its default value. This allows the instantiation of smileys with customizable colors.

  2. **Introduce a new instance variable:** Create a variable called `my_complexion` and assign the `complexion` parameter to it. This step ensures that each smiley instance can maintain its own color state.
  ![image](https://github.com/user-attachments/assets/9a203e0f-422d-4e7d-b320-4ed4f9917ebc)


  4. **Rationale for `my_complexion`:** Using a distinct instance variable like `my_complexion` avoids potential conflicts with the method parameter names and clarifies that it is an attribute specific to the object.

  5. **Bulk rename:** We want to update our grid to use the value of complexion, but we have so many `Y`'s in the grid. Use your IDE's refactoring tool to rename all instances of the **symbol** `Y` to `X`. Where `X` is the value of the `complexion` variable. Include a screenshot evidencing you have found the correct refactor tool and the changes made.

  ![Bulk Rename](screenshots/bulk_rename.png)

  5. **Update the `complexion` method:** Adjust this method to return `self.my_complexion`, ensuring that whatever color is assigned during instantiation is what the smiley displays.

  6. **Verification:** Run the updated code to confirm that Smileys still defaults to yellow unless specified otherwise.

  ### 3.4. Flexible Colors – Step 3

  With the foundational changes in place, it's now possible to implement varied smiley colors for different emotional expressions.

  1. **Adjust the `Sad` class initialization:** In the `Sad` class's initializer method, change the superclass call to include the `complexion` argument with the value `self.BLUE`, as shown:

     ```python
     super().__init__(complexion=self.BLUE)
     ```

  2. **Test color functionality for the Sad smiley:** Execute the program to verify that the Sad smiley now appears blue.

  3. **Ensure the Happy smiley remains yellow:** Confirm that changes to the Sad smiley do not affect the default color of the Happy smiley, which should still display in yellow.
   ![image](https://github.com/user-attachments/assets/61fdaa60-ce24-404d-9bd4-e93b1ad18e3b)


  5. **Design and Implement An Angry Smiley:** Create an Angry smiley class that inherits from the `Smiley` class. Set the color of the Angry smiley to red by passing `self.RED` as the `complexion` argument in the superclass call.
   ![image](https://github.com/user-attachments/assets/0254cbac-a80c-47da-a9d2-b127675d920f)


  ***
