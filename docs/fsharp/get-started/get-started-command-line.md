---
title: "F # ile komut satırı araçları ile çalışmaya başlama"
description: "F # platformlar arası .NET Core CLI ile kullanmayı öğrenin."
keywords: "Visual f #, f #, işlev, .NET, .NET Core programlama"
author: cartermp
ms.author: phcart
ms.date: 06/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 615db1ec-6ef3-4de2-bae6-4586affa9771
ms.openlocfilehash: a23d4861ce599f20f37ecd0564a0187e7b9b739f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-f-with-the-net-core-cli"></a><span data-ttu-id="efac6-104">F # .NET Core CLI ile kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="efac6-104">Get started with F# with the .NET Core CLI</span></span>

<span data-ttu-id="efac6-105">Bu makalede, nasıl, F # .NET Core üzerinde kullanmaya başlamak yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="efac6-105">This article covers how you can get started with using F# on .NET Core.</span></span> <span data-ttu-id="efac6-106">Bir konsol uygulaması tarafından çağrılan bir sınıf kitaplığı ile birden çok proje çözümü oluşturma üzerinden geçer.</span><span class="sxs-lookup"><span data-stu-id="efac6-106">It will go through building a multi-project solution with a Class Library that is called by a Console Application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="efac6-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="efac6-107">Prerequisites</span></span>

