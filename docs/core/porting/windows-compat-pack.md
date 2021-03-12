---
title: Bağlantı noktası kodu için Windows Uyumluluk Paketi 'ni kullanma
description: Windows Uyumluluk Paketi hakkında bilgi edinin ve bunu kullanarak .NET 5 ve .NET Core 3,1 ' ye mevcut .NET Framework kodu bağlantı noktası oluşturabilirsiniz.
author: terrajobst
ms.date: 03/04/2021
ms.openlocfilehash: c90cc960cd9ff3707877afc023f95e0e03716aab
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604820"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-5"></a><span data-ttu-id="47776-103">.NET 5 + için Windows Uyumluluk Paketi ' ni kullanarak bağlantı noktası kodu</span><span class="sxs-lookup"><span data-stu-id="47776-103">Use the Windows Compatibility Pack to port code to .NET 5+</span></span>

<span data-ttu-id="47776-104">.NET Framework mevcut kodu .NET 'e taşırken bulunan en yaygın sorunlardan bazıları, yalnızca .NET Framework bulunan API ve teknolojilerin bağımlılıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="47776-104">Some of the most common issues found when porting existing code from .NET Framework to .NET are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="47776-105">*Windows Uyumluluk Paketi* bu teknolojilerin çoğunu sağlar, bu sayede .NET uygulamaları ve .NET Standard kitaplıklarını derlemek çok daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="47776-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET applications and .NET Standard libraries.</span></span>

