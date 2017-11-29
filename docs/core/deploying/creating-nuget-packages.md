---
title: "Çapraz Platform araçları ile bir NuGet paketi oluşturma"
description: "Bir NuGet paketi 'dotnet pack' komutuyla oluşturmayı öğrenin."
keywords: .NET, .NET core NuGet
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2f0415c1-110b-433d-87c1-ae3d543a8844
ms.openlocfilehash: a5738a4f3755a959660db4be683677673af61ef9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a><span data-ttu-id="faac1-104">Çapraz Platform araçları ile bir NuGet paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="faac1-104">How to Create a NuGet Package with Cross Platform Tools</span></span>

> [!NOTE]
> <span data-ttu-id="faac1-105">UNIX kullanarak komut satırı örnekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="faac1-105">The following shows command-line samples using Unix.</span></span>  <span data-ttu-id="faac1-106">`dotnet pack` Aşağıda gösterildiği gibi komutu Windows'da aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="faac1-106">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="faac1-107">.NET Core 1.0 için kitaplıkları NuGet paketleri olarak dağıtılmış beklenir.</span><span class="sxs-lookup"><span data-stu-id="faac1-107">For .NET Core 1.0, libraries are expected to be distributed as NuGet packages.</span></span>  <span data-ttu-id="faac1-108">Aslında nasıl tüm .NET standart kitaplıkları dağıtılmış tüketilen ve budur.</span><span class="sxs-lookup"><span data-stu-id="faac1-108">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span>  <span data-ttu-id="faac1-109">Bu en kolay gerçekleştirilir `dotnet pack` komutu.</span><span class="sxs-lookup"><span data-stu-id="faac1-109">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="faac1-110">Yalnızca NuGet dağıtmak istediğiniz bir harika yeni kitaplık yazdığınız düşünün.</span><span class="sxs-lookup"><span data-stu-id="faac1-110">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span>  <span data-ttu-id="faac1-111">Bir NuGet paketi ile tam olarak bunu yapmak için platformu araçları çapraz oluşturabilirsiniz!</span><span class="sxs-lookup"><span data-stu-id="faac1-111">You can create a NuGet package with cross platform tools to do exactly that!</span></span>  <span data-ttu-id="faac1-112">Aşağıdaki örnek adlı bir kitaplık varsayar **SuperAwesomeLibrary** hangi hedefleri `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="faac1-112">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="faac1-113">Geçişli bağımlılıkları varsa; diğer bir deyişle, başka bir projeye bağlıdır bir proje çözümünüzle birlikte paketlerini geri yüklemek emin olmak ihtiyacınız vardır `dotnet restore` bir NuGet paketi oluşturmadan önce komutu.</span><span class="sxs-lookup"><span data-stu-id="faac1-113">If you have transitive dependencies; that is, a project which depends on another project, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span>  <span data-ttu-id="faac1-114">Bunu yapmazsanız neden olur `dotnet pack` düzgün çalışmasını komutu.</span><span class="sxs-lookup"><span data-stu-id="faac1-114">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


<span data-ttu-id="faac1-115">Olduktan paketler geri yüklenir, bir kitaplık nerede yaşıyor dizinine gidin:</span><span class="sxs-lookup"><span data-stu-id="faac1-115">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

`$ cd src/SuperAwesomeLibrary`

<span data-ttu-id="faac1-116">Yalnızca tek bir komut komut satırından sonra:</span><span class="sxs-lookup"><span data-stu-id="faac1-116">Then it's just a single command from the command line:</span></span>
    
`$ dotnet pack`

<span data-ttu-id="faac1-117">`/bin/Debug` Klasörü şimdi şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="faac1-117">Your `/bin/Debug` folder will now look like this:</span></span>

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="faac1-118">Bu hata ayıklaması işleyebilen bir paket oluşturur unutmayın.</span><span class="sxs-lookup"><span data-stu-id="faac1-118">Note that this will produce a package which is capable of being debugged.</span></span>  <span data-ttu-id="faac1-119">Bir NuGet paketi yayın ikililerini oluşturmak istiyorsanız, tüm yapmanız gereken ekleyin `-c` / `--configuration` geçin ve kullanmak `release` bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="faac1-119">If you want to build a NuGet package with release binaries, all you need to do is add the `-c`/`--configuration` switch and use `release` as the argument.</span></span>

`$ dotnet pack --configuration release`

<span data-ttu-id="faac1-120">`/bin` Klasörü şimdi sahip olacak bir `release` NuGet paketinizle yayın ikili dosyaları içeren klasör:</span><span class="sxs-lookup"><span data-stu-id="faac1-120">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="faac1-121">Ve şimdi bir NuGet paketi yayımlamak için gerekli dosyaları!</span><span class="sxs-lookup"><span data-stu-id="faac1-121">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="faac1-122">Karıştırmayın `dotnet pack` ile`dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="faac1-122">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="faac1-123">Herhangi bir noktada olduğunu dikkate almak önemlidir `dotnet publish` komut söz konusu.</span><span class="sxs-lookup"><span data-stu-id="faac1-123">It is important to note that at no point is the `dotnet publish` command involved.</span></span>  <span data-ttu-id="faac1-124">`dotnet publish` Komuttur dağıtılmış ve NuGet üzerinden tüketilen bir NuGet paketi oluşturma değil aynı gruptaki -, bağımlılıklarının tümü ile uygulamaları dağıtmak için.</span><span class="sxs-lookup"><span data-stu-id="faac1-124">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -  not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>
