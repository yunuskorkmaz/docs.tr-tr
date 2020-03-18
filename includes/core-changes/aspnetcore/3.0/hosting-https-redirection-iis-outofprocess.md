---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937292"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="c9327-101">Barındırma: IIS işlem dışı uygulamalar için HTTPS yeniden yönlendirmesi etkin</span><span class="sxs-lookup"><span data-stu-id="c9327-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="c9327-102">IIS out-of-process üzerinden barındırma için [ASP.NET Çekirdek Modülü (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) Sürüm 13.0.19218.0 ASP.NET Core 3.0 ve 2.2 uygulamaları için mevcut bir HTTPS yönlendirme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9327-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="c9327-103">Tartışma için [dotnet/AspNetCore#15243'e](https://github.com/dotnet/AspNetCore/issues/15243)bakın.</span><span class="sxs-lookup"><span data-stu-id="c9327-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c9327-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="c9327-104">Version introduced</span></span>

<span data-ttu-id="c9327-105">3,0</span><span class="sxs-lookup"><span data-stu-id="c9327-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c9327-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="c9327-106">Old behavior</span></span>

<span data-ttu-id="c9327-107">ASP.NET Core 2.1 proje şablonu ilk gibi <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> HTTPS <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>ara yazılım yöntemleri için destek tanıttı ve .</span><span class="sxs-lookup"><span data-stu-id="c9327-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="c9327-108">Geliştirme deki uygulamalar varsayılan 443 bağlantı noktasını kullanmadığından, HTTPS yeniden yönlendirmesini etkinleştirmek için yapılandırmanın eklenmesi gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="c9327-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="c9327-109">[HTTP Katı Aktarım Güvenliği (HSTS),](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) yalnızca istek zaten HTTPS kullanıyorsa etkindir.</span><span class="sxs-lookup"><span data-stu-id="c9327-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="c9327-110">Localhost varsayılan olarak atlanır.</span><span class="sxs-lookup"><span data-stu-id="c9327-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c9327-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="c9327-111">New behavior</span></span>

<span data-ttu-id="c9327-112">Core 3.0ASP.NET, IIS HTTPS senaryosu [geliştirildi.](https://github.com/dotnet/AspNetCore/pull/4685)</span><span class="sxs-lookup"><span data-stu-id="c9327-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="c9327-113">Geliştirme yle, bir uygulama sunucunun HTTPS bağlantı `UseHttpsRedirection` noktalarını keşfedebilir ve varsayılan olarak çalışır hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="c9327-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="c9327-114">Süreç içi kitaplık çerçeveyle sürülmeden yalnızca ASP.NET Core 3.0 uygulamalarını etkileyen `IServerAddresses` özellik ile işlem bileşeni bağlantı noktası keşfini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c9327-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="c9327-115">İşlem dışı bileşen, ortam değişkenini `ASPNETCORE_HTTPS_PORT` otomatik olarak eklemek üzere değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="c9327-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="c9327-116">Bu değişiklik, işlem dışı bileşen küresel olarak paylaşıldığından hem ASP.NET Core 2.2 hem de 3.0 uygulamalarını etkiledi.</span><span class="sxs-lookup"><span data-stu-id="c9327-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="c9327-117">ASP.NET Core 2.1 uygulamaları, varsayılan olarak ANCM'nin önceki bir sürümünü kullandıkları için etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="c9327-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="c9327-118">Önceki davranış, Core 3.0.1 ve 3.1.0 Preview 3'ASP.NET ASP.NET Core 2.x'teki davranış değişikliklerini tersine çevirmek için değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="c9327-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="c9327-119">Bu değişiklikler yalnızca IIS'nin işlem dışı uygulamalarını etkiler.</span><span class="sxs-lookup"><span data-stu-id="c9327-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="c9327-120">Yukarıda ayrıntılı olarak, Core 3.0.0 ASP.NET yükleme de ASP.NET `UseHttpsRedirection` Core 2.x uygulamalarda ara etkinleştirme yan etkisi vardı.</span><span class="sxs-lookup"><span data-stu-id="c9327-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="c9327-121">ASP.NET Core 3.0.1 ve 3.1.0 Preview 3'te ANCM'de bir değişiklik yapıldı ve bunları yüklemek artık ASP.NET Core 2.x uygulamaları üzerinde bu etkiye sahip değil.</span><span class="sxs-lookup"><span data-stu-id="c9327-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="c9327-122">ANCM'nin core 3.0.0'ASP.NET doldurulan `ASPNETCORE_HTTPS_PORT` ortam `ASPNETCORE_ANCM_HTTPS_PORT` değişkeni, 3.0.1 ve 3.1.0 Önizleme 3'ASP.NET olarak değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="c9327-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="c9327-123">`UseHttpsRedirection`hem yeni hem de eski değişkenleri anlamak için bu sürümlerde de güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="c9327-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="c9327-124">ASP.NET Core 2.x güncelleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="c9327-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="c9327-125">Sonuç olarak, varsayılan olarak devre dışı bırakılmış olmanın önceki davranışına geri döner.</span><span class="sxs-lookup"><span data-stu-id="c9327-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c9327-126">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c9327-126">Reason for change</span></span>

<span data-ttu-id="c9327-127">Core 3.0 işlevselliği ASP.NET geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="c9327-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c9327-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c9327-128">Recommended action</span></span>

<span data-ttu-id="c9327-129">Tüm istemcilerin HTTPS kullanmasını istiyorsanız hiçbir işlem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c9327-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="c9327-130">Bazı istemcilerin HTTP'yi kullanmasına izin vermek için aşağıdaki adımlardan birini izleyin:</span><span class="sxs-lookup"><span data-stu-id="c9327-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="c9327-131">Projenizin `UseHttpsRedirection` `UseHsts` `Startup.Configure` yöntemine yapılan aramaları kaldırın ve uygulamayı yeniden dağıtın.</span><span class="sxs-lookup"><span data-stu-id="c9327-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="c9327-132">*web.config* dosyanızda, ortam `ASPNETCORE_HTTPS_PORT` değişkenini boş bir dize olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c9327-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="c9327-133">Bu değişiklik, uygulamayı yeniden dağıtmadan doğrudan sunucuda oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="c9327-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="c9327-134">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c9327-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="c9327-135">`UseHttpsRedirection`hala olabilir:</span><span class="sxs-lookup"><span data-stu-id="c9327-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="c9327-136">ASP.NET Core 2.x'te ortam `ASPNETCORE_HTTPS_PORT` değişkenini uygun bağlantı noktası numarasına ayarlayarak el ile etkinleştirilir (çoğu üretim senaryosunda 443).</span><span class="sxs-lookup"><span data-stu-id="c9327-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="c9327-137">Boş bir dize değeri ile `ASPNETCORE_ANCM_HTTPS_PORT` tanımlayarak Core 3.x ASP.NET devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="c9327-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="c9327-138">Bu değer, önceki `ASPNETCORE_HTTPS_PORT` örnekle aynı şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c9327-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="c9327-139">Core 3.0.0 uygulamaları ASP.NET çalışan makineler, ASP.NET Core 3.1.0 Preview 3 ANCM'yi yüklemeden önce ASP.NET Core 3.0.1 çalışma süresini yüklemelidir.</span><span class="sxs-lookup"><span data-stu-id="c9327-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="c9327-140">Bunu yapmak, `UseHttpsRedirection` ASP.NET Core 3.0 uygulamaları için beklendiği gibi çalışmaya devam etmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9327-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="c9327-141">Azure Uygulama Hizmeti'nde ANCM, genel yapısı nedeniyle çalışma zamanından ayrı bir zamanlamada dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="c9327-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="c9327-142">ANCM, Core 3.0.1 ve 3.1.0 ASP.NET dağıtıldıktan sonra bu değişikliklerle birlikte Azure'a dağıtıldı.</span><span class="sxs-lookup"><span data-stu-id="c9327-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="c9327-143">Kategori</span><span class="sxs-lookup"><span data-stu-id="c9327-143">Category</span></span>

<span data-ttu-id="c9327-144">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="c9327-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c9327-145">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c9327-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
