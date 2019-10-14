---
title: Modüller, işleyiciler ve ara yazılım
description: Modüller, işleyiciler ve ara yazılım ile HTTP isteklerini işleme hakkında bilgi edinin.
author: danroth27
ms.author: daroth
ms.date: 10/11/2019
ms.openlocfilehash: b0be6109b9226bddbb9cbe4cebf114fd2b2a6114
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291156"
---
# <a name="modules-handlers-and-middleware"></a>Modüller, işleyiciler ve ara yazılım

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Core bir uygulama, bir dizi ara yazılım üzerine kurulmuştur. Middlewares, istekleri ve yanıtları işlemek için bir işlem hattına düzenlenmiş işleyicileridir. Web Forms uygulamasında HTTP işleyicileri ve modülleri benzer sorunları çözecektir. ASP.NET Core, modüller, işleyiciler, *Global.asax.cs*ve uygulama yaşam döngüsü, ara yazılım ile değiştirilmiştir. Bu bölümde, bir Blazor uygulaması bağlamında hangi ara yazılımı öğreneceksiniz.

## <a name="overview"></a>Genel Bakış

ASP.NET Core isteği ardışık düzeni, bir dizi istekten oluşur ve bunlardan sonra çağırılır. Aşağıdaki diyagramda kavram gösterilmektedir. Yürütmenin iş parçacığı siyah okları izler.

![Konfigüre](media/middleware/request-delegate-pipeline.png)

Önceki diyagramda yaşam döngüsü olaylarının bir kavramı yoktur. Bu kavram, ASP.NET Web Forms isteklerinin nasıl işlendiği konusunda temel bir deneyimdir. Bu sistem, hangi işlemin gerçekleşmekte olduğunu ve ara yazılımın herhangi bir noktaya eklenmesine olanak sağlar. Ara yazılım, istek ardışık düzenine eklendiği sırayla yürütülür. Bunlar, genellikle *Startup.cs*içinde yapılandırma dosyaları yerine kodda de eklenirler.

## <a name="katana"></a>Katana

Katana ile tanıdık okuyucular ASP.NET Core rahat bir şekilde yararlanacaktır. Aslında Katana, ASP.NET Core türetildiği bir çerçevedir. ASP.NET 4. x için benzer bir ara yazılım ve ardışık düzen desenleri getirmiştir. Katana için tasarlanan ara yazılım ASP.NET Core işlem hattı ile çalışacak şekilde uyarlanabilir.

## <a name="common-middleware"></a>Ortak ara yazılım

ASP.NET 4. x birçok modül içerir. Benzer bir biçimde, ASP.NET Core birçok ara yazılım bileşeni de mevcuttur. IIS modülleri, ASP.NET Core bazı durumlarda kullanılabilir. Diğer durumlarda, yerel ASP.NET Core ara yazılımı kullanılabilir olabilir.

Aşağıdaki tabloda, ASP.NET Core ' deki değiştirme ara yazılımı ve bileşenleri listelenmektedir.

|Modül                 |ASP.NET 4. x modülü           |ASP.NET Core seçeneği|
|-----------------------|-----------------------------|-------------------|
|HTTP hataları            |`CustomErrorModule`          |[Durum kodu sayfaları ara yazılımı](/aspnet/core/fundamentals/error-handling#usestatuscodepages)|
|Varsayılan belge       |`DefaultDocumentModule`      |[Varsayılan dosyalar ara yazılımı](/aspnet/core/fundamentals/static-files#serve-a-default-document)|
|Dizin tarama     |`DirectoryListingModule`     |[Dizin tarama ara yazılımı](/aspnet/core/fundamentals/static-files#enable-directory-browsing)|
|Dinamik sıkıştırma    |`DynamicCompressionModule`   |[Yanıt sıkıştırma ara yazılımı](/aspnet/core/performance/response-compression)|
|Başarısız istek izleme|`FailedRequestsTracingModule`|[Günlüğe kaydetme ASP.NET Core](/aspnet/core/fundamentals/logging/index#tracesource-provider)|
|Dosya önbelleğe alma           |`FileCacheModule`            |[Yanıt önbelleğe alma ara yazılımı](/aspnet/core/performance/caching/middleware)|
|HTTP önbelleği           |`HttpCacheModule`            |[Yanıt önbelleğe alma ara yazılımı](/aspnet/core/performance/caching/middleware)|
|HTTP günlüğü           |`HttpLoggingModule`          |[Günlüğe kaydetme ASP.NET Core](/aspnet/core/fundamentals/logging/index)|
|HTTP yeniden yönlendirme       |`HttpRedirectionModule`      |[URL yeniden yazma ara yazılımı](/aspnet/core/fundamentals/url-rewriting)|
|ISAPI filtreleri          |`IsapiFilterModule`          |[Yazılımlar](/aspnet/core/fundamentals/middleware/index)|
|I                  |`IsapiModule`                |[Yazılımlar](/aspnet/core/fundamentals/middleware/index)|
|İstek filtreleme      |`RequestFilteringModule`     |[URL yeniden yazma ara yazılımı ırule](/aspnet/core/fundamentals/url-rewriting#irule-based-rule)|
|URL yeniden yazma&#8224;   |`RewriteModule`              |[URL yeniden yazma ara yazılımı](/aspnet/core/fundamentals/url-rewriting)|
|Statik sıkıştırma     |`StaticCompressionModule`    |[Yanıt sıkıştırma ara yazılımı](/aspnet/core/performance/response-compression)|
|Statik içerik         |`StaticFileModule`           |[Statik dosya ara yazılımı](/aspnet/core/fundamentals/static-files)|
|URL yetkilendirmesi      |`UrlAuthorizationModule`     |[ASP.NET Core kimliği](/aspnet/core/security/authentication/identity)|

Bu liste ayrıntılı değildir ancak iki çerçeve arasında hangi eşlemenin mevcut olduğunu fikir vermelidir. Daha ayrıntılı bir liste için bkz. [ASP.NET Core Ile IIS modülleri](/aspnet/core/host-and-deploy/iis/modules).

## <a name="custom-middleware"></a>Özel ara yazılım

Yerleşik ara yazılım, bir uygulama için gereken tüm senaryoları işleyemez. Böyle durumlarda, kendi ara ortamınızı oluşturmak mantıklı olur. En basit olan basit bir temsilciyle, ara yazılım tanımlamanın birden çok yolu vardır. Bir sorgu dizesinden gelen kültür isteğini kabul eden aşağıdaki ara yazılımı göz önünde bulundurun:

```csharp
public class Startup
{
    public void Configure(IApplicationBuilder app)
    {
        app.Use(async (context, next) =>
        {
            var cultureQuery = context.Request.Query["culture"];

            if (!string.IsNullOrWhiteSpace(cultureQuery))
            {
                var culture = new CultureInfo(cultureQuery);

                CultureInfo.CurrentCulture = culture;
                CultureInfo.CurrentUICulture = culture;
            }

            // Call the next delegate/middleware in the pipeline
            await next();
        });

        app.Run(async (context) =>
            await context.Response.WriteAsync(
                $"Hello {CultureInfo.CurrentCulture.DisplayName}"));
    }
}
```

Ara yazılım, `IMiddleware` arabirimini veya aşağıdaki ara yazılım kuralını uygulayarak da sınıf olarak tanımlanabilir. Daha fazla bilgi için bkz. [özel ASP.NET Core ara yazılımı yazma](/aspnet/core/fundamentals/middleware/write).

>[!div class="step-by-step"]
>[Önceki](data.md)
>[İleri](config.md)
