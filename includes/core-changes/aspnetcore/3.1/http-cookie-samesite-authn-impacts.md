---
ms.openlocfilehash: b0d093cc30a09b3248cc57a521b386bf581b5451
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552156"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="049d9-101">HTTP: Browser SameSite değişikliklerinin etkisi kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="049d9-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="049d9-102">Chrome ve Firefox gibi bazı tarayıcılar, tanımlama bilgileri için `SameSite` uygulamalarında önemli değişiklikler yaptı.</span><span class="sxs-lookup"><span data-stu-id="049d9-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="049d9-103">Değişiklikler, OpenID Connect ve WS-Federation gibi uzak kimlik doğrulama senaryolarını etkiler ve bu, `SameSite=None`göndermesi için kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="049d9-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="049d9-104">Ancak, iOS 12 ' de ve diğer tarayıcıların bazı eski sürümlerinde `SameSite=None` kesilir.</span><span class="sxs-lookup"><span data-stu-id="049d9-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="049d9-105">Uygulamanın bu sürümleri algılaması ve `SameSite`atması gerekir.</span><span class="sxs-lookup"><span data-stu-id="049d9-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="049d9-106">Bu sorunla ilgili tartışmak için bkz. [ASPNET/AspNetCore # 14996](https://github.com/aspnet/AspNetCore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="049d9-106">For discussion on this issue, see [aspnet/AspNetCore#14996](https://github.com/aspnet/AspNetCore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="049d9-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="049d9-107">Version introduced</span></span>

<span data-ttu-id="049d9-108">3,1 Preview 1</span><span class="sxs-lookup"><span data-stu-id="049d9-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="049d9-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="049d9-109">Old behavior</span></span>

<span data-ttu-id="049d9-110">`SameSite`, HTTP tanımlama bilgilerine yönelik 2016 taslak standart uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="049d9-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="049d9-111">Siteler arası Istek sahteciliği 'nin (CSRF) azaltılmasına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="049d9-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="049d9-112">Bu, başlangıçta yeni parametreler ekleyerek sunucuların kabul etmesinin tercih edildiği bir özellik olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="049d9-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="049d9-113">ASP.NET Core 2,0 `SameSite`için başlangıç desteğini ekledi.</span><span class="sxs-lookup"><span data-stu-id="049d9-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="049d9-114">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="049d9-114">New behavior</span></span>

<span data-ttu-id="049d9-115">Google, geriye doğru uyumlu olmayan yeni bir taslak standardı önerdi.</span><span class="sxs-lookup"><span data-stu-id="049d9-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="049d9-116">Standart, varsayılan modu `Lax` olarak değiştirir ve geri çevirmek için yeni bir giriş `None` ekler. Çoğu uygulama tanımlama bilgisi için yeterli `Lax`. Ancak, OpenID Connect ve WS-Federation oturum açma gibi siteler arası senaryoları keser.</span><span class="sxs-lookup"><span data-stu-id="049d9-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="049d9-117">İsteğin akışlarına yönelik farklılıklar nedeniyle çoğu OAuth oturum açma işlemleri etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="049d9-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="049d9-118">Yeni `None` parametresi, önceki taslak standardını uygulayan istemcilerle uyumluluk sorunlarına neden olur (örneğin, iOS 12).</span><span class="sxs-lookup"><span data-stu-id="049d9-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="049d9-119">Chrome 80, değişiklikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="049d9-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="049d9-120">Chrome ürün başlatma zaman çizelgesi için bkz. [SameSite Updates](https://www.chromium.org/updates/same-site) .</span><span class="sxs-lookup"><span data-stu-id="049d9-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="049d9-121">ASP.NET Core 3,1, yeni `SameSite` davranışını uygulayacak şekilde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="049d9-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="049d9-122">Güncelleştirme, `SameSite=None` yayma `SameSiteMode.None` davranışını yeniden tanımlar ve `SameSite` özniteliğini atlamak için `SameSiteMode.Unspecified` yeni bir değer ekler.</span><span class="sxs-lookup"><span data-stu-id="049d9-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="049d9-123">Tanımlama bilgilerini kullanan bazı bileşenler, OpenID Connect bağıntı ve nonce tanımlama bilgileri gibi senaryolarına daha belirgin değerler ayarlamış olsa da, tüm tanımlama bilgisi API 'Leri artık varsayılan `Unspecified`.</span><span class="sxs-lookup"><span data-stu-id="049d9-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="049d9-124">Bu alandaki diğer son değişiklikler için bkz. [http: bazı tanımlama bilgisi SameSite Varsayılanları None olarak değiştirildi](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="049d9-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="049d9-125">ASP.NET Core 3,0 ' de, çoğu varsayılan değer <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> olarak değiştirilmiştir (ancak yine de önceki standart kullanılarak).</span><span class="sxs-lookup"><span data-stu-id="049d9-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="049d9-126">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="049d9-126">Reason for change</span></span>

