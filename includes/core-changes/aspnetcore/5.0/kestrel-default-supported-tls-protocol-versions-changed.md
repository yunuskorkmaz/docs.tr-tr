---
ms.openlocfilehash: 3244a36808fb687663241e704d08775ea5c96720
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803231"
---
### <a name="kestrel-default-supported-tls-protocol-versions-changed"></a><span data-ttu-id="6b4b9-101">Kestrel: desteklenen varsayılan TLS protokol sürümleri değiştirildi</span><span class="sxs-lookup"><span data-stu-id="6b4b9-101">Kestrel: Default supported TLS protocol versions changed</span></span>

<span data-ttu-id="6b4b9-102">Kestrel artık, daha önce olduğu gibi TLS 1,1 ve TLS 1,2 protokollerinin bağlantılarını kısıtlamak yerine sistem varsayılan TLS protokolü sürümlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b4b9-102">Kestrel now uses the system default TLS protocol versions rather than restricting connections to the TLS 1.1 and TLS 1.2 protocols like it did previously.</span></span>

<span data-ttu-id="6b4b9-103">Bu değişiklik şunları sağlar:</span><span class="sxs-lookup"><span data-stu-id="6b4b9-103">This change allows:</span></span>

* <span data-ttu-id="6b4b9-104">TLS 1,3, bunu destekleyen ortamlarda varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b4b9-104">TLS 1.3 to be used by default in environments that support it.</span></span>
* <span data-ttu-id="6b4b9-105">TLS 1,0, bazı ortamlarda (varsayılan olarak Windows Server 2016 gibi) kullanılmak üzere genellikle [istenmez](/security/engineering/solving-tls1-problem).</span><span class="sxs-lookup"><span data-stu-id="6b4b9-105">TLS 1.0 to be used in some environments (such as Windows Server 2016 by default), which is usually [not desirable](/security/engineering/solving-tls1-problem).</span></span>

<span data-ttu-id="6b4b9-106">Tartışma için bkz. sorun [DotNet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563).</span><span class="sxs-lookup"><span data-stu-id="6b4b9-106">For discussion, see issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6b4b9-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6b4b9-107">Version introduced</span></span>

<span data-ttu-id="6b4b9-108">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="6b4b9-108">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6b4b9-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="6b4b9-109">Old behavior</span></span>

<span data-ttu-id="6b4b9-110">Kestrel, bağlantıların varsayılan olarak TLS 1,1 veya TLS 1,2 kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b4b9-110">Kestrel required that connections use TLS 1.1 or TLS 1.2 by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6b4b9-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="6b4b9-111">New behavior</span></span>

<span data-ttu-id="6b4b9-112">Kestrel, işletim sisteminin kullanılacak en iyi Protokolü seçmesini ve güvenli olmayan protokolleri engellemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b4b9-112">Kestrel allows the operating system to choose the best protocol to use and to block insecure protocols.</span></span> <span data-ttu-id="6b4b9-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>Artık yerine varsayılan olarak olur `SslProtocols.None` `SslProtocols.Tls12 | SslProtocols.Tls11` .</span><span class="sxs-lookup"><span data-stu-id="6b4b9-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> now defaults to `SslProtocols.None` instead of `SslProtocols.Tls12 | SslProtocols.Tls11`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6b4b9-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="6b4b9-114">Reason for change</span></span>

<span data-ttu-id="6b4b9-115">Bu değişiklik, kullanılabilir hale geldiğinde TLS 1,3 ve gelecekteki TLS sürümlerini destekleyecek şekilde yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6b4b9-115">The change was made to support TLS 1.3 and future TLS versions by default as they become available.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6b4b9-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6b4b9-116">Recommended action</span></span>

<span data-ttu-id="6b4b9-117">Uygulamanıza özgü bir neden olmadığı takdirde, yeni varsayılan değerleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b4b9-117">Unless your app has a specific reason not to, you should use the new defaults.</span></span> <span data-ttu-id="6b4b9-118">Sisteminizin yalnızca güvenli protokollere izin verecek şekilde yapılandırıldığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="6b4b9-118">Verify your system is configured to allow only secure protocols.</span></span>

<span data-ttu-id="6b4b9-119">Eski protokolleri devre dışı bırakmak için aşağıdaki eylemlerden birini gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="6b4b9-119">To disable older protocols, take one of the following actions:</span></span>

* <span data-ttu-id="6b4b9-120">[Windows yönergeleriyle](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry)TLS 1,0, sistem genelinde gibi eski protokolleri devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="6b4b9-120">Disable older protocols, such as TLS 1.0, system-wide with the [Windows instructions](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry).</span></span> <span data-ttu-id="6b4b9-121">Bu, şu anda tüm Windows sürümlerinde varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6b4b9-121">It's currently enabled by default on all Windows versions.</span></span>
* <span data-ttu-id="6b4b9-122">Kodda hangi protokolleri desteklemek istediğinizi el ile aşağıdaki gibi seçin:</span><span class="sxs-lookup"><span data-stu-id="6b4b9-122">Manually select which protocols you want to support in code as follows:</span></span>

    ```csharp
    using System.Security.Authentication;
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
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="6b4b9-123">Ne yazık ki belirli protokolleri dışlayacak bir API yok.</span><span class="sxs-lookup"><span data-stu-id="6b4b9-123">Unfortunately, there's no API to exclude specific protocols.</span></span>

#### <a name="category"></a><span data-ttu-id="6b4b9-124">Kategori</span><span class="sxs-lookup"><span data-stu-id="6b4b9-124">Category</span></span>

<span data-ttu-id="6b4b9-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b4b9-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6b4b9-126">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6b4b9-126">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
