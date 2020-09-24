---
title: Uygulama başlatma
description: Uygulamanız için başlangıç mantığını tanımlama hakkında bilgi edinin.
author: csharpfritz
ms.author: jefritz
ms.date: 02/25/2020
ms.openlocfilehash: 883f9a3fbe2d52cb7d0fbc5dfc94ce829a5d2bf3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158194"
---
# <a name="app-startup"></a>Uygulama başlatma

ASP.NET için yazılan uygulamalar genellikle, `global.asax.cs` `Application_Start` hangi hizmetlerin yapılandırıldığını ve hem HTML işleme hem de .net işlemesi için kullanılabilir hale getirildiğini denetleyen olayı tanımlayan bir dosya olur. Bu bölümde, ASP.NET Core ve Blazor Server ile ilgili işlerin nasıl biraz farklı olduğu açıklanır.

## <a name="application_start-and-web-forms"></a>Application_Start ve Web Forms

Varsayılan Web formları `Application_Start` yöntemi, birçok yapılandırma görevini işlemek için yıllarca bir amaç artmıştır.  Visual Studio 2019 ' de varsayılan şablona sahip yeni bir Web Forms projesi artık aşağıdaki yapılandırma mantığını içerir:

- `RouteConfig` -Uygulama URL 'SI yönlendirme
- `BundleConfig` -CSS ve JavaScript paketleme ve küçültmeye yönelik

Bu dosyaların her biri `App_Start` klasöründe bulunur ve uygulamamız başlangıcında yalnızca bir kez çalıştırılır.  `RouteConfig` Varsayılan proje şablonunda, `FriendlyUrlSettings` Uygulama URL 'lerinin dosya uzantısını yok saymasını sağlamak için Web formları için ' i ekler `.ASPX` .  Varsayılan şablon Ayrıca, `.ASPX` uzantıları açan dosya adı ile kolay URL 'ye sayfalar için kalıcı http yeniden yönlendirme durum kodları (HTTP 301) sağlayan bir yönerge içerir.

ASP.NET Core ve Blazor ile bu yöntemler `Startup` basitleşilir ve sınıfla birleştirilir ya da ortak web teknolojilerinin yararına ortadan kaldırılır.

## <a name="blazor-server-startup-structure"></a>Blazor sunucusu başlangıç yapısı

Blazor Server uygulamaları ASP.NET Core 3,0 veya üzeri bir uygulamanın üstünde bulunur.  ASP.NET Core Web uygulamaları, `Startup.cs` uygulamanın kök klasöründeki sınıfında bir çift yöntem aracılığıyla yapılandırılır.  Başlangıç sınıfının varsayılan içeriği aşağıda listelenmiştir

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

ASP.NET Core geri kalanı gibi, başlangıç sınıfı bağımlılık ekleme ilkeleri ile oluşturulur.  , `IConfiguration` Oluşturucuya sağlanır ve yapılandırma sırasında daha sonra erişmek üzere ortak bir özellikte oluşturulur.

`ConfigureServices`ASP.NET Core tanıtılan Yöntem, Framework 'ün yerleşik bağımlılık ekleme kapsayıcısı için çeşitli ASP.NET Core Framework hizmetlerinin yapılandırılmasını sağlar.  Çeşitli `services.Add*` Yöntemler, kimlik doğrulaması, Razor sayfaları, MVC denetleyici yönlendirmesi, SignalR ve Blazor Server etkileşimleri gibi özellikleri çok sayıda diğerleri arasında etkinleştiren hizmetler ekler.  Bu yöntem, Web formlarında gerekli değildir, çünkü ASPX, ASCX, ASHX ve ASMX dosyalarını ayrıştırma ve işleme, web.config yapılandırma dosyasında ASP.NET başvuruda bulunarak tanımlanmıştı.  ASP.NET Core bağımlılık ekleme hakkında daha fazla bilgi [Çevrimiçi belgelerde](/aspnet/core/fundamentals/dependency-injection)bulunabilir.

`Configure`Yöntemi, ASP.NET Core IÇIN http işlem hattı kavramını tanıtır.  Bu yöntemde, uygulamamıza gönderilen her isteği işleyecek olan [ara yazılımı](middleware.md) yukarıdan aşağıya doğru bildiririz. Varsayılan yapılandırmada bu özelliklerin çoğu, Web Forms yapılandırma dosyaları genelinde dağınık ve artık başvuru kolaylığı için tek bir yerde.

