# TeXstudio_ProgressChecker

A TeXstudio macro that gives you a rough idea as to where in a LaTeX document's bodt your current cursor position is.

## Brief Overview

In short, this macro first stores the current cursor position (column, row) in variables, as well as the content of the line on which the cursor is currently located. By design, this macro only works if the user is on a line with some kind of text, and which does not contain a `\begin{}` or `\end{}` command, for reasons that will be detailed below.

Thereafter, the macro finds the line positions of the `\begin{document}` and `\end{document}` commands, and also stores these in variables. Thereafter, it runs a loop from the former line to the latter, checking whether lines contain only comments. If not, it adds to a counter of the number of lines. Thereafter, it calculuates the rough position by determining the relative position of the user by comparing the number of lines before and after the relative cursor position (which is also determined during the loop) before giving the user values for how many lines came before the position, how many come after it, and the percentage values relative to the number of lines in the body.

Finally, the macro searches for the line that the user was on, and returns the user to the exact cursor position that they were previously at, meaning that the macro should generally not interrupt the workflow by requiring the user to re-find their original position.

It's a bit hard to gauge how accurate the calculations actually are for what I was trying to achieve with this, but even if not perfect, they're likely close enough to accurate that inaccuracies probably shouldn't have any impact on the user experience.
