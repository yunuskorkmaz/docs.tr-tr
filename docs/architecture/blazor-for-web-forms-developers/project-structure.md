---
title: Blazor uygulamaları için proje yapısı
description: web formları ve Blazor projelerinin proje yapılarının ASP.NET karşılaştırın.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 2c383e86ff22f5a3460476998992b66e9417cc11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401580"
---
# <a name="project-structure-for-blazor-apps"></a>Blazor uygulamaları için proje yapısı

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Önemli proje yapısı farklılıklarına rağmen, ASP.NET Web Formları ve Blazor benzer birçok kavramı paylaşır. Burada, bir Blazor projesinin yapısına bakacağız ve bunu ASP.NET web formları projesiyle karşılaştıracağız.

İlk Blazor uygulamanızı oluşturmak için, [Blazor'un başlangıç adımlarını](/aspnet/core/blazor/get-started)takip edin. Bir Blazor Server uygulaması veya ASP.NET Core'da barındırılan bir Blazor WebAssembly uygulaması oluşturmak için yönergeleri izleyebilirsiniz. Barındırma modeline özgü mantık dışında, her iki projedeki kodun çoğu aynıdır.

## <a name="project-file"></a>Proje dosyası

Blazor Server uygulamaları .NET Core projeleridir. Blazor Server uygulaması nın proje dosyası alabildiği kadar basittir:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Blazor WebAssembly uygulaması için proje dosyası biraz daha ilgili görünüyor (tam sürüm numaraları değişebilir):

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <RazorLangVersion>3.0</RazorLangVersion>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Blazor" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.Build" Version="3.1.0" PrivateAssets="all" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.HttpClient" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.DevServer" Version="3.1.0" PrivateAssets="all" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\Shared\BlazorWebAssemblyApp1.Shared.csproj" />
  </ItemGroup>

</Project>
```

Blazor WebAssembly projeleri ,NET Core yerine .NET Standard'ı hedefler, çünkü tarayıcıda WebAssembly tabanlı .NET çalışma zamanında çalışırlar. .NET'i bir sunucu veya geliştirici makinesinde yaptığınız gibi bir web tarayıcısına yükleyemezsiniz. Sonuç olarak, proje tek tek paket referansları kullanarak Blazor çerçevesine başvurur.

Buna karşılık, varsayılan bir ASP.NET Web Forms *projesi,.csproj* dosyasında neredeyse 300 XML satırı içerir ve bunların çoğu projedeki çeşitli kod ve içerik dosyalarını açıkça listeler. .NET Core ve .NET Standart tabanlı projelerdeki basitleştirmelerin çoğu, genellikle yalnızca Web SDK `Microsoft.NET.Sdk.Web` olarak adlandırılan SDK'ya başvurarak içe aktarılan varsayılan hedefler ve özelliklerden gelir. Web SDK, projeye kod ve içerik dosyalarının eklenmesini kolaylaştıran joker karakterler ve diğer kolaylıklar içerir. Dosyaları açıkça listelamanız gerekmez. .NET Core'u hedef alırken, Web SDK hem .NET Core hem de ASP.NET Core paylaşılan çerçevelerine çerçeve referansları ekler. **Çerçeveler, Çözüm Gezgini** penceresindeki **Bağımlılıklar** > **Çerçeveleri** düğümünden görülebilir. Paylaşılan çerçeveler, .NET Core'u yüklerken makineye yüklenen derlemekoleksiyonlarıdır.

Desteklenmelerine rağmen, tek tek derleme başvuruları .NET Core projelerinde daha az yaygındır. Çoğu proje bağımlılığı NuGet paket başvuruları olarak işlenir. Sadece .NET Core projelerinde üst düzey paket bağımlılıklarına başvurmanız gerekir. Geçişli bağımlılıklar otomatik olarak dahil edilir. Paketleri referans ASP.NET Web Formlar projelerinde yaygın olarak bulunan *packages.config* dosyasını kullanmak yerine, `<PackageReference>` paket başvuruları öğe kullanılarak proje dosyasına eklenir.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Giriş noktası

Blazor Server uygulamasının giriş noktası, konsol uygulamasında gördüğünüz gibi *Program.cs* dosyasında tanımlanır. Uygulama yürütüldüğünde, web uygulamalarına özgü varsayılanları kullanarak bir web barındırma örneği oluşturur ve çalıştırZ. Web barındırma, Blazor Server uygulamasının yaşam döngüsünü yönetir ve ana bilgisayar düzeyinde hizmetler kurar. Bu tür hizmetlere örnek olarak yapılandırma, günlüğe kaydetme, bağımlılık enjeksiyonu ve HTTP sunucusu verilebilir. Bu kod çoğunlukla ortak ve genellikle değişmeden bırakılır.

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

Blazor WebAssembly uygulamaları da *Program.cs*bir giriş noktası tanımlar. Kod biraz farklı görünüyor. Kod, uygulama nın ana bilgisayara aynı ana bilgisayar düzeyindeki hizmetleri sağlamak üzere uygulama ana bilgisayarını ayarlaması açısından benzer. Ancak, WebAssembly uygulama ana bilgisayarı doğrudan tarayıcıda yürütüldettiği için bir HTTP sunucusu ayarlamaz.

Blazor uygulamaları, `Startup` uygulamanın başlangıç mantığını tanımlamak için *Global.asax* dosyası yerine bir sınıfa sahiptir. Sınıf, `Startup` uygulamayı ve uygulamaya özel hizmetleri yapılandırmak için kullanılır. Blazor Server uygulamasında sınıf, `Startup` Blazor'un istemci tarayıcılar ve sunucu arasında kullandığı gerçek zamanlı bağlantı için bitiş noktasını ayarlamak için kullanılır. Blazor WebAssembly uygulamasında, `Startup` sınıf uygulamanın kök bileşenlerini ve bunların nerede işlenmesi gerektiğini tanımlar. [App başlangıç](./app-startup.md) bölümündeki sınıfa `Startup` daha derinlemesine bakacağız.

## <a name="static-files"></a>Statik dosyalar

Web Formları ASP.NET projelerinaksine, Blazor projesindeki tüm dosyalar statik dosya olarak istenemez. Yalnızca *wwwroot* klasöründeki dosyalar web adresine yöneliktir. Bu klasör, uygulamanın "web kökü" olarak adlandırılır. Uygulamanın web kökünün dışındaki hiçbir şey web adresine bağlı *değildir.* Bu kurulum, proje dosyalarının web üzerinde yanlışlıkla açığa çıkarılmasını engelleyen ek bir güvenlik düzeyi sağlar.

## <a name="configuration"></a>Yapılandırma

ASP.NET Web Formları uygulamalarındaki yapılandırma genellikle bir veya daha fazla *web.config* dosyası kullanılarak gerçekleştirilir. Blazor uygulamaları genellikle *web.config* dosyaları yok. Bunu yaparlarsa, dosya yalnızca IIS'de barındırıldığında IIS'ye özgü ayarları yapılandırmak için kullanılır. Bunun yerine, Blazor Server uygulamaları ASP.NET Core yapılandırma soyutlamalarını kullanır (Blazor WebAssembly uygulamaları şu anda aynı yapılandırma soyutlamalarını desteklemez, ancak bu gelecekte eklenen bir özellik olabilir). Örneğin, varsayılan Blazor Server uygulaması bazı ayarları *appsettings.json'da*depolar.

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

[Yapılandırma](./config.md) bölümünde ASP.NET Core projelerinde yapılandırma hakkında daha fazla bilgi edineceğiz.

## <a name="razor-components"></a>Jilet bileşenleri

Blazor projelerindeki dosyaların çoğu *jiletli* dosyalardır. Razor, html ve C# tabanlı, dinamik olarak web ui oluşturmak için kullanılan cazip bir dildir. *.razor* dosyaları, uygulamanın ui'sini oluşturan bileşenleri tanımlar. Çoğunlukla, bileşenler hem Blazor Server hem de Blazor WebAssembly uygulamaları için aynıdır. Blazor'daki bileşenler, ASP.NET Web Formlar'daki kullanıcı denetimlerine benzer.

Her Razor bileşen dosyası, proje oluşturulurken bir .NET sınıfına derlenir. Oluşturulan sınıf bileşenin durumunu yakalar, oluşturma mantığı, yaşam döngüsü yöntemleri, olay işleyicileri ve diğer mantık. [Blazor bölümüyle yeniden kullanılabilir UI bileşenlerinin binadaki](./components.md) bileşenleri yazmaya bakacağız.

*_Imports.jilet* dosyaları Razor bileşen dosyaları değildir. Bunun yerine, aynı klasör içinde ve alt klasörlerinde diğer *.razor* dosyalarına içe aktarılan bir dizi Razor yönergeleri tanımlarlar. Örneğin, *_Imports.razor* dosyası, yaygın olarak `using` kullanılan ad alanları için deyim eklemenin geleneksel bir yoludur:

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a>Sayfalar

Blazor uygulamalarındaki sayfalar nerede? Blazor, ASP.NET Web Forms uygulamalarındaki *.aspx* dosyaları gibi adreslenebilir sayfalar için ayrı bir dosya uzantısı tanımlamaz. Bunun yerine, sayfalar bileşenlere rotalar atayarak tanımlanır. Rota genellikle Razor yönergesi `@page` kullanılarak atanır. Örneğin, `Counter` *Pages/Counter.razor* dosyasında yazılan bileşen aşağıdaki yolu tanımlar:

```razor
@page "/counter"
```

Blazor'da yönlendirme istemci tarafından işlenir, sunucuda değil. Kullanıcı tarayıcıda gezinirken, Blazor gezinmeyi yakalar ve bileşeni eşleşen rotayla işler.

Bileşen yolları şu anda bileşenin dosya konumu tarafından *.aspx* sayfalarında olduğu gibi çıkarılmaz. Bu özellik gelecekte eklenebilir. Her rota bileşenüzerinde açıkça belirtilmelidir. Routable bileşenlerinin *Sayfalar* klasöründe saklanması özel bir anlam ifade etmez ve tamamen bir kuraldır.

Blazor'da [Sayfalar, yönlendirme ve düzenler](./pages-routing-layouts.md) bölümünde yönlendirmeyi daha ayrıntılı olarak inceeceğiz.

## <a name="layout"></a>Düzen

ASP.NET Web Formları uygulamalarında, ortak sayfa düzeni ana sayfalar *(Site.Master)* kullanılarak gerçekleştirilir. Blazor uygulamalarında, sayfa düzeni mizanpaj bileşenleri *(Shared/MainLayout.razor)* kullanılarak işlenir. Düzen bileşenleri [Sayfa, yönlendirme ve düzenler](./pages-routing-layouts.md) bölümünde daha ayrıntılı olarak ele alınacaktır.

## <a name="bootstrap-blazor"></a>Bootstrap Blazor

Blazor'u tuzağa düşürmek için uygulamanın şunları yapması gerekir:

- Sayfada kök bileşenin *(App.Razor)* nerede işlenmesi gerektiğini belirtin.
- İlgili Blazor çerçeve komut dosyasını ekleyin.

Blazor Server uygulamasında, kök bileşenin ana sayfası *_Host.cshtml* dosyasında tanımlanır. Bu dosya bir bileşen değil, bir Razor Page tanımlar. Razor Pages, sunucu adreslenebilir bir sayfa tanımlamak için Razor sözdizimini kullanır, tıpkı *.aspx* sayfasına çok benzer. Yöntem, `Html.RenderComponentAsync<TComponent>(RenderMode)` kök düzeyindebir bileşenin nerede işlenmesi gerektiğini tanımlamak için kullanılır. Seçenek, `RenderMode` bileşenin nasıl işlenmesi gerektiğini gösterir. Aşağıdaki tabloda desteklenen `RenderMode` seçenekler sıralanır.

|Seçenek                        |Açıklama       |
|------------------------------|------------------|
|`RenderMode.Server`           |Tarayıcı ile bağlantı kurulduktan sonra etkileşimli olarak işlenir|
|`RenderMode.ServerPrerendered`|Önce önceden işlenmiş ve daha sonra etkileşimli olarak işlenmiş|
|`RenderMode.Static`           |Statik içerik olarak işlenir|

*_framework/blazor.server.js* komut dosyası başvurusu sunucuile gerçek zamanlı bağlantı kurar ve ardından tüm kullanıcı etkileşimleri ve Kullanıcı Arabirimi güncelleştirmeleri ile ilgilenir.

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

Blazor WebAssembly uygulamasında, ana sayfa *wwwroot/index.html*altında basit bir statik HTML dosyasıdır. Öğe, `<app>` kök bileşenin nerede işlenmesi gerektiğini belirtmek için kullanılır.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>Loading...</app>

    <script src="_framework/blazor.webassembly.js"></script>
</body>
</html>
```

İşlenecek belirli bileşen, bileşenin nerede `Startup.Configure` işlenmesi gerektiğini belirten ilgili bir CSS seçiciyle uygulama yönteminde yapılandırılır.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IComponentsApplicationBuilder app)
    {
        app.AddComponent<App>("app");
    }
}
```

## <a name="build-output"></a>Üretim oluşturma

Bir Blazor projesi inşa edildiğinde, tüm Razor bileşeni ve kod dosyaları tek bir derlemede derlenir. Web Formları projelerinin ASP.NET aksine Blazor, Web-oğlık mantığı mantığının çalışma zamanı derlemesini desteklemez.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

Blazor Server uygulamasını çalıştırmak `F5` için Visual Studio'ya basın. Blazor uygulamaları çalışma zamanı derlemeyi desteklemez. Kod ve bileşen biçimlendirme değişikliklerinin sonuçlarını görmek için, hata ayıklayıcı ekli uygulamayı yeniden oluşturup yeniden başlatın. Hata ayıklama ekli olmadan çalıştırırsanız (`Ctrl+F5`), Visual Studio dosya değişiklikleri için saatler ve değişiklikler yapılırken uygulamayı yeniden başlatır. Değişiklikler yapıldıkça tarayıcıyı el ile yenilersiniz.

Blazor WebAssembly uygulamasını çalıştırmak için aşağıdaki yaklaşımlardan birini seçin:

- İstemci projesini doğrudan geliştirme sunucusunu kullanarak çalıştırın.
- uygulamayı ASP.NET Core ile barındırırken sunucu projesini çalıştırın.

Blazor WebAssembly uygulamaları Visual Studio kullanarak hata ayıklama desteklemez. Uygulamayı çalıştırmak için, `Ctrl+F5` `F5`". Bunun yerine Blazor WebAssembly uygulamalarını doğrudan tarayıcıda hata ayıklayabilirsiniz. Ayrıntılar için [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) bölümüne bakın.

>[!div class="step-by-step"]
>[Önceki](hosting-models.md)
>[Sonraki](app-startup.md)
