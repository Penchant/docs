# MATLAB Style Guidelines
## Naming Conventions
1. variables are camelCase
2. classes are TitleCase
3. constants are ALL_CAPS
4. function names are either functionname or functionName
    1. prefer all lowercase to match the official MathWorks style, but use camelCase when function names are long or hard to read as all lowercase.
5. avoid variable names that shadow function names
    1. examples include
    ```matlab
    alpha, angle, axes, axis, balance, beta, contrast, gamma, image, info, input, length, line, mode, power, rank, run, start, text, type, mean, std, median
    ```

## Variables
1. pre-allocate arrays brefore loops
2. pre-allocate large arrays to increase performance

## Conditionals
1. assign complicated conditionals to a local variable

example:
```matlab
isOutOfBounds = (value >= lowerBound) && (value <= upperBound)
if (isOutOfBounds || isnan(value))
    ...
end
```
2. always include the `otherwise` condition in `switch` statements

## General Style
1. NO TABS, use 4 spaces instead
    1. this is the default in MATLAB's editor
2. limit line lengths to 120 characters
    1. this is a soft limit
    2. indent continued lines
3. split lines at graceful places
    1. split after operators
    2. split after commands
    ```matlab
    x = a + b + c + ...
        d + e;
    plot(x, y, SomeOption1, 'something', ...
         SomeLongOption, 'SomeLongValue');
    ```
4. only use one statement per line; e.g. don't do
```matlab
variable1 = statement1; variable2 = statement2;
```
5. separate code blocks with MATLAB's section delimiter: `$$`
    1. this makes it easier to produce html documentation with MATLAB
6. ignore function outputs using `~`
```matlab
[Q,~] = qr(A)
```

## File Rules
1. the filename is the same as the function name
2. the file/function header comments should be declared at the top of the file, above the function line
3. at the top of scripts, clear the workspace and close figures
```matlab
clear all;
close all;
```

## Comments
1. prefer [MATLAB markup](https://www.mathworks.com/help/matlab/matlab_prog/marking-up-matlab-comments-for-publishing.html) for comments
1. prefer full-line comments over end-of-line comments
    1. end-of-line comments are harder to maintain
    
### Function Header
1. write the name of the function with a brief description
2. show how the function is called
3. if necessary, write a detailed description of what the function does
4. describe input parameters and return values
5. put a blank space between the help header and the copyright/license
    1. this stops the copyright and license from showing up in the help text
6. license: MIT
7. copyright: Audio Logic Inc

The above also applies to scripts, with the exception that there are no inputs or return values to describe. 

example:
```matlab
% testFunction A dummy test function
%
% [output1, output2] = testFunction(input1, input2)
%
% This test function performs operation foo and returns objects of type bar
%
% Parameters
% ----------
%   input1 : the first input
%   input2 : the second input
%
% Returns
% -------
%   output1 : the first output
%   output2 : the second output

% Copyright 2020 Audio Logic Inc
%
% THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
% INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
% PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE
% FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
% ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
%
% DeveloperName
% Audio Logic Inc
% 985 Technology Blvd
% Bozeman, MT 59718
% openspeech@flatearthinc.com
```
# References
[Matlab Style Book](http://www.datatool.com/downloads/MatlabStyle2%20book.pdf)

[The Elements of Matlab Style](https://www.amazon.com/Elements-Matlab-Style-Richard-Johnson/dp/0521732581)
