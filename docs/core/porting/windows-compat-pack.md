---
title: .NET Core 'a bağlantı noktası için Windows Uyumluluk paketini kullanın
description: Windows Uyumluluk Paketi hakkında bilgi edinin ve onu .NET Core 'a mevcut .NET Framework kodu ile bağlantı noktası için nasıl kullanabileceğinizi öğrenin.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 65530987a3cded941b6a292118ed9bfdb6f5b86c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715475"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="4b76d-103">.NET Core 'a bağlantı noktası için Windows Uyumluluk paketini kullanın</span><span class="sxs-lookup"><span data-stu-id="4b76d-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="4b76d-104">Mevcut kodun .NET Core 'a taşıma sırasında bulunan en yaygın sorunlardan bazıları yalnızca .NET Framework bulunan API ve teknolojilerin bağımlılıklarıdır.</span><span class="sxs-lookup"><span data-stu-id="4b76d-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="4b76d-105">*Windows Uyumluluk Paketi* bu teknolojilerin çoğunu sağlar, bu sayede .NET Core uygulamaları ve .NET Standard kitaplıklarını derlemek çok daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="4b76d-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="4b76d-106">Bu paket, API kümesini önemli ölçüde artıran ve neredeyse hiçbir değişiklik yapılmaksızın mevcut kodu derlenen [.NET Standard 2,0 ' nin](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="4b76d-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="4b76d-107">.NET Standard taahhüdünü korumak için ("tüm .NET uygulamalarının sağladığı API kümesidir"), paket kayıt defteri, Windows Yönetim Araçları (WMI) veya yansıma yayma gibi tüm platformlarda çalışmayan teknolojiler içermez GetVersionEx.</span><span class="sxs-lookup"><span data-stu-id="4b76d-107">In order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), the pack doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="4b76d-108">Windows Uyumluluk Paketi .NET Standard en üstünde bulunur ve yalnızca Windows olan teknolojiler için erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b76d-108">The Windows Compatibility Pack sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="4b76d-109">.NET Core 'a geçmek isteyen ancak ilk adım olarak Windows 'ta kalmak için plan yapmak isteyen müşteriler için özellikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b76d-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="4b76d-110">Bu senaryoda yalnızca Windows teknolojilerini kullanamayacak, mimari avantajsız yalnızca bir geçiş değildir.</span><span class="sxs-lookup"><span data-stu-id="4b76d-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with no architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="4b76d-111">Paket içeriği</span><span class="sxs-lookup"><span data-stu-id="4b76d-111">Package contents</span></span>

<span data-ttu-id="4b76d-112">Windows Uyumluluk Paketi, [Microsoft. Windows. Compatibility NuGet paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) aracılığıyla sağlanır ve .NET Core veya .NET Standard ' i hedefleyen projelerden başvurulabilirler.</span><span class="sxs-lookup"><span data-stu-id="4b76d-112">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="4b76d-113">Aşağıdaki teknoloji alanlarından yalnızca Windows 'un yanı sıra platformlar arası API 'Ler dahil olmak üzere 20.000 API 'si sağlar:</span><span class="sxs-lookup"><span data-stu-id="4b76d-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="4b76d-114">Kod Sayfaları</span><span class="sxs-lookup"><span data-stu-id="4b76d-114">Code Pages</span></span>
- <span data-ttu-id="4b76d-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="4b76d-115">CodeDom</span></span>
- <span data-ttu-id="4b76d-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4b76d-116">Configuration</span></span>
- <span data-ttu-id="4b76d-117">Dizin Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="4b76d-117">Directory Services</span></span>
- <span data-ttu-id="4b76d-118">Çizim</span><span class="sxs-lookup"><span data-stu-id="4b76d-118">Drawing</span></span>
- <span data-ttu-id="4b76d-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="4b76d-119">ODBC</span></span>
- <span data-ttu-id="4b76d-120">İzinler</span><span class="sxs-lookup"><span data-stu-id="4b76d-120">Permissions</span></span>
- <span data-ttu-id="4b76d-121">Bağlantı noktaları</span><span class="sxs-lookup"><span data-stu-id="4b76d-121">Ports</span></span>
- <span data-ttu-id="4b76d-122">Windows Access Control listeleri (ACL)</span><span class="sxs-lookup"><span data-stu-id="4b76d-122">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="4b76d-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="4b76d-123">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="4b76d-124">Windows şifrelemesi</span><span class="sxs-lookup"><span data-stu-id="4b76d-124">Windows Cryptography</span></span>
- <span data-ttu-id="4b76d-125">Windows olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="4b76d-125">Windows EventLog</span></span>
- <span data-ttu-id="4b76d-126">Windows Yönetim Araçları (WMI)</span><span class="sxs-lookup"><span data-stu-id="4b76d-126">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="4b76d-127">Windows Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="4b76d-127">Windows Performance Counters</span></span>
- <span data-ttu-id="4b76d-128">Windows Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="4b76d-128">Windows Registry</span></span>
- <span data-ttu-id="4b76d-129">Windows Çalışma Zamanı önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="4b76d-129">Windows Runtime Caching</span></span>
- <span data-ttu-id="4b76d-130">Windows Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="4b76d-130">Windows Services</span></span>

<span data-ttu-id="4b76d-131">Daha fazla bilgi için bkz. [Uyumluluk paketinin belirtimi](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="4b76d-131">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="4b76d-132">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="4b76d-132">Get started</span></span>

1. <span data-ttu-id="4b76d-133">Taşıma işleminden önce, [taşıma işlemine](index.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="4b76d-133">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="4b76d-134">Mevcut kodu .NET Core 'a veya .NET Standard taşırken, [Microsoft. Windows. Compatibility NuGet paketini](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)yükledikten sonra.</span><span class="sxs-lookup"><span data-stu-id="4b76d-134">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="4b76d-135">Windows üzerinde kalmak isterseniz, hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="4b76d-135">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="4b76d-136">Linux veya macOS 'ta .NET Core uygulamasını veya .NET Standard kitaplığını çalıştırmak istiyorsanız, platformlar arası çalışmayan API 'lerin kullanımını bulmak için [API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) ' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b76d-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="4b76d-137">Bu API 'lerin kullanımlarını kaldırın, bunları platformlar arası alternatifler ile değiştirin ya da şunun gibi bir platform denetimi kullanarak koruma edin:</span><span class="sxs-lookup"><span data-stu-id="4b76d-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="4b76d-138">Tanıtım için [Windows Uyumluluk Paketi 'Nin Channel 9 videosunu](https://channel9.msdn.com/Events/Connect/2017/T123)inceleyin.</span><span class="sxs-lookup"><span data-stu-id="4b76d-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
