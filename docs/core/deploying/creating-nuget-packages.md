---
title: .NET Core komut satırı arabirimi (CLI) araçlarını bir NuGet paketi oluşturma
description: Bir NuGet paketi 'dotnet paketi' komutuyla oluşturmayı öğrenin.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 14e3dc265991634b4ef4814fb149f0aaebbcfab6
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170060"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="7e636-103">.NET Core komut satırı arabirimi (CLI) araçlarını bir NuGet paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e636-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="7e636-104">Aşağıda, UNIX kullanan komut satırı örnekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7e636-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="7e636-105">`dotnet pack` Burada gösterilen şekilde, Windows üzerinde aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="7e636-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="7e636-106">.NET standard ve .NET Core kitaplıkları, NuGet paketleri olarak dağıtılmış beklenir.</span><span class="sxs-lookup"><span data-stu-id="7e636-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="7e636-107">Aslında nasıl tüm .NET standart kitaplıklarına dağıtılmış ve kullanıldığını belirmenize budur.</span><span class="sxs-lookup"><span data-stu-id="7e636-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="7e636-108">Bu en kolay ile yapılır `dotnet pack` komutu.</span><span class="sxs-lookup"><span data-stu-id="7e636-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="7e636-109">Az önce NuGet dağıtmak istediğiniz bir harika yeni kitaplık yazdığınız varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7e636-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="7e636-110">Tam olarak bunu yapmak için platformlar arası araçlarla NuGet paketi oluşturabilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="7e636-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span> <span data-ttu-id="7e636-111">Aşağıdaki örnekte adlı bir kitaplığı varsayılır **SuperAwesomeLibrary** hangi hedeflerin `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="7e636-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="7e636-112">Geçişli bağımlılıkları varsa, diğer bir deyişle, başka bir pakete bağımlı bir proje ile tüm çözümünüz için paketleri geri yüklediğinizden emin olmak ihtiyacınız `dotnet restore` NuGet paketini oluşturmadan önce komutu.</span><span class="sxs-lookup"><span data-stu-id="7e636-112">If you have transitive dependencies; that is, a project which depends on another package, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span> <span data-ttu-id="7e636-113">Bunu yapmazsanız sonuçlanır `dotnet pack` düzgün çalışmasını komutu.</span><span class="sxs-lookup"><span data-stu-id="7e636-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="7e636-114">Olduktan sonra paketleri geri yüklenir, burada kitaplık bulunduğu dizine gidin:</span><span class="sxs-lookup"><span data-stu-id="7e636-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
$ cd src/SuperAwesomeLibrary`
```

<span data-ttu-id="7e636-115">Yalnızca tek bir komutu komut satırından sonra:</span><span class="sxs-lookup"><span data-stu-id="7e636-115">Then it's just a single command from the command line:</span></span>

```console
$ dotnet pack
```

<span data-ttu-id="7e636-116">`/bin/Debug` Klasör şimdi şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="7e636-116">Your `/bin/Debug` folder will now look like this:</span></span>

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="7e636-117">Bu ayıklanan özelliğine sahip olan bir paket oluşturur unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7e636-117">Note that this will produce a package which is capable of being debugged.</span></span> <span data-ttu-id="7e636-118">NuGet paketi sürüm ikili dosyaları oluşturmak istiyorsanız, tüm yapmanız gereken eklemek `--configuration` (veya `-c`) kullanın ve geçiş `release` bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="7e636-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```console
$ dotnet pack --configuration release
```

<span data-ttu-id="7e636-119">`/bin` Klasör artık sahip olacak bir `release` NuGet paketinizi yayın ikili dosyaları içeren klasör:</span><span class="sxs-lookup"><span data-stu-id="7e636-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="7e636-120">Ve artık bir NuGet paketi yayımlamak için gerekli dosyaları sahipsiniz!</span><span class="sxs-lookup"><span data-stu-id="7e636-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="7e636-121">Karıştırmayın `dotnet pack` ile `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="7e636-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="7e636-122">Hiçbir noktada olduğuna dikkat edin önemlidir `dotnet publish` komut söz konusu.</span><span class="sxs-lookup"><span data-stu-id="7e636-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="7e636-123">`dotnet publish` Komutu tüm bağımlılıklarını dağıtılmış ve NuGet aracılığıyla kullanılan NuGet paketini oluşturmak için değil aynı paket--uygulama dağıtmak için.</span><span class="sxs-lookup"><span data-stu-id="7e636-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e636-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e636-124">See also</span></span>

- [<span data-ttu-id="7e636-125">Hızlı Başlangıç: Bir paketi oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="7e636-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)