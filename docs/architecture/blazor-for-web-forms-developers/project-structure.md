---
title: Blazor uygulamaları için proje yapısı
description: ASP.NET Web Forms ve Blazor projelerinin proje yapılarının nasıl karşılaştırılacağını öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: aa9157bd8627e7a03e33872c3023f91ba3d66951
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520225"
---
# <a name="project-structure-for-blazor-apps"></a>Blazor uygulamaları için proje yapısı

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Önemli proje yapısı farklılıklarına karşın, ASP.NET Web Forms ve Blazor birçok benzer kavramı paylaşır. Burada, bir Blazor projesinin yapısına bakacağız ve bunu bir ASP.NET Web Forms projesiyle karşılaştıracağız.

İlk Blazor uygulamanızı oluşturmak için [Blazor Başlarken adımlarında](/aspnet/core/blazor/get-started)bulunan yönergeleri izleyin. Yönergeleri izleyerek ASP.NET Core barındırılan bir Blazor Server uygulaması ya da Blazor WebAssembly uygulaması oluşturabilirsiniz. Barındırma modeline özgü mantık dışında, her iki projedeki kodun çoğu aynıdır.

## <a name="project-file"></a>Proje dosyası

Blazor Server uygulamaları .NET Core projelerdir. Blazor Server uygulamasının proje dosyası, şu kadar basit bir işlemdir:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Bir Blazor WebAssembly uygulamasının proje dosyası biraz daha ilgili görünüyor (tam sürüm numaraları değişebilir):

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

Blazor WebAssembly projeleri, bir WebAssembly tabanlı .NET çalışma zamanında tarayıcıda çalıştırıldıklarından .NET Core yerine .NET Standard hedefleyin. Bir sunucu veya geliştirici makinesinde kullanabileceğiniz gibi bir Web tarayıcısına .NET yükleyemezsiniz. Sonuç olarak, proje bağımsız paket başvurularını kullanarak Blazor Framework 'e başvurur.

Karşılaştırmayla, varsayılan bir ASP.NET Web Forms projesi *. csproj* dosyasında neredeyse 300 satır xml içerir ve bu, çoğu, projedeki çeşitli kod ve içerik dosyalarını açıkça listeler. .NET Core ve .NET Standard tabanlı projelerdeki birçok basitleştirmeyle, genellikle yalnızca Web SDK 'Sı olarak adlandırılan `Microsoft.NET.Sdk.Web` SDK 'sına başvurarak içeri aktarılan varsayılan hedeflerden ve özelliklerden gelir. Web SDK 'Sı, kod ve içerik dosyalarının projeye eklenmesini kolaylaştıran joker karakterler ve diğer kolaylığı içerir. Dosyaları açıkça listemeniz gerekmez. .NET Core 'u hedeflerken, Web SDK hem .NET Core hem de ASP.NET Core paylaşılan çerçevelere çerçeve başvuruları ekler. Çerçeveler, **Çözüm Gezgini** penceresindeki **Bağımlılıklar**  > **çerçeveler** düğümünden görülebilir. Paylaşılan çerçeveler, .NET Core yüklenirken makinede yüklü olan derlemelerin koleksiyonlarıdır.

Desteklenseler de, bireysel derleme başvuruları .NET Core projelerinde daha az yaygındır. Çoğu proje bağımlılığı, NuGet paket başvuruları olarak işlenir. Yalnızca .NET Core projelerinde en üst düzey paket bağımlılıklarına başvurmanız gerekir. Geçişli bağımlılıklar otomatik olarak eklenir. ASP.NET Web Forms projelerinde yaygın olarak bulunan *Packages. config* dosyasını kullanmak yerine, paket başvuruları, `<PackageReference>` öğesi kullanılarak proje dosyasına eklenir.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Giriş noktası

Blazor sunucusu uygulamasının giriş noktası, bir konsol uygulamasında gördüğünüz gibi, *program.cs* dosyasında tanımlanmıştır. Uygulama yürütüldüğünde Web uygulamalarına özgü varsayılan değerleri kullanarak bir Web ana bilgisayar örneği oluşturur ve çalıştırır. Web ana bilgisayarı, Blazor Server uygulamasının yaşam döngüsünü yönetir ve konak düzeyindeki hizmetleri ayarlar. Bu hizmetlere örnek olarak yapılandırma, günlüğe kaydetme, bağımlılık ekleme ve HTTP sunucusu verilebilir. Bu kod çoğunlukla ortak olduğundan, genellikle değişmeden kalır.

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

Blazor WebAssembly Apps, *program.cs*içinde bir giriş noktası da tanımlar. Kod biraz farklı görünüyor. Kod, uygulamaya aynı ana bilgisayar düzeyi hizmetleri sağlamak için uygulama ana bilgisayarı ayarlamada benzerdir. Ancak doğrudan tarayıcıda yürütüldüğü için WebAssembly uygulama ana bilgisayarı bir HTTP sunucusu ayarladı.

