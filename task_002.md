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

The above structure gets displayed as a list which can be visualised as follows:

```
-> My Layer Group (bolded)
-> My layer 1
-> My layer 2
-> My Layer Group 2 (bolded)
-> My layer 3
```

Now, the GUI allows to drag and drop the above layers to sort them. For example, user can drag "My layer 1" and drop it so it lands as a first element of the "My Layer Group 2" changing the website to look like this:

```
-> My Layer Group (bolded)
-> My layer 2
-> My Layer Group 2 (bolded)
-> My layer 1
-> My layer 3
```

The event that website will generate will look as follows:
`%{"old" => 2, "new" => 4}`

The task is to write an algorithm that will find the "path" to the dragged element:

```
%{layer_group: 0, layer: 0} = find_path(project, data["old"])
```

### Examples

List changed to:

```
-> My Layer Group (bolded)
-> My layer 1
-> My layer 2
-> My layer 3
-> My Layer Group 2 (bolded)
```

Event: `%{"old" => 5, "new" => 4}`

Expected result: `%{layer_group: 1, layer: 0}`

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