---
title: .NET oturumu açma
author: IEvangelist
description: Microsoft. Extensions. Logging NuGet paketi tarafından sunulan günlüğe kaydetme çerçevesini nasıl kullanacağınızı öğrenin.
ms.author: dapine
ms.date: 09/30/2020
ms.openlocfilehash: a742e192f8e080e2c76ebeb005168647e440d8ef
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614764"
---
# <a name="logging-in-net"></a>.NET oturumu açma

.NET, çeşitli yerleşik ve üçüncü taraf oturum açma sağlayıcılarıyla birlikte çalışarak bir günlüğe kaydetme API 'sini destekler. Bu makalede, yerleşik sağlayıcılarla günlüğe kaydetme API 'sinin nasıl kullanılacağı gösterilmektedir. Bu makalede gösterilen kod örneklerinin çoğu, [genel ana bilgisayarı](generic-host.md)kullanan tüm .NET uygulamaları için geçerlidir. Genel ana bilgisayarı kullanmayan uygulamalar için bkz. [konak konsol olmayan uygulama](#non-host-console-app).

## <a name="create-logs"></a>Günlükleri oluştur

Günlükler oluşturmak için <xref:Microsoft.Extensions.Logging.ILogger%601> [bağımlılık ekleme (dı)](dependency-injection.md)öğesinden bir nesne kullanın.

Aşağıdaki örnek:

- `ILogger<Worker>`Türün tam adı olan bir günlük *kategorisini* kullanan bir günlükçü oluşturur `Worker` . Günlük kategorisi, her günlük ile ilişkili bir dizedir.
- Bu <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> düzeyde günlüğe kaydedilecek çağrılar `Information` . Günlük *düzeyi* günlüğe kaydedilen etkinliğin önem derecesini gösterir.

:::code language="csharp" source="snippets/configuration/worker-service/Worker.cs" range="9-24" highlight="12":::

[Düzeyler](#log-level) ve [Kategoriler](#log-category) Bu makalenin ilerleyen kısımlarında daha ayrıntılı olarak açıklanmıştır.

## <a name="configure-logging"></a>Günlüğe kaydetmeyi yapılandırma

Günlüğe kaydetme yapılandırması genellikle `Logging` *appSettings*'in bölümü tarafından sağlanır. `{Environment}` *. JSON* dosyaları. Aşağıdaki *appsettings.Development.js* dosyadaki .net Worker hizmet şablonları tarafından oluşturulmuştur:

:::code language="json" source="snippets/configuration/worker-service/appsettings.Development.json":::

Önceki JSON 'da:

- `"Default"`, `"Microsoft"` Ve `"Microsoft.Hosting.Lifetime"` kategorileri belirtilir.
- `"Microsoft"`Kategori, ile başlayan tüm kategoriler için geçerlidir `"Microsoft"` .
- `"Microsoft"`Günlük düzeyindeki `Warning` ve daha yüksek kategori günlükleri.
- Kategori kategorisinden `"Microsoft.Hosting.Lifetime"` daha özeldir `"Microsoft"` , bu nedenle `"Microsoft.Hosting.Lifetime"` Kategori "Information" ve üzeri günlük düzeyinde günlüğe kaydedilir.
- Belirli bir günlük sağlayıcısı belirtilmedi, bu nedenle `LogLevel` [Windows olay](logging-providers.md#windows-eventlog)günlüğü hariç tüm etkin günlük sağlayıcıları için geçerlidir.

`Logging`Özelliği <xref:Microsoft.Extensions.Logging.LogLevel> ve günlük sağlayıcısı özelliklerine sahip olabilir. `LogLevel`Seçili kategoriler için günlüğe kaydedilecek en düşük [düzeyi](#log-level) belirtir. Önceki JSON 'da `Information` ve `Warning` günlük düzeyleri belirtilmiştir. `LogLevel` Günlüğün önem derecesini ve 0 ile 6 arasındaki aralıkları belirtir:

`Trace` = 0, `Debug` = 1, `Information` = 2, `Warning` = 3, `Error` = 4, `Critical` = 5 ve `None` = 6.

Bir `LogLevel` belirtildiğinde, belirtilen düzeydeki ve daha yüksek iletiler için günlüğe kaydetme etkinleştirilir. Önceki JSON 'da `Default` Kategori, ve üzeri için günlüğe kaydedilir `Information` . Örneğin,, `Information` , `Warning` `Error` ve `Critical` iletileri günlüğe kaydedilir. Hayır `LogLevel` belirtilmemişse, günlüğe kaydetme varsayılan olarak `Information` düzeydir. Daha fazla bilgi için bkz. [günlük düzeyleri](#log-level).

Sağlayıcı özelliği, bir özelliği belirtebilir `LogLevel` . `LogLevel` sağlayıcı altında, bu sağlayıcının günlüğe kaydedilecek düzeyleri belirtir ve sağlayıcı olmayan günlük ayarlarını geçersiz kılar. Dosyasında aşağıdaki *appsettings.js* göz önünde bulundurun:

:::code language="json" source="snippets/configuration/worker-service/appsettings.Staging.json":::

`Logging.{ProviderName}.LogLevel`' Deki geçersiz kılma ayarlarındaki ayarlar `Logging.LogLevel` . Önceki JSON 'da, `Debug` sağlayıcının varsayılan günlük düzeyi şu şekilde ayarlanır `Information` :

`Logging:Debug:LogLevel:Default:Information`

Yukarıdaki ayar, `Information` hariç her kategori için günlük düzeyini belirtir `Logging:Debug:` `Microsoft.Hosting` . Belirli bir kategori listelendiğinde, belirtilen kategori varsayılan kategoriyi geçersiz kılar. Önceki JSON 'da `Logging:Debug:LogLevel` Kategoriler `"Microsoft.Hosting"` ve `"Default"` içindeki ayarları geçersiz kılın `Logging:LogLevel`

En düşük günlük düzeyi şu şekilde belirtilebilir:

- Belirli sağlayıcılar: Örneğin, `Logging:EventSource:LogLevel:Default:Information`
- Belirli Kategoriler: Örneğin, `Logging:LogLevel:Microsoft:Warning`
- Tüm sağlayıcılar ve tüm Kategoriler: `Logging:LogLevel:Default:Warning`

Minimum düzeyin altındaki tüm Günlükler şu ***değildir***:

- Sağlayıcıya geçirildi.
- Günlüğe kaydedilir veya gösterilir.

Tüm günlükleri gizlemek için [LogLevel. None](xref:Microsoft.Extensions.Logging.LogLevel)belirtin. `LogLevel.None` 6 değerine sahiptir `LogLevel.Critical` (5).

Bir sağlayıcı, [günlük kapsamlarını](#log-scopes)destekliyorsa, etkinleştirilip etkinleştirilmeyeceğini `IncludeScopes` belirtir. Daha fazla bilgi için bkz. [günlük kapsamları](#log-scopes)

Aşağıdaki *appsettings.js* dosyadaki tüm yerleşik sağlayıcıların ayarlarını içerir:

:::code language="json" source="snippets/configuration/worker-service/appsettings.Production.json":::

Yukarıdaki örnekte:

- Kategoriler ve düzeyler önerilen değerler değildir. Varsayılan tüm sağlayıcıları göstermek için örnek sağlanır.
- `Logging.{ProviderName}.LogLevel`' Deki geçersiz kılma ayarlarındaki ayarlar `Logging.LogLevel` . Örneğin, içindeki düzeyi `Debug.LogLevel.Default` içindeki düzeyi geçersiz kılar `LogLevel.Default` .
- Her sağlayıcının *diğer adı* kullanılır. Her sağlayıcı, tam nitelikli tür adı yerine yapılandırmada kullanılabilecek bir *diğer ad* tanımlar. Yerleşik sağlayıcıların diğer adları şunlardır:
  - Konsol
  - Hata ayıklama
  - EventSource
  - EventLog
  - AzureAppServicesFile
  - AzureAppServicesBlob
  - ApplicationInsights

### <a name="set-log-level-by-command-line-environment-variables-and-other-configuration"></a>Günlük düzeyini komut satırı, ortam değişkenleri ve diğer yapılandırma ile ayarlama

Günlük düzeyi herhangi bir [yapılandırma sağlayıcısından](configuration-providers.md)ayarlanabilir.

Aşağıdaki komutlar:

- Ortam anahtarını `Logging:LogLevel:Microsoft` Windows üzerinde bir değeri olarak ayarlayın `Information` .
- .NET Worker hizmeti şablonlarıyla oluşturulan bir uygulamayı kullanırken ayarları test edin. `dotnet run`Komutun kullanıldıktan sonra proje dizininde çalıştırılması gerekir `set` .

```cmd
set Logging__LogLevel__Microsoft=Information
dotnet run
```

Önceki ortam ayarı:

- Yalnızca ' de ayarlanan komut penceresinden başlatılan işlemlerde ayarlanır.
- Visual Studio ile başlatılan uygulamalar tarafından okunamaz.

Aşağıdaki [Setx](/windows-server/administration/windows-commands/setx) komutu, Windows 'daki ortam anahtarını ve değerini de ayarlar. Farklı olarak `set` , `setx` ayarlar kalıcı hale getirilir. `/M`Anahtar, değişkeni sistem ortamında ayarlar. `/M`Kullanılmazsa, bir kullanıcı ortam değişkeni ayarlanır.

```cmd
setx Logging__LogLevel__Microsoft=Information /M
```

[Azure App Service](https://azure.microsoft.com/services/app-service/), **Ayarlar > yapılandırma** sayfasında **Yeni uygulama ayarı** ' nı seçin. Azure App Service uygulama ayarları şunlardır:

- Rest 'de şifrelenir ve şifreli bir kanal üzerinden iletilir.
- Ortam değişkenleri olarak sunulur.

Ortam değişkenlerini kullanarak .NET yapılandırma değerlerini ayarlama hakkında daha fazla bilgi için bkz. [ortam değişkenleri](configuration-providers.md#environment-variable-configuration-provider).

## <a name="how-filtering-rules-are-applied"></a>Filtreleme kuralları nasıl uygulanır

Bir <xref:Microsoft.Extensions.Logging.ILogger%601> nesne oluşturulduğunda, <xref:Microsoft.Extensions.Logging.ILoggerFactory> nesne bu günlükçü için uygulanacak her sağlayıcı için tek bir kural seçer. Bir örnek tarafından yazılan tüm iletiler `ILogger` , seçilen kurallara göre filtrelenmiştir. Her sağlayıcı ve kategori çifti için en özel kural, kullanılabilir kurallardan seçilir.

Belirli bir kategori için oluşturulan her sağlayıcı için aşağıdaki algoritma kullanılır `ILogger` :

- Sağlayıcı veya diğer adıyla eşleşen tüm kuralları seçin. Hiçbir eşleşme bulunmazsa, boş bir sağlayıcıya sahip tüm kurallar ' ı seçin.
- Önceki adımın sonucunda, en uzun eşleşen kategori ön ekine sahip kurallar ' ı seçin. Eşleşme bulunmazsa, kategori belirtmeyen tüm kuralları seçin.
- Birden çok kural seçilirse, **son** olanı götürün.
- Hiçbir kural seçilmemişse, <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.SetMinimumLevel(Microsoft.Extensions.Logging.ILoggingBuilder,Microsoft.Extensions.Logging.LogLevel)?displayProperty=nameWithType> En düşük günlük düzeyini belirtmek için kullanın.

## <a name="log-category"></a>Günlük kategorisi

Bir `ILogger` nesne oluşturulduğunda, bir *Kategori* belirtilir. Bu kategori, bu örneği tarafından oluşturulan her günlük iletisine dahildir `ILogger` . Kategori dizesi rastgele, ancak kural sınıf adını kullanmaktır. Örneğin, bir hizmet içeren bir uygulamada aşağıdaki nesne gibi bir, kategori şöyle olabilir `"Example.DefaultService"` :

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger<DefaultService> _logger;

        public DefaultService(ILogger<DefaultService> logger) =>
            _logger = logger;

        // ...
    }
}
```

Kategoriyi açıkça belirtmek için şunu çağırın <xref:Microsoft.Extensions.Logging.LoggerFactory.CreateLogger%2A?displayProperty=nameWithType> :

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger _logger;

        public DefaultService(ILoggerFactory loggerFactory) =>
            _logger = logger.CreateLogger("CustomCategory");

        // ...
    }
}
```

`CreateLogger`Sabit bir adla çağırmak, olayların kategoriye göre düzenlenebilmesi için birden çok yöntemde kullanıldığında faydalı olabilir.

`ILogger<T>` , `CreateLogger` tam nitelikli tür adı ile çağırma ile eşdeğerdir `T` .

## <a name="log-level"></a>Günlük düzeyi

Aşağıdaki tabloda <xref:Microsoft.Extensions.Logging.LogLevel> değerler, kolaylık `Log{LogLevel}` genişletme yöntemi ve önerilen kullanım listelenmektedir:

| LogLevel | Değer | Yöntem | Açıklama |
|--|--|--|--|
| [İzleme](xref:Microsoft.Extensions.Logging.LogLevel) | 0 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogTrace%2A> | En ayrıntılı iletileri içerir. Bu iletilerde hassas uygulama verileri bulunabilir. Bu iletiler varsayılan olarak devre dışıdır ve üretimde ***etkinleştirilmemelidir.*** |
| [H](xref:Microsoft.Extensions.Logging.LogLevel) | 1 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> | Hata ayıklama ve geliştirme için. Yüksek hacimden dolayı üretimde dikkatli olarak kullanın. |
| [Bilgi](xref:Microsoft.Extensions.Logging.LogLevel) | 2 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> | Uygulamanın genel akışını izler. Uzun süreli bir değere sahip olabilir. |
| [Uyarı](xref:Microsoft.Extensions.Logging.LogLevel) | 3 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogWarning%2A> | Olağandışı veya beklenmeyen olaylar için. Genellikle, uygulamanın başarısız olmasına neden olmayan hataları veya koşulları içerir. |
| [Hata](xref:Microsoft.Extensions.Logging.LogLevel) | 4 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogError%2A> | İşlenemeyen hatalar ve özel durumlar için. Bu iletiler, uygulama genelinde bir hata değil, geçerli işlemde veya istekte bir hata olduğunu gösterir. |
| [Kritik](xref:Microsoft.Extensions.Logging.LogLevel) | 5 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogCritical%2A> | Anında ilgilenilmesi gereken hatalarda. Örnekler: veri kaybı senaryoları, disk alanı yetersiz. |
| [Hiçbiri](xref:Microsoft.Extensions.Logging.LogLevel) | 6 |  | Hiçbir ileti yazılması gerektiğini belirtir. |

Önceki tabloda, `LogLevel` En düşük önem derecesine göre listelenmiştir.

[Günlük](xref:Microsoft.Extensions.Logging.LoggerExtensions) yönteminin ilk parametresi, <xref:Microsoft.Extensions.Logging.LogLevel> Günlüğün önem derecesini gösterir. Çağırmak yerine `Log(LogLevel, ...)` , çoğu Geliştirici [günlük {LogLevel}](xref:Microsoft.Extensions.Logging.LoggerExtensions) uzantı yöntemlerini çağırır. `Log{LogLevel}`Uzantı yöntemleri [günlük yöntemini çağırır ve LogLevel değerini belirtir](https://github.com/dotnet/extensions/blob/release/3.1/src/Logging/Logging.Abstractions/src/LoggerExtensions.cs). Örneğin, aşağıdaki iki günlük çağrısı işlevsel olarak eşdeğerdir ve aynı günlüğü üretir:

```csharp
public void LogDetails()
{
    var logMessage = "Details for log.";

    _logger.Log(LogLevel.Information, AppLogEvents.Details, logMessage);
    _logger.LogInformation(AppLogEvents.Details, logMessage);
}
```

`AppLogEvents.Details` olay KIMLIĞIDIR ve örtülü olarak sabit bir değerle temsil edilir <xref:System.Int32> . `AppLogEvents` , çeşitli adlandırılmış tanımlayıcı sabitleri kullanıma sunan ve [günlük olay kimliği](#log-event-id) bölümünde görüntülenen bir sınıftır.

Aşağıdaki kod oluşturur `Information` ve `Warning` günlükleri:

```csharp
public async Task<T> GetAsync<T>(string id)
{
    _logger.LogInformation(AppLogEvents.Read, "Reading value for {Id}", id);

    var result = await _repository.GetAsync(id);
    if (result is null)
    {
        _logger.LogWarning(AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
    }

    return result;
}
```

Yukarıdaki kodda, ilk `Log{LogLevel}` parametresi `AppLogEvents.Read` [günlük olay kimliğidir](#log-event-id). İkinci parametre, kalan Yöntem parametreleri tarafından belirtilen bağımsız değişken değerleri için yer tutucuları olan bir ileti şablonudur. Yöntem parametreleri bu makalenin ilerleyen kısımlarında bulunan [ileti şablonu](#log-message-template) bölümünde açıklanmaktadır.

Uygun günlük düzeyini yapılandırın ve `Log{LogLevel}` belirli bir depolama ortamına ne kadar günlük çıkışının yazıldığını denetlemek için doğru yöntemleri çağırın. Örneğin:

- Üretimde:
  - Veya düzeylerinde günlüğe kaydetme, `Trace` `Information` yüksek hacimli ayrıntılı günlük iletileri oluşturur. Maliyetleri denetlemek ve veri depolama sınırlarını aşmamak için, `Trace` `Information` iletileri yüksek hacimli ve düşük maliyetli bir veri deposuna günlüğe kaydedin. `Trace`Belirli kategorileri ve sınırlamayı değerlendirin `Information` .
  - Düzeylerde oturum açma, `Warning` `Critical` birkaç günlük iletisi üretmelidir.
    - Maliyetler ve depolama sınırları genellikle bir sorun değildir.
    - Birkaç günlük veri deposu seçimlerine daha fazla esneklik sağlar.
- Geliştirme aşamasında:
  - `Warning` olarak ayarlayın.
  - `Trace` `Information` Sorun giderirken veya ileti ekleyin. Çıktıyı sınırlandırmak için, `Trace` `Information` yalnızca araştırma bölümündeki Kategoriler için ayarlayın.

Aşağıdaki JSON kümeleri `Logging:Console:LogLevel:Microsoft:Information` :

:::code language="json" source="snippets/configuration/worker-service/appsettings.MSFT.json":::

## <a name="log-event-id"></a>Günlüğe olay KIMLIĞI

Her günlük bir *olay tanımlayıcı*belirtebilir, <xref:Microsoft.Extensions.Logging.EventId> `Id` ve isteğe bağlı ReadOnly özellikleri olan bir yapıdır `Name` . Örnek kaynak kodu, `AppLogEvents` olay kimliklerini tanımlamak için sınıfını kullanır:

```csharp
internal static class AppLogEvents
{
    internal const int Create = 1000;
    internal const int Read = 1001;
    internal const int Update = 1002;
    internal const int Delete = 1003;

    internal const int Details = 3000;
    internal const int Error = 3001;

    internal const int ReadNotFound = 4000;
    internal const int UpdateNotFound = 4001;

    // ...
}
```

Olay KIMLIĞI bir olay kümesini ilişkilendirir. Örneğin, bir depodan değer okuma ile ilgili tüm Günlükler olabilir `1001` .

Günlüğe kaydetme sağlayıcısı, olay KIMLIĞINI günlüğe kaydetme iletisindeki bir KIMLIK alanında veya hiç değil, günlüğe alabilir. Hata ayıklama sağlayıcısı olay kimliklerini göstermiyor. Konsol sağlayıcısı, etkinlik kimliklerini kategoriden sonra parantez içinde gösterir:

```console
info: Example.DefaultService.GetAsync[1001]
      Reading value for a1b2c3
warn: Example.DefaultService.GetAsync[4000]
      GetAsync(a1b2c3) not found
```

Bazı günlük sağlayıcıları olay KIMLIĞINI bir alanda depolar, bu da KIMLIĞE filtrelemeye olanak tanır.

## <a name="log-message-template"></a>Günlük iletisi şablonu

Her günlük API 'SI bir ileti şablonu kullanır. İleti şablonu, bağımsız değişkenlerin sağlandığı yer tutucuları içerebilir. Sayılar değil, yer tutucular için adları kullanın. Adlarının, değerlerinin sağlanması için hangi parametrelerin kullanılacağını belirleyen yer tutucular sırası. Aşağıdaki kodda, parametre adları ileti şablonunda sıra dışında:

```csharp
string p1 = "param1";
string p2 = "param2";
_logger.LogInformation("Parameter values: {p2}, {p1}", p1, p2);
```

Yukarıdaki kod, sırasıyla parametre değerleriyle bir günlük iletisi oluşturur:

```text
Parameter values: param1, param2
```

Bu yaklaşım, günlük sağlayıcılarının [anlam veya yapılandırılmış günlük kaydı](https://github.com/NLog/NLog/wiki/How-to-use-structured-logging)uygulamasına olanak sağlar. Bağımsız değişkenler yalnızca biçimli ileti şablonuna değil, günlük sistemine geçirilir. Bu, günlük sağlayıcılarının parametre değerlerini alan olarak depolamasına olanak sağlar. Aşağıdaki günlükçü yöntemini göz önünde bulundurun:

```csharp
_logger.LogInformation("Getting item {Id} at {RunTime}", id, DateTime.Now);
```

Örneğin, Azure Tablo depolama alanına oturum açarken:

- Her Azure Tablo varlığı `ID` ve özellikleri olabilir `RunTime` .
- Özellikleri olan tablolar günlüğe kaydedilen verilerde sorguları basitleştirir. Örneğin, bir sorgu belirli bir aralıktaki tüm günlükleri, `RunTime` kısa mesajdaki zaman aşımını ayrıştırmadan bulabilir.

## <a name="log-exceptions"></a>Günlük özel durumları

Günlükçü yöntemlerinde bir özel durum parametresi alan aşırı yüklemeleri var:

```csharp
public void Test(string id)
{
    try
    {
        if (id == "none")
        {
            throw new Exception("Default Id detected.");
        }
    }
    catch (Exception ex)
    {
        _logger.LogWarning(
            AppLogEvents.Error, ex,
            "Failed to process iteration: {Id}", id)
    }
}
```

Özel durum günlüğe kaydetme, sağlayıcıya özgüdür.

### <a name="default-log-level"></a>Varsayılan günlük düzeyi

Varsayılan günlük düzeyi ayarlanmamışsa varsayılan günlük düzeyi değeri olur `Information` .

Örneğin, aşağıdaki çalışan hizmeti uygulamasını göz önünde bulundurun:

- .NET Worker şablonlarıyla oluşturulur.
- *appsettings.js* ve *appsettings.Development.js* silinmiş ya da yeniden adlandırıldı.

Önceki kurulumla, gizlilik veya giriş sayfasına gidildiğinde `Trace` `Debug` Kategori adında birçok, ve `Information`  ile ileti üretilir `Microsoft` .

Aşağıdaki kod, varsayılan günlük düzeyi yapılandırmada ayarlanmamışsa varsayılan günlük düzeyini ayarlar:

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging => logging.SetMinimumLevel(LogLevel.Warning));
}
```

### <a name="filter-function"></a>Filter işlevi

Configuration veya Code tarafından kendisine atanmış kuralları olmayan tüm sağlayıcılar ve kategoriler için bir filtre işlevi çağrılır:

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddFilter((provider, category, logLevel) =>
                {
                    return provider.Contains("ConsoleLoggerProvider")
                        && (category.Contains("Example") || category.Contains("Microsoft"))
                        && logLevel >= LogLevel.Information;
                }));
}
```

Önceki kod, kategori içerdiğinde `Example` veya `Microsoft` ve günlük düzeyi `Information` veya daha yüksek olduğunda konsol günlüklerini görüntüler.

## <a name="log-scopes"></a>Günlük kapsamları

 *Kapsam* bir mantıksal işlemler kümesini gruplandırabilir. Bu gruplandırma, kümenin bir parçası olarak oluşturulan her günlüğe aynı verileri eklemek için kullanılabilir. Örneğin, bir işlemin işlenmesi kapsamında oluşturulan her günlük işlem KIMLIĞI içerebilir.

Kapsam:

- <xref:System.IDisposable>, Yöntemi tarafından döndürülen türdür <xref:Microsoft.Extensions.Logging.ILogger.BeginScope%2A> .
- Atılana kadar sürer.

Aşağıdaki sağlayıcılar kapsamları destekler:

- `Console`
- [AzureAppServicesFile ve AzureAppServicesBlob](xref:Microsoft.Extensions.Logging.AzureAppServices.BatchingLoggerOptions.IncludeScopes)

Bir blok içinde günlükçü çağrılarını sarmalayarak kapsam kullanın `using` :

```csharp
public async Task<T> GetAsync<T>(string id)
{
    T result;

    using (_logger.BeginScope("using block message"))
    {
        _logger.LogInformation(
            AppLogEvents.Read, "Reading value for {Id}", id);

        var result = await _repository.GetAsync(id);
        if (result is null)
        {
            _logger.LogWarning(
                AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
        }
    }

    return result;
}
```

Aşağıdaki JSON konsol sağlayıcısı için kapsamları etkinleştirdi:

:::code language="json" source="snippets/configuration/worker-service/appsettings.IncludeScopes.json" highlight="9":::

Aşağıdaki kod konsol sağlayıcısı için kapsamları etkinleştirilir:

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging((_, logging) =>
                logging.ClearProviders()
                    .AddConsole(options => options.IncludeScopes = true));
}
```

## <a name="non-host-console-app"></a>Konak olmayan konsol uygulaması

[Genel ana bilgisayarı](generic-host.md) olmayan uygulamalar için günlük kaydı kodu, [sağlayıcıların Eklenme](#add-providers) ve [günlükçülerin oluşturulduğu](#create-logs)yönteme göre farklılık gösterir. Konak olmayan bir konsol uygulamasında, `Add{provider name}` oluşturma sırasında sağlayıcının uzantı yöntemini çağırın `LoggerFactory` :

```csharp
class Program
{
    static void Main(string[] args)
    {
        using var loggerFactory = LoggerFactory.Create(builder =>
        {
            builder
                .AddFilter("Microsoft", LogLevel.Warning)
                .AddFilter("System", LogLevel.Warning)
                .AddFilter("LoggingConsoleApp.Program", LogLevel.Debug)
                .AddConsole();
        });

        ILogger logger = loggerFactory.CreateLogger<Program>();
        logger.LogInformation("Example log message");
    }
}
```

`loggerFactory`Nesne bir örnek oluşturmak için kullanılır <xref:Microsoft.Extensions.Logging.ILogger> .

## <a name="create-logs-in-main"></a>Ana oturum oluşturma

Aşağıdaki kod, `Main` `ILogger` konak oluşturulduktan sonra bir örneğinden bir örnek alarak oturum açar:

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;

class Program
{
    static Task Main(string[] args)
    {
        IHost host = Host.CreateDefaultBuilder(args).Build();

        var logger = host.Services.GetRequiredService<ILogger<Program>>();
        logger.LogInformation("Host created.");

        return host.RunAsync();
    }
}
```

### <a name="no-asynchronous-logger-methods"></a>Zaman uyumsuz günlükçü yöntemi yok

Günlüğe kaydetme, zaman uyumsuz kodun performans maliyetine değer olmaması kadar hızlı olmalıdır. Günlüğe kaydetme veri deposu yavaşsa doğrudan yazma. Günlük iletilerini başlangıçta hızlı bir mağazaya yazmayı ve sonra bunları yavaş depoya daha sonra taşımayı düşünün. Örneğin, SQL Server oturum açarken `Log` Yöntemler zaman uyumlu olduğundan doğrudan bir yöntemde yapmayın `Log` . Bunun yerine, günlük iletilerini bir bellek içi kuyruğa eşzamanlı olarak ekleyin ve bir arka plan çalışanı, SQL Server veri gönderme zaman uyumsuz çalışmasını sağlamak için iletileri kuyruktan çekin.

## <a name="change-log-levels-in-a-running-app"></a>Çalışan bir uygulamadaki günlük düzeylerini değiştirme

Günlüğe kaydetme API 'SI, bir uygulama çalışırken günlük düzeylerini değiştirme senaryosu içermez. Ancak, bazı yapılandırma sağlayıcıları yapılandırmayı yeniden yükleme yeteneğine sahiptir ve bu, günlüğe kaydetme yapılandırması üzerinde etkili bir şekilde gerçekleşir. Örneğin, [dosya yapılandırma sağlayıcısı](configuration-providers.md#file-configuration-provider) günlük yapılandırmasını varsayılan olarak yeniden yükler. Uygulama çalışırken kodda yapılandırma değiştirilirse uygulama, uygulamanın günlük yapılandırmasını güncelleştirmek için [IController. Reload](xref:Microsoft.Extensions.Configuration.IConfigurationRoot.Reload%2A) ' i çağırabilir.

## <a name="nuget-packages"></a>NuGet paketleri

<xref:Microsoft.Extensions.Logging.ILogger%601>Ve <xref:Microsoft.Extensions.Logging.ILoggerFactory> arabirimleri ve uygulamaları .NET Core SDK dahil edilmiştir. Bunlar ayrıca aşağıdaki NuGet paketlerinde de kullanılabilir:

- Arabirimler [Microsoft. Extensions. Logging. soyutlamalar](https://www.nuget.org/packages/Microsoft.Extensions.Logging.Abstractions)içinde bulunur.
- Varsayılan uygulamalar [Microsoft. Extensions. Logging](https://www.nuget.org/packages/microsoft.extensions.logging)' dir.

## <a name="apply-log-filter-rules-in-code"></a>Koddaki günlük filtresi kurallarını Uygula

Günlük filtresi kurallarını ayarlamak için tercih edilen yaklaşım [yapılandırma](configuration.md)kullanmaktır.

Aşağıdaki örnek, koddaki filtre kurallarının nasıl kaydedileceği gösterilmektedir:

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
               logging.AddFilter("System", LogLevel.Debug)
                  .AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)
                  .AddFilter<ConsoleLoggerProvider>("Microsoft", LogLevel.Trace));
}
```

`logging.AddFilter("System", LogLevel.Debug)``System`Kategori ve günlük düzeyini belirtir `Debug` . Belirli bir sağlayıcı yapılandırılmadığı için filtre tüm sağlayıcılara uygulanır.

`AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)` belirtir

- `Debug`Günlüğe kaydetme sağlayıcısı.
- Günlük düzeyi `Information` ve üzeri.
- İle başlayan tüm kategoriler `"Microsoft"` .

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'te günlüğe kaydetme sağlayıcıları](logging-providers.md)
- [.NET ' te özel bir günlüğe kaydetme sağlayıcısı uygulama](custom-logging-provider.md)
- [.NET 'te yüksek performanslı günlüğe kaydetme](high-performance-logging.md)
- [GitHub.com/DotNet/Extensions](https://github.com/dotnet/extensions/issues) deposu 'nda günlüğe kaydetme hataları oluşturulmalıdır
