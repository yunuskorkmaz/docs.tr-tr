---
ms.openlocfilehash: 8b6d334677991382d235fd53cd3c98e3a77d650d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539624"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="d6922-101">HTTP: Browser SameSite değişikliklerinin etkisi kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="d6922-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="d6922-102">Chrome ve Firefox gibi bazı tarayıcılar, tanımlama bilgileri için uygulamalarında önemli değişiklikler yaptı `SameSite` .</span><span class="sxs-lookup"><span data-stu-id="d6922-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="d6922-103">Değişiklikler OpenID Connect ve WS-Federation gibi uzak kimlik doğrulama senaryolarını etkiler ve bu, göndermesi tarafından kabul etmelidir `SameSite=None` .</span><span class="sxs-lookup"><span data-stu-id="d6922-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="d6922-104">Ancak, `SameSite=None` iOS 12 ve diğer tarayıcıların bazı eski sürümlerinde kesilir.</span><span class="sxs-lookup"><span data-stu-id="d6922-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="d6922-105">Uygulamanın bu sürümleri algılaması ve atlama yapması gerekir `SameSite` .</span><span class="sxs-lookup"><span data-stu-id="d6922-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="d6922-106">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="d6922-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d6922-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d6922-107">Version introduced</span></span>

<span data-ttu-id="d6922-108">3,1 Preview 1</span><span class="sxs-lookup"><span data-stu-id="d6922-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d6922-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="d6922-109">Old behavior</span></span>

<span data-ttu-id="d6922-110">`SameSite` , HTTP tanımlama bilgilerine yönelik 2016 taslak standart uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="d6922-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="d6922-111">Siteler arası Istek sahteciliği 'nin (CSRF) azaltılmasına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="d6922-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="d6922-112">Bu, başlangıçta yeni parametreler ekleyerek sunucuların kabul etmesinin tercih edildiği bir özellik olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d6922-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="d6922-113">ASP.NET Core 2,0 için başlangıç desteği eklendi `SameSite` .</span><span class="sxs-lookup"><span data-stu-id="d6922-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d6922-114">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="d6922-114">New behavior</span></span>

