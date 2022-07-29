## Readme and Documentation
The readme .etc should be eventually written in markaround and converted to markdown for github.

## Syntax
While syntax is customisable, the defaults should:
1. First and foremost, follows the markdown defaults. A standard markdown file should compile to itself when run through markaround (so long as it's not doing some funky stuff with its characters).
2. Secondly, the syntax should look decent. Customising syntax should not be a necessity.

### Only the defintion is define by default
Have nothing aside from the method of definition accesible without some sort of config/definition file.
Then so customising is not a necessity, provide a default config.

#### Problems
- What happens if the default config is not found?
I assume the program would have to interpret the file as a simple markdown file then.
- How is the config read?
Some (not necessarily incompatible) options:
`markaround -C definitions.ma file.ma` the exact syntax of `-C` vs `-S` or other alternatives is somewhat trivial.
`cat definitions.ma file.ma | markaround`
`markaround definitions.ma file.ma` markaround could concatenate for you?
`markaround file.ma` with `defintions.ma` automatically sourced from `$XDG_CONFIG_HOME/markaround`.
