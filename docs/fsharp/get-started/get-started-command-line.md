---
title: 'F # ile komut satırı araçları ile çalışmaya başlama'
description: 'F # .NET Core CLI kullanarak bir işletim sistemine (Windows, macOs veya Linux) üzerinde bir basit birden çok proje çözümü oluşturmayı öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 03/26/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e48e1291bbe91da0d9ca2adbb08662bd106c8fb4
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="a3945-103">F # .NET Core CLI ile kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="a3945-103">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="a3945-104">Bu makalede, nasıl, F # ile .NET Core CLI ile herhangi bir işletim sistemine (Windows, macOS veya Linux) kullanmaya başlayabilir yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3945-104">This article covers how you can get started with F# on any operating system (Windows, macOS, or Linux) with the .NET Core CLI.</span></span> <span data-ttu-id="a3945-105">Bu, bir konsol uygulaması tarafından çağrılan bir sınıf kitaplığı ile birden çok proje çözümü oluşturma üzerinden gider.</span><span class="sxs-lookup"><span data-stu-id="a3945-105">It goes through building a multi-project solution with a class library that is called by a console application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a3945-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a3945-106">Prerequisites</span></span>

<span data-ttu-id="a3945-107">Başlamak için yüklemelisiniz [.NET Core SDK 1.0 veya üstü](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="a3945-107">To begin, you must install the [.NET Core SDK 1.0 or later](https://www.microsoft.com/net/download/).</span></span> <span data-ttu-id="a3945-108">Yan yana yüklemeler desteklediği .NET Core SDK ' nın önceki bir sürümünü kaldırmak için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="a3945-108">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="a3945-109">Bu makalede, nasıl bir komut satırını kullanın ve tercih edilen bir metin Düzenleyicisi'ni bildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="a3945-109">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="a3945-110">Zaten, kullanmazsanız [Visual Studio Code](https://code.visualstudio.com) olarak bir metin düzenleyicisi F # için kullanışlı bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="a3945-110">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="a3945-111">IntelliSense, daha iyi söz dizimi vurgulama ve diğerleri gibi harika özellikler almak için indirebilirsiniz [Ionide uzantısı](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="a3945-111">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="build-a-simple-multi-project-solution"></a><span data-ttu-id="a3945-112">Basit bir birden çok proje çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a3945-112">Build a simple multi-project solution</span></span>

<span data-ttu-id="a3945-113">Bir komut istemi/Terminali açın ve kullanmak [dotnet yeni](../../core/tools/dotnet-new.md) adlı yeni çözüm dosyasını oluşturmak için komutu `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="a3945-113">Open a command prompt/terminal and use the [dotnet new](../../core/tools/dotnet-new.md) command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="a3945-114">Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="a3945-114">The following directory structure is produced after running the previous command:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a><span data-ttu-id="a3945-115">Bir sınıf kitaplığı yazma</span><span class="sxs-lookup"><span data-stu-id="a3945-115">Write a class library</span></span>

<span data-ttu-id="a3945-116">Değiştirme dizinleri *FSNetCore*.</span><span class="sxs-lookup"><span data-stu-id="a3945-116">Change directories to *FSNetCore*.</span></span>

<span data-ttu-id="a3945-117">Kullanım `dotnet new` komutu, bir sınıf kitaplığı projesi oluştur **src** kitaplığı adlı klasörü.</span><span class="sxs-lookup"><span data-stu-id="a3945-117">Use the `dotnet new` command, create a class library project in the **src** folder named Library.</span></span>

```
dotnet new lib -lang F# -o src/Library
```

<span data-ttu-id="a3945-118">Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="a3945-118">The following directory structure is produced after running the previous command:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="a3945-119">Değiştir `Library.fs` aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="a3945-119">Replace the contents of `Library.fs` with the following code:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="a3945-120">Newtonsoft.Json NuGet paketi kitaplığı projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a3945-120">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="a3945-121">Ekleme `Library` için proje `FSNetCore` çözümünü kullanarak [dotnet sln ekleme](../../core/tools/dotnet-sln.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="a3945-121">Add the `Library` project to the `FSNetCore` solution using the [dotnet sln add](../../core/tools/dotnet-sln.md) command:</span></span>

```
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="a3945-122">Kullanarak NuGet bağımlılıkları geri `dotnet restore` komutu ([nota bakın](#dotnet-restore-note)) çalıştırıp `dotnet build` Projeyi derlemek için.</span><span class="sxs-lookup"><span data-stu-id="a3945-122">Restore the NuGet dependencies using the `dotnet restore` command ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="write-a-console-application-that-consumes-the-class-library"></a><span data-ttu-id="a3945-123">Sınıf kitaplığı tüketen bir konsol uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="a3945-123">Write a console application that consumes the class library</span></span>

<span data-ttu-id="a3945-124">Kullanım `dotnet new` komutu, bir konsol uygulaması oluşturun **src** uygulama adlı klasörü.</span><span class="sxs-lookup"><span data-stu-id="a3945-124">Use the `dotnet new` command, create a console application in the **src** folder named App.</span></span>

```
dotnet new console -lang F# -o src/App
```

<span data-ttu-id="a3945-125">Önceki komutu çalıştırdıktan sonra aşağıdaki dizin yapısını oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="a3945-125">The following directory structure is produced after running the previous command:</span></span>

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

<span data-ttu-id="a3945-126">Değiştir `Program.fs` aşağıdaki kod ile dosya:</span><span class="sxs-lookup"><span data-stu-id="a3945-126">Replace the contents of the `Program.fs` file with the following code:</span></span>

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

<span data-ttu-id="a3945-127">Bir başvuru ekleyin `Library` kullanarak proje [dotnet Başvuru Ekle](../../core/tools/dotnet-add-reference.md).</span><span class="sxs-lookup"><span data-stu-id="a3945-127">Add a reference to the `Library` project using [dotnet add reference](../../core/tools/dotnet-add-reference.md).</span></span>

```
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="a3945-128">Ekleme `App` için proje `FSNetCore` çözümünü kullanarak `dotnet sln add` komutu:</span><span class="sxs-lookup"><span data-stu-id="a3945-128">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="a3945-129">NuGet bağımlılıkları geri `dotnet restore` ([nota bakın](#dotnet-restore-note)) çalıştırıp `dotnet build` Projeyi derlemek için.</span><span class="sxs-lookup"><span data-stu-id="a3945-129">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="a3945-130">Değişiklik dizinine `src/App` konsol projesi ve geçirme projeyi `Hello World` bağımsız değişken olarak:</span><span class="sxs-lookup"><span data-stu-id="a3945-130">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments:</span></span>

```
cd src/App
dotnet run Hello World
```

<span data-ttu-id="a3945-131">Aşağıdaki sonuçları görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="a3945-131">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]