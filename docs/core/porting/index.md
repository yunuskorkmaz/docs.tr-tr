---
title: .NET Framework'den .NET Core'a bağlantı noktası
description: Taşıma işlemini anlayın ve bir .NET Framework projesini .NET Core'a taşımayaparken yararlı olabileceğiniz araçları keşfedin.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: e483bb6e48dad6c3bf71bfa81e704a137fc02094
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937312"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a><span data-ttu-id="84093-103">.NET Framework'den .NET Core'a taşımaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="84093-103">Overview of porting from .NET Framework to .NET Core</span></span>

<span data-ttu-id="84093-104">Şu anda .NET Core'a taşımak istediğiniz .NET Framework'de çalışan kodunuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="84093-104">You might have code that currently runs on the .NET Framework that you're interested in porting to .NET Core.</span></span> <span data-ttu-id="84093-105">Bu makalede aşağıdakiler sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="84093-105">This article provides:</span></span>

* <span data-ttu-id="84093-106">Taşıma işlemine genel bakış.</span><span class="sxs-lookup"><span data-stu-id="84093-106">An overview of the porting process.</span></span>
* <span data-ttu-id="84093-107">Kodunuzu .NET Core'a taşımanızda yararlı olabileceğiniz araçların listesi.</span><span class="sxs-lookup"><span data-stu-id="84093-107">A list of tools that you may find helpful when you're porting your code to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="84093-108">Taşıma işlemine genel bakış</span><span class="sxs-lookup"><span data-stu-id="84093-108">Overview of the porting process</span></span>

<span data-ttu-id="84093-109">Projenizi .NET Core'a taşımayaparken aşağıdaki işlemi kullanmanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="84093-109">We recommend you use the following process when porting your project to .NET Core:</span></span>

1. <span data-ttu-id="84093-110">.NET Framework 4.7.2 veya daha yüksek bir hedefe bağlantı noktası yapmak istediğiniz tüm projeleri yeniden hedeflenin.</span><span class="sxs-lookup"><span data-stu-id="84093-110">Retarget all projects you wish to port to target .NET Framework 4.7.2 or higher.</span></span>

   <span data-ttu-id="84093-111">Bu adım, .NET Core belirli bir API'yi desteklemediğinde .NET Framework'e özgü hedefler için API alternatiflerini kullanabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="84093-111">This step ensures that you can use API alternatives for .NET Framework-specific targets when .NET Core doesn't support a particular API.</span></span>

2. <span data-ttu-id="84093-112">Derlemelerinizi analiz etmek ve .NET Core'a taşınabilir olup olmadıklarını görmek için [.NET Taşınabilirlik Çözümleyicisini](../../standard/analyzers/portability-analyzer.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="84093-112">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and see if they're portable to .NET Core.</span></span>

   <span data-ttu-id="84093-113">API Taşınabilirlik Çözümleyiciaracı derlenmiş derlemelerinizi analiz eder ve bir rapor oluşturur.</span><span class="sxs-lookup"><span data-stu-id="84093-113">The API Portability Analyzer tool analyzes your compiled assemblies and generates a report.</span></span> <span data-ttu-id="84093-114">Bu rapor, net core'da bulunmayan üst düzey taşınabilirlik özetini ve kullandığınız her API'nın dökümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="84093-114">This report shows a high-level portability summary and a breakdown of each API you're using that isn't available on NET Core.</span></span>

