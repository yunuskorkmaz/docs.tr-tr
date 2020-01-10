---
title: .NET Core CLI bir NuGet paketi oluşturma
description: "' DotNet Pack ' komutuyla bir NuGet paketi oluşturmayı öğrenin."
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: ddc19faa7547637036686146f8600f40713541a8
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740868"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="34340-103">.NET Core komut satırı arabirimi (CLı) araçlarıyla bir NuGet paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="34340-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="34340-104">Aşağıda UNIX kullanan komut satırı örnekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="34340-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="34340-105">Burada gösterildiği gibi `dotnet pack` komutu, Windows 'ta aynı şekilde çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34340-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="34340-106">.NET Standard ve .NET Core kitaplıklarının NuGet paketleri olarak dağıtılması beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="34340-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="34340-107">Bu, tüm .NET Standard kitaplıklarının dağıtılma ve tüketilme olgusuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="34340-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="34340-108">Bu, `dotnet pack` komutuyla kolayca yapılır.</span><span class="sxs-lookup"><span data-stu-id="34340-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="34340-109">NuGet üzerinden dağıtmak istediğiniz harika yeni bir kitaplığı yazdığınız hakkında düşünün.</span><span class="sxs-lookup"><span data-stu-id="34340-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="34340-110">Tek yapmanız gereken, platformlar arası araçlarla bir NuGet paketi oluşturabilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="34340-110">You can create a NuGet package with cross-platform tools to do exactly that!</span></span> <span data-ttu-id="34340-111">Aşağıdaki örnek, `netstandard1.0`hedefleyen **Superawesomelibrary** adlı bir kitaplık olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="34340-111">The following example assumes a library called **SuperAwesomeLibrary** that targets `netstandard1.0`.</span></span>

<span data-ttu-id="34340-112">Başka bir pakete bağlı bir proje olan geçişli bağımlılıklarınız varsa, bir NuGet paketi oluşturmadan önce `dotnet restore` komutuyla tüm çözüme yönelik paketleri geri yüklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="34340-112">If you have transitive dependencies, that is, a project that depends on another package, make sure to restore packages for the entire solution with the `dotnet restore` command before you create a NuGet package.</span></span> <span data-ttu-id="34340-113">Bunun başarısız olması, `dotnet pack` komutunun düzgün şekilde çalışmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="34340-113">Failing to do so will result in the `dotnet pack` command not working properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="34340-114">Paketlerin geri yüklenmesini sağlamaktan sonra, kitaplığın yaşadığı dizine gidebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="34340-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="34340-115">Bu durumda, komut satırından yalnızca tek bir komuttur:</span><span class="sxs-lookup"><span data-stu-id="34340-115">Then it's just a single command from the command line:</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="34340-116">*/Bin/Debug* klasörünüz şimdi şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="34340-116">Your */bin/Debug* folder will now look like this:</span></span>

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="34340-117">Bu, hata ayıklama yapabilen bir paket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="34340-117">This produces a package that is capable of being debugged.</span></span> <span data-ttu-id="34340-118">Yayın ikilileriyle bir NuGet paketi oluşturmak istiyorsanız, tüm yapmanız gereken `--configuration` (veya `-c`) anahtarını ekleyip bağımsız değişken olarak `release` kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="34340-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```dotnetcli
dotnet pack --configuration release
```

<span data-ttu-id="34340-119">*/Bin* klasörünüz artık sürüm Ikilileriyle NuGet paketinizi içeren bir *Sürüm* klasörüne sahip olur:</span><span class="sxs-lookup"><span data-stu-id="34340-119">Your */bin* folder will now have a *release* folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="34340-120">Artık bir NuGet paketi yayımlamak için gerekli dosyalara sahipsiniz!</span><span class="sxs-lookup"><span data-stu-id="34340-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="34340-121">`dotnet pack` `dotnet publish` karıştırmayın</span><span class="sxs-lookup"><span data-stu-id="34340-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="34340-122">Dahil edilen `dotnet publish` komut olmadığı unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="34340-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="34340-123">`dotnet publish` komutu, aynı paket içindeki tüm bağımlılıklarıyla uygulama dağıtmaya yöneliktir; NuGet ile dağıtılacak ve tüketilecek bir NuGet paketi oluşturmak için değildir.</span><span class="sxs-lookup"><span data-stu-id="34340-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="34340-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34340-124">See also</span></span>

- [<span data-ttu-id="34340-125">Hızlı başlangıç: paket oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="34340-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
