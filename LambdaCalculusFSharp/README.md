# メモ

## これはなに

[LambdaCalculusFSharp](https://github.com/WhiteBlackGoose/LambdaCalculusFSharp/tree/main)について、コードリーディングしながら取ったメモ。

文法事項というより、どういうことを考えるのがいいのか、ということも含めて知りたい。

## ディレクトリ構成

```sh
tree .
.
├── LICENSE
├── LambdaCalculus
│   ├── LambdaCalculus
│   │   ├── Atoms.fs
│   │   ├── LambdaCalculus.fsproj
│   │   ├── Output.fs
│   │   ├── Parsing
│   │   │   ├── Parsing.fs
│   │   │   └── TextParsing.fs
│   │   ├── ToCSharp.fs
│   │   └── Utils.fs
│   ├── LambdaCalculus.sln
│   ├── LambdaCalculusConsole
│   │   ├── LambdaCalculusConsole.fsproj
│   │   └── Program.fs
│   ├── LambdaCalculusTests
│   │   ├── AlphaEquality.fs
│   │   ├── BetaReduction.fs
│   │   ├── EtaReduction.fs
│   │   ├── LambdaCalculusTests.fsproj
│   │   ├── Parsing.fs
│   │   ├── Program.fs
│   │   └── Substitution.fs
│   └── LambdaCalculusWeb
│       ├── App.razor
│       ├── LambdaCalculusWeb.csproj
│       ├── Pages
│       │   └── Index.razor
│       ├── Program.cs
│       ├── Properties
│       │   └── launchSettings.json
│       ├── Shared
│       │   ├── MainLayout.razor
│       │   └── MainLayout.razor.css
│       ├── _Imports.razor
│       └── wwwroot
│           ├── favicon.ico
│           ├── icon-192.png
│           └── index.html
└── README.md

11 directories, 30 files
```

## README.md

> The library serves no production purpose and made exclusively out of academic interest. It has a web app made for demonstration.

痺れた。

## LambdaCalculusConsole

`LambdaCalculus/LambdaCalculusConsole/Program.fs`

```fs
open System
open LambdaCalculus.Utils
open LambdaCalculus.Parsing
open LambdaCalculus.Output
open LambdaCalculus.Atoms
open LambdaCalculus.ToCSharp
...
```

`LambdaCalculus/LambdaCalculus`配下を使用している。






`LambdaCalculus/LambdaCalculus/Parsing/Parsing.fs`

- `parse`
  - パースする
  - 文字列の置き換え（λや空白）
