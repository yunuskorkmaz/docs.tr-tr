---
title: Windows Uyumluluk Paketi kullanılarak .NET çekirdek - bağlantı noktası oluşturma
description: Windows Uyumluluk Paketi hakkında bilgi edinmek ve nasıl, kullanabilir, .NET Core için var olan .NET Framework koda bağlantı noktası
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 4ef7d9c847d48ae7bbb2d553b1c05cb90a1c5a7a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="using-the-windows-compatibility-pack"></a><span data-ttu-id="507d8-103">Windows Uyumluluk Paketi kullanma</span><span class="sxs-lookup"><span data-stu-id="507d8-103">Using the Windows Compatibility Pack</span></span>

<span data-ttu-id="507d8-104">.NET Core, var olan kodu bağlantı noktası oluşturma, geliştiriciler yüz en yaygın sorunları API'leri ve yalnızca .NET Framework mevcut teknolojiler üzerinde bağımlı biridir.</span><span class="sxs-lookup"><span data-stu-id="507d8-104">One of the most common issues that developers face when porting their existing code to .NET Core is that they depend on APIs and technologies that only exist in the .NET Framework.</span></span> <span data-ttu-id="507d8-105">*Windows Uyumluluk Paketi* .NET standart kitaplıkları yanı sıra .NET Core uygulamalar oluşturmak için var olan kodu daha uygun hale bu teknolojilerin birçoğu sağlamanın hakkında sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="507d8-105">The *Windows Compatibility Pack* is about providing many of these technologies so that building .NET Core applications as well as .NET Standard libraries becomes much more viable for existing code.</span></span>

<span data-ttu-id="507d8-106">Bu mantıksal bir pakettir [.NET standart 2.0 uzantısı](../whats-new/index.md#api-changes-and-library-support) önemli ölçüde artırır API kümesi ve var olan kodu derlendiğinden emin neredeyse hiçbir değişikliğe.</span><span class="sxs-lookup"><span data-stu-id="507d8-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/index.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="507d8-107">Ancak .NET Standard promise tutmak için ("tüm .NET uygulamalarını API kümesi olmasından"), bu kayıt defteri gibi tüm platformlarda Windows Yönetim Araçları (WMI) çalışamaz teknolojileri eklemediniz veya yansıma yayma API'ler.</span><span class="sxs-lookup"><span data-stu-id="507d8-107">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="507d8-108">*Windows Uyumluluk Paketi* .NET standart üstünde bulunur ve Windows yalnızca teknolojileri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="507d8-108">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="507d8-109">.NET Core ancak Windows bir ilk adım olarak kalmak için plan taşımak istediğiniz müşteriler için özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="507d8-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="507d8-110">Bu senaryoda, yalnızca Windows teknolojileri kullanan yazdıramama yalnızca geçiş hurdle sıfır mimari avantajları sahip olur.</span><span class="sxs-lookup"><span data-stu-id="507d8-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="507d8-111">Paket içeriğini</span><span class="sxs-lookup"><span data-stu-id="507d8-111">Package contents</span></span>

<span data-ttu-id="507d8-112">*Windows Uyumluluk Paketi* NuGet paketi üzerinden sağlanan [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) ve .NET Core veya .NET standart hedefleme projelerden başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="507d8-112">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="507d8-113">20. 000'hakkında bilgi sağlayan aşağıdaki teknoloji alanlarına yalnızca Windows hem de platformlar arası API'lerden dahil olmak üzere API:</span><span class="sxs-lookup"><span data-stu-id="507d8-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="507d8-114">Kod Sayfaları</span><span class="sxs-lookup"><span data-stu-id="507d8-114">Code Pages</span></span>
* <span data-ttu-id="507d8-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="507d8-115">CodeDom</span></span>
* <span data-ttu-id="507d8-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="507d8-116">Configuration</span></span>
* <span data-ttu-id="507d8-117">Dizin Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="507d8-117">Directory Services</span></span>
* <span data-ttu-id="507d8-118">Çizim</span><span class="sxs-lookup"><span data-stu-id="507d8-118">Drawing</span></span>
* <span data-ttu-id="507d8-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="507d8-119">ODBC</span></span>
* <span data-ttu-id="507d8-120">İzinler</span><span class="sxs-lookup"><span data-stu-id="507d8-120">Permissions</span></span>
* <span data-ttu-id="507d8-121">Bağlantı noktaları</span><span class="sxs-lookup"><span data-stu-id="507d8-121">Ports</span></span>
* <span data-ttu-id="507d8-122">Windows erişim denetim listeleri (ACL)</span><span class="sxs-lookup"><span data-stu-id="507d8-122">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="507d8-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="507d8-123">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="507d8-124">Windows şifrelemesi</span><span class="sxs-lookup"><span data-stu-id="507d8-124">Windows Cryptography</span></span>
* <span data-ttu-id="507d8-125">Windows olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="507d8-125">Windows EventLog</span></span>
* <span data-ttu-id="507d8-126">Windows Yönetim Araçları (WMI)</span><span class="sxs-lookup"><span data-stu-id="507d8-126">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="507d8-127">Windows performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="507d8-127">Windows Performance Counters</span></span>
* <span data-ttu-id="507d8-128">Windows Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="507d8-128">Windows Registry</span></span>
* <span data-ttu-id="507d8-129">Windows çalışma zamanı önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="507d8-129">Windows Runtime Caching</span></span>
* <span data-ttu-id="507d8-130">Windows Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="507d8-130">Windows Services</span></span>

<span data-ttu-id="507d8-131">Daha fazla bilgi için bkz: [uyumluluk paketinin belirtim](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="507d8-131">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="507d8-132">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="507d8-132">Get started</span></span>

1. <span data-ttu-id="507d8-133">Bağlantı noktası oluşturma önce bir göz atalım emin olun [bağlantı noktası oluşturma işlemi](index.md).</span><span class="sxs-lookup"><span data-stu-id="507d8-133">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="507d8-134">.NET Core veya .NET standart varolan kod bağlantı noktası oluşturma, NuGet paket yüklemesi [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="507d8-134">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="507d8-135">Windows üzerinde kalmasını istiyorsanız, başlamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="507d8-135">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="507d8-136">.NET Core uygulama veya .NET standart kitaplığı, Linux veya macOS çalıştırmak istiyorsanız, kullanmak [API Çözümleyicisi](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) platformlar arası çalışmaz API'leri kullanımını bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="507d8-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="507d8-137">Bu API kullanımları kaldırma, platformlar arası seçenekleri ile değiştirin ya da bunları gibi bir platform denetimi kullanarak koruma:</span><span class="sxs-lookup"><span data-stu-id="507d8-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="507d8-138">Gösteri için kullanıma [Windows uyumluluk paketinin Channel 9 video](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="507d8-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

