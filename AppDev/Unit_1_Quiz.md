# Android Development Fundamentals Quiz
For B.Tech 3rd Year Students

## Instructions
- This quiz contains 20 multiple-choice questions
- Each question has one correct answer
- Read each question carefully before selecting your answer
- Answers with explanations are provided at the end

## Questions

1. Which programming language is primarily used for Android app development?
   a) Python
   b) JavaScript
   c) Java
   d) Ruby

2. What is the basic building block of an Android application's user interface?
   a) Intent
   b) Activity
   c) Service
   d) Fragment

3. In Android, what file contains the app's package name and declares its components?
   a) build.gradle
   b) AndroidManifest.xml
   c) strings.xml
   d) R.java

4. Which method is called when an Activity is first created?
   a) onStart()
   b) onCreate()
   c) onResume()
   d) onInit()

5. What is the entry point for the Android application?
   a) main() method
   b) First Activity declared in manifest
   c) Application class
   d) onCreate() method

6. Which folder in an Android project contains the layout files?
   a) /java
   b) /drawable
   c) /layout
   d) /values

7. What is an Intent in Android?
   a) A messaging object used to request an action
   b) A database structure
   c) A layout element
   d) A thread management system

8. Which method is used to switch between Activities?
   a) switchActivity()
   b) changeActivity()
   c) startActivity()
   d) moveToActivity()

9. What is the parent class for all UI elements in Android?
   a) UIElement
   b) View
   c) Widget
   d) Component

10. Which lifecycle method is called when an Activity becomes visible but not in focus?
    a) onStart()
    b) onResume()
    c) onVisible()
    d) onShow()

11. What is the purpose of R.java file in Android?
    a) Contains resource definitions
    b) Handles runtime permissions
    c) Manages database operations
    d) Controls app navigation

12. Which XML attribute is used to set the text of a TextView?
    a) android:text
    b) android:string
    c) android:value
    d) android:content

13. What is the default orientation of LinearLayout?
    a) Vertical
    b) Horizontal
    c) Grid
    d) Relative

14. Which method is called when an Activity is no longer visible to the user?
    a) onStop()
    b) onPause()
    c) onHide()
    d) onInvisible()

15. What is the purpose of the Activity Stack in Android?
    a) Memory management
    b) Managing background tasks
    c) Managing the navigation history
    d) Handling network requests

16. In Java, what is the access modifier that makes a variable accessible only within its class?
    a) public
    b) protected
    c) private
    d) default

17. Which component is used to store structured data in Android?
    a) SharedPreferences
    b) SQLite Database
    c) Content Provider
    d) All of the above

18. What is the purpose of the layout_weight attribute in LinearLayout?
    a) Sets the importance of the view
    b) Determines how much space the view should occupy
    c) Sets the view's visibility
    d) Controls the view's animation weight

19. Which file is used to define string resources in Android?
    a) values.xml
    b) strings.xml
    c) text.xml
    d) resource.xml

20. What is the purpose of the Android Debug Bridge (ADB)?
    a) To debug Java code
    b) To connect and communicate with Android devices
    c) To create Android layouts
    d) To manage app permissions

## Answers and Explanations

1. c) Java
   > Java is the primary language for Android development, although Kotlin is now also officially supported.

2. b) Activity
   > Activities are fundamental building blocks that represent screens in an Android app.

3. b) AndroidManifest.xml
   > The manifest file contains essential information about the app that the Android system needs.

4. b) onCreate()
   > onCreate() is called when the Activity is first created, used for initialization.

5. b) First Activity declared in manifest
   > The first Activity with the MAIN action and LAUNCHER category serves as the entry point.

6. c) /layout
   > Layout files are stored in the /res/layout directory.

7. a) A messaging object used to request an action
   > Intents are used to request actions and communicate between components.

8. c) startActivity()
   > startActivity() is used to launch a new Activity.

9. b) View
   > View is the base class for all UI components in Android.

10. a) onStart()
    > onStart() is called when the Activity becomes visible but isn't in focus.

11. a) Contains resource definitions
    > R.java automatically generates IDs for all resources in your app.

12. a) android:text
    > android:text is used to set the text content of a TextView.

13. a) Vertical
    > LinearLayout's default orientation is vertical.

14. a) onStop()
    > onStop() is called when an Activity is no longer visible.

15. c) Managing the navigation history
    > The Activity Stack manages app navigation and back-stack behavior.

16. c) private
    > private restricts access to within the declaring class only.

17. d) All of the above
    > All these components can be used to store different types of data.

18. b) Determines how much space the view should occupy
    > layout_weight defines how remaining space should be distributed.

19. b) strings.xml
    > strings.xml is used to define string resources for internationalization.

20. b) To connect and communicate with Android devices
    > ADB is a versatile command-line tool for debugging and communicating with Android devices.

## Score Interpretation
- 18-20 correct: Excellent understanding of Android fundamentals
- 15-17 correct: Good grasp of the basics
- 12-14 correct: Satisfactory knowledge, but review weak areas
- Below 12: Need to revisit the fundamental concepts
