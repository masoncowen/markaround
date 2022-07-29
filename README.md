# markaround
Extension for markaround designed for compilation to both LaTeX and HTML
Very much a personal project.

Currently no code, here's some ideas I'd like to implement.
Very much just a scratchpad of ideas at the moment.

## Compilation and Written variables.
This will involve a vim-plugin or perl filter of some kind.
The concept for written variables is just syntactic sugar for arduous tasks that Markdown/Markaround can do already.
Example:
- [[Link]] could be syntactic sugar for [Link](Link) (Whether this is a written variable or just syntactic sugar is questionable).
- $var = hello (not the syntax I'd like), could be a temporary quickhand for the writing session.
- `$var, the value of \$var when this was written was $var.` would be saved as `hello, the value of \$var when this was written was hello.`, and would compile to 'hello, the value of $var when this was written was hello.'
- Should definitions of written variables be deleted after use?

## Imports
This will import the contents of another file.
```markaround
% Here we have imported a file containing macros
[@Macros.ma]
[@File1.md]

```

## Definitions
Markaround will by default be a superset of markdown.
But the ability to change the syntax should be available.
It's unlikely that you should be able to change the definition syntax itself so it should be reletively verbose so it doesn't take up desired characters.
Though you should be able to define a character as an alias for definition.
Definition should probably come in two forms of Written and Compilation?
You wouldn't want inconsistent syntax in a file while writing but there is some use in having temporary syntax.
MC takes 2 arguments space-separated, first is desired syntax, second is output, all spaces after first two (immediately after \MC and after the syntax) are considered part of the output.
```markaround
\MarkaroundDefineAtCompilation $\1 \MarkaroundDefineAtCompilation \1
$ *\1* **\1**
$ __\1__ _\1_
```
This changes the compilation command to be a `$`, the syntax is then used to define `*word*` as `**word**` (or **word**).
This is just a personal pet peeve with markdown.
- Why do we need two different ways for italics and bolds?
- Why is the method for bold both double characters rather than single?

The `\1` is the first argument, `\1` to `\0` are reserved (in the context of definition) as the arguments to be passed for the desired outcome.
Since a space is assumed to be the end of the syntax definition, and it would be unclear where one argument ends a space will be expected between two arguments next to each other.
e.g. `$ &\1\2 \1 and \2` will match `&fish chips` to `fish and chips` while `&fishchips` would be `fishchips and `.
If a space is desired otherwise `\ ` is usable.
