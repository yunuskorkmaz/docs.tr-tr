---
title: .NET Core ile .NET Framework'ten taşıma
description: Taşıma işlemlerini anlamanıza ve .NET Core için bir .NET Framework projesi taşırken faydalı bulabileceğiniz araçları keşfedin.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: d273b3abe46de59aa55b5b9a531d3c572a065124
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48835398"
---
# <a name="porting-to-net-core-from-net-framework"></a><span data-ttu-id="6b316-103">.NET Core ile .NET Framework'ten taşıma</span><span class="sxs-lookup"><span data-stu-id="6b316-103">Porting to .NET Core from .NET Framework</span></span>

<span data-ttu-id="6b316-104">.NET Framework üzerinde çalışan kod kendinizi, kodunuzu .NET Core 1.0 üzerinde çalışan ilginizi çekebilir.</span><span class="sxs-lookup"><span data-stu-id="6b316-104">If you've got code running on the .NET Framework, you may be interested in running your code on .NET Core 1.0.</span></span>  <span data-ttu-id="6b316-105">Bu makalede, taşıma işlemine genel bakış ve bir listesi için .NET Core taşırken faydalı bulabileceğiniz anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b316-105">This article covers an overview of the porting process and a list of the tools you may find helpful when porting to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="6b316-106">Taşıma işlemine genel bakış</span><span class="sxs-lookup"><span data-stu-id="6b316-106">Overview of the Porting Process</span></span>

<span data-ttu-id="6b316-107">Taşıma için önerilen işlemi aşağıdaki adımları dizisini izler.</span><span class="sxs-lookup"><span data-stu-id="6b316-107">The recommended process for porting follows the following series of steps.</span></span>  <span data-ttu-id="6b316-108">İşlemin bu parçaların her biri daha ayrıntılı olarak daha fazla makale bölümünde değinilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6b316-108">Each of these parts of the process are covered in more detail in further articles.</span></span>

1. <span data-ttu-id="6b316-109">Tanımlamak ve üçüncü taraf bağımlılıklarınızı hesap.</span><span class="sxs-lookup"><span data-stu-id="6b316-109">Identify and account for your third-party dependencies.</span></span>

   <span data-ttu-id="6b316-110">Bu, üçüncü taraf bağımlılıkları olan, bağımlı nasıl anlama içerecektir bunları sağlanmıyorsa de .NET Core ve adımlar üzerinde çalıştırmak için uygulayabileceğiniz nasıl.</span><span class="sxs-lookup"><span data-stu-id="6b316-110">This will involve understanding what your third-party dependencies are, how you depend on them, how to see if they also run on .NET Core, and steps you can take if they don't.</span></span>
   
2. <span data-ttu-id="6b316-111">Hedef .NET Framework 4.6.2 taşımak istediğiniz tüm projeleri yeniden hedefle</span><span class="sxs-lookup"><span data-stu-id="6b316-111">Retarget all projects you wish to port to target .NET Framework 4.6.2.</span></span>

   <span data-ttu-id="6b316-112">Bu, belirli bir API'yi burada .NET Core desteği durumlarda .NET Framework özel hedefler için API alternatifler kullanabilirsiniz sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b316-112">This ensures that you can use API alternatives for .NET Framework-specific targets in the cases where .NET Core can't support a particular API.</span></span>
   
3. <span data-ttu-id="6b316-113">Kullanım [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) bütünleştirilmiş kodlarınızı analiz edin ve kendi sonuçlarına göre bağlantı noktası için bir plan geliştirin.</span><span class="sxs-lookup"><span data-stu-id="6b316-113">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and develop a plan to port based on its results.</span></span>

   <span data-ttu-id="6b316-114">API taşınabilirlik Çözümleyicisi aracını derlenmiş bütünleştirilmiş kodlarınızı analiz edin ve üst düzey taşınabilirlik Özet gösteren bir rapor ve .NET Core üzerinde kullanılamayan, kullanmakta olduğunuz her API bir dökümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6b316-114">The API Portability Analyzer tool will analyze your compiled assemblies and generate a report which shows a high-level portability summary and a breakdown of each API you're using that isn't available on .NET Core.</span></span>  <span data-ttu-id="6b316-115">Bu raporu analizini yanı sıra kullanabilirsiniz, nasıl, kodunuzu üzerinden bağlantı noktası bir plan geliştirmek için kod tabanı.</span><span class="sxs-lookup"><span data-stu-id="6b316-115">You can use this report alongside an analysis of your codebase to develop a plan for how you'll port your code over.</span></span>
   
4. <span data-ttu-id="6b316-116">Testleri kod bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="6b316-116">Port your tests code.</span></span>

   <span data-ttu-id="6b316-117">.NET Core'a taşıma temelinizde böyle büyük bir değişiklik olduğundan, yüksek oranda üzerinden kod bağlantı noktası olarak testleri çalıştırabilmeniz için unity'nin testlerinizi almak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="6b316-117">Because porting to .NET Core is such a big change to your codebase, it's highly recommended to get your tests ported so that you can run tests as you port code over.</span></span>  <span data-ttu-id="6b316-118">.NET Core 1.0, bugün MSTest, xUnit ve Nunit'i destekler.</span><span class="sxs-lookup"><span data-stu-id="6b316-118">MSTest, xUnit, and NUnit all support .NET Core 1.0 today.</span></span>
   
6. <span data-ttu-id="6b316-119">Taşıma için planınızı yürütün!</span><span class="sxs-lookup"><span data-stu-id="6b316-119">Execute your plan for porting!</span></span>

## <a name="tools-to-help"></a><span data-ttu-id="6b316-120">Yardımcı olacak araçlar</span><span class="sxs-lookup"><span data-stu-id="6b316-120">Tools to help</span></span>

<span data-ttu-id="6b316-121">Yararlı bulabilirsiniz araçları kısa bir listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6b316-121">Here's a short list of the tools you'll find helpful:</span></span>

* <span data-ttu-id="6b316-122">NuGet - [Nuget istemci](https://dist.nuget.org/index.html) veya [NuGet paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft'un .NET uygulamaları için Paket Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="6b316-122">NuGet - [Nuget Client](https://dist.nuget.org/index.html) or [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft's package manager for .NET implementations.</span></span>
* <span data-ttu-id="6b316-123">API Portability Analyzer - [komut satırı aracını](https://github.com/Microsoft/dotnet-apiport/releases) veya [Visual Studio Uzantısı](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), nasıl taşınabilir kod arasında .NET Framework ve .NET Core ile olan bir rapor oluşturabilen bir araç zinciri bir derleme tarafından bütünleştirilmiş kod çözümleme sorunları.</span><span class="sxs-lookup"><span data-stu-id="6b316-123">Api Portability Analyzer - [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) or [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core, with an assembly-by-assembly breakdown of issues.</span></span>  <span data-ttu-id="6b316-124">Bkz: [işlemi yardımcı olacak araçlar](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="6b316-124">See [Tooling to help you on the process](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) for more information.</span></span>
* <span data-ttu-id="6b316-125">Ters paket arama - A [yararlı web hizmeti](https://packagesearch.azurewebsites.net) türü için arama yapın ve bu türü içeren paketleri olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6b316-125">Reverse Package Search - A [useful web service](https://packagesearch.azurewebsites.net) that allows you to search for a type and find packages containing that type.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6b316-126">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="6b316-126">Next steps</span></span>

[<span data-ttu-id="6b316-127">Üçüncü taraf bağımlılıklarını çözümleme.</span><span class="sxs-lookup"><span data-stu-id="6b316-127">Analyzing your third-party dependencies.</span></span>](third-party-deps.md)
   
