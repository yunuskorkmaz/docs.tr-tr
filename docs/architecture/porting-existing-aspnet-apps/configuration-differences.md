---
title: ASP.NET MVC ve ASP.NET Core arasındaki yapılandırma farklılıkları
description: Yapılandırma değerleri nasıl depolanır ve ASP.NET ile ASP.NET Core arasında önemli ölçüde değiştirilir. Bu bölüm, ayrıntıları ve ASP.NET 'den ASP.NET Core 'e nasıl geçiş yapılacağını inceler.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: cdac00334f86a147dfa9c8b99412b5f3facad8fd
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639229"
---
# <a name="configuration-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core arasındaki yapılandırma farklılıkları

Yapılandırma değerleri nasıl depolanır ve ASP.NET ile ASP.NET Core arasında önemli ölçüde değiştirilir.

## <a name="aspnet-mvc-configuration"></a>ASP.NET MVC yapılandırması

ASP.NET uygulamalarında, yapılandırma yerleşik .NET yapılandırma dosyalarını kullanır, uygulama klasöründeki *web.config* ve sunucuda *machine.config* . Çoğu ASP.NET MVC ve Web API uygulaması, ayarlarını yapılandırma dosyası `appSettings` veya `connectionStrings` öğelerinde depolar. Bazıları, bir ayarlar sınıfına eşlenemeyen özel yapılandırma bölümleri de kullanır.

Bir .NET Framework uygulamasındaki yapılandırmaya, sınıfı kullanılarak erişilir `System.Configuration.ConfigurationManager` . Ne yazık ki bu sınıf yapılandırma öğelerine statik erişim sağlar. Sonuç olarak, çok az sayıda ASP.NET MVC uygulaması, yapılandırma ayarlarına soyut erişim veya gerektiğinde bunları ekleme eğilimindedir. Bunun yerine, çoğu .NET Framework uygulama, uygulamanın bir ayarı kullanması için ihtiyaç duyacağı her yerde yapılandırma sistemine doğrudan erişim eğilimindedir.

Tipik ASP.NET MVC yapılandırma erişimi:

```csharp
string connectionString =
    ConfigurationManager.ConnectionStrings["DefaultConnection"]
        .ConnectionString;
```

## <a name="aspnet-core-configuration"></a>ASP.NET Core yapılandırması

ASP.NET Core uygulamalarda, yapılandırma, yapılandırılabilir. Ancak, çoğu uygulama Standart proje şablonlarının bir parçası olarak bir dizi varsayılan kümesi kullanır ve bu `ConfigureWebHostDefaults` Yöntem içinde kullanılır. Varsayılan ayarlar, *üzerindeappsettings.Development.js* gibi ortama özgü dosyalarla *appsettings.jstemel* ayarları geçersiz KıLABILME özelliği ile JSON biçimli dosyaları kullanır. Ayrıca, varsayılan yapılandırma sistemi, dosya tabanlı tüm ayarları aynı adlandırılmış ayar için mevcut olan herhangi bir ortam değişkeniyle daha da geçersiz kılar. Bu pek çok senaryoda faydalıdır ve özellikle barındırma ortamına dağıtım yaparken yararlıdır, çünkü yapılandırma dosyalarının dağıtımı, önemli üretim yapılandırma ayarlarının yanlışlıkla üzerine yazılıp yazılmayacağı konusunda endişelenmenize gerek kalmaz. Yapılandırma değerleri, komut satırı bağımsız değişkenleri olarak da bulunabilir.

Yapılandırma değerlerine erişim, .NET Core 'da birçok şekilde yapılabilir. Bağımlılık ekleme, .NET Core 'da yerleşik olduğundan, yapılandırma değerlerine genellikle gereken sınıflara eklenen bir arabirim üzerinden erişilir. Bu, gibi bir arabirimi geçirmeyi gerektirebilir <xref:Microsoft.Extensions.Configuration.IConfiguration> , ancak genellikle [Seçenekler modelini](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/options)kullanarak sınıfın gerektirdiği ayarları geçirmek daha iyidir.

