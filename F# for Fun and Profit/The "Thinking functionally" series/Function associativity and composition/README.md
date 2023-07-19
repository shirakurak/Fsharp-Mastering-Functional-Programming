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

example:

```fs
// f: int -> float
let f (x:int) = float x * 3.0

// g: float -> bool
let g (x:float) = x > 4.0
```

composition:

```fs
// h: int -> bool
let h (x: int) =
  let y = f(x)
  g(y)

// compact
let h (x:int) = g ( f(x) )
```

can define:

```fs
// compose: ('a -> 'b) -> ('b -> 'c) -> 'a -> 'c
let compose f g x = g ( f(x) )

// >>
let (>>) f g x = g ( f(x) )
```

example:

```fs
let add1 x = x + 1
let times2 x = x * 2

let add1Times2 x = (>>) add1 times2 x

// old style
let add1Times2 x = times2(add1 x)

// new style
let add1Times2 = add1 >> times2
```

Note:

- not be possible in a non-functional programming
- every function has one input and one output, so composition is possible

## Using the composition operator in practice

## Composition vs. pipeline

---
practice

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

> let add1 x = x + 1;;
val add1: x: int -> int

> let times2 x = x * 2;;
val times2: x: int -> int

> let add1Times2 x = (>>) add1 times2 x;;
val add1Times2: x: int -> int

> add1Times2 3;;
val it: int = 8

> let add n x = n + x;;
val add: n: int -> x: int -> int

> let times n x = x * n;;
val times: n: int -> x: int -> int

> let add5Times3 = add 5 >> times 3;;
val add5Times3: (int -> int)

> add5Times3 1;;
val it: int = 18

> let twice f = f >> f;;
val twice: f: ('a -> 'a) -> ('a -> 'a)
```
