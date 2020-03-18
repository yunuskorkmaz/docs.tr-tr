---
title: .NET Core CLI ile NuGet paketi oluşturun
description: "'dotnet paketi' komutuyla bir NuGet paketi oluşturmayı öğrenin."
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920913"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a><span data-ttu-id="88d01-103">.NET Core CLI ile NuGet paketi nasıl oluşturulur?</span><span class="sxs-lookup"><span data-stu-id="88d01-103">How to create a NuGet package with the .NET Core CLI</span></span>

> [!NOTE]
> <span data-ttu-id="88d01-104">Aşağıdaki Unix kullanarak komut satırı örnekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="88d01-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="88d01-105">Burada `dotnet pack` gösterildiği gibi komut Windows'da da aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="88d01-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="88d01-106">.NET Standard ve .NET Core kitaplıklarının NuGet paketleri olarak dağıtılması beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="88d01-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="88d01-107">Bu aslında tüm .NET Standart kitaplıklarının nasıl dağıtıldığı ve tüketildiğini.</span><span class="sxs-lookup"><span data-stu-id="88d01-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="88d01-108">Bu en kolay `dotnet pack` komutu ile yapılır.</span><span class="sxs-lookup"><span data-stu-id="88d01-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="88d01-109">NuGet üzerinden dağıtmak istediğiniz harika bir yeni kütüphane yazdığınızı düşünün.</span><span class="sxs-lookup"><span data-stu-id="88d01-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="88d01-110">Bunu tam olarak yapmak için çapraz platform araçları ile bir NuGet paketi oluşturabilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="88d01-110">You can create a NuGet package with cross-platform tools to do exactly that!</span></span> <span data-ttu-id="88d01-111">Aşağıdaki örnek, **SuperAwesomeLibrary** adlı bir `netstandard1.0`kitaplığı hedefler varsayar.</span><span class="sxs-lookup"><span data-stu-id="88d01-111">The following example assumes a library called **SuperAwesomeLibrary** that targets `netstandard1.0`.</span></span>

<span data-ttu-id="88d01-112">Geçişli bağımlılıklarınız varsa, yani başka bir pakete dayanan bir projevarsa, bir NuGet `dotnet restore` paketi oluşturmadan önce komutla tüm çözüm için paketleri geri yüklediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="88d01-112">If you have transitive dependencies, that is, a project that depends on another package, make sure to restore packages for the entire solution with the `dotnet restore` command before you create a NuGet package.</span></span> <span data-ttu-id="88d01-113">Aksi takdirde komutun `dotnet pack` düzgün çalışmaması durumunda.</span><span class="sxs-lookup"><span data-stu-id="88d01-113">Failing to do so will result in the `dotnet pack` command not working properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="88d01-114">Paketlerin geri yüklendiğinden emin olduktan sonra, kitaplığın yaşadığı dizine gidebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="88d01-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="88d01-115">O zaman komut satırından sadece tek bir komut:</span><span class="sxs-lookup"><span data-stu-id="88d01-115">Then it's just a single command from the command line:</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="88d01-116">*/bin/Hata Ayıklama* klasörünüz şimdi şu şekilde görünecektir:</span><span class="sxs-lookup"><span data-stu-id="88d01-116">Your */bin/Debug* folder will now look like this:</span></span>

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="88d01-117">Bu debugged olma yeteneğine sahip bir paket üretir.</span><span class="sxs-lookup"><span data-stu-id="88d01-117">This produces a package that is capable of being debugged.</span></span> <span data-ttu-id="88d01-118">Sürüm ikilileri içeren bir NuGet paketi oluşturmak istiyorsanız, tek yapmanız `--configuration` gereken `-c`(veya) `release` anahtarını eklemek ve bağımsız değişken olarak kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="88d01-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```dotnetcli
dotnet pack --configuration release
```

<span data-ttu-id="88d01-119">*/bin* klasörünüz artık Sürüm ikilileriyle birlikte NuGet paketinizi içeren bir *sürüm* klasörüne sahip olacaktır:</span><span class="sxs-lookup"><span data-stu-id="88d01-119">Your */bin* folder will now have a *release* folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="88d01-120">Ve şimdi bir NuGet paketi yayınlamak için gerekli dosyaları var!</span><span class="sxs-lookup"><span data-stu-id="88d01-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="88d01-121">Ile karıştırmayın `dotnet pack``dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="88d01-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="88d01-122">Hiçbir noktada ilgili `dotnet publish` komut olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="88d01-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="88d01-123">Komut, `dotnet publish` tüm bağımlılıkları olan uygulamaları aynı pakette dağıtmak içindir -- NuGet üzerinden dağıtılacak ve tüketilecek bir NuGet paketi oluşturmak için değil.</span><span class="sxs-lookup"><span data-stu-id="88d01-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="88d01-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88d01-124">See also</span></span>

- [<span data-ttu-id="88d01-125">Quickstart: Bir paket oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="88d01-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
