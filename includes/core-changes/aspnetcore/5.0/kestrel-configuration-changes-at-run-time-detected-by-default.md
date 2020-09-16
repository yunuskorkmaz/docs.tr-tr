---
ms.openlocfilehash: d00b8ecaa61b358e062d85a2b68ca8a95cada442
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803254"
---
### <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a><span data-ttu-id="6a930-101">Kestrel: çalışma zamanında varsayılan olarak algılanan yapılandırma değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="6a930-101">Kestrel: Configuration changes at run time detected by default</span></span>

<span data-ttu-id="6a930-102">Kestrel şimdi `Kestrel` `IConfiguration` , çalışma zamanında projenin örneğinin bölümünde yapılan değişikliklere (örneğin, *appsettings.jsaçık*) yeniden davranır.</span><span class="sxs-lookup"><span data-stu-id="6a930-102">Kestrel now reacts to changes made to the `Kestrel` section of the project's `IConfiguration` instance (for example, *appsettings.json*) at run time.</span></span> <span data-ttu-id="6a930-103">*Üzerindeappsettings.js*kullanarak Kestrel yapılandırma hakkında daha fazla bilgi edinmek Için [uç nokta yapılandırması](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration)'nda *appsettings.jshakkında* bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6a930-103">To learn more about how to configure Kestrel using *appsettings.json*, see the *appsettings.json* example in [Endpoint configuration](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span></span>

<span data-ttu-id="6a930-104">Kestrel, bu yapılandırma değişikliklerine tepki vermek için uç noktaları gerektiği şekilde bağlar, çözer ve yeniden bağlayın.</span><span class="sxs-lookup"><span data-stu-id="6a930-104">Kestrel will bind, unbind, and rebind endpoints as necessary to react to these configuration changes.</span></span>

<span data-ttu-id="6a930-105">Tartışma için bkz. sorun [DotNet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807).</span><span class="sxs-lookup"><span data-stu-id="6a930-105">For discussion, see issue [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6a930-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6a930-106">Version introduced</span></span>

<span data-ttu-id="6a930-107">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="6a930-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6a930-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="6a930-108">Old behavior</span></span>

<span data-ttu-id="6a930-109">ASP.NET Core 5,0 Preview 6 ' dan önce Kestrel, çalışma zamanında yapılandırmanın değiştirilmesini desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="6a930-109">Before ASP.NET Core 5.0 Preview 6, Kestrel didn't support changing configuration at run time.</span></span>

<span data-ttu-id="6a930-110">ASP.NET Core 5,0 Preview 6 ' da, çalışma zamanında yapılandırma değişikliklerine yeniden davranma özelliğinin varsayılan davranışını kabul edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a930-110">In ASP.NET Core 5.0 Preview 6, you could opt into the now-default behavior of reacting to configuration changes at run time.</span></span> <span data-ttu-id="6a930-111">Gerekli bağlama Kestrel yapılandırması el ile:</span><span class="sxs-lookup"><span data-stu-id="6a930-111">Opting in required binding Kestrel's configuration manually:</span></span>

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

#### <a name="new-behavior"></a><span data-ttu-id="6a930-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="6a930-112">New behavior</span></span>

<span data-ttu-id="6a930-113">Kestrel, varsayılan olarak çalışma zamanında yapılandırma değişikliklerine tepki verir.</span><span class="sxs-lookup"><span data-stu-id="6a930-113">Kestrel reacts to configuration changes at run time by default.</span></span> <span data-ttu-id="6a930-114">Bu değişikliği desteklemek için, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> `KestrelServerOptions.Configure(IConfiguration, bool)` `reloadOnChange: true` Varsayılan olarak ile çağırır.</span><span class="sxs-lookup"><span data-stu-id="6a930-114">To support that change, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> calls `KestrelServerOptions.Configure(IConfiguration, bool)` with `reloadOnChange: true` by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6a930-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="6a930-115">Reason for change</span></span>

<span data-ttu-id="6a930-116">Sunucu tamamen yeniden başlatılmadan çalışma zamanında bitiş noktası yeniden yapılandırması desteklemek için değişiklik yapıldı.</span><span class="sxs-lookup"><span data-stu-id="6a930-116">The change was made to support endpoint reconfiguration at run time without completely restarting the server.</span></span> <span data-ttu-id="6a930-117">Tam sunucu yeniden başlatmasından farklı olarak, değiştirilmemiş uç noktalar geçici olarak geçici olarak ilişkisiz olmaz.</span><span class="sxs-lookup"><span data-stu-id="6a930-117">Unlike with a full server restart, unchanged endpoints aren't unbound even temporarily.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6a930-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6a930-118">Recommended action</span></span>

* <span data-ttu-id="6a930-119">Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değişmediğinden çoğu senaryo için, bu değişikliğin etkisi yoktur ve hiçbir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6a930-119">For most scenarios in which Kestrel's default configuration section doesn't change at run time, this change has no impact and no action is needed.</span></span>
* <span data-ttu-id="6a930-120">Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değişme ve Kestrel 'e yanıt vermesini gerektiren senaryolar için, bu artık varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="6a930-120">For scenarios in which Kestrel's default configuration section does change at run time and Kestrel should react to it, this is now the default behavior.</span></span>
* <span data-ttu-id="6a930-121">Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değiştiği ve Kestrel 'e yanıt vermeme senaryolarında, aşağıdaki gibi devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6a930-121">For scenarios in which Kestrel's default configuration section changes at run time and Kestrel shouldn't react to it, you can opt out as follows:</span></span>

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

<span data-ttu-id="6a930-122">**Notlar:**</span><span class="sxs-lookup"><span data-stu-id="6a930-122">**Notes:**</span></span>

<span data-ttu-id="6a930-123">Bu değişiklik aşırı yükleme davranışını değiştirmez, bu da `KestrelServerOptions.Configure(IConfiguration)` davranışa varsayılan olarak devam eder `reloadOnChange: false` .</span><span class="sxs-lookup"><span data-stu-id="6a930-123">This change doesn't modify the behavior of the `KestrelServerOptions.Configure(IConfiguration)` overload, which still defaults to the `reloadOnChange: false` behavior.</span></span>

<span data-ttu-id="6a930-124">Yapılandırma kaynağının yeniden yüklemeyi desteklediğinden emin olmak da önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6a930-124">It's also important to make sure the configuration source supports reloading.</span></span> <span data-ttu-id="6a930-125">JSON kaynakları için, yeniden yükleme çağırarak yapılandırılır `AddJsonFile(path, reloadOnChange: true)` .</span><span class="sxs-lookup"><span data-stu-id="6a930-125">For JSON sources, reloading is configured by calling `AddJsonFile(path, reloadOnChange: true)`.</span></span> <span data-ttu-id="6a930-126">Yeniden yükleme, *appsettings.json* ve appSettings için varsayılan olarak zaten yapılandırılmıştır *. { Environment}. JSON*.</span><span class="sxs-lookup"><span data-stu-id="6a930-126">Reloading is already configured by default for *appsettings.json* and *appsettings.{Environment}.json*.</span></span>

#### <a name="category"></a><span data-ttu-id="6a930-127">Kategori</span><span class="sxs-lookup"><span data-stu-id="6a930-127">Category</span></span>

<span data-ttu-id="6a930-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6a930-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6a930-129">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6a930-129">Affected APIs</span></span>

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