<span data-ttu-id="efac6-108">Başlamak için yüklemelisiniz [.NET Core SDK 1.0 veya üstü](https://dot.net/core).</span><span class="sxs-lookup"><span data-stu-id="efac6-108">To begin, you must install the [.NET Core SDK 1.0 or later](https://dot.net/core).</span></span> <span data-ttu-id="efac6-109">Yan yana yüklemeler desteklediği .NET Core SDK ' nın önceki bir sürümünü kaldırmak için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="efac6-109">There is no need to uninstall a previous version of the .NET Core SDK, as it supports side-by-side installations.</span></span>

<span data-ttu-id="efac6-110">Bu makalede, nasıl bir komut satırını kullanın ve tercih edilen bir metin Düzenleyicisi'ni bildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="efac6-110">This article assumes that you know how to use a command line and have a preferred text editor.</span></span> <span data-ttu-id="efac6-111">Zaten, kullanmazsanız [Visual Studio Code](https://code.visualstudio.com) olarak bir metin düzenleyicisi F # için kullanışlı bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="efac6-111">If you don't already use it, [Visual Studio Code](https://code.visualstudio.com) is a great option as a text editor for F#.</span></span> <span data-ttu-id="efac6-112">IntelliSense, daha iyi söz dizimi vurgulama ve diğerleri gibi harika özellikler almak için indirebilirsiniz [Ionide uzantısı](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="efac6-112">To get awesome features like IntelliSense, better syntax highlighting, and more, you can download the [Ionide Extension](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span>

## <a name="building-a-simple-multi-project-solution"></a><span data-ttu-id="efac6-113">Basit bir birden çok proje çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="efac6-113">Building a Simple Multi-project Solution</span></span>

<span data-ttu-id="efac6-114">Bir komut istemi/Terminali açın ve kullanmak `dotnet new` adlı yeni çözüm dosyasını oluşturmak için komutu `FSNetCore`:</span><span class="sxs-lookup"><span data-stu-id="efac6-114">Open a command prompt/terminal and use the `dotnet new` command to create new solution file called `FSNetCore`:</span></span>

```
dotnet new sln -o FSNetCore
```

<span data-ttu-id="efac6-115">Ayarlayamadı dizin yapısını komutu Tamamlanıyor sonucunda oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="efac6-115">The folowing directory structure is produced as a result of the command completing:</span></span>

```
FSNetCore
    ├── FSNetCore.sln
```

<span data-ttu-id="efac6-116">Değiştirme dizinleri *FSNetCore* ve projeleri çözüm klasörüne eklemeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="efac6-116">Change directories to *FSNetCore* and start adding projects to the solution folder.</span></span>
 
### <a name="writing-a-class-library"></a><span data-ttu-id="efac6-117">Bir sınıf kitaplığı yazma</span><span class="sxs-lookup"><span data-stu-id="efac6-117">Writing a Class library</span></span>

<span data-ttu-id="efac6-118">Kullanım `dotnet new` komutu, bir sınıf kitaplığı proje oluştur **src** kitaplığı adlı klasörü.</span><span class="sxs-lookup"><span data-stu-id="efac6-118">Use the `dotnet new` command, create a Class Library project in the **src** folder named Library.</span></span> 

```bash
dotnet new lib -lang F# -o src/Library 
```

<span data-ttu-id="efac6-119">Aşağıdaki dizin yapısını komutu Tamamlanıyor sonucunda oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="efac6-119">The following directory structure is produced as a result of the command completing:</span></span>

```
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

<span data-ttu-id="efac6-120">Değiştir `Library.fs` aşağıdaki:</span><span class="sxs-lookup"><span data-stu-id="efac6-120">Replace the contents of `Library.fs` with the following:</span></span>

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value = 
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value  (JsonConvert.SerializeObject(value))
```

<span data-ttu-id="efac6-121">Newtonsoft.Json NuGet paketi kitaplığı projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="efac6-121">Add the Newtonsoft.Json NuGet package to the Library project.</span></span>

```bash
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

<span data-ttu-id="efac6-122">Ekleme `Library` için proje `FSNetCore` çözümünü kullanarak `dotnet sln add` komutu:</span><span class="sxs-lookup"><span data-stu-id="efac6-122">Add the `Library` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/Library/Library.fsproj
```

<span data-ttu-id="efac6-123">NuGet bağımlılıkları geri `dotnet restore` ([nota bakın](#dotnet-restore-note)) çalıştırıp `dotnet build` Projeyi derlemek için.</span><span class="sxs-lookup"><span data-stu-id="efac6-123">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

### <a name="writing-a-console-application-which-consumes-the-class-library"></a><span data-ttu-id="efac6-124">Sınıf kitaplığı tüketir bir konsol uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="efac6-124">Writing a Console Application which Consumes the Class Library</span></span>

<span data-ttu-id="efac6-125">Kullanım `dotnet new` komutu, bir konsol uygulaması oluşturmak **src** uygulama adlı klasörü.</span><span class="sxs-lookup"><span data-stu-id="efac6-125">Use the `dotnet new` command, create a Console app in the **src** folder named App.</span></span> 

```bash
dotnet new console -lang F# -o src/App 
```

<span data-ttu-id="efac6-126">Aşağıdaki dizin yapısını komutu Tamamlanıyor sonucunda oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="efac6-126">The following directory structure is produced as a result of the command completing:</span></span>

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

<span data-ttu-id="efac6-127">Değişiklik `Program.fs` için:</span><span class="sxs-lookup"><span data-stu-id="efac6-127">Change `Program.fs` to:</span></span>

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

<span data-ttu-id="efac6-128">Bir başvuru ekleyin `Library` kullanarak proje `dotnet add reference`.</span><span class="sxs-lookup"><span data-stu-id="efac6-128">Add a reference to the `Library` project using `dotnet add reference`.</span></span>

```bash
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

<span data-ttu-id="efac6-129">Ekleme `App` için proje `FSNetCore` çözümünü kullanarak `dotnet sln add` komutu:</span><span class="sxs-lookup"><span data-stu-id="efac6-129">Add the `App` project to the `FSNetCore` solution using the `dotnet sln add` command:</span></span>

```bash
dotnet sln add src/App/App.fsproj
```

<span data-ttu-id="efac6-130">NuGet bağımlılıkları geri `dotnet restore` ([nota bakın](#dotnet-restore-note)) çalıştırıp `dotnet build` Projeyi derlemek için.</span><span class="sxs-lookup"><span data-stu-id="efac6-130">Restore the NuGet dependencies, `dotnet restore` ([see note](#dotnet-restore-note)) and run `dotnet build` to build the project.</span></span>

<span data-ttu-id="efac6-131">Değişiklik dizinine `src/App` konsol projesi ve geçirme projeyi `Hello World` bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="efac6-131">Change directory to the `src/App` console project and run the project passing `Hello World` as arguments.</span></span>

```bash
cd src/App
dotnet run Hello World
``` 

<span data-ttu-id="efac6-132">Aşağıdaki sonuçları görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="efac6-132">You should see the following results:</span></span>

```
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]