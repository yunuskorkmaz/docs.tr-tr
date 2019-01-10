---
title: Kullanmaya başlama F# komut satırı araçları ile
description: Basit bir çoklu proje çözümü oluşturmayı öğrenin F# .NET Core CLI kullanarak tüm işletim sistemlerinde (Windows, macOs veya Linux).
ms.date: 03/26/2018
ms.openlocfilehash: bc9b223fcf133ffe8b19d5284dcbd3c14a426235
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152105"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Kullanmaya başlama F# .NET Core CLI ile

Bu makalede ele alınmaktadır nasıl ile başlayabilirsiniz F# .NET Core CLI ile tüm işletim sistemlerinde (Windows, macOS veya Linux). Bu, bir konsol uygulaması tarafından çağrılan bir sınıf kitaplığı ile bir çoklu proje çözümü oluşturma sürecinde gider.

## <a name="prerequisites"></a>Önkoşullar

Başlamak için en son yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download/).

Bu makalede, komut satırını kullanın ve tercih edilen bir metin düzenleyicisi bildiğiniz varsayılır. Bu, zaten kullanmıyorsanız, [Visual Studio Code](get-started-vscode.md) için bir metin düzenleyicisi olarak mükemmel bir seçenektir F#.

## <a name="build-a-simple-multi-project-solution"></a>Basit bir çoklu proje çözümü oluşturma

Bir komut istemi/terminal açın ve kullanmak [yeni dotnet](../../core/tools/dotnet-new.md) adlı yeni bir çözüm dosyası oluşturmak için komut `FSNetCore`:

```console
dotnet new sln -o FSNetCore
```

Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını üretilir:

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Bir sınıf kitaplığı yazma

Dizinleri *FSNetCore*.

Kullanım `dotnet new` komutu, bir sınıf kitaplığı projesi oluşturma **src** kitaplığı adlı bir klasör.

```console
dotnet new classlib -lang F# -o src/Library
```

Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını üretilir:

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Öğesinin içeriğini değiştirin `Library.fs` aşağıdaki kod ile:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

Newtonsoft.Json NuGet paketini kitaplığı projeye ekleyin.

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Ekleme `Library` için proje `FSNetCore` çözümünü kullanarak [dotnet sln ekleme](../../core/tools/dotnet-sln.md) komutu:

```console
dotnet sln add src/Library/Library.fsproj
```

Çalıştırma `dotnet build` Projeyi derlemek için. Çözümlenmemiş bağımlılıklar oluşturma sırasında geri yüklenir.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Sınıf kitaplığı kullanan bir konsol uygulaması yazma

Kullanım `dotnet new` komutu, bir konsol uygulamasında oluşturma **src** uygulama adlı bir klasör.

```console
dotnet new console -lang F# -o src/App
```

Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını üretilir:

```console
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

Öğesinin içeriğini değiştirin `Program.fs` dosyasındaki kodu aşağıdaki kodla:

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

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Ekleme `App` için proje `FSNetCore` çözümünü kullanarak `dotnet sln add` komutu:

```console
dotnet sln add src/App/App.fsproj
```

NuGet bağımlılıklarını geri `dotnet restore` çalıştırıp `dotnet build` Projeyi derlemek için.

Dizini `src/App` geçirme projeyi çalıştırın ve konsol projesi `Hello World` bağımsız değişkenler olarak:

```console
cd src/App
dotnet run Hello World
```

Aşağıdaki sonuçları görmeniz gerekir:

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>Sonraki adımlar

Ardından, kullanıma [Turu F# ](../tour.md) farklı hakkında daha fazla bilgi edinmek için F# özellikleri.
