---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968193"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="0dea8-101">HTTP: Tarayıcı SameSite değişiklikleri kimlik doğrulamayı etkiler</span><span class="sxs-lookup"><span data-stu-id="0dea8-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="0dea8-102">Chrome ve Firefox gibi bazı tarayıcılar, çerezler `SameSite` için kendi uygulamalarında kırma değişiklikler yaptı.</span><span class="sxs-lookup"><span data-stu-id="0dea8-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="0dea8-103">Değişiklikler, OpenID Connect ve WS-Federation gibi uzaktan kimlik doğrulama senaryolarını `SameSite=None`etkiler ve bu senaryoyu göndererek devre dışı bırakmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="0dea8-104">Ancak, `SameSite=None` iOS 12 ve diğer tarayıcıların bazı eski sürümlerinde molalar.</span><span class="sxs-lookup"><span data-stu-id="0dea8-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="0dea8-105">Uygulama bu sürümleri koklamak ve `SameSite`atlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="0dea8-106">Bu konuda tartışma için [dotnet/aspnetcore#14996'ya](https://github.com/dotnet/aspnetcore/issues/14996)bakın.</span><span class="sxs-lookup"><span data-stu-id="0dea8-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0dea8-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0dea8-107">Version introduced</span></span>

<span data-ttu-id="0dea8-108">3.1 Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="0dea8-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0dea8-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="0dea8-109">Old behavior</span></span>

<span data-ttu-id="0dea8-110">`SameSite`HTTP çerezleri için 2016 taslak standart uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="0dea8-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="0dea8-111">Bu Çapraz Site İstek Sahtesini (CSRF) azaltmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0dea8-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="0dea8-112">Bu, başlangıçta sunucuların yeni parametreleri ekleyerek tercih edeceği bir özellik olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0dea8-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="0dea8-113">ASP.NET Core 2.0 için `SameSite`ilk destek ekledi.</span><span class="sxs-lookup"><span data-stu-id="0dea8-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0dea8-114">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="0dea8-114">New behavior</span></span>

<span data-ttu-id="0dea8-115">Google, geriye dönük uyumlu olmayan yeni bir taslak standart önerdi.</span><span class="sxs-lookup"><span data-stu-id="0dea8-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="0dea8-116">Standart varsayılan modu değiştirir `Lax` ve devre `None` dışı bırakmak için yeni bir giriş ekler. `Lax` çoğu uygulama çerezleri için yeterlidir; ancak, OpenID Connect ve WS-Federation girişi gibi siteleri arası senaryoları kırar.</span><span class="sxs-lookup"><span data-stu-id="0dea8-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="0dea8-117">OAuth girişlerinin çoğu, isteğin akışındaki farklılıklar nedeniyle etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="0dea8-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="0dea8-118">Yeni `None` parametre, önceki taslak standardı (örneğin, iOS 12) uygulayan istemcilerle uyumluluk sorunlarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0dea8-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="0dea8-119">Chrome 80 değişiklikleri içerecektir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="0dea8-120">Bkz. Chrome ürün lansman zaman çizelgesi için [Aynı Site Güncelleştirmeleri.](https://www.chromium.org/updates/same-site)</span><span class="sxs-lookup"><span data-stu-id="0dea8-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="0dea8-121">ASP.NET Core 3.1 yeni `SameSite` davranışı uygulamak için güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="0dea8-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="0dea8-122">`SameSiteMode.None` Güncelleştirme, yarama `SameSite=None` davranışını yeniden tanımlar ve özniteliği `SameSiteMode.Unspecified` atlamak `SameSite` için yeni bir değer ekler.</span><span class="sxs-lookup"><span data-stu-id="0dea8-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="0dea8-123">Tanımlama bilgileri kullanan bazı `Unspecified`bileşenler, OpenID Connect korelasyon ve nonce tanımlama bilgileri gibi senaryolarına daha spesifik değerler ayarlasa da, tüm çerez API'leri artık varsayılan olarak varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0dea8-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="0dea8-124">Bu alandaki diğer son değişiklikler için [bkz: HTTP: Bazı çerez SameSite varsayılanları Hiçbiri olarak değiştirildi.](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none)</span><span class="sxs-lookup"><span data-stu-id="0dea8-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="0dea8-125">Core 3.0ASP.NET, çoğu varsayılan değer <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (ancak yine de önceki standardı kullanarak) değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="0dea8-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0dea8-126">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="0dea8-126">Reason for change</span></span>

<span data-ttu-id="0dea8-127">Tarayıcı ve belirtim, önceki metinde belirtildiği gibi değişir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0dea8-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0dea8-128">Recommended action</span></span>

<span data-ttu-id="0dea8-129">Üçüncü taraf oturum açma gibi uzak sitelerle etkileşimde bulunan uygulamaların şunları</span><span class="sxs-lookup"><span data-stu-id="0dea8-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="0dea8-130">Bu senaryoları birden çok tarayıcıda test edin.</span><span class="sxs-lookup"><span data-stu-id="0dea8-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="0dea8-131">[Destek eski tarayıcılarda](#support-older-browsers)tartışılan çerez ilkesi tarayıcısını sniffing azaltma uygulayın.</span><span class="sxs-lookup"><span data-stu-id="0dea8-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="0dea8-132">Test ve tarayıcı koklama yönergeleri için aşağıdaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="0dea8-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="0dea8-133">Etkilenip etkilenmediğinizi belirleyin</span><span class="sxs-lookup"><span data-stu-id="0dea8-133">Determine if you're affected</span></span>

<span data-ttu-id="0dea8-134">Web uygulamanızı yeni davranışı seçebilen bir istemci sürümünü kullanarak test edin.</span><span class="sxs-lookup"><span data-stu-id="0dea8-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="0dea8-135">Chrome, Firefox ve Microsoft Edge Chromium'un tümü test etmek için kullanılabilecek yeni opt-in özellik bayraklarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="0dea8-136">Özellikle Safari'yi uyguladıktan sonra uygulamanızın eski istemci sürümleriyle uyumlu olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="0dea8-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="0dea8-137">Daha fazla bilgi için [bkz.](#support-older-browsers)</span><span class="sxs-lookup"><span data-stu-id="0dea8-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="0dea8-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="0dea8-138">Chrome</span></span>

<span data-ttu-id="0dea8-139">Chrome 78 ve daha sonra yanıltıcı test sonuçları verir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="0dea8-140">Bu sürümler geçici bir azaltma vardır ve çerezlerin iki dakikadan daha eski izin verir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="0dea8-141">Uygun test bayrakları etkinleştirildiğinde, Chrome 76 ve 77 daha doğru sonuçlar verir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="0dea8-142">Yeni davranışı sınamak için `chrome://flags/#same-site-by-default-cookies` etkine geçiş yapın.</span><span class="sxs-lookup"><span data-stu-id="0dea8-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="0dea8-143">Chrome 75 ve daha önceki yeni `None` ayarı ile başarısız olduğu bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="0dea8-144">Daha fazla bilgi için [bkz.](#support-older-browsers)</span><span class="sxs-lookup"><span data-stu-id="0dea8-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="0dea8-145">Google, eski Chrome sürümlerini kullanıma sunmaz.</span><span class="sxs-lookup"><span data-stu-id="0dea8-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="0dea8-146">Ancak, test etmek için yeterli olacak Krom, eski sürümlerini indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dea8-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="0dea8-147">[İndirkrom'daki](https://www.chromium.org/getting-involved/download-chromium)talimatları izleyin.</span><span class="sxs-lookup"><span data-stu-id="0dea8-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="0dea8-148">Krom 76 Win64</span><span class="sxs-lookup"><span data-stu-id="0dea8-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="0dea8-149">Krom 74 Win64</span><span class="sxs-lookup"><span data-stu-id="0dea8-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="0dea8-150">Safari</span><span class="sxs-lookup"><span data-stu-id="0dea8-150">Safari</span></span>

<span data-ttu-id="0dea8-151">Safari 12, önceki taslağı kesinlikle uyguladı ve `None` tanımlama bilgilerindeki yeni değeri görürse başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="0dea8-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="0dea8-152">Bu destek [eski tarayıcılarda](#support-older-browsers)gösterilen tarayıcı koklama kodu üzerinden kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0dea8-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="0dea8-153">Safari 12 ve 13'ün yanı sıra WebKit tabanlı, Işletim Sistemi tarzı girişleri Microsoft Kimlik Doğrulama Kitaplığı (MSAL), Active Directory Authentication Library (ADAL) veya hangi kitaplığı kullanıyorsanız kullanarak test ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0dea8-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="0dea8-154">Sorun, temel işletim sistemi sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0dea8-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="0dea8-155">OSX Mojave 10.14 ve iOS 12'nin yeni davranışla uyumluluk sorunları olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="0dea8-156">OSX Catalina 10.15 veya iOS 13'e yükseltme sorunu giderir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="0dea8-157">Safari'nin şu anda yeni belirtim davranışını sınaması için bir kabul bayrağı yok.</span><span class="sxs-lookup"><span data-stu-id="0dea8-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="0dea8-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="0dea8-158">Firefox</span></span>

<span data-ttu-id="0dea8-159">Yeni standart için Firefox desteği sürüm 68 üzerinde test edilebilir `about:config` ve daha sonra `network.cookie.sameSite.laxByDefault`özellik bayrağı ile sayfada seçerek .</span><span class="sxs-lookup"><span data-stu-id="0dea8-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="0dea8-160">Firefox'un eski sürümlerinde uyumluluk sorunları bildirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="0dea8-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="0dea8-161">Microsoft Edge</span></span>

<span data-ttu-id="0dea8-162">Microsoft Edge eski `SameSite` standardı desteklerken, sürüm 44 itibariyle yeni standartla uyumluluk sorunları yoktu.</span><span class="sxs-lookup"><span data-stu-id="0dea8-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="0dea8-163">Microsoft Edge Krom</span><span class="sxs-lookup"><span data-stu-id="0dea8-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="0dea8-164">Özellik bayrağı `edge://flags/#same-site-by-default-cookies`.</span><span class="sxs-lookup"><span data-stu-id="0dea8-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="0dea8-165">Microsoft Edge Chromium 78 ile test edilerken uyumluluk sorunları gözlenmedi.</span><span class="sxs-lookup"><span data-stu-id="0dea8-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="0dea8-166">Elektron</span><span class="sxs-lookup"><span data-stu-id="0dea8-166">Electron</span></span>

<span data-ttu-id="0dea8-167">Electron sürümleri Krom eski sürümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="0dea8-168">Örneğin, Microsoft Teams tarafından kullanılan Electron sürümü, eski davranışı sergileyen Krom 66'dır.</span><span class="sxs-lookup"><span data-stu-id="0dea8-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="0dea8-169">Ürününüzün kullandığı Electron sürümüyle kendi uyumluluk testinizi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="0dea8-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="0dea8-170">Daha fazla bilgi için [bkz.](#support-older-browsers)</span><span class="sxs-lookup"><span data-stu-id="0dea8-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="0dea8-171">Eski tarayıcıları destekleyin</span><span class="sxs-lookup"><span data-stu-id="0dea8-171">Support older browsers</span></span>

<span data-ttu-id="0dea8-172">2016 `SameSite` standardı, bilinmeyen değerlerin değer `SameSite=Strict` olarak ele alınmasını zorunlu kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0dea8-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="0dea8-173">Sonuç olarak, orijinal standardı destekleyen eski tarayıcılar, değeri `SameSite` .'ye `None`sahip bir özellik gördüklerinde kırılabilir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="0dea8-174">Web uygulamaları, bu eski tarayıcıları desteklemek istiyorlarsa tarayıcı koklama uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0dea8-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="0dea8-175">ASP.NET Core, `User-Agent` istek üstbilgi değerleri son derece kararsız olduğundan ve haftalık olarak değiştiğinden tarayıcı koklama uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="0dea8-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="0dea8-176">Bunun yerine, çerez ilkesindeki bir uzantı noktası belirli bir mantık eklemenize `User-Agent`olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0dea8-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="0dea8-177">*Startup.cs*olarak, aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0dea8-177">In *Startup.cs*, add the following code:</span></span>

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

##### <a name="opt-out-switches"></a><span data-ttu-id="0dea8-178">Devre dışı bırakma anahtarları</span><span class="sxs-lookup"><span data-stu-id="0dea8-178">Opt-out switches</span></span>

<span data-ttu-id="0dea8-179">Uyumluluk `Microsoft.AspNetCore.SuppressSameSiteNone` anahtarı, yeni ASP.NET Core çerez davranışını geçici olarak devre dışı bırakmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0dea8-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="0dea8-180">Projenizdeki *runtimeconfig.template.json* dosyasına aşağıdaki JSON'u ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0dea8-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="0dea8-181">Diğer Sürümler</span><span class="sxs-lookup"><span data-stu-id="0dea8-181">Other Versions</span></span>

<span data-ttu-id="0dea8-182">İlgili `SameSite` düzeltme emaları için önümüzdeki düzeltme emareleri:</span><span class="sxs-lookup"><span data-stu-id="0dea8-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="0dea8-183">ASP.NET Core 2.1, 2.2 ve 3.0</span><span class="sxs-lookup"><span data-stu-id="0dea8-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="0dea8-184">`Microsoft.Owin`4.1</span><span class="sxs-lookup"><span data-stu-id="0dea8-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="0dea8-185">`System.Web`(.NET Framework 4.7.2 ve sonrası için)</span><span class="sxs-lookup"><span data-stu-id="0dea8-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="0dea8-186">Kategori</span><span class="sxs-lookup"><span data-stu-id="0dea8-186">Category</span></span>

<span data-ttu-id="0dea8-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0dea8-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0dea8-188">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0dea8-188">Affected APIs</span></span>

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
