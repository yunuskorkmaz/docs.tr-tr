---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937292"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="34dd2-101">Barındırma: IIS işlem dışı uygulamalar için HTTPS yönlendirmesi etkinleştirildi</span><span class="sxs-lookup"><span data-stu-id="34dd2-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="34dd2-102">IIS işlem dışı ile barındırmak için [ASP.NET Core modülünün (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) sürüm 13.0.19218.0, var olan bir https yeniden yönlendirme özelliğini ASP.NET Core 3,0 ve 2,2 uygulamaları için sunar.</span><span class="sxs-lookup"><span data-stu-id="34dd2-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="34dd2-103">Tartışma için bkz. [DotNet/AspNetCore # 15243](https://github.com/dotnet/AspNetCore/issues/15243).</span><span class="sxs-lookup"><span data-stu-id="34dd2-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="34dd2-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="34dd2-104">Version introduced</span></span>

<span data-ttu-id="34dd2-105">3.0</span><span class="sxs-lookup"><span data-stu-id="34dd2-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="34dd2-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="34dd2-106">Old behavior</span></span>

<span data-ttu-id="34dd2-107">ASP.NET Core 2,1 proje şablonu, önce <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> ve <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>gibi HTTPS ara yazılım yöntemlerine yönelik destek sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="34dd2-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="34dd2-108">Geliştirme aşamasında uygulamalar varsayılan 443 bağlantı noktasını kullandıklarından, HTTPS yeniden yönlendirme özelliğinin etkinleştirilmesi, yapılandırmanın eklenmesi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="34dd2-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="34dd2-109">[Http katı aktarım güvenliği (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) yalnızca Istek zaten https kullanıyorsa etkindir.</span><span class="sxs-lookup"><span data-stu-id="34dd2-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="34dd2-110">Localhost varsayılan olarak atlanır.</span><span class="sxs-lookup"><span data-stu-id="34dd2-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="34dd2-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="34dd2-111">New behavior</span></span>

<span data-ttu-id="34dd2-112">ASP.NET Core 3,0 ' de IIS HTTPS senaryosu [geliştirilmiştir](https://github.com/dotnet/AspNetCore/pull/4685).</span><span class="sxs-lookup"><span data-stu-id="34dd2-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="34dd2-113">Geliştirme sayesinde, bir uygulama sunucunun HTTPS bağlantı noktalarını bulabilir ve varsayılan olarak `UseHttpsRedirection` çalışır.</span><span class="sxs-lookup"><span data-stu-id="34dd2-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="34dd2-114">İşlem içi bileşen bağlantı noktası bulma işlemini yalnızca ASP.NET Core 3,0 uygulamalarını etkileyen `IServerAddresses` özelliği ile gerçekleştirdi. böylece işlem içi kitaplık Framework ile birlikte sürümlüdür.</span><span class="sxs-lookup"><span data-stu-id="34dd2-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="34dd2-115">`ASPNETCORE_HTTPS_PORT` ortam değişkenini otomatik olarak eklemek için işlem dışı bileşen değişti.</span><span class="sxs-lookup"><span data-stu-id="34dd2-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="34dd2-116">Bu değişiklik, işlem dışı bileşen genel olarak paylaşıldığı için ASP.NET Core 2,2 ve 3,0 uygulamalarından her ikisini de etkilemiştir.</span><span class="sxs-lookup"><span data-stu-id="34dd2-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="34dd2-117">ASP.NET Core 2,1 uygulamaları, varsayılan olarak ANCM 'nin önceki bir sürümünü kullandıkları için etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="34dd2-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="34dd2-118">Önceki davranış ASP.NET Core 3.0.1 ve 3.1.0 Preview 3 ' te değiştirilmiştir ASP.NET Core 2. x içindeki davranış değişiklikleri tersine çevirin.</span><span class="sxs-lookup"><span data-stu-id="34dd2-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="34dd2-119">Bu değişiklikler yalnızca IIS işlem dışı uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="34dd2-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="34dd2-120">Yukarıda açıklandığı gibi, yükleme ASP.NET Core 3.0.0, ASP.NET Core 2. x uygulamalarında `UseHttpsRedirection` ara yazılımını da etkinleştiren yan etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="34dd2-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="34dd2-121">ASP.NET Core 3.0.1 ve 3.1.0 Preview 3 ' te bir değişiklik yapılmıştır. bu nedenle, bunları yüklemek artık ASP.NET Core 2. x uygulamaları üzerinde bu etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="34dd2-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="34dd2-122">ASP.NET Core 3.0.0 içinde doldurulmuş bir `ASPNETCORE_HTTPS_PORT` ortam değişkeni, ASP.NET Core 3.0.1 ve 3.1.0 Preview 3 ' te `ASPNETCORE_ANCM_HTTPS_PORT` olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="34dd2-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="34dd2-123">`UseHttpsRedirection` Ayrıca, hem yeni hem de eski değişkenleri anlamak için bu sürümlerde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="34dd2-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="34dd2-124">2\. x ASP.NET Core güncelleştirilmeyecek.</span><span class="sxs-lookup"><span data-stu-id="34dd2-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="34dd2-125">Sonuç olarak, varsayılan olarak devre dışı bırakılmakta olan önceki davranışa geri döner.</span><span class="sxs-lookup"><span data-stu-id="34dd2-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="34dd2-126">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="34dd2-126">Reason for change</span></span>

<span data-ttu-id="34dd2-127">ASP.NET Core 3,0 işlevselliği geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="34dd2-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="34dd2-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="34dd2-128">Recommended action</span></span>

<span data-ttu-id="34dd2-129">Tüm istemcilerin HTTPS kullanmasını istiyorsanız herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="34dd2-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="34dd2-130">Bazı istemcilerin HTTP kullanmasına izin vermek için aşağıdaki adımlardan birini uygulayın:</span><span class="sxs-lookup"><span data-stu-id="34dd2-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="34dd2-131">`UseHttpsRedirection` ve `UseHsts` olan çağrıları projenizin `Startup.Configure` yönteminden kaldırın ve uygulamayı yeniden dağıtın.</span><span class="sxs-lookup"><span data-stu-id="34dd2-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="34dd2-132">*Web. config* dosyanızda `ASPNETCORE_HTTPS_PORT` ortam değişkenini boş bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="34dd2-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="34dd2-133">Bu değişiklik, uygulamayı yeniden dağıtmaya gerek kalmadan doğrudan sunucuda meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="34dd2-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="34dd2-134">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="34dd2-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="34dd2-135">`UseHttpsRedirection` şu olmaya devam edebilir:</span><span class="sxs-lookup"><span data-stu-id="34dd2-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="34dd2-136">`ASPNETCORE_HTTPS_PORT` ortam değişkenini uygun bağlantı noktası numarası olarak ayarlayarak ASP.NET Core 2. x içinde el ile etkinleştirilir (çoğu üretim senaryosunda 443).</span><span class="sxs-lookup"><span data-stu-id="34dd2-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="34dd2-137">Boş bir dize değeriyle `ASPNETCORE_ANCM_HTTPS_PORT` tanımlayarak ASP.NET Core 3. x içinde devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="34dd2-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="34dd2-138">Bu değer, yukarıdaki `ASPNETCORE_HTTPS_PORT` örnekle aynı biçimde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="34dd2-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="34dd2-139">ASP.NET Core 3.0.0 uygulamalarını çalıştıran makineler ASP.NET Core 3.1.0 Preview 3 ANCM 'yi yüklemeden önce ASP.NET Core 3.0.1 çalışma zamanını yüklemelidir.</span><span class="sxs-lookup"><span data-stu-id="34dd2-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="34dd2-140">Bunun yapılması, `UseHttpsRedirection` ASP.NET Core 3,0 uygulamaları için beklendiği gibi çalışmaya devam etmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="34dd2-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="34dd2-141">Azure App Service ' de, genel doğası nedeniyle çalışma zamanından ayrı bir zamanlamaya göre dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="34dd2-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="34dd2-142">ANCM, ASP.NET Core 3.0.1 ve 3.1.0 dağıtıldıktan sonra bu değişikliklerle Azure 'a dağıtıldı.</span><span class="sxs-lookup"><span data-stu-id="34dd2-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="34dd2-143">Kategori</span><span class="sxs-lookup"><span data-stu-id="34dd2-143">Category</span></span>

<span data-ttu-id="34dd2-144">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="34dd2-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="34dd2-145">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="34dd2-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
