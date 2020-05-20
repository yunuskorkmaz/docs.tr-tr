---
title: Cloud Native uygulamalar için IdentityServer
description: Azure için Cloud Native .NET uygulamaları tasarlama | IdentityServer
ms.date: 05/13/2020
ms.openlocfilehash: 81cce30568becacda29f65f9506398790af321e0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614038"
---
# <a name="identityserver-for-cloud-native-applications"></a>Bulutta yerel uygulamalar için IdentityServer

IdentityServer, ASP.NET Core için OpenID Connect (OıDC) ve OAuth 2,0 standartları uygulayan açık kaynaklı bir kimlik doğrulama sunucusudur. Web, yerel, mobil veya API uç noktaları olsun, tüm uygulamalarınıza yönelik isteklerin kimliklerinin doğrulanması için ortak bir yol sağlamak üzere tasarlanmıştır. IdentityServer, birden çok uygulama ve uygulama türü için çoklu oturum açma (SSO) uygulamak için kullanılabilir. Kullanıcı arabirimi olmadan, genellikle belirteç verme, doğrulama ve yenileme içeren hizmet tabanlı kimlik doğrulaması ile, oturum açma formları ve benzer kullanıcı arabirimleri aracılığıyla gerçek kullanıcıların kimliğini doğrulamak için kullanılabilir. IdentityServer, özelleştirilebilir bir çözüm olarak tasarlanmıştır. Her örnek genellikle tek bir kuruluşa ve/veya uygulama gereksinimlerine uyacak şekilde özelleştirilir.

## <a name="common-web-app-scenarios"></a>Ortak Web uygulaması senaryoları

Genellikle, uygulamaların aşağıdaki senaryolardan bazılarını veya tümünü desteklemesi gerekir:

- İnsan kullanıcıları Web uygulamalarına bir tarayıcıyla erişiyor.
- Tarayıcı tabanlı uygulamalardan arka uç Web API 'Lerine erişen insan kullanıcıları.
- Mobil/yerel istemcilerde, arka uç Web API 'Lerine erişen insan kullanıcıları.
- Arka uç Web API 'Lerine erişen diğer uygulamalar (etkin bir kullanıcı veya Kullanıcı arabirimi olmadan).
- Herhangi bir uygulamanın kendi kimliğini kullanarak veya kullanıcının kimliğine temsilci atamak için diğer Web API 'Leriyle etkileşmesi gerekebilir.

![Uygulama türleri ve senaryolar](./media/application-types.png)

**Şekil 8-1**. Uygulama türleri ve senaryolar.

Bu senaryoların her birinde, sunulan işlevlerin yetkisiz kullanıma karşı korunması gerekir. Bu, genellikle bir kaynak için istek yapan kullanıcının veya sorumlunun kimlik doğrulamasını gerektirir. Bu kimlik doğrulaması SAML2p, WS-beslenir veya OpenID Connect gibi birkaç ortak protokolden birini kullanabilir. API 'lerle iletişim kurmak genellikle OAuth2 protokolünü ve güvenlik belirteçleri desteğini kullanır. Bu kritik çapraz güvenlik sorunlarının ve uygulama ayrıntılarının uygulamalardan ayrılması, tutarlılığı sağlar ve güvenlik ve bakım özelliklerini geliştirir. Bu kaygıları IdentityServer gibi özel bir ürünle dış olarak eklemek, her uygulamanın bu sorunların kendisini çözmesine yardımcı olur.

