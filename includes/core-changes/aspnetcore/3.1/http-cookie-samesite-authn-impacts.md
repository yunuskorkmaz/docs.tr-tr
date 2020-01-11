---
ms.openlocfilehash: 02602c70689a6d2729e03d3d7230cda5ae7a4994
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902030"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP: Browser SameSite değişikliklerinin etkisi kimlik doğrulaması

Chrome ve Firefox gibi bazı tarayıcılar, tanımlama bilgileri için `SameSite` uygulamalarında önemli değişiklikler yaptı. Değişiklikler, OpenID Connect ve WS-Federation gibi uzak kimlik doğrulama senaryolarını etkiler ve bu, `SameSite=None`göndermesi için kabul etmelidir. Ancak, iOS 12 ' de ve diğer tarayıcıların bazı eski sürümlerinde `SameSite=None` kesilir. Uygulamanın bu sürümleri algılaması ve `SameSite`atması gerekir.

Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996).

#### <a name="version-introduced"></a>Sunulan sürüm

3,1 Preview 1

#### <a name="old-behavior"></a>Eski davranış

`SameSite`, HTTP tanımlama bilgilerine yönelik 2016 taslak standart uzantısıdır. Siteler arası Istek sahteciliği 'nin (CSRF) azaltılmasına yöneliktir. Bu, başlangıçta yeni parametreler ekleyerek sunucuların kabul etmesinin tercih edildiği bir özellik olarak tasarlanmıştır. ASP.NET Core 2,0 `SameSite`için başlangıç desteğini ekledi.

#### <a name="new-behavior"></a>Yeni davranış