Şekil 2-2 `IConfiguration` ' de bir Razor sayfasına geçme ve yapılandırma ayarlarına erişme işlemlerinin nasıl yapılacağı gösterilmektedir:

```csharp
using Microsoft.Extensions.Configuration;

public class TestModel : PageModel
{
    private readonly IConfiguration _configuration;

    public TestModel(IConfiguration configuration)
    {
        _configuration= configuration;
    }

    public ContentResult OnGet()
    {
        var myKeyValue = _configuration["MyKey"];

        // ...
    }
}
```

**Şekil 2-2.** İle yapılandırma değerlerine erişme `IConfiguration` .

Seçenekler modelini kullanarak, ayarlar erişimi benzerdir, ancak, Şekil 2-3 gösterdiği gibi, tüketen sınıf tarafından gerek duyulan ayarlara kesin ve daha belirgin bir şekilde yazılır.

```csharp
public class PositionOptions
{
    public const string Position = nameof(Position);

    public string Title { get; set; }
    public string Name { get; set; }
}

public class Test2Model : PageModel
{
    private readonly PositionOptions _options;

    public Test2Model(IOptions<PositionOptions> options)
    {
        _options = options.Value;
    }

    public ContentResult OnGet()
    {
        return Content($"Title: {_options.Title}\nName: {_options.Name}");
    }
}
```

**Şekil 2-3.** ASP.NET Core ' de seçenekler deseninin kullanımı.

Seçenekler deseninin çalışması için, uygulama başlatıldığında seçenekler türü ' de yapılandırılmalıdır `ConfigureServices` :

```csharp
// required in ConfigureServices
services.Configure<PositionOptions>(Configuration.GetSection(PositionOptions.Position));
```

## <a name="migrate-configuration"></a>Yapılandırmayı geçir

.NET Framework bir uygulamanın yapılandırma ayarlarının .NET Core 'a nasıl bağlantı noktası alınacağını düşünürken, ilk adım kullanılmakta olan tüm yapılandırma ayarlarını belirlemektir. Bunların çoğu, uygulamanın kök klasöründeki *web.config* dosyasında olacaktır, ancak bazı uygulamalar ayarların paylaşılan *machine.config* dosyasında da bulunması beklenir.

Yapılandırma dosyalarındaki tüm ayarlar kataloglandığında, bir sonraki adım, ayarların uygulamanın kendisinde nerede ve nasıl kullanıldığını belirlemek için olmalıdır. Bazı ayarlar kullanılmıyorsa, bu büyük olasılıkla geçişten atlanabilir. Her ayar için, kodu geçirdiğinizde herhangi bir şey kaçırmadığınızdan emin olmak için, kullanılmakta olan tüm yerleri göz önünde bulabilirsiniz.

ASP.NET uygulamasını hala koruyorsanız, statik başvuruların `ConfigurationManager` ve arabirimlerin üzerinden erişime karşı değiştirilmesini önlemeye yardımcı olabilir. Bu, ASP.NET Core yapılandırma sistemine geçişi kolaylaştıracaktır. Genel olarak, dış kaynaklara statik erişim kodun test ve bakımını daha zor hale getirir. bu nedenle, uygulamanın bu kalıbı takip eden bir yerde olması gerekir.

## <a name="references"></a>Başvurular

- [ASP.NET Core yapılandırma](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/)
- [ASP.NET Core'da seçenek deseni](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/options)
- [Yapılandırmayı ASP.NET Core geçir](https://docs.microsoft.com/aspnet/core/migration/configuration)
- [Statik yapılandırma erişimini yeniden düzenleme](https://ardalis.com/refactoring-static-config-access/)

>[!div class="step-by-step"]
>[Önceki](middleware-modules-handlers.md) 
> [Sonraki](routing-differences.md)
