---
title: Komut satırı araçlarıyla F# çalışmaya başlama
description: Herhangi bir işletim sisteminde (Windows, macOs veya Linux F# ) .NET Core CLI kullanarak basit bir çoklu proje çözümü oluşturmayı öğrenin.
ms.date: 03/26/2018
ms.openlocfilehash: f9177e653273e5a2191407c4fb22343ded11fece
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117926"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>.NET Core CLI ile çalışmaya F# başlama

Bu makalede, .NET Core CLI ile herhangi bir işletim sisteminde F# (Windows, MacOS veya Linux) kullanmaya nasıl başlacağınız açıklanmaktadır. Konsol uygulaması tarafından çağrılan bir sınıf kitaplığıyla birden çok projeli bir çözüm oluşturma işlemi ilerler.

## <a name="prerequisites"></a>Önkoşullar

Başlamak için en son [.NET Core SDK](https://dotnet.microsoft.com/download)yüklemelisiniz.

Bu makalede, bir komut satırı kullanmayı ve tercih edilen bir metin düzenleyicisine nasıl sahip olduğunuzu bildiğiniz varsayılır. Henüz kullanmıyorsanız, [Visual Studio Code](get-started-vscode.md) için F#metin düzenleyicisi olarak harika bir seçenektir.

## <a name="build-a-simple-multi-project-solution"></a>Basit bir çoklu proje çözümü oluşturma

Bir komut istemi/terminali açın ve yeni çözüm dosyası `FSNetCore`oluşturmak için [DotNet New](../../core/tools/dotnet-new.md) komutunu kullanın:

```dotnetcli
dotnet new sln -o FSNetCore
```

Önceki komut çalıştırıldıktan sonra aşağıdaki dizin yapısı üretilir:

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Sınıf kitaplığı yazma

Dizinleri *Fsnetcore*olarak değiştirin.

Kitaplık adlı **src** klasöründe bir sınıf kitaplığı projesi oluşturun komutunukullanın.`dotnet new`

```dotnetcli
dotnet new classlib -lang F# -o src/Library
```

Önceki komut çalıştırıldıktan sonra aşağıdaki dizin yapısı üretilir:

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

İçeriğini `Library.fs` aşağıdaki kodla değiştirin:

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

Newtonsoft. JSON NuGet paketini kitaplık projesine ekleyin.

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

[DotNet sln Add](../../core/tools/dotnet-sln.md) komutunu kullanarak `FSNetCore` projeyiçözümeekleyin:`Library`

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

Projeyi `dotnet build` derlemek için ' i çalıştırın. Çözümlenmemiş bağımlılıklar derleme sırasında geri yüklenecek.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Sınıf kitaplığını tüketen bir konsol uygulaması yazma

Komutunu kullanın, uygulama adlı src klasöründe bir konsol uygulaması oluşturun. `dotnet new`

```dotnetcli
dotnet new console -lang F# -o src/App
```

Önceki komut çalıştırıldıktan sonra aşağıdaki dizin yapısı üretilir:

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

`Program.fs` Dosyanın içeriğini aşağıdaki kodla değiştirin:

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

`Library` [DotNet Add Reference](../../core/tools/dotnet-add-reference.md)kullanarak projeye bir başvuru ekleyin.

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Şu komutu kullanarak `FSNetCore` `App` projeyi`dotnet sln add` çözüme ekleyin:

```dotnetcli
dotnet sln add src/App/App.fsproj
```

NuGet bağımlılıklarını `dotnet restore` geri yükleyin ve projeyi derlemek `dotnet build` için çalıştırın.

Dizini `src/App` konsol projesi olarak değiştirin ve bağımsız değişken olarak geçirilen `Hello World` projeyi çalıştırın:

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

Daha sonra, farklı F# özellikler hakkında daha fazla bilgi edinmek için [turuna F# ](../tour.md) göz atın.
