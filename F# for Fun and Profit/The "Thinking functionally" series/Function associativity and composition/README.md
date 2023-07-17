# Function associativity and composition

## Function associativity

```fs
let F x y z = x y z
```

mean

```fs
// left associative
let F x y z = (x y) z
```

`x`: two parameter function
→ `z`: apply the intermediate function(partial application of `y`)

If want to do **right** association

```fs
let F x y z = x (y z)
let F x y z = y z |> x  // forward pipe
let F x y z = x <| y z  // backward pipe
```

## Function composition



## Using the composition operator in practice

## Composition vs. pipeline
