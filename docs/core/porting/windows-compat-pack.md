---
title: Kod la .NET Core bağlantı noktası için Windows Uyumluluk Paketini kullanma
description: Windows Uyumluluk Paketi ve varolan .NET Framework kodunu .NET Core'a bağlantı noktasına getirmek için nasıl kullanabileceğiniz hakkında bilgi edinin.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 91a653b2345d414c18ebdb6e8b7d6d49bbdbb83e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733617"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="823a9-103">Kod la .NET Core bağlantı noktası için Windows Uyumluluk Paketini kullanma</span><span class="sxs-lookup"><span data-stu-id="823a9-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="823a9-104">Varolan kodu .NET Core'a taşıma yaparken bulunan en yaygın sorunlardan bazıları, yalnızca .NET Framework'de bulunan API'lere ve teknolojilere bağımlılıktır.</span><span class="sxs-lookup"><span data-stu-id="823a9-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="823a9-105">*Windows Uyumluluk Paketi* bu teknolojilerin çoğunu sağlar, bu nedenle .NET Core uygulamaları ve .NET Standart kitaplıkları oluşturmak çok daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="823a9-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="823a9-106">Uyumluluk [paketi,.NET Standart 2.0'ın](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) API kümesini önemli ölçüde artıran mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="823a9-106">The compatibility pack is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases the API set.</span></span> <span data-ttu-id="823a9-107">Varolan kod, neredeyse hiçbir değişiklik olmadan derlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="823a9-107">Existing code compiles with almost no modifications.</span></span> <span data-ttu-id="823a9-108">"Tüm .NET uygulamalarının sağladığı API kümesi" sözünü tutmak için ,.NET Standardı kayıt defteri, Windows Yönetim Araçları (WMI) veya yansıma yayan API'ler gibi tüm platformlarda çalışamayacak teknolojileri içermez.</span><span class="sxs-lookup"><span data-stu-id="823a9-108">To keep its promise of "the set of APIs that all .NET implementations provide", .NET Standard doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span> <span data-ttu-id="823a9-109">Windows Uyumluluk Paketi .NET Standard'ın üstünde yer alan ve yalnızca Windows'a özel teknolojilere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="823a9-109">The Windows Compatibility Pack sits on top of .NET Standard and provides access to these Windows-only technologies.</span></span> <span data-ttu-id="823a9-110">Özellikle .NET Core'a geçmek isteyen ancak en azından ilk adım olarak Windows'da kalmayı planlayan müşteriler için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="823a9-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows, at least as a first step.</span></span> <span data-ttu-id="823a9-111">Bu senaryoda, yalnızca Windows teknolojilerini kullanabilmek geçiş engelini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="823a9-111">In that scenario, being able to use Windows-only technologies removes the migration hurdle.</span></span>

## <a name="package-contents"></a><span data-ttu-id="823a9-112">Paket içeriği</span><span class="sxs-lookup"><span data-stu-id="823a9-112">Package contents</span></span>

<span data-ttu-id="823a9-113">Windows Uyumluluk Paketi [Microsoft.Windows.Compatibility NuGet paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) üzerinden sağlanır ve .NET Core veya .NET Standard'ı hedefleyen projelerden başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="823a9-113">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="823a9-114">Yalnızca Windows'a özel ve aşağıdaki teknoloji alanlarından çapraz platform API'leri de dahil olmak üzere yaklaşık 20.000 API sağlar:</span><span class="sxs-lookup"><span data-stu-id="823a9-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="823a9-115">Kod Sayfaları</span><span class="sxs-lookup"><span data-stu-id="823a9-115">Code Pages</span></span>
- <span data-ttu-id="823a9-116">Codedom</span><span class="sxs-lookup"><span data-stu-id="823a9-116">CodeDom</span></span>
- <span data-ttu-id="823a9-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="823a9-117">Configuration</span></span>
- <span data-ttu-id="823a9-118">Dizin Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="823a9-118">Directory Services</span></span>
- <span data-ttu-id="823a9-119">Çizim</span><span class="sxs-lookup"><span data-stu-id="823a9-119">Drawing</span></span>
- <span data-ttu-id="823a9-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="823a9-120">ODBC</span></span>
- <span data-ttu-id="823a9-121">İzinler</span><span class="sxs-lookup"><span data-stu-id="823a9-121">Permissions</span></span>
- <span data-ttu-id="823a9-122">Bağlantı Noktaları</span><span class="sxs-lookup"><span data-stu-id="823a9-122">Ports</span></span>
- <span data-ttu-id="823a9-123">Windows Erişim Denetim Listeleri (ACL)</span><span class="sxs-lookup"><span data-stu-id="823a9-123">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="823a9-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="823a9-124">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="823a9-125">Windows Şifreleme</span><span class="sxs-lookup"><span data-stu-id="823a9-125">Windows Cryptography</span></span>
- <span data-ttu-id="823a9-126">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="823a9-126">Windows EventLog</span></span>
- <span data-ttu-id="823a9-127">Windows Yönetim Araçları (WMI)</span><span class="sxs-lookup"><span data-stu-id="823a9-127">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="823a9-128">Windows Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="823a9-128">Windows Performance Counters</span></span>
- <span data-ttu-id="823a9-129">Windows Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="823a9-129">Windows Registry</span></span>
- <span data-ttu-id="823a9-130">Windows Runtime Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="823a9-130">Windows Runtime Caching</span></span>
- <span data-ttu-id="823a9-131">Windows Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="823a9-131">Windows Services</span></span>

<span data-ttu-id="823a9-132">Daha fazla bilgi için [uyumluluk paketinin belirtimine](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="823a9-132">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="823a9-133">Başlarken</span><span class="sxs-lookup"><span data-stu-id="823a9-133">Get started</span></span>

1. <span data-ttu-id="823a9-134">Taşımadan önce, [Taşıma işlemine](index.md)bir göz attıktan emin olun.</span><span class="sxs-lookup"><span data-stu-id="823a9-134">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="823a9-135">Varolan kodu .NET Core veya .NET Standard'a taşımayaparken, [Microsoft.Windows.Compatibility NuGet paketini](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="823a9-135">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="823a9-136">Windows'da kalmak istiyorsanız, tamamen hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="823a9-136">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="823a9-137">Linux veya macOS'ta .NET Core uygulamasını veya .NET Standart kitaplığını çalıştırmak istiyorsanız, çapraz platformda çalışmayan API'lerin kullanımını bulmak için [API Analyzer'ı](../../standard/analyzers/api-analyzer.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="823a9-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="823a9-138">Bu API'lerin kullanımlarını kaldırın, platform ötesi alternatiflerle değiştirin veya aşağıdaki gibi bir platform denetimi kullanarak onları korur:</span><span class="sxs-lookup"><span data-stu-id="823a9-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="823a9-139">Bir demo için, [Windows Uyumluluk Paketi'nin Kanal 9 videosuna](https://channel9.msdn.com/Events/Connect/2017/T123)göz atın.</span><span class="sxs-lookup"><span data-stu-id="823a9-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