<span data-ttu-id="d6922-115">Google, geriye doğru uyumlu olmayan yeni bir taslak standardı önerdi.</span><span class="sxs-lookup"><span data-stu-id="d6922-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="d6922-116">Standart varsayılan modu olarak değiştirir ve geri `Lax` çevirmek için yeni bir giriş ekler `None` . `Lax` çoğu uygulama tanımlama bilgisi için yeterli olacaktır; ancak, OpenID Connect ve WS-Federation oturum açma gibi siteler arası senaryoları keser.</span><span class="sxs-lookup"><span data-stu-id="d6922-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="d6922-117">İsteğin akışlarına yönelik farklılıklar nedeniyle çoğu OAuth oturum açma işlemleri etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="d6922-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="d6922-118">Yeni `None` parametre, önceki taslak standardını uygulayan istemcilerle uyumluluk sorunlarına neden olur (örneğin, iOS 12).</span><span class="sxs-lookup"><span data-stu-id="d6922-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="d6922-119">Chrome 80, değişiklikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d6922-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="d6922-120">Chrome ürün başlatma zaman çizelgesi için bkz. [SameSite Updates](https://www.chromium.org/updates/same-site) .</span><span class="sxs-lookup"><span data-stu-id="d6922-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="d6922-121">ASP.NET Core 3,1, yeni davranışı uygulamak için güncelleştirilmiştir `SameSite` .</span><span class="sxs-lookup"><span data-stu-id="d6922-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="d6922-122">Güncelleştirme, öğesinin davranışını yeniden tanımlar `SameSiteMode.None` `SameSite=None` ve `SameSiteMode.Unspecified` özniteliği atlamak için yeni bir değer ekler `SameSite` .</span><span class="sxs-lookup"><span data-stu-id="d6922-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="d6922-123">`Unspecified`Tanımlama bilgilerini kullanan bazı bileşenler, OpenID Connect bağıntı ve nonce tanımlama bilgileri gibi senaryolarına daha belirgin bir şekilde değer ayarlamış olsa da, tüm tanımlama bilgisi API 'leri için varsayılan olarak ' i</span><span class="sxs-lookup"><span data-stu-id="d6922-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="d6922-124">Bu alandaki diğer son değişiklikler için bkz. [http: bazı tanımlama bilgisi SameSite Varsayılanları None olarak değiştirildi](../../../../docs/core/compatibility/2.2-3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="d6922-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](../../../../docs/core/compatibility/2.2-3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="d6922-125">ASP.NET Core 3,0 ' de, çoğu varsayılan <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> olarak olarak değiştirilmiştir <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (ancak yine de önceki standart kullanılarak).</span><span class="sxs-lookup"><span data-stu-id="d6922-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d6922-126">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="d6922-126">Reason for change</span></span>

<span data-ttu-id="d6922-127">Tarayıcı ve belirtim, önceki metinde özetlenen şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="d6922-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d6922-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d6922-128">Recommended action</span></span>

<span data-ttu-id="d6922-129">Üçüncü taraf oturum açma gibi uzak sitelerle etkileşim kuran uygulamalar şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="d6922-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="d6922-130">Bu senaryoları birden çok tarayıcıda test edin.</span><span class="sxs-lookup"><span data-stu-id="d6922-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="d6922-131">[Daha eski tarayıcıları desteklemek](#support-older-browsers)için açıklanan tanımlama bilgisi İlkesi tarayıcı algılaması risk azaltma ' yı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d6922-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="d6922-132">Test ve tarayıcı algılama yönergeleri için aşağıdaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="d6922-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="d6922-133">Etkilenip etkilenmediğini belirleme</span><span class="sxs-lookup"><span data-stu-id="d6922-133">Determine if you're affected</span></span>

<span data-ttu-id="d6922-134">Yeni davranışı kabul eden bir istemci sürümünü kullanarak Web uygulamanızı test edin.</span><span class="sxs-lookup"><span data-stu-id="d6922-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="d6922-135">Chrome, Firefox ve Microsoft Edge Bermium tümünde test için kullanılabilecek yeni bir katılım özelliği bayrakları vardır.</span><span class="sxs-lookup"><span data-stu-id="d6922-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="d6922-136">Düzeltme eklerini uyguladıktan sonra uygulamanızın eski istemci sürümleriyle uyumlu olduğunu doğrulayın, özellikle Safari.</span><span class="sxs-lookup"><span data-stu-id="d6922-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="d6922-137">Daha fazla bilgi için bkz. [eski tarayıcıları destekleme](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="d6922-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="d6922-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="d6922-138">Chrome</span></span>

<span data-ttu-id="d6922-139">Chrome 78 ve üzeri, yanıltıcı test sonuçları elde.</span><span class="sxs-lookup"><span data-stu-id="d6922-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="d6922-140">Bu sürümlerin yerinde geçici bir risk azaltma ve iki dakikadan daha eski tanımlama bilgilerine izin verme.</span><span class="sxs-lookup"><span data-stu-id="d6922-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="d6922-141">Uygun test bayrakları etkinken, Chrome 76 ve 77 daha doğru sonuçlar elde edin.</span><span class="sxs-lookup"><span data-stu-id="d6922-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="d6922-142">Yeni davranışı test etmek için, etkin ' e geçiş yapın `chrome://flags/#same-site-by-default-cookies` .</span><span class="sxs-lookup"><span data-stu-id="d6922-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="d6922-143">Chrome 75 ve öncesi, yeni ayar ile başarısız olarak bildirilir `None` .</span><span class="sxs-lookup"><span data-stu-id="d6922-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="d6922-144">Daha fazla bilgi için bkz. [eski tarayıcıları destekleme](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="d6922-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="d6922-145">Google, eski Chrome sürümlerini kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d6922-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="d6922-146">Ancak, test için yeterli olacak şekilde, Kmıum 'un eski sürümlerini indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6922-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="d6922-147">[Kmıum indirme](https://www.chromium.org/getting-involved/download-chromium)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d6922-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="d6922-148">Kmıum 76 Win64</span><span class="sxs-lookup"><span data-stu-id="d6922-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="d6922-149">Kmıum 74 Win64</span><span class="sxs-lookup"><span data-stu-id="d6922-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="d6922-150">Safari</span><span class="sxs-lookup"><span data-stu-id="d6922-150">Safari</span></span>

<span data-ttu-id="d6922-151">Safari 12, önceki taslağı kesin olarak uyguladık ve tanımlama bilgilerinde yeni değeri görütüyse başarısız olur `None` .</span><span class="sxs-lookup"><span data-stu-id="d6922-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="d6922-152">Bu, [eski tarayıcıları destekleme](#support-older-browsers)bölümünde gösterilen tarayıcı algılama kodu aracılığıyla kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6922-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="d6922-153">Safari 12 ve 13 ' ün yanı sıra, Microsoft kimlik doğrulama kitaplığı (MSAL), Active Directory Authentication Library (ADAL) veya kullandığınız kitaplığı kullanarak WebKit tabanlı, işletim sistemi stili oturum açma işlemlerini de test edin.</span><span class="sxs-lookup"><span data-stu-id="d6922-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="d6922-154">Sorun, temel alınan işletim sistemi sürümüne bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="d6922-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="d6922-155">OSX Mojave 10,14 ve iOS 12 ' nin yeni davranışla uyumluluk sorunlarına sahip olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="d6922-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="d6922-156">OSX Catalina 10,15 veya iOS 13 ' e yükseltmek sorunu düzeltir.</span><span class="sxs-lookup"><span data-stu-id="d6922-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="d6922-157">Safari 'nin şu anda yeni belirtim davranışını test etmek için bir katılım bayrağı yoktur.</span><span class="sxs-lookup"><span data-stu-id="d6922-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="d6922-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="d6922-158">Firefox</span></span>

<span data-ttu-id="d6922-159">Yeni standart için Firefox desteği, sürüm 68 ve üzeri sürümlerde, özellik bayrağıyla sayfada yeniden çalıştırılarak test edilebilir `about:config` `network.cookie.sameSite.laxByDefault` .</span><span class="sxs-lookup"><span data-stu-id="d6922-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="d6922-160">Firefox 'un eski sürümlerinde uyumluluk sorunları bildirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="d6922-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="d6922-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="d6922-161">Microsoft Edge</span></span>

<span data-ttu-id="d6922-162">Microsoft Edge, `SameSite` sürüm 44 itibariyle eski standardı desteklese de, yeni standart ile herhangi bir uyumluluk sorununa sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="d6922-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="d6922-163">Microsoft Edge Kmuum</span><span class="sxs-lookup"><span data-stu-id="d6922-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="d6922-164">Özellik bayrağı `edge://flags/#same-site-by-default-cookies` .</span><span class="sxs-lookup"><span data-stu-id="d6922-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="d6922-165">Microsoft Edge Kmıum 78 ile test edilirken hiçbir uyumluluk sorunu gözlemlenmedi.</span><span class="sxs-lookup"><span data-stu-id="d6922-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="d6922-166">Tron</span><span class="sxs-lookup"><span data-stu-id="d6922-166">Electron</span></span>

<span data-ttu-id="d6922-167">Elektron sürümleri, daha eski bir Kmıum sürümlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d6922-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="d6922-168">Örneğin, Microsoft ekipleri tarafından kullanılan elektron sürümü, eski davranışı gösteren Kmıum 66 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d6922-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="d6922-169">Ürününüzün kullandığı elektron sürümüyle kendi uyumluluk testinizi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="d6922-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="d6922-170">Daha fazla bilgi için bkz. [eski tarayıcıları destekleme](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="d6922-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="d6922-171">Eski tarayıcıları destekleme</span><span class="sxs-lookup"><span data-stu-id="d6922-171">Support older browsers</span></span>

<span data-ttu-id="d6922-172">2016 `SameSite` Standart uygulanan, bilinmeyen değerler değer olarak değerlendirilir `SameSite=Strict` .</span><span class="sxs-lookup"><span data-stu-id="d6922-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="d6922-173">Sonuç olarak, özgün standardı destekleyen eski tarayıcılar, değeri olan bir özellik görtiklerinde kesintiye uğramayabilir `SameSite` `None` .</span><span class="sxs-lookup"><span data-stu-id="d6922-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="d6922-174">Web uygulamaları, bu eski tarayıcıları desteklemeyi amaçlarsa tarayıcı algılaması gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="d6922-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="d6922-175">ASP.NET Core, `User-Agent` istek üst bilgisi değerleri son derece kararsız olduğundan ve haftalık olarak değişeceğinden sizin için tarayıcı algılaması uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="d6922-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="d6922-176">Bunun yerine, tanımlama bilgisi ilkesindeki bir uzantı noktası, özel bir mantığı eklemenize olanak tanır `User-Agent` .</span><span class="sxs-lookup"><span data-stu-id="d6922-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="d6922-177">*Startup.cs*içinde aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6922-177">In *Startup.cs*, add the following code:</span></span>

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

##### <a name="opt-out-switches"></a><span data-ttu-id="d6922-178">Kabul etme anahtarları</span><span class="sxs-lookup"><span data-stu-id="d6922-178">Opt-out switches</span></span>

<span data-ttu-id="d6922-179">`Microsoft.AspNetCore.SuppressSameSiteNone`Uyumluluk anahtarı, yeni ASP.NET Core tanımlama bilgisi davranışının geçici olarak devre dışı kalmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6922-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="d6922-180">Aşağıdaki JSON öğesini projenizdeki bir dosyaya *runtimeconfig.template.js* ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d6922-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="d6922-181">Diğer sürümler</span><span class="sxs-lookup"><span data-stu-id="d6922-181">Other Versions</span></span>

<span data-ttu-id="d6922-182">İlgili `SameSite` düzeltme eklerine şu şekilde katılın:</span><span class="sxs-lookup"><span data-stu-id="d6922-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="d6922-183">ASP.NET Core 2,1, 2,2 ve 3,0</span><span class="sxs-lookup"><span data-stu-id="d6922-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="d6922-184">`Microsoft.Owin` 4,1</span><span class="sxs-lookup"><span data-stu-id="d6922-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="d6922-185">`System.Web` (.NET Framework 4.7.2 ve üzeri)</span><span class="sxs-lookup"><span data-stu-id="d6922-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="d6922-186">Kategori</span><span class="sxs-lookup"><span data-stu-id="d6922-186">Category</span></span>

<span data-ttu-id="d6922-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d6922-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d6922-188">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d6922-188">Affected APIs</span></span>

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
