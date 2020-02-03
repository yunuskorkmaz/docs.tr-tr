---
title: .NET Core 'a bağlantı noktası için Windows Uyumluluk paketini kullanın
description: Windows Uyumluluk Paketi hakkında bilgi edinin ve onu .NET Core 'a mevcut .NET Framework kodu ile bağlantı noktası için nasıl kullanabileceğinizi öğrenin.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 91a653b2345d414c18ebdb6e8b7d6d49bbdbb83e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733617"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="44c65-103">.NET Core 'a bağlantı noktası için Windows Uyumluluk paketini kullanın</span><span class="sxs-lookup"><span data-stu-id="44c65-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="44c65-104">Mevcut kodun .NET Core 'a taşıma sırasında bulunan en yaygın sorunlardan bazıları yalnızca .NET Framework bulunan API ve teknolojilerin bağımlılıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="44c65-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="44c65-105">*Windows Uyumluluk Paketi* bu teknolojilerin çoğunu sağlar, bu sayede .NET Core uygulamaları ve .NET Standard kitaplıklarını derlemek çok daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="44c65-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="44c65-106">Uyumluluk Paketi, API kümesini önemli ölçüde artıran [.NET Standard 2,0 ' nin](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) bir mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="44c65-106">The compatibility pack is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases the API set.</span></span> <span data-ttu-id="44c65-107">Mevcut kod, neredeyse hiçbir değişiklik ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="44c65-107">Existing code compiles with almost no modifications.</span></span> <span data-ttu-id="44c65-108">"Tüm .NET uygulamalarının sağladığı API 'Ler kümesi" taahhüdünü sürdürmek için .NET Standard, kayıt defteri, Windows Yönetim Araçları (WMI) veya yansıma yayma API 'Leri gibi tüm platformlarda çalışmayan teknolojiler içermez.</span><span class="sxs-lookup"><span data-stu-id="44c65-108">To keep its promise of "the set of APIs that all .NET implementations provide", .NET Standard doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span> <span data-ttu-id="44c65-109">Windows Uyumluluk Paketi .NET Standard en üstünde bulunur ve yalnızca bu Windows teknolojilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="44c65-109">The Windows Compatibility Pack sits on top of .NET Standard and provides access to these Windows-only technologies.</span></span> <span data-ttu-id="44c65-110">Özellikle .NET Core 'a geçmek isteyen ancak en azından ilk bir adım olarak Windows 'ta kalmak için plan yapmak isteyen müşteriler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="44c65-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows, at least as a first step.</span></span> <span data-ttu-id="44c65-111">Bu senaryoda, yalnızca Windows teknolojilerini kullanabilmek, geçişi ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="44c65-111">In that scenario, being able to use Windows-only technologies removes the migration hurdle.</span></span>

## <a name="package-contents"></a><span data-ttu-id="44c65-112">Paket içeriği</span><span class="sxs-lookup"><span data-stu-id="44c65-112">Package contents</span></span>

<span data-ttu-id="44c65-113">Windows Uyumluluk Paketi, [Microsoft. Windows. Compatibility NuGet paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) aracılığıyla sağlanır ve .NET Core veya .NET Standard ' i hedefleyen projelerden başvurulabilirler.</span><span class="sxs-lookup"><span data-stu-id="44c65-113">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="44c65-114">Aşağıdaki teknoloji alanlarından yalnızca Windows 'un yanı sıra platformlar arası API 'Ler dahil olmak üzere 20.000 API 'si sağlar:</span><span class="sxs-lookup"><span data-stu-id="44c65-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="44c65-115">Kod Sayfaları</span><span class="sxs-lookup"><span data-stu-id="44c65-115">Code Pages</span></span>
- <span data-ttu-id="44c65-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="44c65-116">CodeDom</span></span>
- <span data-ttu-id="44c65-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="44c65-117">Configuration</span></span>
- <span data-ttu-id="44c65-118">Dizin Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="44c65-118">Directory Services</span></span>
- <span data-ttu-id="44c65-119">İnizde</span><span class="sxs-lookup"><span data-stu-id="44c65-119">Drawing</span></span>
- <span data-ttu-id="44c65-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="44c65-120">ODBC</span></span>
- <span data-ttu-id="44c65-121">İzinler</span><span class="sxs-lookup"><span data-stu-id="44c65-121">Permissions</span></span>
- <span data-ttu-id="44c65-122">Bağlantı Noktaları</span><span class="sxs-lookup"><span data-stu-id="44c65-122">Ports</span></span>
- <span data-ttu-id="44c65-123">Windows Access Control listeleri (ACL)</span><span class="sxs-lookup"><span data-stu-id="44c65-123">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="44c65-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="44c65-124">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="44c65-125">Windows şifrelemesi</span><span class="sxs-lookup"><span data-stu-id="44c65-125">Windows Cryptography</span></span>
- <span data-ttu-id="44c65-126">Windows olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="44c65-126">Windows EventLog</span></span>
- <span data-ttu-id="44c65-127">Windows Yönetim Araçları (WMI)</span><span class="sxs-lookup"><span data-stu-id="44c65-127">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="44c65-128">Windows Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="44c65-128">Windows Performance Counters</span></span>
- <span data-ttu-id="44c65-129">Windows Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="44c65-129">Windows Registry</span></span>
- <span data-ttu-id="44c65-130">Windows Çalışma Zamanı önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="44c65-130">Windows Runtime Caching</span></span>
- <span data-ttu-id="44c65-131">Windows Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="44c65-131">Windows Services</span></span>

<span data-ttu-id="44c65-132">Daha fazla bilgi için bkz. [Uyumluluk paketinin belirtimi](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="44c65-132">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="44c65-133">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="44c65-133">Get started</span></span>

1. <span data-ttu-id="44c65-134">Taşıma işleminden önce, [taşıma işlemine](index.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="44c65-134">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="44c65-135">Mevcut kodu .NET Core 'a veya .NET Standard taşırken, [Microsoft. Windows. Compatibility NuGet paketini](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)yükledikten sonra.</span><span class="sxs-lookup"><span data-stu-id="44c65-135">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="44c65-136">Windows üzerinde kalmak isterseniz, hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="44c65-136">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="44c65-137">Linux veya macOS 'ta .NET Core uygulamasını veya .NET Standard kitaplığını çalıştırmak istiyorsanız, platformlar arası çalışmayan API 'lerin kullanımını bulmak için [API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) ' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="44c65-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="44c65-138">Bu API 'lerin kullanımlarını kaldırın, bunları platformlar arası alternatifler ile değiştirin ya da şunun gibi bir platform denetimi kullanarak koruma edin:</span><span class="sxs-lookup"><span data-stu-id="44c65-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="44c65-139">Tanıtım için [Windows Uyumluluk Paketi 'Nin Channel 9 videosunu](https://channel9.msdn.com/Events/Connect/2017/T123)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="44c65-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