<span data-ttu-id="049d9-127">Tarayıcı ve belirtim, önceki metinde özetlenen şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="049d9-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="049d9-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="049d9-128">Recommended action</span></span>

<span data-ttu-id="049d9-129">Üçüncü taraf oturum açma gibi uzak sitelerle etkileşim kuran uygulamalar şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="049d9-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="049d9-130">Bu senaryoları birden çok tarayıcıda test edin.</span><span class="sxs-lookup"><span data-stu-id="049d9-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="049d9-131">[Daha eski tarayıcıları desteklemek](#support-older-browsers)için açıklanan tanımlama bilgisi İlkesi tarayıcı algılaması risk azaltma ' yı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="049d9-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="049d9-132">Test ve tarayıcı algılama yönergeleri için aşağıdaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="049d9-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="049d9-133">Etkilenip etkilenmediğini belirleme</span><span class="sxs-lookup"><span data-stu-id="049d9-133">Determine if you're affected</span></span>

<span data-ttu-id="049d9-134">Yeni davranışı kabul eden bir istemci sürümünü kullanarak Web uygulamanızı test edin.</span><span class="sxs-lookup"><span data-stu-id="049d9-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="049d9-135">Chrome, Firefox ve Microsoft Edge Bermium tümünde test için kullanılabilecek yeni bir katılım özelliği bayrakları vardır.</span><span class="sxs-lookup"><span data-stu-id="049d9-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="049d9-136">Düzeltme eklerini uyguladıktan sonra uygulamanızın eski istemci sürümleriyle uyumlu olduğunu doğrulayın, özellikle Safari.</span><span class="sxs-lookup"><span data-stu-id="049d9-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="049d9-137">Daha fazla bilgi için bkz. [eski tarayıcıları destekleme](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="049d9-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="049d9-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="049d9-138">Chrome</span></span>

<span data-ttu-id="049d9-139">Chrome 78 ve üzeri, yanıltıcı test sonuçları elde.</span><span class="sxs-lookup"><span data-stu-id="049d9-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="049d9-140">Bu sürümlerin yerinde geçici bir risk azaltma ve iki dakikadan daha eski tanımlama bilgilerine izin verme.</span><span class="sxs-lookup"><span data-stu-id="049d9-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="049d9-141">Uygun test bayrakları etkinken, Chrome 76 ve 77 daha doğru sonuçlar elde edin.</span><span class="sxs-lookup"><span data-stu-id="049d9-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="049d9-142">Yeni davranışı test etmek için `chrome://flags/#same-site-by-default-cookies` etkin olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="049d9-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="049d9-143">Chrome 75 ve önceki sürümleri, yeni `None` ayarıyla başarısız olacak şekilde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="049d9-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="049d9-144">Daha fazla bilgi için bkz. [eski tarayıcıları destekleme](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="049d9-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="049d9-145">Google, eski Chrome sürümlerini kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="049d9-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="049d9-146">Ancak, test için yeterli olacak şekilde, Kmıum 'un eski sürümlerini indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="049d9-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="049d9-147">[Kmıum indirme](https://www.chromium.org/getting-involved/download-chromium)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="049d9-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="049d9-148">Kmıum 76 Win64</span><span class="sxs-lookup"><span data-stu-id="049d9-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="049d9-149">Kmıum 74 Win64</span><span class="sxs-lookup"><span data-stu-id="049d9-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="049d9-150">Safari</span><span class="sxs-lookup"><span data-stu-id="049d9-150">Safari</span></span>

<span data-ttu-id="049d9-151">Safari 12, önceki taslağı tamamen uyguladık ve tanımlama bilgilerinde yeni `None` değeri görülemezse başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="049d9-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="049d9-152">Bu, [eski tarayıcıları destekleme](#support-older-browsers)bölümünde gösterilen tarayıcı algılama kodu aracılığıyla kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="049d9-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="049d9-153">Safari 12 ve 13 ' ün yanı sıra, Microsoft kimlik doğrulama kitaplığı (MSAL), Active Directory Authentication Library (ADAL) veya kullandığınız kitaplığı kullanarak WebKit tabanlı, işletim sistemi stili oturum açma işlemlerini de test edin.</span><span class="sxs-lookup"><span data-stu-id="049d9-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="049d9-154">Sorun, temel alınan işletim sistemi sürümüne bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="049d9-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="049d9-155">OSX Mojave 10,14 ve iOS 12 ' nin yeni davranışla uyumluluk sorunlarına sahip olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="049d9-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="049d9-156">OSX Catalina 10,15 veya iOS 13 ' e yükseltmek sorunu düzeltir.</span><span class="sxs-lookup"><span data-stu-id="049d9-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="049d9-157">Safari 'nin şu anda yeni belirtim davranışını test etmek için bir katılım bayrağı yoktur.</span><span class="sxs-lookup"><span data-stu-id="049d9-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="049d9-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="049d9-158">Firefox</span></span>

<span data-ttu-id="049d9-159">Yeni standart için Firefox desteği, sürüm 68 ve üzeri sürümlerde, özellik bayrağı `network.cookie.sameSite.laxByDefault``about:config` sayfasında ' de seçilerek test edilebilir.</span><span class="sxs-lookup"><span data-stu-id="049d9-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="049d9-160">Firefox 'un eski sürümlerinde uyumluluk sorunları bildirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="049d9-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="049d9-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="049d9-161">Microsoft Edge</span></span>

<span data-ttu-id="049d9-162">Microsoft Edge, sürüm 44 itibariyle eski `SameSite` standardını desteklese de, yeni standart ile herhangi bir uyumluluk sorununa sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="049d9-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="049d9-163">Microsoft Edge Kmuum</span><span class="sxs-lookup"><span data-stu-id="049d9-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="049d9-164">Özellik bayrağı `edge://flags/#same-site-by-default-cookies`.</span><span class="sxs-lookup"><span data-stu-id="049d9-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="049d9-165">Microsoft Edge Kmıum 78 ile test edilirken hiçbir uyumluluk sorunu gözlemlenmedi.</span><span class="sxs-lookup"><span data-stu-id="049d9-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="049d9-166">Tron</span><span class="sxs-lookup"><span data-stu-id="049d9-166">Electron</span></span>

<span data-ttu-id="049d9-167">Elektron sürümleri, daha eski bir Kmıum sürümlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="049d9-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="049d9-168">Örneğin, Microsoft ekipleri tarafından kullanılan elektron sürümü, eski davranışı gösteren Kmıum 66 ' dir.</span><span class="sxs-lookup"><span data-stu-id="049d9-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="049d9-169">Ürününüzün kullandığı elektron sürümüyle kendi uyumluluk testinizi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="049d9-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="049d9-170">Daha fazla bilgi için bkz. [eski tarayıcıları destekleme](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="049d9-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="049d9-171">Eski tarayıcıları destekleme</span><span class="sxs-lookup"><span data-stu-id="049d9-171">Support older browsers</span></span>

<span data-ttu-id="049d9-172">2016 `SameSite` standart uygulanan, bilinmeyen değerler `SameSite=Strict` değer olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="049d9-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="049d9-173">Sonuç olarak, özgün standardı destekleyen eski tarayıcılar, `None`bir `SameSite` özelliği görtiklerinde kesintiye uğratır.</span><span class="sxs-lookup"><span data-stu-id="049d9-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="049d9-174">Web uygulamaları, bu eski tarayıcıları desteklemeyi amaçlarsa tarayıcı algılaması gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="049d9-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="049d9-175">ASP.NET Core, `User-Agent` istek üst bilgisi değerleri son derece kararsız olduğundan ve haftalık olarak değişeceğinden sizin için tarayıcı algılaması uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="049d9-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="049d9-176">Bunun yerine, tanımlama bilgisi ilkesindeki bir uzantı noktası, `User-Agent`özel mantık eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="049d9-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="049d9-177">*Startup.cs*içinde aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="049d9-177">In *Startup.cs*, add the following code:</span></span>

```csharp
private void CheckSameSite(HttpContext httpContext, CookieOptions options)
{
    if (options.SameSite == SameSiteMode.None) 
    { 
        var userAgent = httpContext.Request.Headers["User-Agent"].ToString();
        // TODO: Use your User Agent library of choice here. 
        if (/* UserAgent doesn't support new behavior */) 
        { 
            options.SameSite = SameSiteMode.Unspecified;
        }
    }
}

public void ConfigureServices(IServiceCollection services) 
{ 
    services.Configure<CookiePolicyOptions>(options => 
    { 
        options.MinimumSameSitePolicy = SameSiteMode.Unspecified;
        options.OnAppendCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
        options.OnDeleteCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
    }); 
} 

public void Configure(IApplicationBuilder app) 
{ 
    // Before UseAuthentication or anything else that writes cookies.
    app.UseCookiePolicy();

    app.UseAuthentication(); 
    // code omitted for brevity
}
```

##### <a name="opt-out-switches"></a><span data-ttu-id="049d9-178">Kabul etme anahtarları</span><span class="sxs-lookup"><span data-stu-id="049d9-178">Opt-out switches</span></span>

<span data-ttu-id="049d9-179">`Microsoft.AspNetCore.SuppressSameSiteNone` uyumluluk anahtarı, yeni ASP.NET Core tanımlama bilgisi davranışının geçici olarak devre dışı kalmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="049d9-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="049d9-180">Aşağıdaki JSON *öğesini projenizdeki runtimeconfig. Template. JSON* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="049d9-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{ 
  "configProperties": { 
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true" 
  } 
}
```

##### <a name="other-versions"></a><span data-ttu-id="049d9-181">Diğer sürümler</span><span class="sxs-lookup"><span data-stu-id="049d9-181">Other Versions</span></span>

<span data-ttu-id="049d9-182">İlgili `SameSite` düzeltme ekleri şu şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="049d9-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="049d9-183">ASP.NET Core 2,1, 2,2 ve 3,0</span><span class="sxs-lookup"><span data-stu-id="049d9-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="049d9-184">`Microsoft.Owin` 4,1</span><span class="sxs-lookup"><span data-stu-id="049d9-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="049d9-185">`System.Web` (.NET Framework 4.7.2 ve üzeri için)</span><span class="sxs-lookup"><span data-stu-id="049d9-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="049d9-186">Kategori</span><span class="sxs-lookup"><span data-stu-id="049d9-186">Category</span></span>

<span data-ttu-id="049d9-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="049d9-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="049d9-188">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="049d9-188">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieBuilder.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieOptions.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`
- `Overload:Microsoft.AspNetCore.Http.CookieBuilder.SameSite`
- `Overload:Microsoft.AspNetCore.Http.CookieOptions.SameSite`
- `T:Microsoft.AspNetCore.Http.SameSiteMode`
- `T:Microsoft.Net.Http.Headers.SameSiteMode`
- `Overload:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite`

-->