Google, geriye doğru uyumlu olmayan yeni bir taslak standardı önerdi. Standart, varsayılan modu `Lax` olarak değiştirir ve geri çevirmek için yeni bir giriş `None` ekler. Çoğu uygulama tanımlama bilgisi için yeterli `Lax`. Ancak, OpenID Connect ve WS-Federation oturum açma gibi siteler arası senaryoları keser. İsteğin akışlarına yönelik farklılıklar nedeniyle çoğu OAuth oturum açma işlemleri etkilenmez. Yeni `None` parametresi, önceki taslak standardını uygulayan istemcilerle uyumluluk sorunlarına neden olur (örneğin, iOS 12). Chrome 80, değişiklikleri içerir. Chrome ürün başlatma zaman çizelgesi için bkz. [SameSite Updates](https://www.chromium.org/updates/same-site) .

ASP.NET Core 3,1, yeni `SameSite` davranışını uygulayacak şekilde güncelleştirildi. Güncelleştirme, `SameSite=None` yayma `SameSiteMode.None` davranışını yeniden tanımlar ve `SameSite` özniteliğini atlamak için `SameSiteMode.Unspecified` yeni bir değer ekler. Tanımlama bilgilerini kullanan bazı bileşenler, OpenID Connect bağıntı ve nonce tanımlama bilgileri gibi senaryolarına daha belirgin değerler ayarlamış olsa da, tüm tanımlama bilgisi API 'Leri artık varsayılan `Unspecified`.

Bu alandaki diğer son değişiklikler için bkz. [http: bazı tanımlama bilgisi SameSite Varsayılanları None olarak değiştirildi](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none). ASP.NET Core 3,0 ' de, çoğu varsayılan değer <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> olarak değiştirilmiştir (ancak yine de önceki standart kullanılarak).

#### <a name="reason-for-change"></a>Değişiklik nedeni

Tarayıcı ve belirtim, önceki metinde özetlenen şekilde değişir.

#### <a name="recommended-action"></a>Önerilen eylem

Üçüncü taraf oturum açma gibi uzak sitelerle etkileşim kuran uygulamalar şunlar gerekir:

* Bu senaryoları birden çok tarayıcıda test edin.
* [Daha eski tarayıcıları desteklemek](#support-older-browsers)için açıklanan tanımlama bilgisi İlkesi tarayıcı algılaması risk azaltma ' yı uygulayın.

Test ve tarayıcı algılama yönergeleri için aşağıdaki bölüme bakın.

##### <a name="determine-if-youre-affected"></a>Etkilenip etkilenmediğini belirleme

Yeni davranışı kabul eden bir istemci sürümünü kullanarak Web uygulamanızı test edin. Chrome, Firefox ve Microsoft Edge Bermium tümünde test için kullanılabilecek yeni bir katılım özelliği bayrakları vardır. Düzeltme eklerini uyguladıktan sonra uygulamanızın eski istemci sürümleriyle uyumlu olduğunu doğrulayın, özellikle Safari. Daha fazla bilgi için bkz. [eski tarayıcıları destekleme](#support-older-browsers).

##### <a name="chrome"></a>Chrome

Chrome 78 ve üzeri, yanıltıcı test sonuçları elde. Bu sürümlerin yerinde geçici bir risk azaltma ve iki dakikadan daha eski tanımlama bilgilerine izin verme. Uygun test bayrakları etkinken, Chrome 76 ve 77 daha doğru sonuçlar elde edin. Yeni davranışı test etmek için `chrome://flags/#same-site-by-default-cookies` etkin olarak değiştirin. Chrome 75 ve önceki sürümleri, yeni `None` ayarıyla başarısız olacak şekilde bildirilir. Daha fazla bilgi için bkz. [eski tarayıcıları destekleme](#support-older-browsers).

Google, eski Chrome sürümlerini kullanılabilir hale getirir. Ancak, test için yeterli olacak şekilde, Kmıum 'un eski sürümlerini indirebilirsiniz. [Kmıum indirme](https://www.chromium.org/getting-involved/download-chromium)bölümündeki yönergeleri izleyin.

* [Kmıum 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Kmıum 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Safari 12, önceki taslağı tamamen uyguladık ve tanımlama bilgilerinde yeni `None` değeri görülemezse başarısız olur. Bu, [eski tarayıcıları destekleme](#support-older-browsers)bölümünde gösterilen tarayıcı algılama kodu aracılığıyla kaçınılmalıdır. Safari 12 ve 13 ' ün yanı sıra, Microsoft kimlik doğrulama kitaplığı (MSAL), Active Directory Authentication Library (ADAL) veya kullandığınız kitaplığı kullanarak WebKit tabanlı, işletim sistemi stili oturum açma işlemlerini de test edin. Sorun, temel alınan işletim sistemi sürümüne bağımlıdır. OSX Mojave 10,14 ve iOS 12 ' nin yeni davranışla uyumluluk sorunlarına sahip olduğu bilinmektedir. OSX Catalina 10,15 veya iOS 13 ' e yükseltmek sorunu düzeltir. Safari 'nin şu anda yeni belirtim davranışını test etmek için bir katılım bayrağı yoktur.

##### <a name="firefox"></a>Firefox

Yeni standart için Firefox desteği, sürüm 68 ve üzeri sürümlerde, özellik bayrağı `network.cookie.sameSite.laxByDefault``about:config` sayfasında ' de seçilerek test edilebilir. Firefox 'un eski sürümlerinde uyumluluk sorunları bildirilmemiştir.

##### <a name="microsoft-edge"></a>Microsoft Edge

Microsoft Edge, sürüm 44 itibariyle eski `SameSite` standardını desteklese de, yeni standart ile herhangi bir uyumluluk sorununa sahip değildir.

##### <a name="microsoft-edge-chromium"></a>Microsoft Edge Kmuum

Özellik bayrağı `edge://flags/#same-site-by-default-cookies`. Microsoft Edge Kmıum 78 ile test edilirken hiçbir uyumluluk sorunu gözlemlenmedi.

##### <a name="electron"></a>Tron

Elektron sürümleri, daha eski bir Kmıum sürümlerini içerir. Örneğin, Microsoft ekipleri tarafından kullanılan elektron sürümü, eski davranışı gösteren Kmıum 66 ' dir. Ürününüzün kullandığı elektron sürümüyle kendi uyumluluk testinizi gerçekleştirin. Daha fazla bilgi için bkz. [eski tarayıcıları destekleme](#support-older-browsers).

##### <a name="support-older-browsers"></a>Eski tarayıcıları destekleme

2016 `SameSite` standart uygulanan, bilinmeyen değerler `SameSite=Strict` değer olarak değerlendirilir. Sonuç olarak, özgün standardı destekleyen eski tarayıcılar, `None`bir `SameSite` özelliği görtiklerinde kesintiye uğratır. Web uygulamaları, bu eski tarayıcıları desteklemeyi amaçlarsa tarayıcı algılaması gerçekleştirmelidir. ASP.NET Core, `User-Agent` istek üst bilgisi değerleri son derece kararsız olduğundan ve haftalık olarak değişeceğinden sizin için tarayıcı algılaması uygulamaz. Bunun yerine, tanımlama bilgisi ilkesindeki bir uzantı noktası, `User-Agent`özel mantık eklemenize olanak tanır.

*Startup.cs*içinde aşağıdaki kodu ekleyin:

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

##### <a name="opt-out-switches"></a>Kabul etme anahtarları

`Microsoft.AspNetCore.SuppressSameSiteNone` uyumluluk anahtarı, yeni ASP.NET Core tanımlama bilgisi davranışının geçici olarak devre dışı kalmanızı sağlar. Aşağıdaki JSON *öğesini projenizdeki runtimeconfig. Template. JSON* dosyasına ekleyin:

```json
{ 
  "configProperties": { 
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true" 
  } 
}
```

##### <a name="other-versions"></a>Diğer sürümler

İlgili `SameSite` düzeltme ekleri şu şekilde yapılır:

* ASP.NET Core 2,1, 2,2 ve 3,0
* `Microsoft.Owin` 4,1
* `System.Web` (.NET Framework 4.7.2 ve üzeri için)

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
