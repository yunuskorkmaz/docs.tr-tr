---
title: Uygulamalar için proje yapısı Blazor
description: ASP.NET Web Forms ve projelerinin proje yapılarının nasıl Blazor karşılaştırılacağını öğrenin.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: d91430eb654ee16934408bf064803b34ca700640
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509812"
---
# <a name="project-structure-for-no-locblazor-apps"></a>Uygulamalar için proje yapısı Blazor

Önemli proje yapısı farklılıklarına rağmen, ASP.NET Web Forms ve Blazor birçok benzer kavramı paylaşır. Burada, bir projenin yapısına bakacağız Blazor ve bunu bir ASP.NET Web Forms projesiyle karşılaştıracağız.

İlk uygulamanızı oluşturmak için Blazor [ Blazor Başlarken adımlarında](/aspnet/core/blazor/get-started)bulunan yönergeleri izleyin. Bir Blazor sunucu uygulaması veya Blazor ASP.NET Core barındırılan bir uygulama oluşturmak için yönergeleri takip edebilirsiniz WebAssembly . Barındırma modeline özgü mantık dışında, her iki projedeki kodun çoğu aynıdır.

## <a name="project-file"></a>Proje dosyası

Blazor Sunucu uygulamaları .NET projelerdir. Sunucu uygulamasının proje dosyası, Blazor Şu kadar basit bir işlemdir:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Uygulamanın proje dosyası Blazor WebAssembly biraz daha fazla görünür (tam sürüm numaraları farklılık gösterebilir):

```xml
<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly" Version="5.0.0" />
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.DevServer" Version="5.0.0" PrivateAssets="all" />
    <PackageReference Include="System.Net.Http.Json" Version="5.0.0" />
  </ItemGroup>

</Project>
```

BlazorWebAssembly `Microsoft.NET.Sdk.BlazorWebAssembly` `Microsoft.NET.Sdk.Web` bir WebAssembly tabanlı .NET çalışma zamanında tarayıcıda çalıştırıldıklarından SDK yerine proje hedefleri. Bir sunucu veya geliştirici makinesinde kullanabileceğiniz gibi bir Web tarayıcısına .NET yükleyemezsiniz. Sonuç olarak, proje Blazor tekil paket başvurularını kullanarak çerçeveye başvurur.

Karşılaştırmayla, varsayılan bir ASP.NET Web Forms projesi *. csproj* dosyasında neredeyse 300 satır xml içerir ve bu, çoğu, projedeki çeşitli kod ve içerik dosyalarını açıkça listeler. `.NET 5`Hem hem de uygulamasının sürümü `Blazor Server` ile `Blazor WebAssembly` birleştirilmiş bir çalışma zamanını kolayca paylaşabilir.

Desteklenseler de, bireysel derleme başvuruları .NET projelerinde daha az yaygındır. Çoğu proje bağımlılığı, NuGet paket başvuruları olarak işlenir. Yalnızca .NET projelerinde en üst düzey paket bağımlılıklarına başvurmanız gerekir. Geçişli bağımlılıklar otomatik olarak eklenir. ASP.NET Web Forms projelerinde yaygın olarak bulunan *packages.config* dosyayı kullanmak yerine, paket başvuruları öğesi kullanılarak proje dosyasına eklenir `<PackageReference>` .

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Giriş noktası

BlazorSunucu uygulamasının giriş noktası, bir konsol uygulamasında gördüğünüz gibi *program.cs* dosyasında tanımlanmıştır. Uygulama yürütüldüğünde Web uygulamalarına özgü varsayılan değerleri kullanarak bir Web ana bilgisayar örneği oluşturur ve çalıştırır. Web ana bilgisayarı, Blazor sunucu uygulamasının yaşam döngüsünü yönetir ve konak düzeyi Hizmetleri ayarlar. Bu hizmetlere örnek olarak yapılandırma, günlüğe kaydetme, bağımlılık ekleme ve HTTP sunucusu verilebilir. Bu kod çoğunlukla ortak olduğundan, genellikle değişmeden kalır.

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

BlazorWebAssemblyuygulamalar ayrıca *program.cs* içinde bir giriş noktası tanımlar. Kod biraz farklı görünüyor. Kod, uygulamaya aynı ana bilgisayar düzeyi hizmetleri sağlamak için uygulama ana bilgisayarı ayarlamada benzerdir. WebAssemblyAncak, uygulama ana bilgisayarı doğrudan tarayıcıda yürütüldüğü için BIR http sunucusu ayarlama yapmaz.

Blazor uygulamalar `Startup` , uygulama için başlangıç mantığını tanımlamak üzere *Global. asax* dosyası yerine bir sınıfa sahiptir. `Startup`Sınıfı, uygulamayı ve uygulamaya özgü hizmetleri yapılandırmak için kullanılır. Sunucu uygulamasında Blazor `Startup` sınıfı, Blazor istemci tarayıcıları ve sunucu arasında kullanılan gerçek zamanlı bağlantı için uç noktayı ayarlamak üzere kullanılır. Blazor WebAssembly Uygulamada, `Startup` sınıfı uygulamanın kök bileşenlerini ve bunların oluşturulması gereken yerleri tanımlar. `Startup` [Uygulama başlatma](./app-startup.md) bölümündeki sınıfına daha ayrıntılı bir bakış ekleyeceğiz.

