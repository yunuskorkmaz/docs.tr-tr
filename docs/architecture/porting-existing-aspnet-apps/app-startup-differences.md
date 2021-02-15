---
title: ASP.NET MVC ve ASP.NET Core arasındaki uygulama başlatma farklılıkları
description: ASP.NET MVC ve ASP.NET Core uygulamaların nasıl çalıştığı konusunda önemli ölçüde farklılık gösterir. Önemli farklılıkları ve ASP.NET MVC 'den ASP.NET Core geçiş yapmayı öğrenin.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 4f40bb9cf616ea67b9826ff6a9dfe1c21cd1ea07
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488932"
---
# <a name="app-startup-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core arasındaki uygulama başlatma farklılıkları

ASP.NET MVC uygulamaları, Windows işletim sistemlerinde bulunan birincil web sunucusu olan Internet Information Server (IIS) içinde tamamen geçerlidir. ASP.NET MVC 'den farklı olarak ASP.NET Core uygulamalar yürütülebilir uygulamalardır. Bunları kullanarak komut satırından çalıştırabilirsiniz `dotnet run` . Tüm C# programları, genellikle `public static void Main()` veya benzer bir çeşitleme (Belki de bağımsız değişkenlerle veya destek ile) gibi bir giriş noktası yöntemi vardır `async` . Bu muhtemelen ASP.NET Core ve ASP.NET MVC arasındaki en büyük mimari farklılığı ve ASP.NET Core Windows dışı sistemlerde çalışmasına izin veren çeşitli farklardan biridir.

## <a name="aspnet-mvc-startup"></a>ASP.NET MVC başlatması

IIS 'de barındırılan ASP.NET Apps, belirli nesneleri başlatmak ve bir istek geldiğinde belirli yöntemleri çağırmak için IIS 'yi kullanır. ASP.NET, ' den türetilen *Global. asax* dosyasının sınıfının bir örneğini oluşturur `HttpApplication` . İlk istek alındığında, isteğin kendisini işlemeye başlamadan önce, ASP.NET, `Application_Start` *genel. asax* dosyasının sınıfındaki yöntemini çağırır. ASP.NET MVC uygulaması başladığında çalıştırılması gereken tüm mantık bu yönteme eklenebilir.

ASP.NET MVC ve Web API için birçok NuGet paketi, uygulamanın başlatılması sırasında bazı kodlar çalıştırmaya izin vermek için [Webactivator](https://github.com/davidebbo/WebActivator) paketini kullanır. Kurala göre, bu kod genellikle bir *App_Start* klasöre eklenir ve özniteliği aracılığıyla hemen önce veya hemen sonrasında çalıştırılacak şekilde yapılandırılır `Application_Start` .

Ayrıca, [.net (OWıN) Için açık Web arabirimi ve ASP.NET MVC Ile proje Katana](https://docs.microsoft.com/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana)öğesini kullanmak da mümkündür. Bu durumda, uygulama ASP.NET Core, istek ara yazılımı ayarlamanın ne kadar davranına benzer bir şekilde ayarlamaktan sorumlu bir *Startup.cs* dosyası içerir.

ASP.NET MVC uygulamanız başlatıldığında kodu çalıştırmanız gerekirse, genellikle bu yaklaşımlardan birini kullanacaktır.

## <a name="aspnet-core-startup"></a>ASP.NET Core başlangıç

Daha önce belirtildiği gibi ASP.NET Core uygulamalar tek başına programlardır. Bu nedenle, genellikle uygulamanın giriş noktasını içeren bir *program.cs* dosyası içerirler. Şekil 2-1 ' de bu dosyanın tipik bir örneği gösterilmiştir.

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

**Şekil 2-1**. Tipik bir ASP.NET Core *program.cs* dosyası.

Şekil 2-1 ' de gösterilen kod, uygulama için bir *konak* oluşturur, oluşturur ve çalıştırır. ASP.NET Core uygulama, gösterilen tarafından yapılandırılan ana bilgisayar içinde çalışır `IHostBuilder` . Kullanarak bir ASP.NET Core uygulamasını tamamen yapılandırmak mümkün olsa `IHostBuilder` da, genellikle bu çalışmanın toplu işi bir `Startup` sınıfta yapılır.

`Startup`Sınıfı, ana bilgisayar için iki yöntem sunar: `ConfigureServices` ve `Configure` . `ConfigureServices`Yöntemi, uygulamanın kullanacağı Hizmetleri ve ilgili yaşam sürelerini tanımlamak için kullanılır. `Configure`Yöntemi, bir uygulamaya yönelik her isteğin, ara yazılım tarafından oluşturulan bir istek işlem hattı ayarlanarak nasıl işleneceğini tanımlamak için kullanılır.

Uygulamanın hizmetlerini veya istek işlem hattını yapılandırma ile ilgili kodun yanı sıra, uygulamalar uygulama başladığında çalışması gereken başka bir koda de sahip olabilir. Bu tür kodlar genellikle *program.cs* ' a yerleştirilir veya olarak kaydedilir ve `IHostedService` uygulama başlatıldığında [genel ana bilgisayar](https://docs.microsoft.com/aspnet/core/fundamentals/host/generic-host?view=aspnetcore-3.1&preserve-view=true) tarafından başlatılır.

`IHostedService`Arabirim yalnızca iki yöntem sunar `StartAsync` ve `StopAsync` . Arabirimini ' a kaydedersiniz `ConfigureServices` ve konak, uygulama başlamadan önce yöntemi çağıran geri kalanı yapar `StartAsync` .

## <a name="porting-considerations"></a>Taşıma konuları

Uygulamalarını ASP.NET MVC 'den ASP.NET Core 'e geçirmek isteyen ekipler, uygulamaları başlatıldığında hangi kodun çalıştırıldığını belirlemek ve bu kodun ASP.NET Core uygulamalarında uygun konumu belirlemektir. Uygulama başladığında çalışması gereken özel kod için, özellikle zaman uyumsuz kod, önerilen yaklaşım genellikle bu tür kodları uygulamalara koymalıdır `IHostedService` .

## <a name="references"></a>Başvurular

- [IIS 7 için ASP.NET uygulama yaşam döngüsüne genel bakış](https://docs.microsoft.com/previous-versions/aspnet/bb470252(v=vs.100))
- [IIS 5 ve 6 için ASP.NET uygulama yaşam döngüsüne genel bakış](https://docs.microsoft.com/previous-versions/aspnet/ms178473(v=vs.100))
- [OWIN ve Katana ile Çalışmaya Başlama](https://docs.microsoft.com/aspnet/aspnet/overview/owin-and-katana/getting-started-with-owin-and-katana)
- [WebActivator](https://github.com/davidebbo/WebActivator)
- [ASP.NET Core 'de uygulama başlatma](https://docs.microsoft.com/aspnet/core/fundamentals/startup?view=aspnetcore-3.1&preserve-view=true)
- [ASP.NET Core .NET genel ana bilgisayarı](https://docs.microsoft.com/aspnet/core/fundamentals/host/generic-host?view=aspnetcore-3.1&preserve-view=true)
- [Ihostedservice](https://docs.microsoft.com/dotnet/architecture/microservices/multi-container-microservice-net-applications/background-tasks-with-ihostedservice)

>[!div class="step-by-step"]
>[Önceki](architectural-differences.md) 
> [Sonraki](hosting-differences.md)