IdentityServer, bir ASP.NET Core uygulaması içinde çalışan ara yazılım sağlar ve OpenID Connect ve OAuth2 için destek ekler (bkz. [desteklenen özellikler](http://docs.identityserver.io/en/latest/intro/specs.html)). Kuruluşlar, tüm belirteç tabanlı güvenlik protokollerinde STS görevi gören IdentityServer ara yazılımını kullanarak kendi ASP.NET Core uygulamalarını oluşturur. IdentityServer ara yazılımı, aşağıdakiler dahil olmak üzere standart işlevleri desteklemek için uç noktalar sunar:

- Yetkilendirme (son kullanıcının kimliğini doğrulama)
- Belirteç (bir belirteci programlama yoluyla isteme)
- Bulma (sunucu hakkındaki meta veriler)
- Kullanıcı bilgileri (geçerli bir erişim belirteciyle Kullanıcı bilgilerini al)
- Cihaz yetkilendirmesi (cihaz akışı yetkilendirmesini başlatmak için kullanılır)
- İç denetim (belirteç doğrulama)
- İptal (belirteç iptali)
- Oturumu sonlandır (tüm uygulamalarda çoklu oturum açmayı Tetikle)

## <a name="getting-started"></a>Başlarken

Identityserver4 açık kaynak ve ücretsiz olarak kullanılabilir. Bunu, NuGet paketlerini kullanarak uygulamalarınıza ekleyebilirsiniz. Ana paket, 4.000.000 defa indirilen [ıdentityserver4](https://www.nuget.org/packages/IdentityServer4/) . Temel paket, herhangi bir kullanıcı arabirimi kodu içermez ve yalnızca bellek yapılandırmasında desteklenir. Veritabanını bir veritabanıyla birlikte kullanmak için, IdentityServer için yapılandırma ve işletimsel verileri depolamak üzere Entity Framework Core kullanan [ıdentityserver4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) gibi bir veri sağlayıcısı da isteyebilirsiniz. Kullanıcı arabirimi için, oturum açma için destek eklemek ve IdentityServer ara yazılımını kullanarak oturumu kapatmak için [hızlı başlangıç Kullanıcı arabirimi deposundan](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) ASP.NET Core MVC Uygulamanıza dosya kopyalayabilirsiniz.

## <a name="configuration"></a>Yapılandırma

IdentityServer, her bir özel yüklemenin parçası olarak yapılandırılabilen farklı protokol türlerini ve sosyal kimlik doğrulama sağlayıcılarını destekler. Bu, genellikle yönteminde ASP.NET Core uygulamanın `Startup` sınıfında yapılır `ConfigureServices` . Yapılandırma desteklenen protokollerin ve kullanılacak sunucuların ve uç noktaların yollarını belirtmeyi içerir. Şekil 8-2, ıdentityserver4 hızlı başlangıç Kullanıcı arabirimi projesinden alınan bir örnek yapılandırmayı gösterir:

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        // some details omitted
        services.AddIdentityServer();

          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<insert here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

**Şekil 8-2**. IdentityServer yapılandırılıyor.

IdentityServer, çeşitli protokolleri ve konfigürasyonları test etmek için kullanılabilecek bir genel tanıtım sitesi de barındırır. Bu, üzerinde bulunur [https://demo.identityserver.io/](https://demo.identityserver.io/) ve davranışını buna göre yapılandırma hakkında bilgi içerir `client_id` .

## <a name="javascript-clients"></a>JavaScript istemcileri

Birçok bulutta yerel uygulama, Ön uçtaki sunucu tarafı API 'Leri ve zengin istemci tek sayfa uygulamaları (maça 'lar) ile faydalanır. IdentityServer [JavaScript client](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) `oidc-client.js` , oturum açma, oturumu kapatma ve Web API 'lerinin belirteç tabanlı kimlik doğrulaması için IdentityServer 'ı kullanabilmesi amacıyla, NPM aracılığıyla bir JavaScript istemcisi () sağlar.

## <a name="references"></a>Başvurular

- [IdentityServer belgeleri](http://docs.identityserver.io/en/latest/)
- [Uygulama türleri](https://docs.microsoft.com/azure/active-directory/develop/app-types)
- [JavaScript OıDC istemcisi](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html)

>[!div class="step-by-step"]
>[Önceki](azure-active-directory.md) 
> [Sonraki](security.md)
