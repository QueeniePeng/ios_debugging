# ios_debugging

Debugging Lingo
--------------------------------------------------------------------------------
When solving (and sharing) bugs, it is important to know the right lingo!
Being able to describe your bug precisely is key
(especially when talking to developers)!

logic error:
a bug in a program that causes it to operate incorrectly, but not to terminate
abnormally (or crash)runtime errors: issues that occur while your application is
running—these can be logic errors or errors that cause your application to crash

software bug:
an error, flaw, failure, or fault in a computer program or system that causes
it to produce an incorrect or unexpected result, or to behave in unintended ways

static (or compilation) errors:
issues identified by the compiler that must be fixed prior to running your
application

warning:
issues that might cause problems or have unintended side-effects on your running
application


Debugging Process
--------------------------------------------------------------------------------

4.Try a fix ------------------
^                            |
3.Form a Hypothesis          |
^                            |
2.Gather debug information   |
^                            |
1.Reproduce the problem <- ----


Debugging Tool
--------------------------------------------------------------------------------
Print Debugging: CustomStringConvertible, CustomStringDebugConvertible
BreakPoint Debugging
Visual Debugging


Helpful Link:
--------------------------------------------------------------------------------
Apple: 2012 WWDC Sessions (see "Debugging in Xcode")

GDB and LLDB Command Examples:
https://developer.apple.com/library/content/documentation/IDEs/Conceptual/gdb_to_lldb_transition_guide/document/lldb-command-examples.html#//apple_ref/doc/uid/TP40012917-CH3-SW1


Pro Trip: "Property" Breakpoints
--------------------------------------------------------------------------------
If you set a breakpoint on a line of code containing a property definition,
then your app will pause anytime that property’s value is changing and display
a stack trace of the function calls that ultimately caused the change.

Press Space on Debug area left panel variables for a quick look


Common LLDB Command
--------------------------------------------------------------------------------
frame variable/fr v: shows all the arguments and local variable in current scope
help: shows all command
(command) help: shows subcommands under (command)
help (command) (subcommand): show help on particular subcommand
frame select (number): shows different frame in debug navigator
expression/expr print(""): expression for functions
po (object): shows printable description
expr unsafeBitCast: convert the raw address into an object that we can interact
with, but not able to access its properties & values


Xcode Debugging Hotkeys
--------------------------------------------------------------------------------
Here is a listing of Xcode hotkeys (related to debugging) we mentioned in this course.
Let us know if we missed any!

Show Navigator (⌘+0)
Show Debug Navigator (⌘+6)
Show Breakpoint Navigator (⌘+7)
Show Debug Area (⌘+Shift+Y)
Open Documentation (⌘+Shift+0)
Step Over (F6)
Step Into (F7)
Step Out (F8)
Continue (⌘+Ctrl+Y)
Build (⌘+B)
Run (⌘+R)
Activate/Deactivate Breakpoint (⌘+Y)
Quick Search (⌘+Shift+O)


Quiz Answer
--------------------------------------------------------------------------------
(lldb) breakpoint set --file BugFactory.swift --line 26
- Set a breakpoint in file BugFactory.swift at line 26.

(lldb) breakpoint set --selector viewDidLoad
- Set a breakpoint at all Objective-C methods whose selector is viewDidLoad.

(lldb) breakpoint list
List all breakpoints.

(lldb) thread backtrace all
Show the stack backtraces for all threads.

(lldb) breakpoint disable 1
disabled breakpoint at 1


Fixing the visual bugs
--------------------------------------------------------------------------------
1: Visual shows all bugs on the top left of the view, meaning bugs been added correctly, but wrong position
2: checkout moveBugsAnimation()
3: set breakpoint at line 52 bug.bounds
4: value of bug.bounds always set at
▿origin : CGPoint
    - x : -0.3333333333333286
    - y : 239.66666666666669
  ▿ size : CGSize
    - width : 128.0
    - height : 128.0
5: change bounds to frame to solve the problem

