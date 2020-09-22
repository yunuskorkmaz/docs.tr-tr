---
title: .NET 'teki yapılandırma sağlayıcıları
description: .NET uygulamalarını yapılandırmak için yapılandırma sağlayıcısı API 'sinin nasıl kullanıldığını öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.openlocfilehash: d5333e8e52feb7d28e2149a988dc7ce53a926a50
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874748"
---
# <a name="configuration-providers-in-net"></a>.NET 'teki yapılandırma sağlayıcıları

Yapılandırma sağlayıcılarıyla .NET için yapılandırma mümkündür. Çeşitli yapılandırma kaynaklarını kullanan çeşitli sağlayıcı türleri vardır. Bu makalede, tüm farklı yapılandırma sağlayıcılarının ve bunlara karşılık gelen kaynakların ayrıntıları yer alırlar.

- [Dosya yapılandırma sağlayıcısı](#file-configuration-provider)
- [Ortam değişkeni yapılandırma sağlayıcısı](#environment-variable-configuration-provider)
- [Komut satırı yapılandırma sağlayıcısı](#command-line-configuration-provider)
- [Dosya başına anahtar yapılandırma sağlayıcısı](#key-per-file-configuration-provider)
- [Bellek yapılandırma sağlayıcısı](#memory-configuration-provider)

## <a name="file-configuration-provider"></a>Dosya yapılandırma sağlayıcısı

<xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> , dosya sisteminden yapılandırma yüklemeye yönelik temel sınıftır. Aşağıdaki yapılandırma sağlayıcıları öğesinden türetilir `FileConfigurationProvider` :

- [JSON yapılandırma sağlayıcısı](#json-configuration-provider)
- [XML yapılandırma sağlayıcısı](#xml-configuration-provider)
- [INı yapılandırma sağlayıcısı](#ini-configuration-provider)

### <a name="json-configuration-provider"></a>JSON yapılandırma sağlayıcısı

<xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider>Sınıfı, BIR json dosyasından yapılandırma yükler. [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json)NuGet paketini yükler.

Aşırı yüklemeler şunları belirtebilir:

- Dosyanın isteğe bağlı olup olmadığı
- Dosya değişirse yapılandırmanın yeniden yüklenip yüklenmediğini belirtir

Aşağıdaki kodu inceleyin:

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="1-33,37-38" highlight="17-23":::

Yukarıdaki kod:

- Yönteminde varsayılan olarak eklenmiş olan tüm mevcut yapılandırma sağlayıcılarını temizler <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> .
- On ve *appsettings* *appsettings.js* yüklemek için JSON yapılandırma sağlayıcısını `Environment` yapılandırır. aşağıdaki seçeneklere sahip *JSON* dosyaları:
  - `optional: true`: Dosya isteğe bağlıdır.
  - `reloadOnChange: true` : Değişiklikler kaydedildiğinde dosya yeniden yüklenir.

JSON ayarları, [ortam değişkenleri yapılandırma sağlayıcısı](#environment-variable-configuration-provider) ve [komut satırı yapılandırma sağlayıcısı](#command-line-configuration-provider)ayarları tarafından geçersiz kılınır.

Çeşitli yapılandırma ayarları ile dosyada bir örnek *appsettings.js* aşağıda verilmiştir:

:::code language="json" source="snippets/configuration/console-json/appsettings.json":::

<xref:Microsoft.Extensions.Configuration.IConfigurationBuilder>Örnekten, yapılandırma sağlayıcıları eklendikten sonra <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> nesneyi almak için öğesini çağırabilirsiniz <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> . Yapılandırma kökü bir yapılandırma hiyerarşisinin kökünü temsil eder. Yapılandırma bölümleri, .NET nesnelerinin örneklerine bağlanabilir ve daha sonra <xref:Microsoft.Extensions.Options.IOptions%601> bağımlılık ekleme yoluyla olarak sağlanmış olur.

`TransientFaultHandlingOptions`Aşağıdaki şekilde tanımlanan kayıt türünü göz önünde bulundurun:

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs":::

Kayıt türleri hakkında bilgi için bkz. [C# 9 ' da kayıt türleri](../../csharp/whats-new/csharp-9.md#record-types).

Aşağıdaki kod yapılandırma kökünü oluşturur, bir bölümü `TransientFaultHandlingOptions` kayıt türüne bağlar ve bağlı değerleri konsol penceresine yazdırır:

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="25-32":::

Uygulama aşağıdaki örnek çıktıyı Yazar:

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="34-36":::

### <a name="xml-configuration-provider"></a>XML yapılandırma sağlayıcısı

<xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider>Sınıfı, çalışma zamanında BIR XML dosyasındaki yapılandırmayı yükler. [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml)NuGet paketini yükler.

Aşağıdaki kod XML yapılandırma sağlayıcısını kullanarak XML dosyalarının yapılandırmasını gösterir.

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="1-28,46,52-53" highlight="17-28":::

Yukarıdaki kod:

- Yönteminde varsayılan olarak eklenmiş olan tüm mevcut yapılandırma sağlayıcılarını temizler <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> .
- , Aşağıdaki seçeneklerle *appsettings.xml* ve *repeating-example.xml* dosyalarını yükleyecek XML yapılandırma sağlayıcısını yapılandırır:
  - `optional: true`: Dosya isteğe bağlıdır.
  - `reloadOnChange: true` : Değişiklikler kaydedildiğinde dosya yeniden yüklenir.
- Ortam değişkenleri yapılandırma sağlayıcısını yapılandırır.
- Verilen bağımsız değişkenler içeriyorsa, komut satırı yapılandırma sağlayıcısını yapılandırır `args` .

XML ayarları, [ortam değişkenleri yapılandırma sağlayıcısı](#environment-variable-configuration-provider) ve [komut satırı yapılandırma sağlayıcısı](#command-line-configuration-provider)ayarları tarafından geçersiz kılınır.

Çeşitli yapılandırma ayarlarına sahip bir örnek *appsettings.xml* dosyası aşağıda verilmiştir:

:::code language="xml" source="snippets/configuration/console-xml/appsettings.xml":::

Aynı öğe adını kullanan yinelenen öğeler, `name` özniteliği öğeleri ayırt etmek için kullanılacaksa çalışır:

:::code language="xml" source="snippets/configuration/console-xml/repeating-example.xml":::

Aşağıdaki kod, önceki yapılandırma dosyasını okur ve anahtarları ve değerleri görüntüler:

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="30-45":::

Uygulama aşağıdaki örnek çıktıyı Yazar:

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="47-51":::

Öznitelikler, değerler sağlamak için kullanılabilir:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <key attribute="value" />
  <section>
    <key attribute="value" />
  </section>
</configuration>
```

Önceki yapılandırma dosyası aşağıdaki anahtarları ile yükler `value` :

- `key:attribute`
- `section:key:attribute`

### <a name="ini-configuration-provider"></a>INı yapılandırma sağlayıcısı

<xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider>Sınıfı, çalışma zamanında BIR INI dosyasındaki yapılandırmayı yükler. [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)NuGet paketini yükler.

Aşağıdaki kod, tüm yapılandırma sağlayıcılarını temizler ve `IniConfigurationProvider` kaynak olarak ıkı INI dosyası ile ekler:

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="1-31,38-39" highlight="18-24":::

Çeşitli yapılandırma ayarlarına sahip bir örnek *appsettings.ini* dosyası aşağıda verilmiştir:

:::code language="ini" source="snippets/configuration/console-ini/appsettings.ini":::

Aşağıdaki kod, önceki yapılandırma ayarlarını konsol penceresine yazarak görüntüler:

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="26-30":::

Uygulama aşağıdaki örnek çıktıyı Yazar:

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="32-37":::

## <a name="environment-variable-configuration-provider"></a>Ortam değişkeni yapılandırma sağlayıcısı

Varsayılan yapılandırmayı kullanarak, <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> yapılandırma *appsettings.json*, appSettings sonrasında anahtar-değer çiftlerinde bulunan yapılandırmayı yükler *.* `Environment` *. JSON*ve gizli yönetici. Bu nedenle, ortamdan okunan anahtar değerleri, *appsettings.json*, appSettings öğesinden okunan değerleri geçersiz kılar *.* `Environment` *. JSON*ve gizli yönetici.

`:`Ayırıcı, tüm platformlarda ortam değişkeni hiyerarşik anahtarlarla birlikte çalışmaz. Çift alt çizgi ( `__` ) otomatik olarak bir ile değiştirilmiştir `:` ve tüm platformlar tarafından desteklenir. Örneğin, `:` ayırıcı [Bash](https://linuxhint.com/bash-environment-variables)tarafından desteklenmez, ancak `__` .

Aşağıdaki `set` Komutlar:

- Windows üzerinde önceki örneğin ortam anahtarlarını ve değerlerini ayarlayın.
- Ayarları varsayılan değerlerinden değiştirerek test edin. `dotnet run`Komutun proje dizininde çalıştırılması gerekir.

```dotnetcli
set SecretKey="Secret key from environment"
set TransientFaultHandlingOptions__Enabled="true"
set TransientFaultHandlingOptions__AutoRetryDelay="00:00:13"

dotnet run
```

Önceki ortam ayarları:

- Yalnızca ' de ayarlanan komut penceresinden başlatılan işlemlerde ayarlanır.
- Visual Studio ile başlatılan Web Apps tarafından okunmayacaktır.

Aşağıdaki [Setx](/windows-server/administration/windows-commands/setx) komutları Windows üzerinde ortam anahtarlarını ve değerlerini ayarlamak için kullanılabilir. Farklı olarak `set` , `setx` ayarlar kalıcı hale getirilir. `/M` değişkeni sistem ortamında ayarlar. `/M`Anahtar kullanılmazsa, bir kullanıcı ortam değişkeni ayarlanır.

```dotnetcli
setx SecretKey "Secret key from setx environment" /M
setx TransientFaultHandlingOptions__Enabled "true" /M
setx TransientFaultHandlingOptions__AutoRetryDelay "00:00:05" /M

dotnet run
```

Yukarıdaki komutların ve appSettings *appsettings.js* geçersiz kılmasını test etmek *.* `Environment` *. JSON*:

- Visual Studio ile: Exit ve Visual Studio 'Yu yeniden başlatın.
- CLı ile: yeni bir komut penceresi başlatın ve girin `dotnet run` .

<xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A>Ortam değişkenlerinin önekini belirtmek için bir dizeyle çağırın:

:::code language="csharp" source="snippets/configuration/console-env/Program.cs" highlight="15-16":::

Yukarıdaki kodda:

- `config.AddEnvironmentVariables(prefix: "CustomPrefix_")` Varsayılan yapılandırma sağlayıcılarından sonra eklenir. Yapılandırma sağlayıcılarını sipariş eden bir örnek için bkz. [XML yapılandırma sağlayıcısı](#xml-configuration-provider).
- Önek ile ayarlanan ortam değişkenleri `CustomPrefix_` varsayılan yapılandırma sağlayıcılarını geçersiz kılar. Bu, öneki olmayan ortam değişkenlerini içerir.

Yapılandırma anahtar-değer çiftleri okunduktan sonra önek çıkarılır.

Aşağıdaki komutlar özel öneki test et:

```dotnetcli
set CustomPrefix__SecretKey="Secret key with CustomPrefix_ environment"
set CustomPrefix_TransientFaultHandlingOptions__Enabled=true
set CustomPrefix_TransientFaultHandlingOptions__AutoRetryDelay=00:00:21

dotnet run
```

Varsayılan yapılandırma, ön eki olan ortam değişkenlerini ve komut satırı bağımsız değişkenlerini yükler `DOTNET_` . `DOTNET_`Ön ek, .NET tarafından [konak](generic-host.md#host-configuration) ve [uygulama yapılandırması](generic-host.md#app-configuration)için kullanılır, ancak kullanıcı yapılandırması için kullanılmaz.

Konak ve uygulama yapılandırması hakkında daha fazla bilgi için bkz. [.NET genel ana bilgisayar](generic-host.md).

[Azure App Service](https://azure.microsoft.com/services/app-service), **Ayarlar > yapılandırma** sayfasında **Yeni uygulama ayarı** ' nı seçin. Azure App Service uygulama ayarları şunlardır:

- Rest 'de şifrelenir ve şifreli bir kanal üzerinden iletilir.
- Ortam değişkenleri olarak sunulur.

### <a name="connection-string-prefixes"></a>Bağlantı dizesi önekleri

Yapılandırma API 'sinin dört bağlantı dizesi ortam değişkeni için özel işleme kuralları vardır. Bu bağlantı dizeleri, uygulama ortamı için Azure bağlantı dizelerini yapılandırmaya dahil edilir. Tabloda gösterilen öneklerle ortam değişkenleri, varsayılan yapılandırmayla veya uygulamasına hiçbir önek sağlanmadığında uygulamaya yüklenir `AddEnvironmentVariables` .

| Bağlantı dizesi öneki | Sağlayıcı                                                                |
|--------------------------|-------------------------------------------------------------------------|
| `CUSTOMCONNSTR_`         | Özel sağlayıcı                                                         |
| `MYSQLCONNSTR_`          | [MySQL](https://www.mysql.com)                                          |
| `SQLAZURECONNSTR_`       | [Azure SQL Veritabanı](https://azure.microsoft.com/services/sql-database) |
| `SQLCONNSTR_`            | [SQL Server](https://www.microsoft.com/sql-server)                      |

Bir ortam değişkeni keşfedildiğinde ve tabloda gösterilen dört önekle yapılandırmaya yüklendiğinde:

- Yapılandırma anahtarı, ortam değişkeni öneki kaldırılarak ve bir yapılandırma anahtarı bölümü () eklenerek oluşturulur `ConnectionStrings` .
- Veritabanı bağlantı sağlayıcısını temsil eden yeni bir yapılandırma anahtar-değer çifti oluşturulur (için `CUSTOMCONNSTR_` , belirtilen sağlayıcı olmayan).

| Ortam değişkeni anahtarı | Dönüştürülen yapılandırma anahtarı | Sağlayıcı yapılandırma girişi                                                    |
|--------------------------|-----------------------------|---------------------------------------------------------------------------------|
| `CUSTOMCONNSTR_{KEY}`    | `ConnectionStrings:{KEY}`   | Yapılandırma girişi oluşturulmamış.                                                |
| `MYSQLCONNSTR_{KEY}`     | `ConnectionStrings:{KEY}`   | Anahtar: `ConnectionStrings:{KEY}_ProviderName` :<br>Değer: `MySql.Data.MySqlClient` |
| `SQLAZURECONNSTR_{KEY}`  | `ConnectionStrings:{KEY}`   | Anahtar: `ConnectionStrings:{KEY}_ProviderName` :<br>Değer: `System.Data.SqlClient`  |
| `SQLCONNSTR_{KEY}`       | `ConnectionStrings:{KEY}`   | Anahtar: `ConnectionStrings:{KEY}_ProviderName` :<br>Değer: `System.Data.SqlClient`  |

### <a name="environment-variables-set-in-launchsettingsjson"></a>launchSettings.jsüzerinde ayarlanan ortam değişkenleri

*launchSettings.js* ' de ayarlanan ortam değişkenleri, Sistem ortamındaki kümeyi geçersiz kılar.

## <a name="command-line-configuration-provider"></a>Komut satırı yapılandırma sağlayıcısı

Varsayılan yapılandırmayı kullanarak, <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> aşağıdaki yapılandırma kaynaklarından sonra komut satırı bağımsız değişkeninden anahtar-değer çiftlerinden yapılandırma yükler:

- Ve *appsettings* *appsettings.js* . `Environment` .. *JSON* dosyaları.
- Ortamdaki uygulama gizli dizileri (gizli yönetici) `Development` .
- Ortam değişkenleri.

Varsayılan olarak, komut satırı üzerinde ayarlanan yapılandırma değerleri, diğer tüm yapılandırma sağlayıcılarıyla ayarlanan yapılandırma değerlerini geçersiz kılar.

### <a name="command-line-arguments"></a>Komut satırı bağımsız değişkenleri

Aşağıdaki komut kullanarak anahtarları ve değerleri ayarlar `=` :

```dotnetcli
dotnet run SecretKey="Secret key from command line"
```

Aşağıdaki komut kullanarak anahtarları ve değerleri ayarlar `/` :

```dotnetcli
dotnet run /SecretKey "Secret key set from forward slash"
```

Aşağıdaki komut kullanarak anahtarları ve değerleri ayarlar `--` :

```dotnetcli
dotnet run --SecretKey "Secret key set from double hyphen"
```

Anahtar değeri:

- `=`' İ izlemelidir, ya da anahtarın bir `--` `/` boşluk izleyen değeri veya öneki olmalıdır.
- Kullanılıyorsa gerekli değildir `=` . Örneğin, `SomeKey=`.

Aynı komut içinde, `=` bir boşluk kullanan anahtar-değer çiftleri ile birlikte kullanılan komut satırı bağımsız değişkeni anahtar-değer çiftlerini karıştırmayın.

## <a name="key-per-file-configuration-provider"></a>Dosya başına anahtar yapılandırma sağlayıcısı

, <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> Dizin dosyalarını yapılandırma anahtar-değer çiftleri olarak kullanır. Anahtar, dosya adıdır. Değer, dosyanın içeriğidir. Dosya başına anahtar yapılandırma sağlayıcısı Docker barındırma senaryolarında kullanılır.

Dosya başına anahtar yapılandırmasını etkinleştirmek için, <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> bir örneğinde genişletme yöntemini çağırın <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder> . `directoryPath`Dosyaların mutlak bir yol olması gerekir.

Aşırı yüklemeler belirtmeye izin ver:

- `Action<KeyPerFileConfigurationSource>`Kaynağı yapılandıran bir temsilci.
- Dizinin isteğe bağlı olup olmadığını ve dizinin yolunu belirtir.

Çift alt çizgi ( `__` ), dosya adlarında yapılandırma anahtarı sınırlayıcısı olarak kullanılır. Örneğin, dosya adı `Logging__LogLevel__System` yapılandırma anahtarını üretir `Logging:LogLevel:System` .

`ConfigureAppConfiguration`Uygulamanın yapılandırmasını belirtmek için Konağı oluştururken çağırın:

```csharp
.ConfigureAppConfiguration((_, configuration) =>
{
    var path = Path.Combine(
        Directory.GetCurrentDirectory(), "path/to/files");

    configuration.AddKeyPerFile(directoryPath: path, optional: true);
})
```

## <a name="memory-configuration-provider"></a>Bellek yapılandırma sağlayıcısı

, <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> Yapılandırma anahtar-değer çiftleri olarak bellek içi koleksiyon kullanır.

Aşağıdaki kod, yapılandırma sistemine bir bellek koleksiyonu ekler:

:::code language="csharp" source="snippets/configuration/console-memory/Program.cs" highlight="16-23":::

Yukarıdaki kodda, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> varsayılan yapılandırma sağlayıcılarından sonra bellek sağlayıcıyı ekler. Yapılandırma sağlayıcılarını sipariş eden bir örnek için bkz. [XML yapılandırma sağlayıcısı](#xml-configuration-provider).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'teki yapılandırma](configuration.md)
- [.NET genel ana bilgisayar](generic-host.md)
- [Özel yapılandırma sağlayıcısı uygulama](custom-configuration-provider.md)
