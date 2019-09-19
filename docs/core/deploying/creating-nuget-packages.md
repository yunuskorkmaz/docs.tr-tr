---
title: .NET Core komut satırı arabirimi (CLı) araçlarıyla bir NuGet paketi oluşturma
description: "' DotNet Pack ' komutuyla bir NuGet paketi oluşturmayı öğrenin."
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: d36a6ee7d524933577928daa9993fba8ce62f6c7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116702"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="c22d2-103">.NET Core komut satırı arabirimi (CLı) araçlarıyla bir NuGet paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c22d2-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="c22d2-104">Aşağıda UNIX kullanan komut satırı örnekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c22d2-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="c22d2-105">Burada `dotnet pack` gösterilen komut, Windows 'ta aynı şekilde çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c22d2-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="c22d2-106">.NET Standard ve .NET Core kitaplıklarının NuGet paketleri olarak dağıtılması beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c22d2-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="c22d2-107">Bu, tüm .NET Standard kitaplıklarının dağıtılma ve tüketilme olgusuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c22d2-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="c22d2-108">Bu, `dotnet pack` komutla en kolay şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="c22d2-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="c22d2-109">NuGet üzerinden dağıtmak istediğiniz harika yeni bir kitaplığı yazdığınız hakkında düşünün.</span><span class="sxs-lookup"><span data-stu-id="c22d2-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="c22d2-110">Tek yapmanız gereken, platformlar arası araçlarla bir NuGet paketi oluşturabilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="c22d2-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span> <span data-ttu-id="c22d2-111">Aşağıdaki örnek, ' i hedefleyen `netstandard1.0` **Superawesomelibrary** adlı bir kitaplık olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="c22d2-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="c22d2-112">Geçişli bağımlılıklarınız varsa; diğer bir deyişle, başka bir pakete bağımlı olan bir proje, bir NuGet paketi oluşturmadan önce `dotnet restore` komutuyla tüm çözümünüze yönelik paketleri geri yüklediğinizden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c22d2-112">If you have transitive dependencies; that is, a project which depends on another package, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span> <span data-ttu-id="c22d2-113">Bunun başarısız olmasının nedeni `dotnet pack` komutun düzgün şekilde çalışmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c22d2-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="c22d2-114">Paketlerin geri yüklenmesini sağlamaktan sonra, kitaplığın yaşadığı dizine gidebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c22d2-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="c22d2-115">Bu durumda, komut satırından yalnızca tek bir komuttur:</span><span class="sxs-lookup"><span data-stu-id="c22d2-115">Then it's just a single command from the command line:</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="c22d2-116">`/bin/Debug` Klasörünüz şimdi şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="c22d2-116">Your `/bin/Debug` folder will now look like this:</span></span>

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="c22d2-117">Bu, hata ayıklama yapabilen bir paket üretebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c22d2-117">Note that this will produce a package which is capable of being debugged.</span></span> <span data-ttu-id="c22d2-118">Yayın ikilileriyle bir NuGet paketi oluşturmak istiyorsanız, tüm yapmanız gereken, `--configuration` (veya `-c`) anahtarını ve bağımsız değişkeni olarak kullanmayı `release` eklemektir.</span><span class="sxs-lookup"><span data-stu-id="c22d2-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```dotnetcli
dotnet pack --configuration release
```

<span data-ttu-id="c22d2-119">Klasörünüz artık sürüm ikilileriyle NuGet `release` paketinizi içeren bir klasöre sahip olur: `/bin`</span><span class="sxs-lookup"><span data-stu-id="c22d2-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="c22d2-120">Artık bir NuGet paketi yayımlamak için gerekli dosyalara sahipsiniz!</span><span class="sxs-lookup"><span data-stu-id="c22d2-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="c22d2-121">İle karıştırmayın `dotnet pack``dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="c22d2-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="c22d2-122">Hiçbir noktadan söz konusu `dotnet publish` komutun olmadığı unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c22d2-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="c22d2-123">Bu `dotnet publish` komut, aynı paketteki tüm bağımlılıklarıyla uygulama dağıtmaya yöneliktir--NuGet paketini, NuGet aracılığıyla dağıtılacak ve tüketilecek şekilde bir NuGet paketi oluşturmak için değil.</span><span class="sxs-lookup"><span data-stu-id="c22d2-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="c22d2-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c22d2-124">See also</span></span>

- [<span data-ttu-id="c22d2-125">Hızlı Başlangıç: Paket oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="c22d2-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
