---
title: .NET Core 'a bağlantı noktası için Windows Uyumluluk paketini kullanın
description: Windows Uyumluluk Paketi hakkında bilgi edinin ve mevcut .NET Framework kodunu .NET Core 'a bağlamak için nasıl kullanabileceğinizi öğrenin
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 71e390881d4e9c7836622abeed49c0ea2e5f7526
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202556"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="3874e-103">.NET Core 'a bağlantı noktası için Windows Uyumluluk paketini kullanın</span><span class="sxs-lookup"><span data-stu-id="3874e-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="3874e-104">Mevcut kodun .NET Core 'a taşıma sırasında bulunan en yaygın sorunlardan bazıları yalnızca .NET Framework bulunan API ve teknolojilerin bağımlılıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="3874e-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in the .NET Framework.</span></span> <span data-ttu-id="3874e-105">*Windows Uyumluluk Paketi* bu teknolojilerin çoğunu sağlar, bu sayede .NET Core uygulamaları ve .NET Standard kitaplıklarını derlemek çok daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="3874e-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="3874e-106">Bu paket, API kümesini önemli ölçüde artıran ve neredeyse hiçbir değişiklik yapılmaksızın mevcut kodu derlenen [.NET Standard 2,0 ' nin](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="3874e-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="3874e-107">Ancak .NET Standard taahhüdünü korumak için ("tüm .NET uygulamalarının sağladığı API kümesidir"), bu, kayıt defteri, Windows Yönetim Araçları (WMI) veya yansıma yayma gibi tüm platformlarda çalışmadığınız teknolojileri içermemektedir GetVersionEx.</span><span class="sxs-lookup"><span data-stu-id="3874e-107">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="3874e-108">*Windows Uyumluluk paketi* .NET Standard en üstünde bulunur ve yalnızca Windows olan teknolojiler için erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3874e-108">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="3874e-109">.NET Core 'a geçmek isteyen ancak ilk adım olarak Windows 'ta kalmak için plan yapmak isteyen müşteriler için özellikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="3874e-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="3874e-110">Bu senaryoda, yalnızca Windows teknolojilerini kullanamayacak, sıfır mimari avantajları olan yalnızca bir geçiş değildir.</span><span class="sxs-lookup"><span data-stu-id="3874e-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="3874e-111">Paket içeriği</span><span class="sxs-lookup"><span data-stu-id="3874e-111">Package contents</span></span>

<span data-ttu-id="3874e-112">*Windows Uyumluluk Paketi* , [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) NuGet paketi aracılığıyla sağlanır ve .NET Core veya .NET Standard hedefleyen projelerden başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="3874e-112">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="3874e-113">Aşağıdaki teknoloji alanlarından yalnızca Windows 'un yanı sıra platformlar arası API 'Ler dahil olmak üzere 20.000 API 'si sağlar:</span><span class="sxs-lookup"><span data-stu-id="3874e-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="3874e-114">Kod Sayfaları</span><span class="sxs-lookup"><span data-stu-id="3874e-114">Code Pages</span></span>
* <span data-ttu-id="3874e-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="3874e-115">CodeDom</span></span>
* <span data-ttu-id="3874e-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3874e-116">Configuration</span></span>
* <span data-ttu-id="3874e-117">Dizin Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3874e-117">Directory Services</span></span>
* <span data-ttu-id="3874e-118">İnizde</span><span class="sxs-lookup"><span data-stu-id="3874e-118">Drawing</span></span>
* <span data-ttu-id="3874e-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="3874e-119">ODBC</span></span>
* <span data-ttu-id="3874e-120">İzinler</span><span class="sxs-lookup"><span data-stu-id="3874e-120">Permissions</span></span>
* <span data-ttu-id="3874e-121">Bağlantı Noktaları</span><span class="sxs-lookup"><span data-stu-id="3874e-121">Ports</span></span>
* <span data-ttu-id="3874e-122">Windows Access Control listeleri (ACL)</span><span class="sxs-lookup"><span data-stu-id="3874e-122">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="3874e-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="3874e-123">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="3874e-124">Windows şifrelemesi</span><span class="sxs-lookup"><span data-stu-id="3874e-124">Windows Cryptography</span></span>
* <span data-ttu-id="3874e-125">Windows olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="3874e-125">Windows EventLog</span></span>
* <span data-ttu-id="3874e-126">Windows Yönetim Araçları (WMI)</span><span class="sxs-lookup"><span data-stu-id="3874e-126">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="3874e-127">Windows performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="3874e-127">Windows Performance Counters</span></span>
* <span data-ttu-id="3874e-128">Windows Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="3874e-128">Windows Registry</span></span>
* <span data-ttu-id="3874e-129">Windows Çalışma Zamanı önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="3874e-129">Windows Runtime Caching</span></span>
* <span data-ttu-id="3874e-130">Windows Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3874e-130">Windows Services</span></span>

<span data-ttu-id="3874e-131">Daha fazla bilgi için bkz. [Uyumluluk paketinin belirtimi](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="3874e-131">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="3874e-132">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="3874e-132">Get started</span></span>

1. <span data-ttu-id="3874e-133">Taşıma işleminden önce, [taşıma işlemine](index.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="3874e-133">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="3874e-134">Mevcut kodu .NET Core 'a veya .NET Standard taşıma sırasında [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)NuGet paketini yüklemek.</span><span class="sxs-lookup"><span data-stu-id="3874e-134">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="3874e-135">Windows üzerinde kalmak isterseniz, hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="3874e-135">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="3874e-136">Linux veya macOS 'ta .NET Core uygulamasını veya .NET Standard kitaplığını çalıştırmak istiyorsanız, platformlar arası çalışmayan API 'lerin kullanımını bulmak için [API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) ' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="3874e-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="3874e-137">Bu API 'lerin kullanımlarını kaldırın, bunları platformlar arası alternatifler ile değiştirin ya da şunun gibi bir platform denetimi kullanarak koruma edin:</span><span class="sxs-lookup"><span data-stu-id="3874e-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="3874e-138">Tanıtım için [Windows Uyumluluk Paketi 'Nin Channel 9 videosunu](https://channel9.msdn.com/Events/Connect/2017/T123)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="3874e-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