Artık bir dosyaya yerleştirilen özel hata sayfasının yapılandırması değildir `web.config` , ancak artık uygulama ortamı etiketlenmezse her zaman gösterilecek şekilde yapılandırılmıştır `Development` .  Ayrıca, ASP.NET Core uygulamalar artık varsayılan olarak, yöntem çağrısıyla TLS ile güvenli sayfalar sunacak şekilde yapılandırılmıştır `UseHttpsRedirection` .

Ardından, beklenmeyen bir yapılandırma yöntemi olarak listelenir `UseStaticFiles` .  ASP.NET Core, statik dosyalar için (JavaScript, CSS ve resim dosyaları gibi) isteklerin desteğinin açıkça etkinleştirilmesi ve yalnızca uygulamanın *Wwwroot* klasöründeki dosyaların varsayılan olarak genel olarak adreslenebilir olması gerekir.

Sonraki satır, web formlarından yapılandırma seçeneklerinden birini çoğaltan birincsahiptir: `UseRouting` .  Bu yöntem ASP.NET Core yönlendiricisini işlem hattına ekler ve burada ya da yönlendirmeyi düşünebileceğiniz tek dosyalarda yapılandırılabilir.  Yönlendirme yapılandırması hakkında daha fazla bilgi [Yönlendirme bölümünde](pages-routing-layouts.md)bulunabilir.

Bu yöntemdeki final ifadesinde ASP.NET Core dinlediği uç noktalar tanımlanmaktadır.  Bunlar, Web sunucusuna erişebileceğiniz ve .NET tarafından işlenmiş ve size döndürülen Web 'de erişilebilir konumlardır.  İlk giriş, `MapBlazorHub` Blazor bileşenlerinin durumunun ve işlemenin işlendiği sunucuya gerçek zamanlı ve kalıcı bağlantı sağlamak için bir SignalR hub 'ı yapılandırır.  `MapFallbackToPage`Yöntem çağrısı, Blazor uygulamasını Başlatan sayfanın Web tarafından erişilebilen konumunu gösterir ve ayrıca uygulamayı istemci tarafı derin bağlama isteklerini işleyecek şekilde yapılandırır.  Bir tarayıcı açarsanız ve varsayılan proje şablonunda olduğu gibi, uygulamanızda doğrudan Blazor işlenmiş yola gittiğinizde bu özelliği çalışır durumda görürsünüz `/counter` . İstek, daha sonra Blazor yönlendiricisini çalıştıran ve sayaç sayfasını işleyen *_Host. cshtml* geri dönüş sayfası tarafından işlenir.

## <a name="upgrading-the-bundleconfig-process"></a>Paketleme Liconfig Işlemini yükseltme

CSS stil sayfaları ve JavaScript dosyaları gibi varlıkları Paketleme Teknolojileri, bu kaynakları yönetmeye yönelik hızlı bir şekilde gelişen araçlar ve teknikler sağlayan diğer teknolojilerle önemli ölçüde geliştirilmiştir.  Bu uçta, statik varlıklarınızı paketlemek için Gryeniden oluşturma/Gulp/WebPack gibi bir düğüm komut satırı aracı kullanmanızı öneririz.

Gryeniden bağlama, Gulp ve WebPack komut satırı araçları ve bunlarla ilişkili yapılandırma işlemleri uygulamanıza eklenebilir ve ASP.NET Core uygulama oluşturma işlemi sırasında bu dosyaları sessizce yoksayar.  `Target`Bir Gulp betiğini ve `min` Bu betiğin içindeki hedefi tetikleyecek aşağıdakine benzer bir sözdizimi ile proje dosyanızın içine bir ekleyerek, görevlerini çalıştırmak için bir çağrı ekleyebilirsiniz

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

CSS ve JavaScript dosyalarınızı yönetmek için her iki strateji hakkında daha fazla ayrıntı için, [ASP.NET Core belgelerinde bulunan statik varlıkları paket halinde ve daha az](/aspnet/core/client-side/bundling-and-minification) bir şekilde bulabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](project-structure.md) 
> [Sonraki](components.md)
