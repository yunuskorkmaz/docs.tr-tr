---
title: Kullanmaya başlama F# komut satırı araçları ile
description: Basit bir çoklu proje çözümü oluşturmayı öğrenin F# .NET Core CLI kullanarak tüm işletim sistemlerinde (Windows, macOs veya Linux).
ms.date: 03/26/2018
ms.openlocfilehash: bc9b223fcf133ffe8b19d5284dcbd3c14a426235
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938703"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="5e9b9-103">Kullanmaya başlama F# .NET Core CLI ile</span><span class="sxs-lookup"><span data-stu-id="5e9b9-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="5e9b9-104">Bu makalede ele alınmaktadır nasıl ile başlayabilirsiniz F# .NET Core CLI ile tüm işletim sistemlerinde (Windows, macOS veya Linux).</span><span class="sxs-lookup"><span data-stu-id="5e9b9-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="5e9b9-105">Bu, bir konsol uygulaması tarafından çağrılan bir sınıf kitaplığı ile bir çoklu proje çözümü oluşturma sürecinde gider.</span><span class="sxs-lookup"><span data-stu-id="5e9b9-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e9b9-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5e9b9-106">Prerequisites</span></span>

<span data-ttu-id="5e9b9-107">Başlamak için en son yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="5e9b9-107">To begin, you must install the latest [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

<span data-ttu-id="5e9b9-108">Bu makalede, komut satırını kullanın ve tercih edilen bir metin düzenleyicisi bildiğiniz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5e9b9-108">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="5e9b9-109">Bu, zaten kullanmıyorsanız, [Visual Studio Code](get-started-vscode.md) için bir metin düzenleyicisi olarak mükemmel bir seçenektir F#.</span><span class="sxs-lookup"><span data-stu-id="5e9b9-109">If you don't already use it, [Visual Studio Code](get-started-vscode.md) is a great option as a text editor for F#.</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="5e9b9-110">Basit bir çoklu proje çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="5e9b9-110">Build a simple multi-project solution</span></span>

<span data-ttu-id="5e9b9-111">Bir komut istemi/terminal açın ve kullanmak [yeni dotnet](../../core/tools/dotnet-new.md) adlı yeni bir çözüm dosyası oluşturmak için komut `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="5e9b9-111">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```console
dotnet new sln -o FSNetCore
```

<span data-ttu-id="5e9b9-112">Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını üretilir:</span><span class="sxs-lookup"><span data-stu-id="5e9b9-112">The following directory structure is produced after running the previous command:</span></span>

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="5e9b9-113">Bir sınıf kitaplığı yazma</span><span class="sxs-lookup"><span data-stu-id="5e9b9-113">Write a class library</span></span>

<span data-ttu-id="5e9b9-114">Dizinleri *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="5e9b9-114">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="5e9b9-115">Kullanım `dotnet new` komutu, bir sınıf kitaplığı projesi oluşturma **src** kitaplığı adlı bir klasör.</span><span class="sxs-lookup"><span data-stu-id="5e9b9-115">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```console
dotnet new classlib -lang F# -o src/Library
```

<span data-ttu-id="5e9b9-116">Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını üretilir:</span><span class="sxs-lookup"><span data-stu-id="5e9b9-116">The following directory structure is produced after running the previous command:</span></span>

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="5e9b9-117">Öğesinin içeriğini değiştirin `Library.fs` aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="5e9b9-117">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="5e9b9-118">Newtonsoft.Json NuGet paketini kitaplığı projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5e9b9-118">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```console
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="5e9b9-119">Ekleme `Library` için proje `FSNetCore` çözümünü kullanarak [dotnet sln ekleme](../../core/tools/dotnet-sln.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="5e9b9-119">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```console
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="5e9b9-120">Çalıştırma `dotnet build` Projeyi derlemek için.</span><span class="sxs-lookup"><span data-stu-id="5e9b9-120">Run `dotnet build` to build the project.</span></span> <span data-ttu-id="5e9b9-121">Çözümlenmemiş bağımlılıklar oluşturma sırasında geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5e9b9-121">Unresolved dependencies will be restored when building.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="5e9b9-122">Sınıf kitaplığı kullanan bir konsol uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="5e9b9-122">Write a console application that consumes the class library</span></span>

<span data-ttu-id="5e9b9-123">Kullanım `dotnet new` komutu, bir konsol uygulamasında oluşturma **src** uygulama adlı bir klasör.</span><span class="sxs-lookup"><span data-stu-id="5e9b9-123">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```console
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="5e9b9-124">Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını üretilir:</span><span class="sxs-lookup"><span data-stu-id="5e9b9-124">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="5e9b9-125">Öğesinin içeriğini değiştirin `Program.fs` dosyasındaki kodu aşağıdaki kodla:</span><span class="sxs-lookup"><span data-stu-id="5e9b9-125">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="5e9b9-126">Bir başvuru ekleyin `Library` kullanarak proje [dotnet Başvuru Ekle](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="5e9b9-126">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```console
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="5e9b9-127">Ekleme `App` için proje `FSNetCore` çözümünü kullanarak `dotnet sln add` komutu:</span><span class="sxs-lookup"><span data-stu-id="5e9b9-127">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```console
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="5e9b9-128">NuGet bağımlılıklarını geri `dotnet restore` çalıştırıp `dotnet build` Projeyi derlemek için.</span><span class="sxs-lookup"><span data-stu-id="5e9b9-128">Restore the NuGet dependencies, `dotnet restore` and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="5e9b9-129">Dizini `src/App` geçirme projeyi çalıştırın ve konsol projesi `Hello World` bağımsız değişkenler olarak:</span><span class="sxs-lookup"><span data-stu-id="5e9b9-129">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```console
cd src/App
dotnet run Hello World
```

<span data-ttu-id="5e9b9-130">Aşağıdaki sonuçları görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="5e9b9-130">You should see the following results:</span></span>

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a><span data-ttu-id="5e9b9-131">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="5e9b9-131">Next steps</span></span>

<span data-ttu-id="5e9b9-132">Ardından, kullanıma [Turu F# ](../tour.md) farklı hakkında daha fazla bilgi edinmek için F# özellikleri.</span><span class="sxs-lookup"><span data-stu-id="5e9b9-132">Next, check out the [Tour of F#](../tour.md) to learn more about different F# features.</span></span>