<span data-ttu-id="47776-106">Uyumluluk Paketi, API kümesini önemli ölçüde artıran [.NET Standard 2,0 ' nin](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) bir mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="47776-106">The compatibility pack is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases the API set.</span></span> <span data-ttu-id="47776-107">Mevcut kod, neredeyse hiçbir değişiklik ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="47776-107">Existing code compiles with almost no modifications.</span></span> <span data-ttu-id="47776-108">"Tüm .NET uygulamalarının sağladığı API 'Ler kümesi" taahhüdünü sürdürmek için .NET Standard, kayıt defteri, Windows Yönetim Araçları (WMI) veya yansıma yayma API 'Leri gibi tüm platformlarda çalışmayan teknolojiler içermez.</span><span class="sxs-lookup"><span data-stu-id="47776-108">To keep its promise of "the set of APIs that all .NET implementations provide", .NET Standard doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span> <span data-ttu-id="47776-109">Windows Uyumluluk Paketi .NET Standard en üstünde bulunur ve yalnızca bu Windows teknolojilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="47776-109">The Windows Compatibility Pack sits on top of .NET Standard and provides access to these Windows-only technologies.</span></span> <span data-ttu-id="47776-110">Özellikle .NET 'e geçmek isteyen ancak en azından ilk bir adım olarak Windows 'ta kalmak için plan yapmak isteyen müşteriler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="47776-110">It's especially useful for customers that want to move to .NET but plan to stay on Windows, at least as a first step.</span></span> <span data-ttu-id="47776-111">Bu senaryoda, yalnızca Windows teknolojilerini kullanabilirsiniz geçiş ' i ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="47776-111">In that scenario, you can use Windows-only technologies removes the migration hurdle.</span></span>

## <a name="package-contents"></a><span data-ttu-id="47776-112">Paket içeriği</span><span class="sxs-lookup"><span data-stu-id="47776-112">Package contents</span></span>

<span data-ttu-id="47776-113">Windows Uyumluluk Paketi, [Microsoft. Windows. Compatibility NuGet paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) aracılığıyla sağlanır ve .net veya .NET Standard hedef olan projelerden başvurulabilirler.</span><span class="sxs-lookup"><span data-stu-id="47776-113">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET or .NET Standard.</span></span>

<span data-ttu-id="47776-114">Aşağıdaki teknoloji alanlarından yalnızca Windows ve platformlar arası API 'Ler dahil olmak üzere 20.000 API 'si sağlar:</span><span class="sxs-lookup"><span data-stu-id="47776-114">It provides about 20,000 APIs, including Windows-only and cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="47776-115">Kod Sayfaları</span><span class="sxs-lookup"><span data-stu-id="47776-115">Code Pages</span></span>
- <span data-ttu-id="47776-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="47776-116">CodeDom</span></span>
- <span data-ttu-id="47776-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47776-117">Configuration</span></span>
- <span data-ttu-id="47776-118">Dizin Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="47776-118">Directory Services</span></span>
- <span data-ttu-id="47776-119">Çizim</span><span class="sxs-lookup"><span data-stu-id="47776-119">Drawing</span></span>
- <span data-ttu-id="47776-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="47776-120">ODBC</span></span>
- <span data-ttu-id="47776-121">İzinler</span><span class="sxs-lookup"><span data-stu-id="47776-121">Permissions</span></span>
- <span data-ttu-id="47776-122">Bağlantı noktaları</span><span class="sxs-lookup"><span data-stu-id="47776-122">Ports</span></span>
- <span data-ttu-id="47776-123">Windows Access Control listeleri (ACL)</span><span class="sxs-lookup"><span data-stu-id="47776-123">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="47776-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="47776-124">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="47776-125">Windows şifrelemesi</span><span class="sxs-lookup"><span data-stu-id="47776-125">Windows Cryptography</span></span>
- <span data-ttu-id="47776-126">Windows olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="47776-126">Windows EventLog</span></span>
- <span data-ttu-id="47776-127">Windows Yönetim Araçları (WMI)</span><span class="sxs-lookup"><span data-stu-id="47776-127">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="47776-128">Windows performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="47776-128">Windows Performance Counters</span></span>
- <span data-ttu-id="47776-129">Windows Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="47776-129">Windows Registry</span></span>
- <span data-ttu-id="47776-130">Windows Çalışma Zamanı önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="47776-130">Windows Runtime Caching</span></span>
- <span data-ttu-id="47776-131">Windows Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="47776-131">Windows Services</span></span>

<span data-ttu-id="47776-132">Daha fazla bilgi için bkz. [Uyumluluk paketinin belirtimi](https://github.com/dotnet/designs/blob/master/accepted/2018/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="47776-132">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/2018/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="47776-133">başlarken</span><span class="sxs-lookup"><span data-stu-id="47776-133">Get started</span></span>

1. <span data-ttu-id="47776-134">Taşıma işleminden önce, [taşıma işlemine](index.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="47776-134">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="47776-135">Mevcut kodu .NET veya .NET Standard taşırken, [Microsoft. Windows. Compatibility NuGet paketini](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)yükler.</span><span class="sxs-lookup"><span data-stu-id="47776-135">When porting existing code to .NET or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="47776-136">Windows üzerinde kalmak isterseniz, hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="47776-136">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="47776-137">Linux veya macOS 'ta .NET uygulamasını veya .NET Standard kitaplığını çalıştırmak istiyorsanız, [API Analyzer](../../standard/analyzers/api-analyzer.md) ' ı kullanarak platformlar arası çalışmayan API 'lerin kullanımını bulun.</span><span class="sxs-lookup"><span data-stu-id="47776-137">If you want to run the .NET application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="47776-138">Bu API 'lerin kullanımlarını kaldırın, bunları platformlar arası alternatifler ile değiştirin ya da şunun gibi bir platform denetimi kullanarak koruma edin:</span><span class="sxs-lookup"><span data-stu-id="47776-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

<span data-ttu-id="47776-139">Tanıtım için [Windows Uyumluluk Paketi 'Nin Channel 9 videosunu](https://channel9.msdn.com/Events/Connect/2017/T123)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="47776-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

## <a name="see-also"></a><span data-ttu-id="47776-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47776-140">See also</span></span>

- [<span data-ttu-id="47776-141">.NET Framework .NET 'a taşıma hakkında genel bakış</span><span class="sxs-lookup"><span data-stu-id="47776-141">Overview of porting from .NET Framework to .NET</span></span>](index.md)
- [<span data-ttu-id="47776-142">ASP.NET Core geçişe ASP.NET</span><span class="sxs-lookup"><span data-stu-id="47776-142">ASP.NET to ASP.NET Core migration</span></span>](/aspnet/core/migration/proper-to-2x)
- [<span data-ttu-id="47776-143">.NET Framework WPF uygulamalarını .NET 'e geçirme</span><span class="sxs-lookup"><span data-stu-id="47776-143">Migrate .NET Framework WPF apps to .NET</span></span>](/dotnet/desktop/wpf/migration/convert-project-from-net-framework?view=netdesktop-5.0&preserve-view=true)
- [<span data-ttu-id="47776-144">.NET Framework Windows Forms uygulamalarını .NET 'a geçirme</span><span class="sxs-lookup"><span data-stu-id="47776-144">Migrate .NET Framework Windows Forms apps to .NET</span></span>](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
- [<span data-ttu-id="47776-145">.NET için bağlantı noktası .NET Framework kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="47776-145">Port .NET Framework libraries to .NET</span></span>](libraries.md)
