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

→ `z`: apply the intermediate function (partial application of `y`)

If want to do **right** association

```fs
let F x y z = x (y z)
let F x y z = y z |> x  // forward pipe
let F x y z = x <| y z  // backward pipe
```

## Function composition

```txt
val f: T1 -> T2
val g: T2 -> T3
val f>>g: T1 -> T3
```

example

```fs
// f: int -> float
let f (x:int) = float x * 3.0

// g: float -> bool
let g (x:float) = x > 4.0
```

composition

```fs
// h: int -> bool
let h (x: int) =
  let y = f(x)
  g(y)

// compact
let h (x:int) = g ( f(x) )
```

## Using the composition operator in practice

## Composition vs. pipeline

---

```sh
$ dotnet fsi
...
> let f (x:int) = float x * 3.0;;
val f: x: int -> float

> let g (x:float) = x > 4.0 ;;
val g: x: float -> bool

> let h (x:int) =
-     let y = f(x)
-     g(y);;
val h: x: int -> bool

> h 1;;
val it: bool = false

> h 2;;
val it: bool = true
```
