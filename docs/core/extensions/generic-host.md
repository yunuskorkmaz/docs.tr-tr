---
title: .NET genel ana bilgisayar
author: IEvangelist
description: Uygulama başlatma ve ömür yönetiminden sorumlu .NET genel ana bilgisayarı hakkında bilgi edinin.
ms.author: dapine
ms.date: 09/18/2020
ms.openlocfilehash: a1f82f6c6b5d250d6e81351aa02e50e23636280b
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608275"
---
# <a name="net-generic-host"></a>.NET genel ana bilgisayar

Çalışan hizmeti şablonları bir .NET genel ana bilgisayarı oluşturur <xref:Microsoft.Extensions.Hosting.HostBuilder> . Genel ana bilgisayar, konsol uygulamaları gibi diğer .NET uygulaması türleriyle birlikte kullanılabilir.

*Ana bilgisayar* , bir uygulamanın kaynaklarını kapsülleyen bir nesnedir, örneğin:

- Bağımlılık ekleme (dı)
- Günlüğe Kaydetme
- Yapılandırma
- `IHostedService` uygulamalarını

Bir konak başlatıldığında, <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> <xref:Microsoft.Extensions.Hosting.IHostedService> hizmet kapsayıcısının barındırılan hizmetler koleksiyonunda kayıtlı her bir uygulamasına çağrı yapılır. Çalışan hizmeti uygulamasında, `IHostedService` örnekleri içeren tüm uygulamaların <xref:Microsoft.Extensions.Hosting.BackgroundService> <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> yöntemlerine sahiptir.