## <a name="static-files"></a>Statik dosyalar

ASP.NET Web Forms projelerinin aksine, projedeki tüm dosyalar Blazor statik dosya olarak istenemez. Yalnızca *Wwwroot* klasöründeki dosyalar Web adreslenebilir. Bu klasöre uygulamanın "Web root" adı verilir. Uygulamanın Web kökünün dışındaki herhangi bir şey, Web 'de adreslenebilir *değildir* . Bu kurulum, proje dosyalarını web üzerinden yanlışlıkla açığa çıkaran ek bir güvenlik düzeyi sağlar.

## <a name="configuration"></a>Yapılandırma

ASP.NET Web Forms uygulamalarında yapılandırma genellikle bir veya daha fazla *web.config* dosyası kullanılarak işlenir. Blazor uygulamalar genellikle *web.config* dosyalarına sahip değildir. Bu dosyalar yalnızca IIS 'de barındırılırken IIS 'e özgü ayarları yapılandırmak için kullanılır. Bunun yerine, Blazor sunucu uygulamaları ASP.NET Core yapılandırma soyutlamalarını kullanır ( Blazor WebAssembly uygulamalar şu anda aynı yapılandırma soyutlamalarını desteklememektedir, ancak gelecekte eklenmiş bir özellik olabilir). Örneğin, varsayılan Blazor sunucu uygulaması *appsettings.js*' de bazı ayarları depolar.

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

Projelerdeki çoğu dosya Blazor *. Razor* dosyalarıdır. Razor, dinamik olarak Web Kullanıcı arabirimi oluşturmak için kullanılan HTML ve C# tabanlı bir şablon oluşturma dilidir. *. Razor* dosyaları uygulamanın kullanıcı arabirimini oluşturan bileşenleri tanımlar. Çoğu bölümde, bileşenler hem Blazor sunucu hem de uygulamalar için aynıdır Blazor WebAssembly . İçindeki bileşenler Blazor , ASP.NET Web Forms içindeki kullanıcı denetimlerine benzerdir.

Her Razor bileşeni dosyası, proje oluşturulduğunda bir .NET sınıfına derlenir. Oluşturulan sınıf, bileşenin durumunu, işleme mantığını, yaşam döngüsü yöntemlerini, olay işleyicilerini ve diğer mantığı yakalar. Yeniden [kullanılabilir kullanıcı arabirimi Blazor bileşenlerinde oluşturma](./components.md) bölümünde bileşen yazma bölümüne bakacağız.

*_Imports. Razor* dosyaları Razor bileşen dosyaları değildir. Bunun yerine, aynı klasörde ve alt klasörlerinde bulunan diğer *. Razor* dosyalarını içeri aktarmak Için bir Razor yönergeleri kümesi tanımlar. Örneğin, bir *_Imports. Razor* dosyası, `using` yaygın olarak kullanılan ad alanları için yönergeler eklemenin geleneksel bir yoludur:

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

Uygulamalardaki Sayfalar nerede Blazor ? Blazor , ASP.NET Web Forms uygulamalarındaki *. aspx* dosyaları gibi adreslenebilir sayfalar için ayrı bir dosya uzantısı tanımlamaz. Bunun yerine, sayfalar bileşenlere rotalar atanarak tanımlanır. Bir yol, genellikle `@page` Razor yönergesi kullanılarak atanır. Örneğin, `Counter` *Pages/Counter. Razor* dosyasında yazılan bileşen aşağıdaki rotayı tanımlar:

```razor
@page "/counter"
```

İçindeki yönlendirme, Blazor sunucuda değil, istemci tarafında işlenir. Kullanıcı tarayıcıda Blazor gezinirken, gezintiyi durdurur ve ardından bileşeni eşleşen yol ile işler.

Bileşen yolları şu anda bileşenin dosya konumu tarafından, *. aspx* sayfalarıyla oldukları gibi çıkarsanamıyor. Bu özellik gelecekte eklenebilir. Her yol, bileşen üzerinde açık olarak belirtilmelidir. Bir *Sayfalar* klasöründe yönlendirilebilir bileşenlerin depolanması özel bir anlamı yoktur ve yalnızca bir kuraldır.

Blazor [Sayfalar, Yönlendirme ve düzenler](./pages-routing-layouts.md) bölümünde ' de yönlendirme sırasında daha ayrıntılı bir ayrıntıya bakacağız.

## <a name="layout"></a>Düzen

ASP.NET Web Forms uygulamalarda, ana sayfalar (*site. Master*) kullanılarak ortak bir sayfa düzeni işlenir. BlazorUygulamalarda, sayfa düzeni Düzen bileşenleri (*paylaşılan/mainlayout. Razor*) kullanılarak işlenir. Düzen bileşenleri [sayfa, Yönlendirme ve düzenler](./pages-routing-layouts.md) bölümünde daha ayrıntılı bir şekilde ele alınacaktır.

