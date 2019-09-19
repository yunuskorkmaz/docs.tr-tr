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
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="0adea-103">.NET Core CLI ile çalışmaya F# başlama</span><span class="sxs-lookup"><span data-stu-id="0adea-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="0adea-104">Bu makalede, .NET Core CLI ile herhangi bir işletim sisteminde F# (Windows, MacOS veya Linux) kullanmaya nasıl başlacağınız açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0adea-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="0adea-105">Konsol uygulaması tarafından çağrılan bir sınıf kitaplığıyla birden çok projeli bir çözüm oluşturma işlemi ilerler.</span><span class="sxs-lookup"><span data-stu-id="0adea-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0adea-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0adea-106">Prerequisites</span></span>

<span data-ttu-id="0adea-107">Başlamak için en son [.NET Core SDK](https://dotnet.microsoft.com/download)yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="0adea-107">To begin, you must install the latest [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="0adea-108">Bu makalede, bir komut satırı kullanmayı ve tercih edilen bir metin düzenleyicisine nasıl sahip olduğunuzu bildiğiniz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="0adea-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="0adea-109">Henüz kullanmıyorsanız, [Visual Studio Code](get-started-vscode.md) için F#metin düzenleyicisi olarak harika bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="0adea-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="0adea-110">Basit bir çoklu proje çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="0adea-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="0adea-111">Bir komut istemi/terminali açın ve yeni çözüm dosyası `FSNetCore`oluşturmak için [DotNet New](../../core/tools/dotnet-new.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0adea-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```dotnetcli
dotnet new sln -o FSNetCore
```

<span data-ttu-id="0adea-112">Önceki komut çalıştırıldıktan sonra aşağıdaki dizin yapısı üretilir:</span><span class="sxs-lookup"><span data-stu-id="0adea-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="0adea-113">Sınıf kitaplığı yazma</span><span class="sxs-lookup"><span data-stu-id="0adea-113">Write a class library</span></span>

<span data-ttu-id="0adea-114">Dizinleri *Fsnetcore*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0adea-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="0adea-115">Kitaplık adlı **src** klasöründe bir sınıf kitaplığı projesi oluşturun komutunukullanın.`dotnet new`</span><span class="sxs-lookup"><span data-stu-id="0adea-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```dotnetcli
dotnet new classlib -lang F# -o src/Library
```

<span data-ttu-id="0adea-116">Önceki komut çalıştırıldıktan sonra aşağıdaki dizin yapısı üretilir:</span><span class="sxs-lookup"><span data-stu-id="0adea-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="0adea-117">İçeriğini `Library.fs` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0adea-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="0adea-118">Newtonsoft. JSON NuGet paketini kitaplık projesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0adea-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="0adea-119">[DotNet sln Add](../../core/tools/dotnet-sln.md) komutunu kullanarak `FSNetCore` projeyiçözümeekleyin:`Library`</span><span class="sxs-lookup"><span data-stu-id="0adea-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="0adea-120">Projeyi `dotnet build` derlemek için ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0adea-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="0adea-121">Çözümlenmemiş bağımlılıklar derleme sırasında geri yüklenecek.</span><span class="sxs-lookup"><span data-stu-id="0adea-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="0adea-122">Sınıf kitaplığını tüketen bir konsol uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="0adea-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="0adea-123">Komutunu kullanın, uygulama adlı src klasöründe bir konsol uygulaması oluşturun. `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="0adea-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```dotnetcli
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="0adea-124">Önceki komut çalıştırıldıktan sonra aşağıdaki dizin yapısı üretilir:</span><span class="sxs-lookup"><span data-stu-id="0adea-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="0adea-125">`Program.fs` Dosyanın içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0adea-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="0adea-126">`Library` [DotNet Add Reference](../../core/tools/dotnet-add-reference.md)kullanarak projeye bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0adea-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="0adea-127">Şu komutu kullanarak `FSNetCore` `App` projeyi`dotnet sln add` çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0adea-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```dotnetcli
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="0adea-128">NuGet bağımlılıklarını `dotnet restore` geri yükleyin ve projeyi derlemek `dotnet build` için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0adea-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="0adea-129">Dizini `src/App` konsol projesi olarak değiştirin ve bağımsız değişken olarak geçirilen `Hello World` projeyi çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0adea-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="0adea-130">Aşağıdaki sonuçları görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="0adea-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="0adea-131">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0adea-131">Next steps</span></span>

<span data-ttu-id="0adea-132">Daha sonra, farklı F# özellikler hakkında daha fazla bilgi edinmek için [turuna F# ](../tour.md) göz atın.</span><span class="sxs-lookup"><span data-stu-id="0adea-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
