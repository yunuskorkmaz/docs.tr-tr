---
title: 'F # ile komut satırı araçları ile çalışmaya başlama'
description: 'F # .NET Core CLI kullanarak bir işletim sistemine (Windows, macOs veya Linux) üzerinde bir basit birden çok proje çözümü oluşturmayı öğrenin.'
ms.date: 03/26/2018
ms.openlocfilehash: 35ec2313742a0b14c92f3de2662a16aff389b214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>F # .NET Core CLI ile kullanmaya başlama

Bu makalede, nasıl, F # ile .NET Core CLI ile herhangi bir işletim sistemine (Windows, macOS veya Linux) kullanmaya başlayabilir yer almaktadır. Bu, bir konsol uygulaması tarafından çağrılan bir sınıf kitaplığı ile birden çok proje çözümü oluşturma üzerinden gider.

## <a name="prerequisites"></a>Önkoşullar

Başlamak için yüklemelisiniz [.NET Core SDK 1.0 veya üstü](https://www.microsoft.com/net/download/). Yan yana yüklemeler desteklediği .NET Core SDK ' nın önceki bir sürümünü kaldırmak için gerek yoktur.

Bu makalede, nasıl bir komut satırını kullanın ve tercih edilen bir metin Düzenleyicisi'ni bildiğinizi varsayar. Zaten, kullanmazsanız [Visual Studio Code](https://code.visualstudio.com) olarak bir metin düzenleyicisi F # için kullanışlı bir seçenektir. IntelliSense, daha iyi söz dizimi vurgulama ve diğerleri gibi harika özellikler almak için indirebilirsiniz [Ionide uzantısı](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).

## <a name="build-a-simple-multi-project-solution"></a>Basit bir birden çok proje çözümü oluşturma

Bir komut istemi/Terminali açın ve kullanmak [dotnet yeni](../../core/tools/dotnet-new.md) adlı yeni çözüm dosyasını oluşturmak için komutu `FSNetCore`:

```
dotnet new sln -o FSNetCore
```

Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını oluşturulur:

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Bir sınıf kitaplığı yazma

Değiştirme dizinleri *FSNetCore*.

Kullanım `dotnet new` komutu, bir sınıf kitaplığı projesi oluştur **src** kitaplığı adlı klasörü.

```
dotnet new lib -lang F# -o src/Library
```

Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını oluşturulur:

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Değiştir `Library.fs` aşağıdaki kod ile:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

Newtonsoft.Json NuGet paketi kitaplığı projeye ekleyin.

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Ekleme `Library` için proje `FSNetCore` çözümünü kullanarak [dotnet sln ekleme](../../core/tools/dotnet-sln.md) komutu:

```
dotnet sln add src/Library/Library.fsproj
```

Kullanarak NuGet bağımlılıkları geri `dotnet restore` komutu ([nota bakın](#dotnet-restore-note)) çalıştırıp `dotnet build` Projeyi derlemek için.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Sınıf kitaplığı tüketen bir konsol uygulaması yazma

Kullanım `dotnet new` komutu, bir konsol uygulaması oluşturun **src** uygulama adlı klasörü.

```
dotnet new console -lang F# -o src/App
```

Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını oluşturulur:

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

Değiştir `Program.fs` aşağıdaki kod ile dosya:

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

Bir başvuru ekleyin `Library` kullanarak proje [dotnet Başvuru Ekle](../../core/tools/dotnet-add-reference.md).

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Ekleme `App` için proje `FSNetCore` çözümünü kullanarak `dotnet sln add` komutu:

```
dotnet sln add src/App/App.fsproj
```

NuGet bağımlılıkları geri `dotnet restore` ([nota bakın](#dotnet-restore-note)) çalıştırıp `dotnet build` Projeyi derlemek için.

Değişiklik dizinine `src/App` konsol projesi ve geçirme projeyi `Hello World` bağımsız değişken olarak:

```
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