---
title: .NET Core kod bağlantı noktası için Windows Uyumluluk Paketi kullanma
description: Windows Uyumluluk Paketi hakkında bilgi edinmek ve nasıl, kullanabilir, bağlantı noktası var olan .NET Framework kodu .NET Core için
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: c4fd888e0fbce86ab317f18fd77374af5d3ca244
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717901"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="dda77-103">.NET Core kod bağlantı noktası için Windows Uyumluluk Paketi kullanma</span><span class="sxs-lookup"><span data-stu-id="dda77-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="dda77-104">.NET Core için mevcut kodu taşıyorsanız, bulunan en yaygın sorunlardan bazılarını, API ve .NET Framework yalnızca bulunur teknolojilerini bağımlılıklardır.</span><span class="sxs-lookup"><span data-stu-id="dda77-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in the .NET Framework.</span></span> <span data-ttu-id="dda77-105">*Windows Uyumluluk Paketi* .NET Core uygulamaları ve .NET standart kitaplıkları oluşturmak çok daha kolay olacak şekilde bu teknolojilerin birçoğu sağlar.</span><span class="sxs-lookup"><span data-stu-id="dda77-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="dda77-106">Bu mantıksal bir pakettir [.NET Standard 2.0 uzantısı](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) önemli ölçüde artar API kümesi ve varolan kodu derlendiğinden emin neredeyse değişikliğe.</span><span class="sxs-lookup"><span data-stu-id="dda77-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="dda77-107">Ancak .NET Standard'ın promise tutulabilmesi için ("tüm .NET uygulamalarında sağlayan API kümesi sağlıyor"), bu kayıt defteri gibi tüm platformlarda Windows Yönetim Araçları (WMI) çalışamaz teknolojileri eklemediğiniz veya yansıma yayma API'ler.</span><span class="sxs-lookup"><span data-stu-id="dda77-107">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="dda77-108">*Windows Uyumluluk Paketi* .NET Standard en üstünde yer alan ve Windows sadece teknolojileri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="dda77-108">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="dda77-109">.NET Core ancak bir ilk adım Windows kalabilmek için plan taşımak istediğiniz müşteriler özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="dda77-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="dda77-110">Bu senaryoda yalnızca Windows teknolojileri kullanacak şekilde boyutlandırılmamışsa, yalnızca bir geçiş hurdle sıfır mimari avantajlarla olur.</span><span class="sxs-lookup"><span data-stu-id="dda77-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="dda77-111">Paket içeriği</span><span class="sxs-lookup"><span data-stu-id="dda77-111">Package contents</span></span>

<span data-ttu-id="dda77-112">*Windows Uyumluluk Paketi* NuGet paketi sağlanan [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) ve .NET Core veya .NET Standard hedefleyen projeleri başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="dda77-112">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="dda77-113">Yaklaşık 20. 000 sağladığı API'leri, yalnızca Windows yanı platformlar arası API'lerinden aşağıdaki teknoloji alanları dahil olmak üzere:</span><span class="sxs-lookup"><span data-stu-id="dda77-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="dda77-114">Kod Sayfaları</span><span class="sxs-lookup"><span data-stu-id="dda77-114">Code Pages</span></span>
* <span data-ttu-id="dda77-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="dda77-115">CodeDom</span></span>
* <span data-ttu-id="dda77-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dda77-116">Configuration</span></span>
* <span data-ttu-id="dda77-117">Dizin Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="dda77-117">Directory Services</span></span>
* <span data-ttu-id="dda77-118">Çizim</span><span class="sxs-lookup"><span data-stu-id="dda77-118">Drawing</span></span>
* <span data-ttu-id="dda77-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="dda77-119">ODBC</span></span>
* <span data-ttu-id="dda77-120">İzinler</span><span class="sxs-lookup"><span data-stu-id="dda77-120">Permissions</span></span>
* <span data-ttu-id="dda77-121">Bağlantı Noktaları</span><span class="sxs-lookup"><span data-stu-id="dda77-121">Ports</span></span>
* <span data-ttu-id="dda77-122">Windows erişim denetim listeleri (ACL)</span><span class="sxs-lookup"><span data-stu-id="dda77-122">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="dda77-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="dda77-123">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="dda77-124">Windows şifreleme</span><span class="sxs-lookup"><span data-stu-id="dda77-124">Windows Cryptography</span></span>
* <span data-ttu-id="dda77-125">Windows olay günlüğü</span><span class="sxs-lookup"><span data-stu-id="dda77-125">Windows EventLog</span></span>
* <span data-ttu-id="dda77-126">Windows Yönetim Araçları (WMI)</span><span class="sxs-lookup"><span data-stu-id="dda77-126">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="dda77-127">Windows performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="dda77-127">Windows Performance Counters</span></span>
* <span data-ttu-id="dda77-128">Windows Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="dda77-128">Windows Registry</span></span>
* <span data-ttu-id="dda77-129">Windows çalışma zamanı önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="dda77-129">Windows Runtime Caching</span></span>
* <span data-ttu-id="dda77-130">Windows Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="dda77-130">Windows Services</span></span>

<span data-ttu-id="dda77-131">Daha fazla bilgi için [uyumluluk paketinin belirtim](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="dda77-131">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="dda77-132">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="dda77-132">Get started</span></span>

1. <span data-ttu-id="dda77-133">Taşıma önce göz atın emin olun [taşıma işlemi](index.md).</span><span class="sxs-lookup"><span data-stu-id="dda77-133">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="dda77-134">.NET Core veya .NET Standard için mevcut kodu taşıyorsanız, NuGet paketini yüklemek [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="dda77-134">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="dda77-135">Windows üzerinde kalmak istiyorsanız, başlamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="dda77-135">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="dda77-136">Linux veya Macos'ta .NET Core uygulaması veya .NET Standard kitaplığı çalıştırmak istediğiniz kullanırsanız [API Çözümleyicisi](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) platformlar arası çalışmaz API kullanım bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="dda77-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="dda77-137">Bu API kullanımları Kaldır, bunları platformlar arası alternatif ile değiştirin veya gibi bir platform denetimi kullanarak bunları koruma:</span><span class="sxs-lookup"><span data-stu-id="dda77-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="dda77-138">Bir tanıtım için kullanıma [Windows Uyumluluk Paketi Channel 9 video](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="dda77-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
