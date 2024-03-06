# Task 2

## Find out which layer to move

### Description

You are working with the below structure:

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
            },
            %Layer{
                name: "My layer 3",
                visibility: 0.2
            }
          ]
        },
        %LayerGroup{
          name: "My Layer Group 2",
          layers: [
            %Layer{
                name: "My layer 4",
                visibility: 1.0
            }
            %Layer{
                name: "My layer 5",
                visibility: 0.67
            }
            %Layer{
                name: "My layer 6",
                visibility: 0.9
            }
          ]
        }
    ]
}
```

The above structure gets displayed as a list which can be visualised as follows:

```
-> My Layer Group (bolded)
-> My layer 1
-> My layer 2
-> My layer 3
-> My Layer Group 2 (bolded)
-> My layer 4
-> My layer 5
-> My layer 6
```

Now, the GUI allows to drag and drop the above layers to sort them. For example, user can drag "My layer 2" and drop it so it lands as a second element of the "My Layer Group 2" changing the website to look like this:

```
-> My Layer Group (bolded)
-> My layer 1
-> My layer 3
-> My Layer Group 2 (bolded)
-> My layer 4
-> My layer 2
-> My layer 5
-> My layer 6
```

The event that website will generate will look as follows:
`%{"old" => 3, "new" => 6}`

The task is to write an algorithm that will find the "path" to the dragged element:

```
%{layer_group_index: 0, layer_index: 1} = find_path(project, data["old"])
```

And make the same algorithm work for drop position:
```
%{layer_group_index: 1, layer_index: 1} = find_path(project, data["new"])
```

Bonus points for a "wrapper" function that will accept `old_position` and `new_position` and return a tuple with two answers (maps with `layer_group_index` and `layer_index` keys).


### Examples

List changed to:

```
-> My Layer Group (bolded)
-> My layer 1
-> My layer 2
-> My layer 3
-> My layer 4
-> My Layer Group 2 (bolded)
-> My layer 5
-> My layer 6
```

Event: `%{"old" => 6, "new" => 5}`

Expected result: `%{layer_group_index: 1, layer_index: 0}`

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