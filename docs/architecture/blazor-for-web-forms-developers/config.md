---
title: Uygulama yapılandırması
description: ConfigurationManager'ı kullanmadan Blazor uygulamalarını nasıl yapılandırıştırmayı öğrenin.
author: csharpfritz
ms.author: jefritz
ms.date: 04/01/2020
ms.openlocfilehash: c780a395f72e2520af86c20c7f6618953a528ff7
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588243"
---
# <a name="app-configuration"></a>Uygulama yapılandırması

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Web Formlar'da uygulama yapılandırmasını yüklemenin birincil yolu,&mdash;sunucudaki *web.config* dosyasındaki girişler veya *web.config*tarafından başvurulan ilgili yapılandırma dosyasıdır. Uygulama ayarları, `ConfigurationManager` veri deposu bağlantı dizeleri ve uygulamaya eklenen diğer genişletilmiş yapılandırma sağlayıcılarıyla etkileşimde kalmak için statik nesneyi kullanabilirsiniz. Aşağıdaki kodda görüldüğü gibi uygulama yapılandırmasıyla etkileşimleri görmek tipiktir:

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

ASP.NET Core ve sunucu tarafı Blazor ile, uygulamanız bir Windows IIS sunucusunda barındırılırsa *web.config* dosyası hazır olabilir. Ancak, bu yapılandırma `ConfigurationManager` ile hiçbir etkileşim yoktur ve diğer kaynaklardan daha yapılandırılmış uygulama yapılandırması alabilirsiniz. Yapılandırmanın nasıl toplandığına ve bir *web.config* dosyasından yapılandırma bilgilerine nasıl erişebileceğinize bir göz atalım.

## <a name="configuration-sources"></a>Yapılandırma kaynakları

ASP.NET Core, uygulamanız için kullanmak isteyebileceğin birçok yapılandırma kaynağı olduğunu kabul eder. Çerçeve varsayılan olarak bu özelliklerden en iyi şekilde sunmaya çalışır. Yapılandırma, ASP.NET Core tarafından bu çeşitli kaynaklardan okunur ve toplanır. Aynı yapılandırma anahtarı için daha sonra yüklenen değerler önceki değerlere göre önceliklidir.

ASP.NET Core, bulut bilincine duyarlı olacak ve uygulamaların yapılandırmasını hem operatörler hem de geliştiriciler için daha kolay hale getirmek üzere tasarlanmıştır. ASP.NET Core çevreye duyarlıdır ve sizin veya `Production` `Development` çevrenizde olup olmadığını bilir. Ortam göstergesi sistem ortamı `ASPNETCORE_ENVIRONMENT` değişkeninde ayarlanır. Hiçbir değer yapılandırılmamışsa, uygulama `Production` varsayılan olarak ortamda çalışmaya başlar.

Uygulamanız, ortamın adına bağlı olarak çeşitli kaynaklardan yapılandırma tetikleyebilir ve ekleyebilir. Varsayılan olarak, yapılandırma listelenen sırada aşağıdaki kaynaklardan yüklenir:

1. *varsa appsettings.json* dosyası
1. *ayarları. {ENVIRONMENT_NAME}.json* dosyası, varsa
1. Varsa diskteki kullanıcı sırları dosyası
1. Ortam değişkenleri
1. Komut satırı bağımsız değişkenleri

## <a name="appsettingsjson-format-and-access"></a>appsettings.json formatı ve erişim

*Appsettings.json* dosyası aşağıdaki JSON gibi yapılandırılmış değerlerle hiyerarşik olabilir:

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

Önceki JSON ile sunulduğunda, yapılandırma sistemi alt değerleri düzleştirir ve tam nitelikli hiyerarşik yollarına başvurur. Bir iki`:`nokta üst üste ( ) karakter hiyerarşideki her özelliği ayırır. Örneğin, yapılandırma anahtarı `section1:key0` nesneliteral `section1` `key0` değerine erişer.

## <a name="user-secrets"></a>Kullanıcı sırları

Kullanıcı sırları şunlardır:

* Uygulama geliştirme klasörünün dışında, geliştiricinin iş istasyonundaki bir JSON dosyasında depolanan yapılandırma değerleri.
* Yalnızca `Development` çevrede çalışırken yüklenir.
* Belirli bir uygulamayla ilişkilidir.
* .NET Core CLI `user-secrets` komutu ile yönetilir.

`user-secrets` Komutu uygulayarak uygulamanızı sırların depolanması için yapılandırın:

```dotnetcli
dotnet user-secrets init
```

Önceki komut proje `UserSecretsId` dosyasına bir öğe ekler. Öğe, uygulama ile sırları ilişkilendirmek için kullanılan bir GUID içerir. Daha sonra `set` komutu ile bir sır tanımlayabilirsiniz. Örnek:

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

Önceki komut, yapılandırma `Parent:ApiKey` anahtarını bir geliştiricinin iş istasyonunda `12345`değeriyle birlikte kullanılabilir hale getirir.

Kullanıcı sırlarını oluşturma, depolama ve yönetme hakkında daha fazla bilgi [için, ASP.NET Core belgesinde uygulama sırlarınıgeliştirmede güvenli depolama](/aspnet/core/security/app-secrets) bölümüne bakın.

## <a name="environment-variables"></a>Ortam değişkenleri

