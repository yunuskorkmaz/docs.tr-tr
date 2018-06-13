---
title: .NET Core için .NET Framework'bağlantı noktası oluşturma
description: Taşıma işlemini anlamanıza ve .NET Core .NET Framework projeye bağlantı noktası oluşturma, faydalı bulabileceğiniz araçları keşfedin.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: bf4f50ca915f21cdda6b99ae6bdf9e837eca3ae7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33210088"
---
# <a name="porting-to-net-core-from-net-framework"></a><span data-ttu-id="3481d-103">.NET Core için .NET Framework'bağlantı noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="3481d-103">Porting to .NET Core from .NET Framework</span></span>

<span data-ttu-id="3481d-104">.NET Framework üzerinde çalışan kodu ekranınız varsa, .NET Core 1.0 kodunuz çalışan ilgilenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3481d-104">If you've got code running on the .NET Framework, you may be interested in running your code on .NET Core 1.0.</span></span>  <span data-ttu-id="3481d-105">Bu makalede taşıma işlemine genel bakış ve .NET Core için bağlantı noktası oluşturma, faydalı bulabileceğiniz araçların listesi yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="3481d-105">This article covers an overview of the porting process and a list of the tools you may find helpful when porting to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="3481d-106">Taşıma işlemine genel bakış</span><span class="sxs-lookup"><span data-stu-id="3481d-106">Overview of the Porting Process</span></span>

<span data-ttu-id="3481d-107">Taşıma için önerilen işlemi aşağıdaki adımları dizi izler.</span><span class="sxs-lookup"><span data-stu-id="3481d-107">The recommended process for porting follows the following series of steps.</span></span>  <span data-ttu-id="3481d-108">İşlemin bu parçaların her birini daha fazla makalelerinde daha ayrıntılı değinilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3481d-108">Each of these parts of the process are covered in more detail in further articles.</span></span>

1. <span data-ttu-id="3481d-109">Tanımlamak ve, üçüncü taraf bağımlılıkları için hesap.</span><span class="sxs-lookup"><span data-stu-id="3481d-109">Identify and account for your third-party dependencies.</span></span>

   <span data-ttu-id="3481d-110">Bu, hangi üçüncü taraf bağımlılıkları olan, bağımlı nasıl anlama gerektireceğini bunları yoksa ayrıca .NET Core ve adımları çalıştırırsanız, görmek için uygulayabileceğiniz nasıl.</span><span class="sxs-lookup"><span data-stu-id="3481d-110">This will involve understanding what your third-party dependencies are, how you depend on them, how to see if they also run on .NET Core, and steps you can take if they don't.</span></span>
   
2. <span data-ttu-id="3481d-111">Hedef .NET Framework 4.6.2 bağlantı noktasına istediğiniz tüm projeleri yeniden hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="3481d-111">Retarget all projects you wish to port to target .NET Framework 4.6.2.</span></span>

   <span data-ttu-id="3481d-112">Bu, .NET Core belirli bir API'yi burada destekleyemez durumlarda .NET Framework özgü hedefler için API alternatifleri kullanabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3481d-112">This ensures that you can use API alternatives for .NET Framework-specific targets in the cases where .NET Core can't support a particular API.</span></span>
   