Blazor uygulamalarının, uygulamanın başlangıç mantığını tanımlamak için bir *Global. asax* dosyası yerine `Startup` sınıfı vardır. @No__t_0 sınıfı, uygulamayı ve uygulamaya özel hizmetleri yapılandırmak için kullanılır. Blazor sunucu uygulamasında `Startup` sınıfı, istemci tarayıcıları ve sunucu arasında Blazor tarafından kullanılan gerçek zamanlı bağlantı için uç noktayı ayarlamak üzere kullanılır. Blazor WebAssembly uygulamasında `Startup` sınıfı, uygulamanın kök bileşenlerini ve bunların oluşturulması gereken yerleri tanımlar. [Uygulama başlangıç](./app-startup.md) bölümünde `Startup` sınıfına daha ayrıntılı bir bakış ekleyeceğiz.

## <a name="static-files"></a>Statik dosyalar

ASP.NET Web Forms projelerinin aksine, bir Blazor projesindeki tüm dosyalar statik dosya olarak istenemez. Yalnızca *Wwwroot* klasöründeki dosyalar Web adreslenebilir. Bu klasöre uygulamanın "Web root" adı verilir. Uygulamanın Web kökünün dışındaki herhangi bir şey, Web 'de adreslenebilir *değildir* . Bu kurulum, proje dosyalarını web üzerinden yanlışlıkla açığa çıkaran ek bir güvenlik düzeyi sağlar.

## <a name="configuration"></a>Yapılandırma

ASP.NET Web Forms uygulamalarında yapılandırma genellikle bir veya daha fazla *Web. config* dosyası kullanılarak işlenir. Blazor uygulamalarında genellikle *Web. config* dosyaları yoktur. Bu dosyalar yalnızca IIS 'de barındırılırken IIS 'e özgü ayarları yapılandırmak için kullanılır. Bunun yerine, Blazor Server uygulamaları ASP.NET Core yapılandırma soyutlamalarını kullanır (Blazor WebAssembly Apps Şu anda aynı yapılandırma soyutlamalarını desteklememektedir, ancak gelecekte eklenmiş bir özellik olabilir). Örneğin, varsayılan Blazor Server uygulaması *appSettings. JSON*içindeki bazı ayarları depolar.

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

[Yapılandırma bölümünde ASP.NET Core](./config.md) projelerde yapılandırma hakkında daha fazla bilgi edineceksiniz.

## <a name="razor-components"></a>Razor bileşenleri

Blazor projelerindeki çoğu dosya *. Razor* dosyalarıdır. Razor, HTML tabanlı ve C# Web Kullanıcı arabirimini dinamik olarak oluşturmak için kullanılan bir şablon oluşturma dilidir. *. Razor* dosyaları uygulamanın kullanıcı arabirimini oluşturan bileşenleri tanımlar. Çoğu bölümde, bileşenler hem Blazor Server hem de Blazor WebAssembly Apps için aynıdır. Blazor içindeki bileşenler ASP.NET Web Forms içindeki kullanıcı denetimlerine benzerdir.

Her Razor bileşeni dosyası, proje oluşturulduğunda bir .NET sınıfına derlenir. Oluşturulan sınıf, bileşenin durumunu, işleme mantığını, yaşam döngüsü yöntemlerini, olay işleyicilerini ve diğer mantığı yakalar. [Blazor ile yeniden kullanılabilir kullanıcı arabirimi bileşenleri oluşturma](./components.md) bölümünde bileşenleri yazma bölümüne bakacağız.

*_Imports. Razor* dosyaları Razor bileşen dosyaları değildir. Bunun yerine, aynı klasörde ve alt klasörlerinde bulunan diğer *. Razor* dosyalarını içeri aktarmak Için bir Razor yönergeleri kümesi tanımlar. Örneğin, bir *_ımports. Razor* dosyası, yaygın olarak kullanılan ad alanları için `using` deyimleri eklemenin geleneksel bir yoludur:

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

Blazor uygulamalarındaki Sayfalar nerede? Blazor, adreslenebilir sayfalar için ASP.NET Web Forms Apps 'teki *. aspx* dosyaları gibi ayrı bir dosya uzantısı tanımlamaz. Bunun yerine, sayfalar bileşenlere rotalar atanarak tanımlanır. Yol, genellikle `@page` Razor yönergesi kullanılarak atanır. Örneğin, *Pages/Counter. Razor* dosyasında yazılan `Counter` bileşeni aşağıdaki rotayı tanımlar:

```razor
@page "/counter"
```

Blazor ' de yönlendirme, sunucuda değil, istemci tarafında işlenir. Kullanıcı tarayıcıda gezinirken, Blazor gezinmeyi karşılar ve ardından bileşeni eşleşen yol ile işler. 

Bileşen yolları şu anda bileşenin dosya konumu tarafından, *. aspx* sayfalarıyla oldukları gibi çıkarsanamıyor. Bu özellik gelecekte eklenebilir. Her yol, bileşen üzerinde açık olarak belirtilmelidir. Bir *Sayfalar* klasöründe yönlendirilebilir bileşenlerin depolanması özel bir anlamı yoktur ve yalnızca bir kuraldır.

