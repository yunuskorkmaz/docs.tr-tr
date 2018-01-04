---
title: "F # ile komut satırı araçları ile çalışmaya başlama"
description: "F # herhangi bir işletim sistemi üzerinde (Windows, MacOS, Linux) kullanmayı ile platformlar arası .NET Core CLI öğrenin."
keywords: "Visual f #, f #, işlev, .NET, .NET Core programlama"
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: 4820a8a306bd478429b497a8b7c70ff170c1c655
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>F # .NET Core CLI ile kullanmaya başlama

Bu makalede ele alınmaktadır nasıl, herhangi bir işletim sistemi üzerinde (Windows, macOS veya Linux) F # .NET Core CLI ile kullanarak başlayabiliriz. Bir konsol uygulaması tarafından çağrılan bir sınıf kitaplığı ile birden çok proje çözümü oluşturma üzerinden geçer.

## <a name="prerequisites"></a>Önkoşullar

Başlamak için yüklemelisiniz [.NET Core SDK 1.0 veya üstü](https://dot.net/core). Yan yana yüklemeler desteklediği .NET Core SDK ' nın önceki bir sürümünü kaldırmak için gerek yoktur.

Bu makalede, nasıl bir komut satırını kullanın ve tercih edilen bir metin Düzenleyicisi'ni bildiğinizi varsayar. Zaten, kullanmazsanız [Visual Studio Code](https://code.visualstudio.com) olarak bir metin düzenleyicisi F # için kullanışlı bir seçenektir. IntelliSense, daha iyi söz dizimi vurgulama ve diğerleri gibi harika özellikler almak için indirebilirsiniz [Ionide uzantısı](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).

## <a name="building-a-simple-multi-project-solution"></a>Basit bir birden çok proje çözümü oluşturma

Bir komut istemi/Terminali açın ve kullanmak `dotnet new` adlı yeni çözüm dosyasını oluşturmak için komutu `FSNetCore`:

```
dotnet new sln -o FSNetCore
```

Ayarlayamadı dizin yapısını komutu Tamamlanıyor sonucunda oluşturulur:

```
FSNetCore
    ├── FSNetCore.sln
```

Değiştirme dizinleri *FSNetCore* ve projeleri çözüm klasörüne eklemeye başlayın.
 
### <a name="writing-a-class-library"></a>Bir sınıf kitaplığı yazma

Kullanım `dotnet new` komutu, bir sınıf kitaplığı proje oluştur **src** kitaplığı adlı klasörü. 

```bash
dotnet new lib -lang F# -o src/Library 
```

Aşağıdaki dizin yapısını komutu Tamamlanıyor sonucunda oluşturulur:

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Değiştir `Library.fs` aşağıdaki:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

Newtonsoft.Json NuGet paketi kitaplığı projeye ekleyin.

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Ekleme `Library` için proje `FSNetCore` çözümünü kullanarak `dotnet sln add` komutu:

```bash
dotnet sln add src/Library/Library.fsproj
```

NuGet bağımlılıkları geri `dotnet restore` ([nota bakın](#dotnet-restore-note)) çalıştırıp `dotnet build` Projeyi derlemek için.

### <a name="writing-a-console-application-which-consumes-the-class-library"></a>Sınıf kitaplığı tüketir bir konsol uygulaması yazma

Kullanım `dotnet new` komutu, bir konsol uygulaması oluşturmak **src** uygulama adlı klasörü. 

```bash
dotnet new console -lang F# -o src/App 
```

Aşağıdaki dizin yapısını komutu Tamamlanıyor sonucunda oluşturulur:

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Değişiklik `Program.fs` için:

```fsharp
open System
open Library

[<EntryPoint>]
let main argv = 
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    argv
    |> Array.map getJsonNetJson
    |> Array.iter (printfn "%s")

    0 // return an integer exit code
```

Bir başvuru ekleyin `Library` kullanarak proje `dotnet add reference`.

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Ekleme `App` için proje `FSNetCore` çözümünü kullanarak `dotnet sln add` komutu:

```bash
dotnet sln add src/App/App.fsproj
```

NuGet bağımlılıkları geri `dotnet restore` ([nota bakın](#dotnet-restore-note)) çalıştırıp `dotnet build` Projeyi derlemek için.

Değişiklik dizinine `src/App` konsol projesi ve geçirme projeyi `Hello World` bağımsız değişken olarak.

```bash
cd src/App
dotnet run Hello World
``` 

Aşağıdaki sonuçları görmeniz gerekir:

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
