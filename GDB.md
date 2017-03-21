# GDB

## Execution flow:

Start the program:  
`run`  
`run cli args here`


Stop the program being debugged:  
`kill`  
`k`

Go to the next line of code:  
`next`  
`n`

Step inside the line of code:  
`step`  
`s`

Resume execution:  
`continue`  
`c`

## Breakpoints:

Set a breakpoint on line 16:  
`break 16` (for line 16)  
`b 16`

Set a breakpoint at the start of a function:  
`break some_func`  
`b some_func`

Set a conditional breakpoint:  
`break 16 if z > 10`

Add a condition to an existing breakpoint:  
`condition 1 my_var == 7` (where 1 is the breakpoint number)  
`cond 1 my_var == 7`

Enable a breakpoint:  
`enable 1`

Disable a breakpoint:  
`disable 1`

Set a temporary (one time) breakpoint on line 16:  
`tbreak 16`  
`tb 16`

Clear a breakpoint on line 16:  
`clear 16`  
`cl 16`

Get a list of breakpoints:  
`info break`  
`i b`

Set a watchpoint on a variable:  
`watch z`  
`w z`

Set a conditional watchpoint:  
`watch (z > 10)`

Get a list of watchpoints:  
`info watch`  
`i w`

## Inspecting

Printing a value of a variable:  
`print val`  
`p val`

Backtrace:  
`backtrace`  
`bt`


Looking at a stack frame in the callstack:  
`frame 0` (for first frame)  
`frame 1` (for the thing that called that, etc)

Go up to the parent frame in the callstack:  
`up`

Go down the callstack to the next child frame:  
`down`


## Command history

Last command:  
`Ctrl+P`  
`<Up arrow>` if not in tui mode

Next command:  
`Ctrl+N`  
`<Down arrow>` if not in tui mode

Repeat last command:  
`<enter>`

## GDB control

TUI mode via command line:  
`gdb -tui` (via command line)

Enter / exit TUI mode:  
`Ctrl+X+A`

Quit GDB:  
`quit`  
`q`

## Source navigation:

Change region of code used for displaying:  
`list sourcefile.cc:1`  
`l sourcefile.cc:1`
