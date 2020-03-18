---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968193"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP: Tarayıcı SameSite değişiklikleri kimlik doğrulamayı etkiler

Chrome ve Firefox gibi bazı tarayıcılar, çerezler `SameSite` için kendi uygulamalarında kırma değişiklikler yaptı. Değişiklikler, OpenID Connect ve WS-Federation gibi uzaktan kimlik doğrulama senaryolarını `SameSite=None`etkiler ve bu senaryoyu göndererek devre dışı bırakmaları gerekir. Ancak, `SameSite=None` iOS 12 ve diğer tarayıcıların bazı eski sürümlerinde molalar. Uygulama bu sürümleri koklamak ve `SameSite`atlamak gerekir.

Bu konuda tartışma için [dotnet/aspnetcore#14996'ya](https://github.com/dotnet/aspnetcore/issues/14996)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.1 Önizleme 1

#### <a name="old-behavior"></a>Eski davranış

`SameSite`HTTP çerezleri için 2016 taslak standart uzantısıdır. Bu Çapraz Site İstek Sahtesini (CSRF) azaltmak için tasarlanmıştır. Bu, başlangıçta sunucuların yeni parametreleri ekleyerek tercih edeceği bir özellik olarak tasarlanmıştır. ASP.NET Core 2.0 için `SameSite`ilk destek ekledi.

#### <a name="new-behavior"></a>Yeni davranış

Google, geriye dönük uyumlu olmayan yeni bir taslak standart önerdi. Standart varsayılan modu değiştirir `Lax` ve devre `None` dışı bırakmak için yeni bir giriş ekler. `Lax` çoğu uygulama çerezleri için yeterlidir; ancak, OpenID Connect ve WS-Federation girişi gibi siteleri arası senaryoları kırar. OAuth girişlerinin çoğu, isteğin akışındaki farklılıklar nedeniyle etkilenmez. Yeni `None` parametre, önceki taslak standardı (örneğin, iOS 12) uygulayan istemcilerle uyumluluk sorunlarına neden olur. Chrome 80 değişiklikleri içerecektir. Bkz. Chrome ürün lansman zaman çizelgesi için [Aynı Site Güncelleştirmeleri.](https://www.chromium.org/updates/same-site)

ASP.NET Core 3.1 yeni `SameSite` davranışı uygulamak için güncelleştirildi. `SameSiteMode.None` Güncelleştirme, yarama `SameSite=None` davranışını yeniden tanımlar ve özniteliği `SameSiteMode.Unspecified` atlamak `SameSite` için yeni bir değer ekler. Tanımlama bilgileri kullanan bazı `Unspecified`bileşenler, OpenID Connect korelasyon ve nonce tanımlama bilgileri gibi senaryolarına daha spesifik değerler ayarlasa da, tüm çerez API'leri artık varsayılan olarak varsayılan olarak kullanılır.

Bu alandaki diğer son değişiklikler için [bkz: HTTP: Bazı çerez SameSite varsayılanları Hiçbiri olarak değiştirildi.](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none) Core 3.0ASP.NET, çoğu varsayılan değer <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (ancak yine de önceki standardı kullanarak) değiştirildi.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Tarayıcı ve belirtim, önceki metinde belirtildiği gibi değişir.

#### <a name="recommended-action"></a>Önerilen eylem

Üçüncü taraf oturum açma gibi uzak sitelerle etkileşimde bulunan uygulamaların şunları

* Bu senaryoları birden çok tarayıcıda test edin.
* [Destek eski tarayıcılarda](#support-older-browsers)tartışılan çerez ilkesi tarayıcısını sniffing azaltma uygulayın.

Test ve tarayıcı koklama yönergeleri için aşağıdaki bölüme bakın.

##### <a name="determine-if-youre-affected"></a>Etkilenip etkilenmediğinizi belirleyin

Web uygulamanızı yeni davranışı seçebilen bir istemci sürümünü kullanarak test edin. Chrome, Firefox ve Microsoft Edge Chromium'un tümü test etmek için kullanılabilecek yeni opt-in özellik bayraklarına sahiptir. Özellikle Safari'yi uyguladıktan sonra uygulamanızın eski istemci sürümleriyle uyumlu olduğunu doğrulayın. Daha fazla bilgi için [bkz.](#support-older-browsers)

##### <a name="chrome"></a>Chrome

Chrome 78 ve daha sonra yanıltıcı test sonuçları verir. Bu sürümler geçici bir azaltma vardır ve çerezlerin iki dakikadan daha eski izin verir. Uygun test bayrakları etkinleştirildiğinde, Chrome 76 ve 77 daha doğru sonuçlar verir. Yeni davranışı sınamak için `chrome://flags/#same-site-by-default-cookies` etkine geçiş yapın. Chrome 75 ve daha önceki yeni `None` ayarı ile başarısız olduğu bildirilmiştir. Daha fazla bilgi için [bkz.](#support-older-browsers)

Google, eski Chrome sürümlerini kullanıma sunmaz. Ancak, test etmek için yeterli olacak Krom, eski sürümlerini indirebilirsiniz. [İndirkrom'daki](https://www.chromium.org/getting-involved/download-chromium)talimatları izleyin.

* [Krom 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Krom 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Safari 12, önceki taslağı kesinlikle uyguladı ve `None` tanımlama bilgilerindeki yeni değeri görürse başarısız oldu. Bu destek [eski tarayıcılarda](#support-older-browsers)gösterilen tarayıcı koklama kodu üzerinden kaçınılmalıdır. Safari 12 ve 13'ün yanı sıra WebKit tabanlı, Işletim Sistemi tarzı girişleri Microsoft Kimlik Doğrulama Kitaplığı (MSAL), Active Directory Authentication Library (ADAL) veya hangi kitaplığı kullanıyorsanız kullanarak test ettiğinizden emin olun. Sorun, temel işletim sistemi sürümüne bağlıdır. OSX Mojave 10.14 ve iOS 12'nin yeni davranışla uyumluluk sorunları olduğu bilinmektedir. OSX Catalina 10.15 veya iOS 13'e yükseltme sorunu giderir. Safari'nin şu anda yeni belirtim davranışını sınaması için bir kabul bayrağı yok.

##### <a name="firefox"></a>Firefox

Yeni standart için Firefox desteği sürüm 68 üzerinde test edilebilir `about:config` ve daha sonra `network.cookie.sameSite.laxByDefault`özellik bayrağı ile sayfada seçerek . Firefox'un eski sürümlerinde uyumluluk sorunları bildirilmemiştir.

##### <a name="microsoft-edge"></a>Microsoft Edge

Microsoft Edge eski `SameSite` standardı desteklerken, sürüm 44 itibariyle yeni standartla uyumluluk sorunları yoktu.

##### <a name="microsoft-edge-chromium"></a>Microsoft Edge Krom

Özellik bayrağı `edge://flags/#same-site-by-default-cookies`. Microsoft Edge Chromium 78 ile test edilerken uyumluluk sorunları gözlenmedi.

##### <a name="electron"></a>Elektron

Electron sürümleri Krom eski sürümleri içerir. Örneğin, Microsoft Teams tarafından kullanılan Electron sürümü, eski davranışı sergileyen Krom 66'dır. Ürününüzün kullandığı Electron sürümüyle kendi uyumluluk testinizi gerçekleştirin. Daha fazla bilgi için [bkz.](#support-older-browsers)

##### <a name="support-older-browsers"></a>Eski tarayıcıları destekleyin

2016 `SameSite` standardı, bilinmeyen değerlerin değer `SameSite=Strict` olarak ele alınmasını zorunlu kılmalıdır. Sonuç olarak, orijinal standardı destekleyen eski tarayıcılar, değeri `SameSite` .'ye `None`sahip bir özellik gördüklerinde kırılabilir. Web uygulamaları, bu eski tarayıcıları desteklemek istiyorlarsa tarayıcı koklama uygulaması gerekir. ASP.NET Core, `User-Agent` istek üstbilgi değerleri son derece kararsız olduğundan ve haftalık olarak değiştiğinden tarayıcı koklama uygulamaz. Bunun yerine, çerez ilkesindeki bir uzantı noktası belirli bir mantık eklemenize `User-Agent`olanak tanır.

*Startup.cs*olarak, aşağıdaki kodu ekleyin:

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

##### <a name="opt-out-switches"></a>Devre dışı bırakma anahtarları

Uyumluluk `Microsoft.AspNetCore.SuppressSameSiteNone` anahtarı, yeni ASP.NET Core çerez davranışını geçici olarak devre dışı bırakmanızı sağlar. Projenizdeki *runtimeconfig.template.json* dosyasına aşağıdaki JSON'u ekleyin:

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a>Diğer Sürümler

İlgili `SameSite` düzeltme emaları için önümüzdeki düzeltme emareleri:

* ASP.NET Core 2.1, 2.2 ve 3.0
* `Microsoft.Owin`4.1
* `System.Web`(.NET Framework 4.7.2 ve sonrası için)

#### <a name="category"></a>Kategori

ASP.NET

#### <a name="affected-apis"></a>Etkilenen API’ler

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
