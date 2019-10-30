---
title: .NET Framework 'den .NET Core 'a bağlantı noktası
description: Bir .NET Framework projesi .NET Core 'a taşıma konusunda yararlı bulabileceğiniz yardım alabileceğiniz işlem ve bulma araçlarını anlayın.
author: cartermp
ms.date: 10/22/2019
ms.custom: seodec18
ms.openlocfilehash: 89f00e5c6ce7f3cea7a3135c9b2856c54a70da40
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038526"
---
# <a name="overview-of-the-porting-process-from-net-framework-to-net-core"></a><span data-ttu-id="9c743-103">.NET Framework 'den .NET Core 'a taşıma işlemine genel bakış</span><span class="sxs-lookup"><span data-stu-id="9c743-103">Overview of the porting process from .NET Framework to .NET Core</span></span>

<span data-ttu-id="9c743-104">Şu anda .NET Core 'a taşıma konusunda ilgilendiğiniz .NET Framework çalışan bir kodunuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c743-104">You might have code that currently runs on the .NET Framework that you're interested in porting to .NET Core.</span></span> <span data-ttu-id="9c743-105">Bu makale şunları sağlar:</span><span class="sxs-lookup"><span data-stu-id="9c743-105">This article provides:</span></span>

* <span data-ttu-id="9c743-106">Taşıma işlemine genel bakış.</span><span class="sxs-lookup"><span data-stu-id="9c743-106">An overview of the porting process.</span></span>
* <span data-ttu-id="9c743-107">Kodunuzu .NET Core 'a taşırken yararlı bulabileceğiniz araçların bir listesi.</span><span class="sxs-lookup"><span data-stu-id="9c743-107">A list of the tools you may find helpful when you're porting your code to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="9c743-108">Taşıma işlemine genel bakış</span><span class="sxs-lookup"><span data-stu-id="9c743-108">Overview of the porting process</span></span>

<span data-ttu-id="9c743-109">Projenizi .NET Core 'a taşıma sırasında aşağıdaki işlemi kullanmanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="9c743-109">We recommend you to use the following process when porting your project to .NET Core:</span></span>

1. <span data-ttu-id="9c743-110">.NET Framework 4.7.2 veya üstünü hedeflemek için bağlantı noktası yapmak istediğiniz tüm projeleri yeniden hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="9c743-110">Retarget all projects you wish to port to target the .NET Framework 4.7.2 or higher.</span></span>

   <span data-ttu-id="9c743-111">Bu adım, .NET Core belirli bir API 'YI desteklemedikleri zaman .NET Framework özel hedefler için API alternatifleri kullanmanıza da sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c743-111">This step ensures that you can use API alternatives for .NET Framework-specific targets when .NET Core doesn't support a particular API.</span></span>

2. <span data-ttu-id="9c743-112">Derlemelerinizi çözümlemek ve .NET Core 'a taşınabilir olup olmadığını görmek için [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) 'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c743-112">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and see if they're portable to .NET Core.</span></span>

   <span data-ttu-id="9c743-113">API taşınabilirlik Çözümleyicisi Aracı, derlenmiş derlemelerinizi analiz eder ve bir rapor oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c743-113">The API Portability Analyzer tool analyzes your compiled assemblies and generates a report.</span></span> <span data-ttu-id="9c743-114">Bu rapor, üst düzey bir taşınabilirlik özetini ve kullanmakta olduğunuz her API 'nin, NET Core 'da kullanılamayan bir dökümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c743-114">This report shows a high-level portability summary and a breakdown of each API you're using that isn't available on NET Core.</span></span>

3. <span data-ttu-id="9c743-115">Bazı platformlarda <xref:System.PlatformNotSupportedException> oluşturan API 'Leri ve bazı diğer olası uyumluluk sorunlarını belirlemek için, projelerinize [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) 'ni yükler.</span><span class="sxs-lookup"><span data-stu-id="9c743-115">Install the [.NET API analyzer](../../standard/analyzers/api-analyzer.md) into your projects to identify APIs throwing <xref:System.PlatformNotSupportedException> on some platforms and some other potential compatibility issues.</span></span>

   <span data-ttu-id="9c743-116">Bu araç, taşınabilirlik Çözümleyicisi 'ne benzer, ancak .NET Core üzerinde şeyler oluşturabilirliğini çözümlemek yerine, çalışma zamanında <xref:System.PlatformNotSupportedException> oluşturacak şekilde bir API kullanıyorsanız analiz edilir.</span><span class="sxs-lookup"><span data-stu-id="9c743-116">This tool is similar to the portability analyzer, but instead of analyzing if things can build on .NET Core, it will analyze if you're using an API in a way that will throw the <xref:System.PlatformNotSupportedException> at runtime.</span></span> <span data-ttu-id="9c743-117">.NET Framework 4.7.2 veya üzeri bir sürümü taşıyorsanız, bu yaygın olmasa da kontrol etmeniz iyidir.</span><span class="sxs-lookup"><span data-stu-id="9c743-117">Although this isn't common if you're moving from .NET Framework 4.7.2 or higher, it's good to check.</span></span>