[Sayfalar, Yönlendirme ve düzenler](./pages-routing-layouts.md) bölümünde Blazor ' de yönlendirme sırasında daha fazla ayrıntı inceleyeceğiz.

## <a name="layout"></a>Düzen

ASP.NET Web Forms uygulamalarda, ortak sayfa düzeni ana sayfalar (*site. Master*) kullanılarak işlenir. Blazor uygulamalarında sayfa düzeni, düzen bileşenleri (*paylaşılan/MainLayout. Razor*) kullanılarak işlenir. Düzen bileşenleri [sayfa, Yönlendirme ve düzenler](./pages-routing-layouts.md) bölümünde daha ayrıntılı bir şekilde ele alınacaktır.

## <a name="bootstrap-blazor"></a>Bootstrap Blazor

Blazor önyüklemek için, uygulamanın şunları yapmanız gerekir:

- Kök bileşenin (*app. Razor*) nerede işleneceğini belirtin.
- Karşılık gelen Blazor Framework betiğini ekleyin.

Blazor sunucusu uygulamasında, kök bileşenin ana bilgisayar sayfası *_host. cshtml* dosyasında tanımlanmıştır. Bu dosya, bir bileşeni değil Razor sayfasını tanımlar. Razor Pages, bir *. aspx* sayfasına benzer şekilde sunucu adreslenebilir bir sayfa tanımlamak için Razor söz dizimi kullanın. @No__t_0 yöntemi, kök düzeyinde bir bileşenin nerede işleneceğini tanımlamak için kullanılır. @No__t_0 seçeneği, bileşenin oluşturulması gereken şekli gösterir. Aşağıdaki tabloda desteklenen `RenderMode` seçenekleri özetlenmektedir.

|Seçenek                        |Açıklama       |
|------------------------------|------------------|
|`RenderMode.Server`           |Tarayıcıyla bir bağlantı kurulduktan sonra etkileşimli olarak işlendi|
|`RenderMode.ServerPrerendered`|Önce ön ve daha sonra etkileşimli olarak işlendi|
|`RenderMode.Static`           |Statik içerik olarak işlendi|

*_Framework/blazor. Server. js* ' ye yönelik betik başvurusu, sunucuyla gerçek zamanlı bağlantı kurar ve ardından tüm kullanıcı etkileşimleri ve Kullanıcı arabirimi güncelleştirmeleriyle ilgilenir.

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

Blazor WebAssembly uygulamasında ana bilgisayar sayfası, *Wwwroot/index.html*altında Basit BIR statik HTML dosyasıdır. @No__t_0 öğesi, kök bileşenin nerede işleneceğini belirtmek için kullanılır.

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

İşlenecek belirli bileşen, uygulamanın `Startup.Configure` yönteminde, bileşenin nerede işleneceğini belirten karşılık gelen bir CSS seçicisiyle yapılandırılır.

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

## <a name="build-output"></a>Derleme çıkışı

Bir Blazor projesi yapılandırıldığında, tüm Razor bileşeni ve kod dosyaları tek bir derlemede derlenir. ASP.NET Web Forms projelerinin aksine, Blazor Kullanıcı arabirimi mantığının çalışma zamanı derlemesini desteklemez.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

Blazor Server uygulamasını çalıştırmak için, Visual Studio 'da `F5` tuşuna basın. Blazor uygulamaları, çalışma zamanı derlemesini desteklemez. Kod ve bileşen biçimlendirme değişikliklerinin sonuçlarını görmek için, uygulamayı yeniden derleyin ve hata ayıklayıcı ekli olarak yeniden başlatın. Hata ayıklayıcı ekli (`Ctrl+F5`) olmadan çalıştırırsanız, Visual Studio dosya değişikliklerini izler ve değişiklikler yapıldığından uygulamayı yeniden başlatır. Değişiklik yapıldığında tarayıcıyı el ile yenilemeniz gerekir.

Blazor WebAssembly uygulamasını çalıştırmak için aşağıdaki yaklaşımlardan birini seçin:

- İstemci projesini doğrudan geliştirme sunucusunu kullanarak çalıştırın.
- ASP.NET Core ile uygulamayı barındırırken sunucu projesini çalıştırın.

Blazor WebAssembly Apps, Visual Studio kullanarak hata ayıklamayı desteklemez. Uygulamayı çalıştırmak için `F5` yerine `Ctrl+F5` kullanın. Bunun yerine Blazor WebAssembly uygulamalarında doğrudan tarayıcıda hata ayıklaması yapabilirsiniz. Ayrıntılar için bkz. [Blazor ASP.NET Core hata ayıklama](/aspnet/core/blazor/debug) .

>[!div class="step-by-step"]
>[Önceki](hosting-models.md)
>[İleri](app-startup.md)