3. <span data-ttu-id="84093-115">Bazı platformlarda ve diğer bazı olası uyumluluk sorunlarını <xref:System.PlatformNotSupportedException> oluşturan API'leri tanımlamak için [.NET API çözümleyicisini](../../standard/analyzers/api-analyzer.md) projelerinize yükleyin.</span><span class="sxs-lookup"><span data-stu-id="84093-115">Install the [.NET API analyzer](../../standard/analyzers/api-analyzer.md) into your projects to identify APIs that throw <xref:System.PlatformNotSupportedException> on some platforms and some other potential compatibility issues.</span></span>

   <span data-ttu-id="84093-116">Bu araç taşınabilirlik çözümleyicisine benzer, ancak kod .NET Core üzerinde inşa edebilirsiniz eğer analiz yerine, bir API çalıştıran zamanda bir <xref:System.PlatformNotSupportedException> atacak bir şekilde bir API kullanıyorsanız analiz eder.</span><span class="sxs-lookup"><span data-stu-id="84093-116">This tool is similar to the portability analyzer, but instead of analyzing if code can build on .NET Core, it analyzes whether you're using an API in a way that will throw a <xref:System.PlatformNotSupportedException> at run time.</span></span> <span data-ttu-id="84093-117">.NET Framework 4.7.2 veya daha yüksek bir yerden hareket ediyorsanız, bu yaygın olmasa da, bunu kontrol etmek iyidir.</span><span class="sxs-lookup"><span data-stu-id="84093-117">Although this isn't common if you're moving from .NET Framework 4.7.2 or higher, it's good to check.</span></span> <span data-ttu-id="84093-118">.NET Core'da özel durumlar oluşturan API'ler hakkında daha fazla bilgi [için,.NET Core'da her zaman özel durumlar oluşturan API'lere](../compatibility/unsupported-apis.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="84093-118">For more information about APIs that throw exceptions on .NET Core, see [APIs that always throw exceptions on .NET Core](../compatibility/unsupported-apis.md).</span></span>

4. <span data-ttu-id="84093-119">Visual `packages.config` [Studio'daki dönüştürme aracıyla](/nuget/consume-packages/migrate-packages-config-to-package-reference)tüm bağımlılıklarınızı [PackageReference](/nuget/consume-packages/package-references-in-project-files) biçimine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="84093-119">Convert all of your `packages.config` dependencies to the [PackageReference](/nuget/consume-packages/package-references-in-project-files) format with the [conversion tool in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span>

   <span data-ttu-id="84093-120">Bu adım, bağımlılıklarınızı eski `packages.config` biçimden dönüştürmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="84093-120">This step involves converting your dependencies from the legacy `packages.config` format.</span></span> <span data-ttu-id="84093-121">`packages.config`.NET Core üzerinde çalışmaz, bu nedenle paket bağımlılıklarınız varsa bu dönüştürme gereklidir.</span><span class="sxs-lookup"><span data-stu-id="84093-121">`packages.config` doesn't work on .NET Core, so this conversion is required if you have package dependencies.</span></span>

5. <span data-ttu-id="84093-122">.NET Core için yeni projeler oluşturun ve kaynak dosyaları kopyalayın veya varolan proje dosyanızı bir araçla dönüştürmeye çalışın.</span><span class="sxs-lookup"><span data-stu-id="84093-122">Create new projects for .NET Core and copy over source files, or attempt to convert your existing project file with a tool.</span></span>

   <span data-ttu-id="84093-123">.NET Core, .NET Framework'den daha basitleştirilmiş (ve farklı) bir [proje dosyası biçimi](../tools/csproj.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="84093-123">.NET Core uses a simplified (and different) [project file format](../tools/csproj.md) than .NET Framework.</span></span> <span data-ttu-id="84093-124">Devam etmek için proje dosyalarınızı bu biçime dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="84093-124">You'll need to convert your project files into this format to continue.</span></span>

6. <span data-ttu-id="84093-125">Test kodunuzu port.</span><span class="sxs-lookup"><span data-stu-id="84093-125">Port your test code.</span></span>

   <span data-ttu-id="84093-126">.NET Core'a geçiş kod tabanınızda önemli bir değişiklik olduğundan, kodunuzu üzerinde bağlantı darken testleri çalıştırabilmeniz için test projelerinizi taşımanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="84093-126">Because porting to .NET Core is such a significant change to your codebase, it's highly recommended to port your test projects so that you can run tests as you port your code over.</span></span> <span data-ttu-id="84093-127">MSTest, xUnit ve NUnit 'in tümü .NET Core üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="84093-127">MSTest, xUnit, and NUnit all work on .NET Core.</span></span>

<span data-ttu-id="84093-128">Ayrıca, [dotnet try-convert](https://github.com/dotnet/try-convert) aracıyla tek bir işlemdeki küçük çözümleri veya tek tek projeleri .NET Core proje dosya biçimine taşımayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84093-128">Additionally, you can attempt to port smaller solutions or individual projects in one operation to the .NET Core project file format with the [dotnet try-convert](https://github.com/dotnet/try-convert) tool.</span></span> <span data-ttu-id="84093-129">`dotnet try-convert`tüm projeleriniz için çalışacağı garanti edilmez ve bağlı olduğunuz davranışta ince değişikliklere neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="84093-129">`dotnet try-convert` is not guaranteed to work for all your projects, and it may cause subtle changes in behavior that you depended on.</span></span> <span data-ttu-id="84093-130">Otomatikleştirilebilen temel şeyleri otomatikleştiren bir _başlangıç noktası_ olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="84093-130">Use it as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="84093-131">Bir projeyi geçirmek için garantili bir çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="84093-131">It isn't a guaranteed solution to migrating a project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="84093-132">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="84093-132">Next steps</span></span>

>[!div class="nextstepaction"]
>[<span data-ttu-id="84093-133">Bağımlılıkları analiz edin</span><span class="sxs-lookup"><span data-stu-id="84093-133">Analyze dependencies</span></span>](third-party-deps.md)