## <a name="bootstrap-no-locblazor"></a>Yükleyebilirsiniz Blazor

Önyükleme yapmak için Blazor uygulamanın şunları yapmanız gerekir:

- Kök bileşenin (*app. Razor*) nerede işleneceğini belirtin.
- İlgili Blazor Framework betiğini ekleyin.

Sunucu uygulamasında Blazor , kök bileşenin ana bilgisayar sayfası *_Host. cshtml* dosyasında tanımlanmıştır. Bu dosya, bir bileşeni değil Razor sayfasını tanımlar. Razor Pages, bir *. aspx* sayfasına benzer şekilde sunucu adreslenebilir bir sayfa tanımlamak için Razor söz dizimi kullanın. `Html.RenderComponentAsync<TComponent>(RenderMode)`Yöntemi, kök düzeyinde bir bileşenin nerede işleneceğini tanımlamak için kullanılır. `RenderMode`Seçeneği, bileşenin oluşturulması gereken şekli gösterir. Aşağıdaki tabloda desteklenen `RenderMode` Seçenekler özetlenmektedir.

|Seçenek                        |Açıklama       |
|------------------------------|------------------|
|`RenderMode.Server`           |Tarayıcıyla bir bağlantı kurulduktan sonra etkileşimli olarak işlendi|
|`RenderMode.ServerPrerendered`|Önce ön ve daha sonra etkileşimli olarak işlendi|
|`RenderMode.Static`           |Statik içerik olarak işlendi|

*_Framework/blazor.server.js* betik başvurusu, sunucuyla gerçek zamanlı bağlantı kurar ve ardından tüm kullanıcı etkileşimleri ve Kullanıcı arabirimi güncelleştirmeleriyle ilgilenir.

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

Blazor WebAssembly Uygulamada, ana bilgisayar sayfası *Wwwroot/index.html* altında basit bir statik HTML dosyasıdır. `<div>`Adlandırılmış kimliği olan öğe, `app` kök bileşenin nerede işleneceğini belirtmek için kullanılır.

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="blazor-web.styles.css" rel="stylesheet" />
</head>

<body>
    <div id="app">Loading...</div>

    <div id="blazor-error-ui">
        An unhandled error has occurred.
        <a href="" class="reload">Reload</a>
        <a class="dismiss">🗙</a>
    </div>
    <script src="_framework/blazor.webassembly.js"></script>
</body>

</html>

```

İşlenecek kök bileşen uygulamanın `Program.Main` yönteminde, bağımlılık ekleme yoluyla farklı Hizmetleri kaydetme esnekliği ile yapılandırılır. [ Blazor İçindeki WebAssembly ](https://docs.microsoft.com/aspnet/core/blazor/fundamentals/dependency-injection?view=aspnetcore-5.0#blazor-webassembly) bir uygulamaya hizmet ekleme konusuna bakabilirsiniz

```csharp
public class Program
{
    public static async Task Main(string[] args)
    {
        var builder = WebAssemblyHostBuilder.CreateDefault(args);
        builder.RootComponents.Add<App>("#app");

        ....
        ....
    }
}
```

## <a name="build-output"></a>Derleme çıkışı

Bir Blazor Proje oluşturulduğunda, tüm Razor bileşeni ve kod dosyaları tek bir derlemede derlenir. ASP.NET Web Forms projelerinin aksine, Blazor UI mantığının çalışma zamanı derlemesini desteklemez.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

BlazorSunucu uygulamasını çalıştırmak için, `F5` Visual Studio 'da ' ya basın. Blazor uygulamalar çalışma zamanı derlemesini desteklemez. Kod ve bileşen biçimlendirme değişikliklerinin sonuçlarını görmek için, uygulamayı yeniden derleyin ve hata ayıklayıcı ekli olarak yeniden başlatın. Hata ayıklayıcı ekli () olmadan çalıştırırsanız `Ctrl+F5` , Visual Studio dosya değişikliklerini izler ve değişiklikler yapıldıktan sonra uygulamayı yeniden başlatır. Değişiklik yapıldığında tarayıcıyı el ile yenilemeniz gerekir.

Uygulamayı çalıştırmak için Blazor WebAssembly aşağıdaki yaklaşımlardan birini seçin:

- İstemci projesini doğrudan geliştirme sunucusunu kullanarak çalıştırın.
- ASP.NET Core ile uygulamayı barındırırken sunucu projesini çalıştırın.

BlazorWebAssemblyuygulamaların her ikisi de tarayıcıda ve Visual Studio 'da hata ayıklaması yapılabilir. Ayrıntılar için bkz. [hata ayıklama ASP.NET Core Blazor WebAssembly ](/aspnet/core/blazor/debug) .

>[!div class="step-by-step"]
>[Önceki](hosting-models.md) 
> [Sonraki](app-startup.md)
