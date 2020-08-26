---
title: 'Komut satırı araçlarıyla F # ile çalışmaya başlama'
description: 'Herhangi bir işletim sisteminde (Windows, macOS veya Linux) .NET Core CLI kullanarak F # üzerinde basit bir çoklu proje çözümü oluşturmayı öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: e652b66337a3122de8e6bd4d62d86fb6082b759d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811996"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>.NET Core CLI ile F # ile çalışmaya başlama

Bu makalede, .NET Core CLI ile herhangi bir işletim sisteminde (Windows, macOS veya Linux) F # ' ı kullanmaya nasıl başlacağınız ele alınmaktadır. Konsol uygulaması tarafından çağrılan bir sınıf kitaplığıyla birden çok projeli bir çözüm oluşturma işlemi ilerler.

## <a name="prerequisites"></a>Önkoşullar

Başlamak için en son [.NET Core SDK](https://dotnet.microsoft.com/download)yüklemelisiniz.

Bu makalede, bir komut satırı kullanmayı ve tercih edilen bir metin düzenleyicisine nasıl sahip olduğunuzu bildiğiniz varsayılır. Henüz kullanmıyorsanız, F # için metin düzenleyicisi olarak harika bir seçenektir [Visual Studio Code](get-started-vscode.md) .

## <a name="build-a-simple-multi-project-solution"></a>Basit bir çoklu proje çözümü oluşturma

Bir komut istemi/terminali açın ve yeni çözüm dosyası oluşturmak için [DotNet New](../../core/tools/dotnet-new.md) komutunu kullanın `FSNetCore` :

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

`dotnet new`Kitaplık adlı **src** klasöründe bir sınıf kitaplığı projesi oluşturun komutunu kullanın.

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
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
    let json = JsonConvert.SerializeObject(value)
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value json
```

NuGet paketindeki Newtonsoft.Jskitaplık projesine ekleyin.

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

`Library` `FSNetCore` [DotNet sln Add](../../core/tools/dotnet-sln.md) komutunu kullanarak projeyi çözüme ekleyin:

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

`dotnet build`Projeyi derlemek için ' i çalıştırın. Çözümlenmemiş bağımlılıklar derleme sırasında geri yüklenecek.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Sınıf kitaplığını tüketen bir konsol uygulaması yazma

Komutunu kullanın `dotnet new` , uygulama adlı **src** klasöründe bir konsol uygulaması oluşturun.

```dotnetcli
dotnet new console -lang "F#" -o src/App
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

`Program.fs` dosyasının içeriğini aşağıdaki kodla değiştirin:

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    for arg in argv do
        let value = getJsonNetJson arg
        printfn "%s" value

    0 // return an integer exit code
```

`Library` [DotNet Add Reference](../../core/tools/dotnet-add-reference.md)kullanarak projeye bir başvuru ekleyin.

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Şu `App` `FSNetCore` komutu kullanarak projeyi çözüme ekleyin `dotnet sln add` :

```dotnetcli
dotnet sln add src/App/App.fsproj
```

NuGet bağımlılıklarını geri yükleyin `dotnet restore` ve `dotnet build` Projeyi derlemek için çalıştırın.

Dizini `src/App` konsol projesi olarak değiştirin ve `Hello World` bağımsız değişken olarak geçirilen projeyi çalıştırın:

```dotnetcli
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

Sonra, farklı F # özellikleri hakkında daha fazla bilgi edinmek için [f # turuna](../tour.md) göz atın.