Uygulama yapılandırmanıza yüklenen bir sonraki değerler kümesi, sistemin ortam değişkenleridir. Sisteminizin tüm ortam değişken ayarlarına artık yapılandırma API'si aracılığıyla erişebilirsiniz. Hiyerarşik değerler, uygulamanızın içinde okunduğunda düzleştirilmiş ve iki nokta üst üste karakterlerle ayrılır. Ancak, bazı işletim sistemleri iki nokta üst üste karakter ortamı değişken adlarını izin vermez. ASP.NET Core, bu sınırlamayı, çift alt çizgiye`__`sahip değerleri erişildiğinde bir üst üste dönüştürerek gider. Yukarıdaki `Parent:ApiKey` kullanıcı sırları bölümünden değer ortam değişkeni `Parent__ApiKey`ile geçersiz kılınabilir.

## <a name="command-line-arguments"></a>Komut satırı bağımsız değişkenleri

Yapılandırma, uygulamanız başlatıldığında komut satırı bağımsız değişkenleri olarak da sağlanabilir. Ayarlanacak yapılandırma değerinin`--`adını ve yapılandırılacak değeri belirtmek için çift çizgi () veya ileri çizgi ()`/`notunu kullanın. Sözdizimi aşağıdaki komutları benzer:

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>web.config dönüşü

Uygulamanızı IIS'de Windows'a dağıttıysanız, *web.config* dosyası uygulamanızı yönetmek için IIS'yi yapılandırmaya devam eder. Varsayılan olarak, IIS ASP.NET Çekirdek Modülüne (ANCM) bir başvuru ekler. ANCM, uygulamanızı Kestrel web sunucusu yerine barındıran yerel bir IIS modülüdür. Bu *web.config* bölümü aşağıdaki XML biçimlendirmesini benzer:

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

Uygulamaya özgü `environmentVariables` `aspNetCore` yapılandırma, öğedeki bir öğeyi iç içe alarak tanımlanabilir. Bu bölümde tanımlanan değerler ASP.NET Core uygulamasına ortam değişkenleri olarak sunulur. Ortam değişkenleri, uygulama nın başlangıç segmentinde uygun şekilde yüklenir.

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

ASP.NET Core arayüz üzerinden <xref:Microsoft.Extensions.Configuration.IConfiguration> uygulama yapılandırması sağlar. Bu yapılandırma arabirimi Blazor bileşenleriniz, Blazor sayfalarınız ve yapılandırmaya erişmesi gereken diğer ASP.NET Çekirdek yönetilen sınıf tarafından istenmelidir. ASP.NET Core çerçevesi bu arabirimi daha önce yapılandırılan çözümlenmiş yapılandırmayla otomatik olarak dolduracaktır. Blazor sayfasında veya bir bileşenin Jilet biçimlendirmesinde, nesneye `IConfiguration` `@inject` *.jilet* dosyasının üst kısmındaki bir yönergeyi şu şekilde enjekte edebilirsiniz:

```razor
@inject IConfiguration Configuration
```

Bu önceki deyim, `IConfiguration` nesneyi `Configuration` Razor şablonunun geri kalanında değişken olarak kullanılabilir hale getirir.

Tek tek yapılandırma ayarları, dizinleyici parametresi olarak aranan yapılandırma ayar hiyerarşisi belirtilerek okunabilir:

```csharp
var mySetting = Configuration["section1:key0"];
```

Önceki örnekten bölüm1 yapılandırmasını almaya benzer <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> `GetSection("section1")` bir sözdizimi ile belirli bir konumda anahtar koleksiyonu almak için yöntemi kullanarak tüm yapılandırma bölümleri getirebilirsiniz.

## <a name="strongly-typed-configuration"></a>Güçlü bir şekilde yazılan yapılandırma

Web Formları ile, <xref:System.Configuration.ConfigurationSection> tür ve ilişkili türlerden devralınan güçlü bir şekilde yazılan bir yapılandırma türü oluşturmak mümkündür. A, `ConfigurationSection` bu yapılandırma değerleri için bazı iş kurallarını ve işlemeyi yapılandırmanıza olanak sağlar.

ASP.NET Çekirdek'te, yapılandırma değerlerini alacak bir sınıf hiyerarşisi belirtebilirsiniz. Bu sınıflar:

* Bir üst sınıftan devralmanız gerekmez.
* Yakalamak `public` istediğiniz yapılandırma yapısı için özellikleri ve tür başvuruları eşleşen özellikleri içermelidir.

Önceki *appsettings.json* örneği için, değerleri yakalamak için aşağıdaki sınıfları tanımlayabilirsiniz:

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

Bu sınıf hiyerarşisi `Startup.ConfigureServices` yönteme aşağıdaki satırı ekleyerek doldurulabilir:

```csharp
services.Configure<MyConfig>(Configuration);
```

Uygulamanın geri kalanında, güçlü bir şekilde yazılan yapılandırma ayarlarını almak için sınıflara bir giriş parametresi veya jilet türü `@inject` `IOptions<MyConfig>` şablonlarında bir yönerge ekleyebilirsiniz. Özellik, `IOptions<MyConfig>.Value` yapılandırma `MyConfig` ayarlarından doldurulan değeri verir.

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

Seçenekler özelliği hakkında daha fazla [bilgi, ASP.NET Çekirdek belgesindeki Seçenekler deseninde](/aspnet/core/fundamentals/configuration/options#options-interfaces) bulunabilir.

>[!div class="step-by-step"]
>[Önceki](middleware.md)
>[Sonraki](security-authentication-authorization.md)
