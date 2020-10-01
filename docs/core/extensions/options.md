---
title: .NET 'teki seçenek kalıbı
author: IEvangelist
description: .NET uygulamalarında ilgili ayarların gruplarını temsil etmek için seçenekler deseninin nasıl kullanılacağını öğrenin.
ms.author: dapine
ms.date: 09/30/2020
ms.openlocfilehash: 5c59a14223ec7c35456e1ea84d3f976e236f45dd
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614752"
---
# <a name="options-pattern-in-net"></a>.NET 'teki seçenek kalıbı

Seçenekler stili, ilişkili ayarlar gruplarına kesin olarak yazılmış erişim sağlamak için sınıfları kullanır. [Yapılandırma ayarları](configuration.md) senaryo tarafından ayrı sınıflara ayrılmışsa, uygulama iki önemli yazılım mühendisliği ilkelerine uyar:

- Yapılandırma ayarlarına bağlı olan [arabirim ayırma ilkesi (ISS) veya kapsülleme](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): senaryolar (sınıflar) yalnızca kullandıkları yapılandırma ayarlarına bağlıdır.
- [Kaygıları ayrımı](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): uygulamanın farklı bölümlerinin ayarları birbirlerine bağımlı değil veya birbirine bağlı değil.

Seçenekler Ayrıca yapılandırma verilerini doğrulamaya yönelik bir mekanizma sağlar. Daha fazla bilgi için [Seçenekler doğrulama](#options-validation) bölümüne bakın.

## <a name="bind-hierarchical-configuration"></a>Hiyerarşik yapılandırmayı bağlama

İlgili yapılandırma değerlerini okumak için tercih edilen yol, Seçenekler modelini kullanmaktır. Örneğin, aşağıdaki yapılandırma değerlerini okumak için:

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

Aşağıdaki sınıfı oluşturun `TransientFaultHandlingOptions` :

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-6":::

Seçenekler sınıfı:

* Ortak parametresiz bir oluşturucuya sahip olmayan Özet olmamalıdır
* Bağlanacak genel okuma-yazma özelliklerini içerir (alanlar bağlı ***değildir*** )

Aşağıdaki kod:

* Sınıfı bölümüne bağlamak için [Configurationciltçi. Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) ' i çağırır `TransientFaultHandlingOptions` `"TransientFaultHandlingOptions"` .
* Yapılandırma verilerini görüntüler.

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="25-32":::

Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.

[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) belirtilen türü bağlar ve döndürür. `ConfigurationBinder.Get<T>` , kullanmaktan daha uygun olabilir `ConfigurationBinder.Bind` . Aşağıdaki kod, sınıfıyla birlikte nasıl kullanılacağını gösterir `ConfigurationBinder.Get<T>` `TransientFaultHandlingOptions` :

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
        .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.

Seçenekler deseninin kullanılmasına yönelik alternatif bir yaklaşım, `"TransientFaultHandlingOptions"` bölümü bağlamak ve [bağımlılık ekleme hizmeti kapsayıcısına](dependency-injection.md)eklemektir. Aşağıdaki kodda, `TransientFaultHandlingOptions` ile hizmet kapsayıcısına eklenir <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> ve yapılandırmaya bağlanır:

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> `key`Parametresi, arama yapılacak yapılandırma bölümünün adıdır. Bunu temsil eden türün adıyla *eşleşmesi gerekmez.* Örneğin, adlı bir bölüm olabilir `"FaultHandling"` ve sınıfı tarafından temsil edilebilir `TransientFaultHandlingOptions` . Bu örnekte, `"FaultHandling"` <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> bunun yerine işlevine geçiş yapabilirsiniz. `nameof`İşleci, adlandırılmış bölüm öğesine karşılık gelen türle eşleşen bir kolaylık olarak kullanılır.

Önceki kodu kullanarak, aşağıdaki kod konum seçeneklerini okur:

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan ***değişiklikler okunamaz.*** Uygulama başladıktan sonra değişiklikleri okumak için [ıoptionssnapshot](#use-ioptionssnapshot-to-read-updated-data)kullanın.

## <a name="options-interfaces"></a>Seçenekler arabirimleri

<xref:Microsoft.Extensions.Options.IOptions%601>:

- Şunları ***desteklemez:***
  - Uygulama başladıktan sonra yapılandırma verilerinin okunması.
  - [Adlandırılmış seçenekler](#named-options-support-using-iconfigurenamedoptions)
- [Tek](dependency-injection.md#singleton) bir olarak kaydedilir ve herhangi bir [hizmet ömrüne](dependency-injection.md#service-lifetimes)eklenebilir.

<xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:

- , [Kapsamlı veya geçici yaşam süreleri](dependency-injection.md#service-lifetimes)içinde her ekleme çözünürlüğünde seçeneklerin yeniden hesaplanması gereken senaryolarda yararlıdır. Daha fazla bilgi için bkz. [güncelleştirilmiş verileri okumak Için ıoptionssnapshot kullanma](#use-ioptionssnapshot-to-read-updated-data).
- [Kapsamlı](dependency-injection.md#scoped) olarak kaydedilir ve bu nedenle tek bir hizmete eklenemez.
- [Adlandırılmış seçenekleri](#named-options-support-using-iconfigurenamedoptions) destekler

<xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:

- , Seçenekleri almak ve örnekler için seçenek bildirimlerini yönetmek için kullanılır `TOptions` .
- [Tek](dependency-injection.md#singleton) bir olarak kaydedilir ve herhangi bir [hizmet ömrüne](dependency-injection.md#service-lifetimes)eklenebilir.
- Desteklememektedir
  - Değişiklik bildirimleri
  - [Adlandırılmış seçenekler](#named-options-support-using-iconfigurenamedoptions)
  - [Yeniden yüklenebilir yapılandırma](#use-ioptionssnapshot-to-read-updated-data)
  - Seçmeli seçenekler geçersiz kılma ( <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> )
  
<xref:Microsoft.Extensions.Options.IOptionsFactory%601> yeni seçenek örnekleri oluşturmaktan sorumludur. Tek bir metodu vardır <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> . Varsayılan uygulama tüm kayıtlı <xref:Microsoft.Extensions.Options.IConfigureOptions%601> ve <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> sonrasında tüm yapılandırmaları çalıştırır ve sonrasında yapılandırma sonrası. Ve arasında ayrım yapar ve <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> <xref:Microsoft.Extensions.Options.IConfigureOptions%601> yalnızca uygun arabirimi çağırır.

<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> , <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> örnekleri önbelleğe almak için tarafından kullanılır `TOptions` . , <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> Değer yeniden hesaplanabilmesi için izleyici içindeki seçenek örneklerini geçersiz kılar ( <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A> ). Değerler ile el ile tanıtılamaz <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A> . <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A>Yöntemi, tüm adlandırılmış örneklerin isteğe bağlı olarak yeniden oluşturulması gerektiğinde kullanılır.

## <a name="use-ioptionssnapshot-to-read-updated-data"></a>Güncelleştirilmiş verileri okumak için ıoptionssnapshot kullanın

kullandığınızda <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> Seçenekler erişildiğinde istek başına bir kez hesaplanır ve isteğin ömrü boyunca önbelleğe alınır. Güncelleştirilmiş yapılandırma değerlerini okumayı destekleyen yapılandırma sağlayıcıları kullanılırken, yapılandırma değişiklikleri uygulama başladıktan sonra okundu.

Ve arasındaki fark `IOptionsMonitor` `IOptionsSnapshot` şudur:

- `IOptionsMonitor` , özellikle tek bağımlılıklarda yararlı olan herhangi bir zamanda geçerli seçenek değerlerini alan bir [tek hizmettir](dependency-injection.md#singleton) .
- `IOptionsSnapshot` kapsamlı bir [hizmettir](dependency-injection.md#scoped) ve nesnenin oluşturulduğu sırada seçeneklerin anlık görüntüsünü sağlar `IOptionsSnapshot<T>` . Seçenekler anlık görüntüleri geçici ve kapsamlı bağımlılıklarla kullanılmak üzere tasarlanmıştır.

Aşağıdaki kod kullanır <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> .

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

Aşağıdaki kod, ' a bağlanan bir yapılandırma örneği kaydeder `TransientFaultHandlingOptions` :

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.

## <a name="ioptionsmonitor"></a>Ioptionsmonitor

Aşağıdaki kod, ' a bağlanan bir yapılandırma örneği kaydeder `TransientFaultHandlingOptions` .

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

Aşağıdaki örnek şunu kullanır <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> :

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.

## <a name="named-options-support-using-iconfigurenamedoptions"></a>IController Enamedooptıons kullanarak adlandırılmış seçenekler desteği

Adlandırılmış seçenekler:

- Aynı özelliklere birden çok yapılandırma bölümü bağlandığı zaman faydalıdır.
- Büyük/küçük harfe duyarlıdır.

Dosyasında aşağıdaki *appsettings.js* göz önünde bulundurun:

```json
{
  "Features": {
    "Personalize": {
      "Enabled": true,
      "ApiKey": "aGEgaGEgeW91IHRob3VnaHQgdGhhdCB3YXMgcmVhbGx5IHNvbWV0aGluZw=="
    },
    "WeatherStation": {
      "Enabled": true,
      "ApiKey": "QXJlIHlvdSBhdHRlbXB0aW5nIHRvIGhhY2sgdXM/"
    }
  }
}
```

Ve bağlamak için iki sınıf oluşturmak yerine `Features:Personalize` `Features:WeatherStation` , her bölüm için aşağıdaki sınıf kullanılır:

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

Aşağıdaki kod, adlandırılmış seçenekleri yapılandırır:

```csharp
ConfigureServices(services =>
{
    services.Configure<Features>(
        Features.Personalize,
        Configuration.GetSection("Features:Personalize"));

    services.Configure<Features>(
        Features.WeatherStation,
        Configuration.GetSection("Features:WeatherStation"));
});
```

Aşağıdaki kod, adlandırılmış seçenekleri gösterir:

```csharp
public class Service
{
    private readonly Features _personalizeFeature;
    private readonly Features _weatherStationFeature;

    public Service(IOptionsSnapshot<Features> namedOptionsAccessor)
    {
        _personalizeFeature = namedOptionsAccessor.Get(Features.Personalize);
        _weatherStationFeature = namedOptionsAccessor.Get(Features.WeatherStation);
    }
}
```

Tüm seçenekler adlandırılmış örneklerdir. <xref:Microsoft.Extensions.Options.IConfigureOptions%601> örnekler, örneği hedefleme olarak değerlendirilir `Options.DefaultName` `string.Empty` . <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> Ayrıca uygular <xref:Microsoft.Extensions.Options.IConfigureOptions%601> . Varsayılan uygulamasının, her birini <xref:Microsoft.Extensions.Options.IOptionsFactory%601> uygun şekilde kullanma mantığı vardır. `null`Adlandırılmış seçenek, belirli bir adlandırılmış örnek yerine tüm adlandırılmış örnekleri hedeflemek için kullanılır. <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> ve <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> Bu kuralı kullanın.

## <a name="optionsbuilder-api"></a>Seçenekno Oluşturucu API 'SI

<xref:Microsoft.Extensions.Options.OptionsBuilder%601> örnekleri yapılandırmak için kullanılır `TOptions` . `OptionsBuilder` adlandırılmış seçenekleri, sonraki çağrıların tümünde olmak yerine ilk çağrının tek bir parametresi olacak şekilde oluşturmayı kolaylaştırır `AddOptions<TOptions>(string optionsName)` . Seçenekler doğrulaması ve `ConfigureOptions` hizmet bağımlılıklarını kabul eden aşırı yüklemeler yalnızca aracılığıyla kullanılabilir `OptionsBuilder` .

`OptionsBuilder`[Seçenekler doğrulama](#options-validation) bölümünde kullanılır.

## <a name="use-di-services-to-configure-options"></a>Ayarları yapılandırmak için dı hizmetlerini kullanma

Seçenekleri iki şekilde yapılandırırken, hizmetlere bağımlılık ekleme işleminden erişilebilir:

- [Options Builder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601)'da [yapılandırmak](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) için bir yapılandırma temsilcisi geçirin. `OptionsBuilder<TOptions>` , seçenekleri yapılandırmak için en fazla beş hizmet kullanılmasına izin veren [yapılandırma](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) yüklerini sağlar:

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- Veya uygulayan bir tür oluşturun <xref:Microsoft.Extensions.Options.IConfigureOptions%601> <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> ve türü bir hizmet olarak kaydedin.

Bir hizmetin oluşturulması daha karmaşık olduğundan, [yapılandırmak](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A)için bir yapılandırma temsilcisinin geçirilmesini öneririz. Bir tür oluşturmak,, [Yapılandır](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A)çağrılırken çerçevenin yaptığı işe eşdeğerdir. [Yapılandırma](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) çağrısı <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> , belirtilen genel hizmet türlerini kabul eden bir oluşturucuya sahip olan geçici bir genel kayıt kaydeder.

## <a name="options-validation"></a>Seçenekler doğrulaması

Seçenekler doğrulaması seçenek değerlerinin doğrulanmasını sağlar.

Dosyasında aşağıdaki *appsettings.js* göz önünde bulundurun:

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

Aşağıdaki sınıf `"Settings"` yapılandırma bölümüne bağlanır ve birkaç `DataAnnotations` kural uygular:

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

Aşağıdaki kod:

- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A>Sınıfına bağlanan bir [seçenekoluşturucu Oluşturucu \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601) almak için çağırır `SettingsOptions` .
- <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A>Kullanarak doğrulamayı etkinleştirmek için çağırır `DataAnnotations` .

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

`ValidateDataAnnotations`Genişletme yöntemi, [Microsoft. Extensions. Options. dataaçıklamalarda](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet paketinde tanımlanmıştır.

Aşağıdaki kod yapılandırma değerlerini veya doğrulama hatalarını görüntüler:

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

Aşağıdaki kod, bir temsilci kullanarak daha karmaşık bir doğrulama kuralı uygular:

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations()
    .Validate(config =>
    {
        if (config.Scale != 0)
        {
            return config.VerbosityLevel > config.Scale;
        }

        return true;
    }, "VerbosityLevel must be > than Scale.");
```

### <a name="ivalidateoptions-for-complex-validation"></a>Karmaşık doğrulama için ıvalidateoptions

Aşağıdaki sınıf şunları uygular <xref:Microsoft.Extensions.Options.IValidateOptions%601> :

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

`IValidateOptions` doğrulama kodunu bir sınıfa taşımaya izin vermez.

Önceki kodu kullanarak, doğrulama ' de `ConfigureServices` aşağıdaki kodla etkinleştirilir:

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a>Yapılandırma sonrası seçenekler

Yapılandırma sonrası ' i ayarlayın <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> . Yapılandırma sonrası tüm <xref:Microsoft.Extensions.Options.IConfigureOptions%601> yapılandırma oluştuktan sonra çalışır ve yapılandırmayı geçersiz kılmanız gerektiğinde senaryolarda yararlı olabilir:

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> , adlandırılmış seçenekleri yapılandırmak için kullanılabilir:

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A>Tüm yapılandırma örneklerini yapılandırmak için kullanın:

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'teki yapılandırma](configuration.md)
