---
title: Uygulama yapılandırması
description: BlazorConfigurationManager kullanılmadan uygulamaları yapılandırmayı öğrenin.
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/01/2020
ms.openlocfilehash: 6154b4f8c7a5bff42e603b12d5ef85468b80224e
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267509"
---
# <a name="app-configuration"></a>Uygulama yapılandırması

Web Forms ' de uygulama yapılandırmasını yüklemeye yönelik birincil yol, *web.config* &mdash; sunucuda veya *web.config*tarafından başvurulan ilgili bir yapılandırma dosyasında bulunanweb.configdosyasında yer alan girişlerdir. Statik nesneyi, uygulama `ConfigurationManager` ayarları, veri deposu bağlantı dizeleri ve uygulamaya eklenen diğer genişletilmiş yapılandırma sağlayıcıları ile etkileşim kurmak için kullanabilirsiniz. Aşağıdaki kodda görüldüğü gibi, uygulama yapılandırması ile etkileşimleri görmek normaldir:

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

ASP.NET Core ve sunucu tarafında Blazor , uygulamanız bir WINDOWS IIS sunucusunda barındırılıyorsa, *web.config* dosyası mevcut olabilir. Bununla birlikte, `ConfigurationManager` Bu yapılandırmayla etkileşim yoktur ve diğer kaynaklardan daha fazla yapılandırılmış uygulama yapılandırması da alabilirsiniz. Yapılandırmanın nasıl toplandığını ve bir *web.config* dosyasından yapılandırma bilgilerine nasıl erişekullanabileceğinizi göz atalım.

## <a name="configuration-sources"></a>Yapılandırma kaynakları

ASP.NET Core, uygulamanız için kullanmak isteyebileceğiniz birçok yapılandırma kaynağını tanır. Framework, varsayılan olarak bu özelliklerden en iyi şekilde bu özellikleri sunmaya çalışır. Yapılandırma ASP.NET Core tarafından bu çeşitli kaynaklardan okunurdur ve toplanır. Aynı yapılandırma anahtarı için daha sonra yüklenen değerler önceki değerlerden önceliklidir.

ASP.NET Core, bulut açısından uyumlu olacak şekilde tasarlanmıştır ve uygulamaların yapılandırılmasını hem operatörler hem de geliştiriciler için daha kolay hale getirir. ASP.NET Core, ortama duyarlı ve veya ortamınızda çalışıp çalışmadığını biliyor `Production` `Development` . Ortam göstergesi, `ASPNETCORE_ENVIRONMENT` Sistem ortamı değişkeninde ayarlanır. Hiçbir değer yapılandırılmamışsa, uygulamanın ortamda çalışması varsayılan olur `Production` .

Uygulamanız, ortam adına göre çeşitli kaynaklardan yapılandırma tetikleyip ekleyebilir. Varsayılan olarak, yapılandırma aşağıdaki kaynaklardan listelenen sırayla yüklenir:

1. Varsa dosyada *appsettings.js*
1. *appSettings. {ENVIRONMENT_NAME}. JSON* dosyası varsa
1. Varsa, diskte Kullanıcı gizli dizileri dosyası
1. Ortam değişkenleri
1. Komut satırı bağımsız değişkenleri

## <a name="appsettingsjson-format-and-access"></a>Biçim ve erişim üzerinde appsettings.js

Dosyadaki *appsettings.js* , aşağıdaki JSON gibi yapılandırılmış değerlerle hiyerarşik olabilir:

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

Önceki JSON ile sunulursa, yapılandırma sistemi alt değerleri düzleştirir ve tam hiyerarşik yollara başvurur. İki nokta ( `:` ) karakteri hiyerarşideki her özelliği ayırır. Örneğin, yapılandırma anahtarı `section1:key0` `section1` nesne değişmez `key0` değerine erişir.

## <a name="user-secrets"></a>Kullanıcı gizli dizileri

Kullanıcı gizli dizileri şunlardır:

* Geliştirici iş istasyonundaki bir JSON dosyasında depolanan yapılandırma değerleri, uygulama geliştirme klasörü dışında.
* Yalnızca ortamda çalışırken yüklenir `Development` .
* Belirli bir uygulamayla ilişkili.
* .NET Core CLI `user-secrets` komutuyla yönetiliyor.

Komutu yürüterek uygulamanızı gizli dizi depolaması için yapılandırın `user-secrets` :

```dotnetcli
dotnet user-secrets init
```

Yukarıdaki komut, `UserSecretsId` proje dosyasına bir öğesi ekler. Öğesi, gizli dizileri uygulamayla ilişkilendirmek için kullanılan bir GUID içerir. Daha sonra komutuyla bir gizli dizi tanımlayabilirsiniz `set` . Örneğin:

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

Yukarıdaki komut, `Parent:ApiKey` yapılandırma anahtarını bir geliştiricinin iş istasyonunda değeri ile kullanılabilir hale getirir `12345` .

