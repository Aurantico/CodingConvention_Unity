# **Unity Coding Convention**

This coding convention serves the following purposes:
- Create a consistent look to the code, so that readers can focus on content, not layout.
- Enable readers to understand the code more quickly by making assumptions based on previous experience.
- Facilitate copying, changing, and maintaining the code.
- Demonstrate Coding best practices (SOLID Principles).

Keep in mind basic concepts of OOP
- Inheritance
- Asbtract Classes and Interfaces
- Polymorphism
- Composition over Inheritance
- Good Design Patterns
- **DO NOT use Singletons (DONT!!!)**

Please keep in mind that we should always be using SOLID principles of OOP
- Single Responsibility
- Open/Close
- Liskov Substitution
- Interface Segregation
- Dependency Inversion

***
***
## **Naming Conventions**

At all times meaningful names should be used for any and all of the parts of the code, from namespaces to local variables  
Please avoid using Hungarian Notation. If our code architecture is good, a simple naming convention like the one following is perfect.

***
### **Namespaces**
- Namespaces should be Nouns, not verbs
- Namespaces should be named based on the System or Subsystem that is being composed and the libraries that it contains
- Namespaces should be named using PascalCase


``` csharp
namespace NotificationSystem { ... }

namespace NotificationSystem.Messages { ... }
```

***
### **Classes and Interfaces**
- Name should be a Noun, not a verb
- Should be named based on the resposibility of the Class/Interface
- Should be named using PascalCase
- Manager, there can only be one manager instance of each type
- Controller, there can be multiple instances at the same time
- Abstract Classes should start with the Letter A, followed by the class name
- Interfaces should start with the Letter I, followed by the Interface name


``` csharp
public class GameManager { ... }

public interface IDamageable { ... }

public abstract Class AUnit : IDamageable { ... }

public class PlayerController : AUnit { ... }
```

***
### **Regions**
Regions are a very useful tool to use when the classes get a bit big, however when we follow good coding practices specially when focusing on the Single responsibility princple, my classes should not be big at all.
For the exception cases we might use Regions to organize the code a bit better.

- Group Global variables
- Group functionality blocks together
- Group Unity Functions
- Group Class Functions
- Group Debuging Functions and Variables
- Keep the same amount of spaces between Regions (3 lines)


``` csharp
public class SomeClass
{
	#region GlobalVariables

		public int SomeInt;

		private float _SomeFloat;

	#endregion GlobalVariables



	#region UnityFunctions

		private void Awake() { }
		private void Start() { }
		private void OnEnable() { }
		...
		private void OnCollisionEnter(...) { }
		..
		private void OnDestroy() { }
	
	#endregion UnityFunction



	#region ClassFunctions

		public void MyPublicFunction() { }

		private void MyPrivateFunction() { }

		...

	#endregion ClassFunctions
}
```

***
### **Variables**
- Public/Internal Variables are named with PascalCase
- Private/Protected Variables are named with _PascalCase (Prepend Underscore)
- Local Variables and Parameters are named with camelCase
- Try not to over use Public
	- if a variable needs to be exposed to the inspector and does not need to be public, make it private/protected and add the "SerializeField" decorator
	- Overusing public clutters the API
	- Overusing public might make code-completion slower


``` csharp
public class SomeClass
{
	public int MyInteger = 0;

	[SerializeField]
	private float _MySerializedFloat = 0.5f;

	private float _MyFloat = 1f;

	private void MyFunction(string myString)
	{
		bool myBool = false;
	}
}
```
***
***
## Layout Convention
- Write only one statement per line.
- Write only one declaration per line.
- If continuation lines are not indented automatically, indent them one tab stop (four spaces).
- Add at least one blank line between method definitions and property definitions.
- Use parentheses to make clauses in an expression apparent, as shown in the following code.

``` csharp
if( (val1 > val2) && (val3 < val4) )
{
	//Code Here
}
```

### Brackets, Spacing, Indentation
- Curly brackets always on a new line
	- Some templating tools / IDEs mess this up so setup the best you can.
- Always include curly brackets (no free-floating ifs)
- Spacing is 4-space-width tab
- Functions with spaces after commas
- Variables always on a new line. 

``` csharp
void MyFunction(int example1, string example2, bool example3)
{
	//Code Here
}
```

### Conditions
- Use [*boolVar == false*] rather than [*!boolVar*] to make intentions **More Explicit**.
- If combining multiple (3 or more) conditions in a single statement consider assigning to a local variable with a descriptive name if it makes sense.
``` csharp
if(boolVal == false)
{
	...
}
```


***
***
## Project Organization 

Try to keep Systems compiled together inside their own folder structure, instead of having a top folder Scripts and have Notifications, Networking folders inside.

	Asstes
		+ Addons
			+ //External Addons if possible
		+ Notifications
			+ Scripts
			+ Scenes
			+ Prefabs
			+ ...
		+ Networking
			+ Scripts
			+ Scenes
			+ Prefabs
			+ ...
		+ Gameplay
			+ Scripts
			+ Scenes
			+ Prefabs
			+ ...

This will allow much more organized files and folder and could potentially greatly decrease compilation time with the Incremental compiler  

  

/// This is under construction...  
/// Lets all complete this Guidelines as we go!