3. <span data-ttu-id="3481d-113">Kullanım [API taşınabilirlik Çözümleyicisi aracını](https://github.com/Microsoft/dotnet-apiport/) derlemeleriniz çözümlemek ve onun sonuçlarına dayalı bağlantı noktasına yönelik bir plan geliştirmek için.</span><span class="sxs-lookup"><span data-stu-id="3481d-113">Use the [API Portability Analyzer tool](https://github.com/Microsoft/dotnet-apiport/) to analyze your assemblies and develop a plan to port based on its results.</span></span>

   <span data-ttu-id="3481d-114">API taşınabilirlik Çözümleyicisi aracını derlenmiş derlemeleriniz çözümleyebilir ve üst düzey taşınabilirlik Özet gösteren bir rapor ve .NET Core üzerinde kullanılabilir değil, kullanmakta olduğunuz her API bir dökümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3481d-114">The API Portability Analyzer tool will analyze your compiled assemblies and generate a report which shows a high-level portability summary and a breakdown of each API you're using that isn't available on .NET Core.</span></span>  <span data-ttu-id="3481d-115">Bu rapor analizini yanında kullanabilirsiniz, nasıl üzerinden kodunuzu bağlantı için bir plan geliştirmek için codebase.</span><span class="sxs-lookup"><span data-stu-id="3481d-115">You can use this report alongside an analysis of your codebase to develop a plan for how you'll port your code over.</span></span>
   
4. <span data-ttu-id="3481d-116">Testleri kodunuzu bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="3481d-116">Port your tests code.</span></span>

   <span data-ttu-id="3481d-117">.NET Core taşıma temelinizde için büyük değişiklik olduğundan, yüksek oranda üzerinden kod bağlantı noktası olarak testleri çalıştırabilmeniz için bağlantı noktası kurulmuş testleri almak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="3481d-117">Because porting to .NET Core is such a big change to your codebase, it's highly recommended to get your tests ported so that you can run tests as you port code over.</span></span>  <span data-ttu-id="3481d-118">Mstest'i, xUnit ve NUnit .NET Core 1.0 bugün destekler.</span><span class="sxs-lookup"><span data-stu-id="3481d-118">MSTest, xUnit, and NUnit all support .NET Core 1.0 today.</span></span>
   
6. <span data-ttu-id="3481d-119">Taşıma için planınızı yürütme!</span><span class="sxs-lookup"><span data-stu-id="3481d-119">Execute your plan for porting!</span></span>

## <a name="tools-to-help"></a><span data-ttu-id="3481d-120">Yardımcı olacak araçlar</span><span class="sxs-lookup"><span data-stu-id="3481d-120">Tools to help</span></span>

<span data-ttu-id="3481d-121">Yararlı bulabilirsiniz araçları kısa bir listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3481d-121">Here's a short list of the tools you'll find helpful:</span></span>

* <span data-ttu-id="3481d-122">NuGet - [Nuget istemci](https://dist.nuget.org/index.html) veya [NuGet paketi Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft'un .NET uygulamaları için Paket Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="3481d-122">NuGet - [Nuget Client](https://dist.nuget.org/index.html) or [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft's package manager for .NET implementations.</span></span>
* <span data-ttu-id="3481d-123">API taşınabilirlik Çözümleyicisi - [komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) veya [Visual Studio Uzantısı](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), nasıl taşınabilir kodunuzu .NET Framework ve .NET Core arasında sahip olduğu bir rapor oluşturabilirsiniz bir araç zinciri bir sorunları dökümünü derleme tarafından derleme.</span><span class="sxs-lookup"><span data-stu-id="3481d-123">Api Portability Analyzer - [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) or [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core, with an assembly-by-assembly breakdown of issues.</span></span>  <span data-ttu-id="3481d-124">Bkz: [işlemi yardımcı olmak için araç](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="3481d-124">See [Tooling to help you on the process](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) for more information.</span></span>
* <span data-ttu-id="3481d-125">Paket arama - A ters [yararlı web hizmeti](https://packagesearch.azurewebsites.net) bir türünü aramak ve bu türü içeren paketler bulmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3481d-125">Reverse Package Search - A [useful web service](https://packagesearch.azurewebsites.net) that allows you to search for a type and find packages containing that type.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3481d-126">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3481d-126">Next steps</span></span>

[<span data-ttu-id="3481d-127">Üçüncü taraf bağımlılıkları çözümleniyor.</span><span class="sxs-lookup"><span data-stu-id="3481d-127">Analyzing your third-party dependencies.</span></span>](third-party-deps.md)
   
