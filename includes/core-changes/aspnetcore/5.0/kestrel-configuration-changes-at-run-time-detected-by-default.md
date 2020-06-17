---
ms.openlocfilehash: d00b8ecaa61b358e062d85a2b68ca8a95cada442
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803254"
---
### <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a>Kestrel: çalışma zamanında varsayılan olarak algılanan yapılandırma değişiklikleri

Kestrel şimdi `Kestrel` `IConfiguration` , çalışma zamanında projenin örneğinin bölümünde yapılan değişikliklere (örneğin, *appsettings.jsaçık*) yeniden davranır. *Üzerindeappsettings.js*kullanarak Kestrel yapılandırma hakkında daha fazla bilgi edinmek Için [uç nokta yapılandırması](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration)'nda *appsettings.jshakkında* bölümüne bakın.

Kestrel, bu yapılandırma değişikliklerine tepki vermek için uç noktaları gerektiği şekilde bağlar, çözer ve yeniden bağlayın.

Tartışma için bkz. sorun [DotNet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807).

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 7

#### <a name="old-behavior"></a>Eski davranış

ASP.NET Core 5,0 Preview 6 ' dan önce Kestrel, çalışma zamanında yapılandırmanın değiştirilmesini desteklememektedir.

ASP.NET Core 5,0 Preview 6 ' da, çalışma zamanında yapılandırma değişikliklerine yeniden davranma özelliğinin varsayılan davranışını kabul edebilirsiniz. Gerekli bağlama Kestrel yapılandırması el ile:

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Hosting;

public class Program
{
    public static void Main(string[] args) =>
        CreateHostBuilder(args).Build().Run();

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

#### <a name="new-behavior"></a>Yeni davranış

Kestrel, varsayılan olarak çalışma zamanında yapılandırma değişikliklerine tepki verir. Bu değişikliği desteklemek için, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> `KestrelServerOptions.Configure(IConfiguration, bool)` `reloadOnChange: true` Varsayılan olarak ile çağırır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Sunucu tamamen yeniden başlatılmadan çalışma zamanında bitiş noktası yeniden yapılandırması desteklemek için değişiklik yapıldı. Tam sunucu yeniden başlatmasından farklı olarak, değiştirilmemiş uç noktalar geçici olarak geçici olarak ilişkisiz olmaz.

#### <a name="recommended-action"></a>Önerilen eylem

* Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değişmediğinden çoğu senaryo için, bu değişikliğin etkisi yoktur ve hiçbir eylem gerekmez.
* Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değişme ve Kestrel 'e yanıt vermesini gerektiren senaryolar için, bu artık varsayılan davranıştır.
* Kestrel 'in varsayılan yapılandırma bölümünün çalışma zamanında değiştiği ve Kestrel 'e yanıt vermeme senaryolarında, aşağıdaki gibi devre dışı bırakabilirsiniz:

    ```csharp
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

**Notlar:**

Bu değişiklik aşırı yükleme davranışını değiştirmez, bu da `KestrelServerOptions.Configure(IConfiguration)` davranışa varsayılan olarak devam eder `reloadOnChange: false` .

Yapılandırma kaynağının yeniden yüklemeyi desteklediğinden emin olmak da önemlidir. JSON kaynakları için, yeniden yükleme çağırarak yapılandırılır `AddJsonFile(path, reloadOnChange: true)` . Yeniden yükleme, *appsettings.json* ve appSettings için varsayılan olarak zaten yapılandırılmıştır *. { Environment}. JSON*.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