Uygulamanın tüm birbirine bağlı kaynaklarını tek bir nesnede dahil etmek için başlıca neden, yaşam süresi yönetimi: uygulama başlatma ve düzgün kapanma üzerinde denetim. Bu, [Microsoft. Extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet paketi ile sağlanır.

## <a name="set-up-a-host"></a>Konak ayarlama

Ana bilgisayar genellikle sınıfında kodla yapılandırılır, oluşturulur ve çalıştırılır `Program` . `Main`Yöntemi:

- <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder>Bir Oluşturucu nesnesi oluşturmak ve yapılandırmak için bir yöntem çağırır.
- <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build>Örnek oluşturmak için çağırır <xref:Microsoft.Extensions.Hosting.IHost> .
- <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> Ana bilgisayar nesnesi üzerinde veya yöntemini çağırır.

.NET Worker hizmet şablonları, genel bir konak oluşturmak için aşağıdaki kodu oluşturur:

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureServices((hostContext, services) =>
            {
                services.AddHostedService<Worker>();
            });
}
```

## <a name="default-builder-settings"></a>Varsayılan Oluşturucu ayarları

<xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>Yöntemi:

- İçerik kökünü tarafından döndürülen yola ayarlar <xref:System.IO.Directory.GetCurrentDirectory> .
- [Ana bilgisayar yapılandırmasını](#host-configuration) şuradan yükler:
  - Ön eki olan ortam değişkenleri `DOTNET_` .
  - Komut satırı bağımsız değişkenleri.
- Uygulama yapılandırmasını şuradan yükler:
  - * Üzerindeappsettings.js*.
  - *appSettings. {Environment}. JSON*.
  - Uygulama ortamda çalıştığında gizli dizi Yöneticisi `Development` .
  - Ortam değişkenleri.
  - Komut satırı bağımsız değişkenleri.
- Aşağıdaki günlük sağlayıcılarını ekler:
  - Konsol
  - Hata ayıklama
  - EventSource
  - Olay günlüğü (yalnızca Windows üzerinde çalışırken)
- Ortam olduğunda kapsam doğrulaması ve [bağımlılık doğrulaması](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) etkinleştirilir `Development` .

`ConfigureServices`Yöntemi, örneğe hizmet ekleme özelliğini kullanıma sunar <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> . Daha sonra, bu hizmetler bağımlılık ekleme yoluyla kullanılabilir hale getirilebilir.

## <a name="framework-provided-services"></a>Framework tarafından sunulan hizmetler

Aşağıdaki hizmetler otomatik olarak kaydedilir:

- [Ihostapplicationlifetime](#ihostapplicationlifetime)
- [Ihostlifetime](#ihostlifetime)
- [Ihostenvironment](#ihostenvironment)

## <a name="ihostapplicationlifetime"></a>Ihostapplicationlifetime

<xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>Başlatma sonrası ve düzgün kapanma görevlerini işlemek için hizmeti herhangi bir sınıfa ekleyin. Arabirimdeki üç özellik, uygulama başlatma ve uygulama durdurma olay işleyicisi yöntemlerini kaydetmek için kullanılan iptal belirteçleridir. Arabirim Ayrıca bir yöntemi içerir <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> .

Aşağıdaki örnek, `IHostedService` olayları kaydeden bir uygulamasıdır `IHostApplicationLifetime` :

:::code language="csharp" source="snippets/configuration/app-lifetime/ExampleHostedService.cs" highlight="18-20":::

Çalışan hizmeti şablonu, uygulamayı eklemek için değiştirilebilir `ExampleHostedService` :

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="1-16,36" highlight="15":::

Uygulama aşağıdaki örnek çıktıyı Yazar:

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="17-35":::

## <a name="ihostlifetime"></a>Ihostlifetime

<xref:Microsoft.Extensions.Hosting.IHostLifetime>Uygulama, ana bilgisayar başladığında ve durdurulduğunda denetler. Kaydedilen son uygulama kullanılır.

`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` Varsayılan `IHostLifetime` uygulama. `ConsoleLifetime`:

- <kbd>CTRL</kbd> + <kbd>C</kbd>, [sigint](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT)veya [sigterm](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) 'i dinler ve <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> başlatma işlemini başlatmak için çağırır.
- Ve gibi uzantıları kaldırır `RunAsync` `WaitForShutdownAsync` .

## <a name="ihostenvironment"></a>Ihostenvironment

<xref:Microsoft.Extensions.Hosting.IHostEnvironment>Aşağıdaki ayarlarla ilgili bilgi almak için hizmeti bir sınıfa ekleyin:

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ApplicationName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootFileProvider?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootPath?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.EnvironmentName?displayProperty=nameWithType>

## <a name="host-configuration"></a>Konak yapılandırması

Ana bilgisayar yapılandırması, uygulamanın özellikleri için kullanılır <xref:Microsoft.Extensions.Hosting.IHostEnvironment> .

Ana Bilgisayar Yapılandırması içinde [HostBuilderContext.Configurlama](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) tarafından kullanılabilir <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> . Sonra `ConfigureAppConfiguration` , `HostBuilderContext.Configuration` uygulama yapılandırması ile değiştirilmiştir.

Konak yapılandırması eklemek için üzerinde öğesini <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> çağırın `IHostBuilder` . `ConfigureHostConfiguration` , eklenebilir sonuçlarla birden çok kez çağrılabilir. Ana bilgisayar, belirli bir anahtardaki bir değeri en son belirleyen seçeneği kullanır.

Aşağıdaki örnek ana bilgisayar yapılandırması oluşturur:

:::code language="csharp" source="snippets/configuration/console-host/Program.cs" highlight="13-19":::

## <a name="app-configuration"></a>Uygulama yapılandırması

Uygulama yapılandırması, üzerinde çağırarak oluşturulur <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> `IHostBuilder` . `ConfigureAppConfiguration` , eklenebilir sonuçlarla birden çok kez çağrılabilir. Uygulama, belirli bir anahtardaki bir değeri en son belirleyen seçeneği kullanır.

Tarafından oluşturulan yapılandırma, `ConfigureAppConfiguration` sonraki işlemler ve dı hizmeti olarak [HostBuilderContext.Config](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) bir hizmet olarak sunulmaktadır. Konak yapılandırması, uygulama yapılandırmasına de eklenir.

Daha fazla bilgi için bkz. [.net 'Teki yapılandırma](configuration.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'teki yapılandırma](configuration.md)
- [ASP.NET Core Web ana bilgisayarı](/aspnet/core/fundamentals/host/web-host)
- Genel ana bilgisayar hataları [GitHub.com/DotNet/Extensions](https://github.com/dotnet/extensions/issues) deposu 'nda oluşturulmalıdır