Kullanıcı parolaları oluşturma, depolama ve yönetme hakkında daha fazla bilgi için, ASP.NET Core belgesinde [geliştirme sırasında uygulama gizli dizileri 'Nin güvenli depolama](/aspnet/core/security/app-secrets) bölümüne bakın.

## <a name="environment-variables"></a>Ortam değişkenleri

Uygulama yapılandırmanıza yüklenen sonraki değer kümesi, sistemin ortam değişkenleridir. Tüm sisteminizin ortam değişkeni ayarlarına artık Yapılandırma API 'SI aracılığıyla erişilebilir. Hiyerarşik değerler, uygulamanızın içinde okuma sırasında düz ve iki nokta üst üste karakteriyle ayrılır. Ancak bazı işletim sistemleri, iki nokta üst üste karakter ortamı değişken adlarına izin vermez. ASP.NET Core Çift alt çizgi () içeren değerleri `__` erişildiğinde iki nokta üst üste dönüştürerek bu sınırlamaya yöneliktir. `Parent:ApiKey`Yukarıdaki Kullanıcı gizli dizileri bölümünün değeri, ortam değişkeniyle geçersiz kılınabilir `Parent__ApiKey` .

## <a name="command-line-arguments"></a>Komut satırı bağımsız değişkenleri

Yapılandırma ayrıca uygulamanız başlatıldığında komut satırı bağımsız değişkenleri olarak da bulunabilir. `--` `/` Ayarlanacak yapılandırma değerinin adını ve yapılandırılacak değeri belirtmek için çift Dash () veya Forward-eğik çizgi () gösterimini kullanın. Söz dizimi aşağıdaki komutlara benzer:

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>web.config dönüşü

Uygulamanızı IIS 'de Windows 'a dağıttıysanız, *web.config* dosyası uygulamanızı yönetmek için yıne de IIS 'yi yapılandırır. IIS, varsayılan olarak ASP.NET Core modülüne (ANCM) bir başvuru ekler. ANCM, Kestrel Web sunucusu yerine uygulamanızı barındıran yerel bir IIS modülüdür. Bu *web.config* bölümü aşağıdaki XML biçimlendirmesine benzer:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

Uygulamaya özel yapılandırma, öğesinde bir öğe yuvalanarak tanımlanabilir `environmentVariables` `aspNetCore` . Bu bölümde tanımlanan değerler, ASP.NET Core uygulamasına ortam değişkenleri olarak sunulur. Ortam değişkenleri, bu uygulama başlatma segmenti için uygun şekilde yüklenir.

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a>Uygulamada yapılandırmayı okuma

ASP.NET Core arabirim aracılığıyla uygulama yapılandırması sağlar <xref:Microsoft.Extensions.Configuration.IConfiguration> . Bu yapılandırma arabirimi, Blazor bileşenlerinizde, Blazor sayfalarınızda ve yapılandırmaya erişmesi gereken diğer ASP.NET Core yönetilen bir sınıftan istenir. ASP.NET Core Framework, bu arabirimi daha önce yapılandırılan çözümlenmiş yapılandırmayla otomatik olarak doldurur. Bir Blazor sayfada veya bileşenin Razor biçimlendirmesinde, `IConfiguration` nesneyi `@inject` *. Razor* dosyasının en üstünde yer alan bir yönergeyle bu şekilde ekleyebilirsiniz:

```razor
@inject IConfiguration Configuration
```

Bu önceki ifade, `IConfiguration` nesneyi `Configuration` Razor şablonunun geri kalanı boyunca değişken olarak kullanılabilir hale getirir.

Bir dizin oluşturucu parametresi olarak aranan yapılandırma ayarı hiyerarşisi belirtilerek ayrı yapılandırma ayarları okunabilir:

```csharp
var mySetting = Configuration["section1:key0"];
```

Tüm yapılandırma bölümlerini, <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> `GetSection("section1")` önceki örnekteki Section1 yapılandırmasını almak için öğesine benzer bir sözdizimi ile, belirli bir konumdaki anahtarların bir koleksiyonunu almak için yöntemini kullanarak getirebilirsiniz.

## <a name="strongly-typed-configuration"></a>Türü kesin belirlenmiş yapılandırma

Web Forms, <xref:System.Configuration.ConfigurationSection> türü ve ilişkili türlerden devralınan kesin türü belirtilmiş bir yapılandırma türü oluşturmak mümkün. `ConfigurationSection`Bu yapılandırma değerleri için bazı iş kurallarını ve işlemeyi yapılandırmanıza izin verilir.

ASP.NET Core, yapılandırma değerlerini alacak bir sınıf hiyerarşisi belirtebilirsiniz. Bu sınıflar:

* Üst sınıftan devralması gerekmez.
* `public`, Yakalamak istediğiniz yapılandırma yapısına yönelik özellikler ve tür başvurularıyla eşleşen özellikleri içermelidir.

Örnek yukarıdaki *appsettings.js* , değerleri yakalamak için aşağıdaki sınıfları tanımlayabilirsiniz:

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

Aşağıdaki satırı yöntemine ekleyerek bu sınıf hiyerarşisi doldurulabilir `Startup.ConfigureServices` :

```csharp
services.Configure<MyConfig>(Configuration);
```

Uygulamanın geri kalanında, `@inject` `IOptions<MyConfig>` kesin olarak belirlenmiş yapılandırma ayarlarını almak için sınıflardaki bir giriş parametresini veya Razor şablonlarındaki bir yönergeyi ekleyebilirsiniz. `IOptions<MyConfig>.Value`Özelliği, `MyConfig` yapılandırma ayarlarından doldurulmuş değeri verir.

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

Seçenekler özelliği hakkında daha fazla bilgi [ASP.NET Core belge ' deki Seçenekler modelinde](/aspnet/core/fundamentals/configuration/options#options-interfaces) bulunabilir.

>[!div class="step-by-step"]
>[Önceki](middleware.md) 
> [Sonraki](security-authentication-authorization.md)
