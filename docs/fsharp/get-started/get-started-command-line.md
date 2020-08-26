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
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="74fd4-103">.NET Core CLI ile F # ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="74fd4-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="74fd4-104">Bu makalede, .NET Core CLI ile herhangi bir işletim sisteminde (Windows, macOS veya Linux) F # ' ı kullanmaya nasıl başlacağınız ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="74fd4-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="74fd4-105">Konsol uygulaması tarafından çağrılan bir sınıf kitaplığıyla birden çok projeli bir çözüm oluşturma işlemi ilerler.</span><span class="sxs-lookup"><span data-stu-id="74fd4-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74fd4-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="74fd4-106">Prerequisites</span></span>

<span data-ttu-id="74fd4-107">Başlamak için en son [.NET Core SDK](https://dotnet.microsoft.com/download)yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="74fd4-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="74fd4-108">Bu makalede, bir komut satırı kullanmayı ve tercih edilen bir metin düzenleyicisine nasıl sahip olduğunuzu bildiğiniz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="74fd4-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="74fd4-109">Henüz kullanmıyorsanız, F # için metin düzenleyicisi olarak harika bir seçenektir [Visual Studio Code](get-started-vscode.md) .</span><span class="sxs-lookup"><span data-stu-id="74fd4-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="74fd4-110">Basit bir çoklu proje çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="74fd4-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="74fd4-111">Bir komut istemi/terminali açın ve yeni çözüm dosyası oluşturmak için [DotNet New](../../core/tools/dotnet-new.md) komutunu kullanın `FSNetCore` :</span><span class="sxs-lookup"><span data-stu-id="74fd4-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```dotnetcli
dotnet new sln -o FSNetCore
```

<span data-ttu-id="74fd4-112">Önceki komut çalıştırıldıktan sonra aşağıdaki dizin yapısı üretilir:</span><span class="sxs-lookup"><span data-stu-id="74fd4-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="74fd4-113">Sınıf kitaplığı yazma</span><span class="sxs-lookup"><span data-stu-id="74fd4-113">Write a class library</span></span>

<span data-ttu-id="74fd4-114">Dizinleri *Fsnetcore*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="74fd4-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="74fd4-115">`dotnet new`Kitaplık adlı **src** klasöründe bir sınıf kitaplığı projesi oluşturun komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="74fd4-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```dotnetcli
dotnet new classlib -lang "F#" -o src/Library
```

<span data-ttu-id="74fd4-116">Önceki komut çalıştırıldıktan sonra aşağıdaki dizin yapısı üretilir:</span><span class="sxs-lookup"><span data-stu-id="74fd4-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="74fd4-117">İçeriğini `Library.fs` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="74fd4-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    let json = JsonConvert.SerializeObject(value)
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value json
```

<span data-ttu-id="74fd4-118">NuGet paketindeki Newtonsoft.Jskitaplık projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74fd4-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="74fd4-119">`Library` `FSNetCore` [DotNet sln Add](../../core/tools/dotnet-sln.md) komutunu kullanarak projeyi çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="74fd4-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="74fd4-120">`dotnet build`Projeyi derlemek için ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="74fd4-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="74fd4-121">Çözümlenmemiş bağımlılıklar derleme sırasında geri yüklenecek.</span><span class="sxs-lookup"><span data-stu-id="74fd4-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="74fd4-122">Sınıf kitaplığını tüketen bir konsol uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="74fd4-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="74fd4-123">Komutunu kullanın `dotnet new` , uygulama adlı **src** klasöründe bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="74fd4-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```dotnetcli
dotnet new console -lang "F#" -o src/App
```

<span data-ttu-id="74fd4-124">Önceki komut çalıştırıldıktan sonra aşağıdaki dizin yapısı üretilir:</span><span class="sxs-lookup"><span data-stu-id="74fd4-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="74fd4-125">`Program.fs` dosyasının içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="74fd4-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="74fd4-126">`Library` [DotNet Add Reference](../../core/tools/dotnet-add-reference.md)kullanarak projeye bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74fd4-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="74fd4-127">Şu `App` `FSNetCore` komutu kullanarak projeyi çözüme ekleyin `dotnet sln add` :</span><span class="sxs-lookup"><span data-stu-id="74fd4-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```dotnetcli
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="74fd4-128">NuGet bağımlılıklarını geri yükleyin `dotnet restore` ve `dotnet build` Projeyi derlemek için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="74fd4-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="74fd4-129">Dizini `src/App` konsol projesi olarak değiştirin ve `Hello World` bağımsız değişken olarak geçirilen projeyi çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="74fd4-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```dotnetcli
cd src/App
dotnet run Hello World
```

<span data-ttu-id="74fd4-130">Aşağıdaki sonuçları görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="74fd4-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="74fd4-131">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="74fd4-131">Next steps</span></span>

<span data-ttu-id="74fd4-132">Sonra, farklı F # özellikleri hakkında daha fazla bilgi edinmek için [f # turuna](../tour.md) göz atın.</span><span class="sxs-lookup"><span data-stu-id="74fd4-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