4. <span data-ttu-id="9c743-118">`packages.config` bağımlılıklarınızın tümünü, [Visual Studio 'daki Dönüştürme aracıyla](/nuget/consume-packages/migrate-packages-config-to-package-reference) [packagereference](/nuget/consume-packages/package-references-in-project-files) biçimine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="9c743-118">Convert all of your `packages.config` dependencies to the [PackageReference](/nuget/consume-packages/package-references-in-project-files) format with the [conversion tool in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span>

   <span data-ttu-id="9c743-119">Bu adım, eski `packages.config` biçiminden bağımlılıklarınızı dönüştürmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="9c743-119">This step involves converting your dependencies from the legacy `packages.config` format.</span></span> <span data-ttu-id="9c743-120">`packages.config`, .NET Core üzerinde çalışmaz, bu nedenle paket bağımlılıklarınız varsa bu dönüştürme gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9c743-120">`packages.config` doesn't work on .NET Core, so this conversion is required if you have package dependencies.</span></span>

5. <span data-ttu-id="9c743-121">.NET Core için yeni projeler oluşturun ve kaynak dosyaları üzerine kopyalayın veya mevcut proje dosyanızı bir araçla dönüştürmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="9c743-121">Create new projects for .NET Core and copy over source files, or attempt to convert your existing project file with a tool.</span></span>

   <span data-ttu-id="9c743-122">.NET Core .NET Framework göre Basitleştirilmiş (ve farklı) bir [Proje dosyası biçimi](../tools/csproj.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c743-122">.NET Core uses a simplified (and different) [project file format](../tools/csproj.md) than .NET Framework.</span></span> <span data-ttu-id="9c743-123">Devam etmek için proje dosyalarınızı bu biçime dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c743-123">You'll need to convert your project files into this format to continue.</span></span>

6. <span data-ttu-id="9c743-124">Test kodunuzun bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="9c743-124">Port your test code.</span></span>

   <span data-ttu-id="9c743-125">.NET Core 'a geçiş yapmak, kod tabanınızda önemli bir değişiklik olduğundan, test etmeniz, kodunuzun bağlantı noktası oluşturduğunuz gibi testler çalıştırabilmeniz için, testlerinizi almak kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="9c743-125">Because porting to .NET Core is such a significant change to your codebase, it's highly recommended to get your tests ported, so that you can run tests as you port your code over.</span></span> <span data-ttu-id="9c743-126">MSTest, xUnit ve NUnit tüm .NET Core üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="9c743-126">MSTest, xUnit, and NUnit all work on .NET Core.</span></span>

<span data-ttu-id="9c743-127">Ayrıca, bir işlemde [DotNet TRY-Convert](https://github.com/dotnet/try-convert) aracı Ile .NET Core proje dosyası biçiminde daha küçük çözümler veya ayrı projeler için bağlantı kurmayı deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c743-127">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [dotnet try-convert](https://github.com/dotnet/try-convert) tool in one operation.</span></span> <span data-ttu-id="9c743-128">`dotnet try-convert` tüm projeleriniz için çalışması garanti edilmez ve bağımlılarınızın bağlı olduğunu fark ettiğiniz davranıştaki değişikliklere neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c743-128">`dotnet try-convert` is not guaranteed to work for all your projects, and it may cause subtle changes in behavior that you may find that you depended on.</span></span> <span data-ttu-id="9c743-129">Otomatikleştirilmiş olabilecek temel şeyleri otomatikleştiren bir _Başlangıç noktası_ olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c743-129">It should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="9c743-130">Projenin geçirilmesi için garantili bir çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="9c743-130">It isn't a guaranteed solution to migrating a project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="9c743-131">Next</span><span class="sxs-lookup"><span data-stu-id="9c743-131">Next</span></span>](net-framework-tech-unavailable.md)
