## Overview of the ExecuteCommandLineProgram Library

ExecuteCommandLineProgram is a .NET (4.5) class library for executing command line programs.

The code was copied and slightly modified from [this answer](http://stackoverflow.com/a/4587739/173497) 
to the Stack Overflow question [How to capture Shell command output in C#?](http://stackoverflow.com/questions/4587415/how-to-capture-shell-command-output-in-c).

Parts of the code were adapted from [a comment by "SeemabK" on Scott Hanselman's blog](http://www.hanselman.com/blog/SoManyMistakesForMeToMakeSoLittleTimecapturingStandardErrorAndStandardOutput.aspx)
and other parts are adapted from code written by Daniel Pryden while working at Sonoma Technology, Inc.

Example usage:

  CommandLineProgramProcessResult result =
    CommandLineProgramProcess.RunProgram(
      @"C:\Program Files (x86)\SomeFolder\SomeProgram.exe",        // Path of executable program
      @"C:\Program Files (x86)\SomeFolder\",                // Path of working directory
      String.Format(@"""{0}""", filePathThatNeedsToBeQuotedArgument),    // Command line arguments
      10 * 60 * 1000);                          // Timeout, in milliseconds
      
  string standardError = result.StandardError;
  string standardOutput = result.StandardOutput;
  int exitCode = result.ExitCode;