---
title: 'Son değişiklik: Kestrel: çalışma zamanında varsayılan olarak algılanan yapılandırma değişiklikleri'
description: "Kestrel başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: varsayılan olarak algılanan çalışma sırasında yapılandırma değişiklikleri"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 2e879f020dd108baa14fa8ff67dee7b948209faf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761346"
---
# <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a><span data-ttu-id="4bdb4-103">Kestrel: çalışma zamanında varsayılan olarak algılanan yapılandırma değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="4bdb4-103">Kestrel: Configuration changes at run time detected by default</span></span>

<span data-ttu-id="4bdb4-104">Kestrel şimdi `Kestrel` `IConfiguration` , çalışma zamanında projenin örneğinin bölümünde yapılan değişikliklere (örneğin, *appsettings.jsaçık*) yeniden davranır.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-104">Kestrel now reacts to changes made to the `Kestrel` section of the project's `IConfiguration` instance (for example, *appsettings.json*) at run time.</span></span> <span data-ttu-id="4bdb4-105">*Üzerindeappsettings.js* kullanarak Kestrel yapılandırma hakkında daha fazla bilgi edinmek Için [uç nokta yapılandırması](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration)'nda *appsettings.jshakkında* bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-105">To learn more about how to configure Kestrel using *appsettings.json*, see the *appsettings.json* example in [Endpoint configuration](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span></span>

<span data-ttu-id="4bdb4-106">Kestrel, bu yapılandırma değişikliklerine tepki vermek için uç noktaları gerektiği şekilde bağlar, çözer ve yeniden bağlayın.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-106">Kestrel will bind, unbind, and rebind endpoints as necessary to react to these configuration changes.</span></span>

<span data-ttu-id="4bdb4-107">Tartışma için bkz. sorun [DotNet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807).</span><span class="sxs-lookup"><span data-stu-id="4bdb4-107">For discussion, see issue [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4bdb4-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4bdb4-108">Version introduced</span></span>

<span data-ttu-id="4bdb4-109">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="4bdb4-109">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="4bdb4-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="4bdb4-110">Old behavior</span></span>

<span data-ttu-id="4bdb4-111">ASP.NET Core 5,0 Preview 6 ' dan önce Kestrel, çalışma zamanında yapılandırmanın değiştirilmesini desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-111">Before ASP.NET Core 5.0 Preview 6, Kestrel didn't support changing configuration at run time.</span></span>

<span data-ttu-id="4bdb4-112">ASP.NET Core 5,0 Preview 6 ' da, çalışma zamanında yapılandırma değişikliklerine yeniden davranma özelliğinin varsayılan davranışını kabul edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-112">In ASP.NET Core 5.0 Preview 6, you could opt into the now-default behavior of reacting to configuration changes at run time.</span></span> <span data-ttu-id="4bdb4-113">Gerekli bağlama Kestrel yapılandırması el ile:</span><span class="sxs-lookup"><span data-stu-id="4bdb4-113">Opting in required binding Kestrel's configuration manually:</span></span>

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Hosting;

public class Program
{
    public static void Main(string[] args) =>
        CreateHostBuilder(args).Build().Run();

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

## <a name="new-behavior"></a><span data-ttu-id="4bdb4-114">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="4bdb4-114">New behavior</span></span>

<span data-ttu-id="4bdb4-115">Kestrel, varsayılan olarak çalışma zamanında yapılandırma değişikliklerine tepki verir.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-115">Kestrel reacts to configuration changes at run time by default.</span></span> <span data-ttu-id="4bdb4-116">Bu değişikliği desteklemek için, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> `KestrelServerOptions.Configure(IConfiguration, bool)` `reloadOnChange: true` Varsayılan olarak ile çağırır.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-116">To support that change, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> calls `KestrelServerOptions.Configure(IConfiguration, bool)` with `reloadOnChange: true` by default.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="4bdb4-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="4bdb4-117">Reason for change</span></span>

<span data-ttu-id="4bdb4-118">Sunucu tamamen yeniden başlatılmadan çalışma zamanında bitiş noktası yeniden yapılandırması desteklemek için değişiklik yapıldı.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-118">The change was made to support endpoint reconfiguration at run time without completely restarting the server.</span></span> <span data-ttu-id="4bdb4-119">Tam sunucu yeniden başlatmasından farklı olarak, değiştirilmemiş uç noktalar geçici olarak geçici olarak ilişkisiz olmaz.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-119">Unlike with a full server restart, unchanged endpoints aren't unbound even temporarily.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4bdb4-120">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4bdb4-120">Recommended action</span></span>

* <span data-ttu-id="4bdb4-121">Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değişmediğinden çoğu senaryo için, bu değişikliğin etkisi yoktur ve hiçbir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-121">For most scenarios in which Kestrel's default configuration section doesn't change at run time, this change has no impact and no action is needed.</span></span>
* <span data-ttu-id="4bdb4-122">Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değişme ve Kestrel 'e yanıt vermesini gerektiren senaryolar için, bu artık varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-122">For scenarios in which Kestrel's default configuration section does change at run time and Kestrel should react to it, this is now the default behavior.</span></span>
* <span data-ttu-id="4bdb4-123">Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değiştiği ve Kestrel 'e yanıt vermeme senaryolarında, aşağıdaki gibi devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4bdb4-123">For scenarios in which Kestrel's default configuration section changes at run time and Kestrel shouldn't react to it, you can opt out as follows:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="4bdb4-124">**Notlar:**</span><span class="sxs-lookup"><span data-stu-id="4bdb4-124">**Notes:**</span></span>

<span data-ttu-id="4bdb4-125">Bu değişiklik aşırı yükleme davranışını değiştirmez, bu da `KestrelServerOptions.Configure(IConfiguration)` davranışa varsayılan olarak devam eder `reloadOnChange: false` .</span><span class="sxs-lookup"><span data-stu-id="4bdb4-125">This change doesn't modify the behavior of the `KestrelServerOptions.Configure(IConfiguration)` overload, which still defaults to the `reloadOnChange: false` behavior.</span></span>

<span data-ttu-id="4bdb4-126">Yapılandırma kaynağının yeniden yüklemeyi desteklediğinden emin olmak da önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-126">It's also important to make sure the configuration source supports reloading.</span></span> <span data-ttu-id="4bdb4-127">JSON kaynakları için, yeniden yükleme çağırarak yapılandırılır `AddJsonFile(path, reloadOnChange: true)` .</span><span class="sxs-lookup"><span data-stu-id="4bdb4-127">For JSON sources, reloading is configured by calling `AddJsonFile(path, reloadOnChange: true)`.</span></span> <span data-ttu-id="4bdb4-128">Yeniden yükleme, *appsettings.json* ve appSettings için varsayılan olarak zaten yapılandırılmıştır *. { Environment}. JSON*.</span><span class="sxs-lookup"><span data-stu-id="4bdb4-128">Reloading is already configured by default for *appsettings.json* and *appsettings.{Environment}.json*.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4bdb4-129">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4bdb4-129">Affected APIs</span></span>

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
