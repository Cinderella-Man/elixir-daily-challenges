# Task 1

## Move layer to another group

### Description

You are given a structure as one below(structs are at the bottom of this readme):

```
project = %Project{
    name: "Blah",
    layer_groups: [
        %LayerGroup{
          name: "My Layer Group",
          layers: [
            %Layer{
                name: "My layer 1",
                visibility: 1.0
            },
            %Layer{
                name: "My layer 2",
                visibility: 0.5
            }
          ]
        },
        %LayerGroup{
          name: "My Layer Group 2",
          layers: [
            %Layer{
                name: "My layer 3",
                visibility: 1.0
            }
          ]
        }
    ]
}
```

Your task is to move `%Layer{name: "My Layer 1"...}` from `%LayerGroup{name: "My Layer Group 1"...}` to `%LayerGroup{name: "My Layer Group 2"...}` as showed below:

```
project = %Project{
    name: "Blah",
    layer_groups: [
        %LayerGroup{
          name: "My Layer Group",
          layers: [
             %Layer{
                name: "My layer 2",
                visibility: 0.5
            }
          ]
        },
        %LayerGroup{
          name: "My Layer Group 2",
          layers: [
            %Layer{
                name: "My layer 1",
                visibility: 1.0
            },
            %Layer{
                name: "My layer 3",
                visibility: 1.0
            }
          ]
        }
    ]
}
```

### Structs

Useful to get this running as soon as possible:

```
defmodule Project do
  defstruct [:name, layer_groups: []]
end

defmodule LayerGroup do
  defstruct [:name, layers: []]
end

defmodule Layer do
  defstruct [:name, :visibility]
end
```

### How to run:

Create a new project:

```
$ mix new task1
```

Open file `task1.ex` inside `task1/lib` directory and paste the structs above the `hello/0` function and the input struct inside, then try your best to write an easy to understand/compact implementation inside this module.

You can then test it by running:

```
$ iex -S mix
...
iex(1)> Task1.hello()
```

Bonus points for adding unit tests!