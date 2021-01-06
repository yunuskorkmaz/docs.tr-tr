---
title: Konsol günlük biçimlendirme
description: Kullanılabilir konsol günlük biçimlendirmesini kullanmayı veya .NET uygulamalarınız için özel günlük biçimlendirmesini uygulamayı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 12/17/2020
ms.openlocfilehash: 0ec8fc2018febe4273aa646d1682be197933f925
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700821"
---
# <a name="console-log-formatting"></a>Konsol günlük biçimlendirme

.NET 5 ' te, ad alanındaki konsol günlüklerine özel biçimlendirme desteği eklenmiştir `Microsoft.Extensions.Logging.Console` . Önceden tanımlanmış üç biçimlendirme seçeneği mevcuttur: [`Simple`](#simple) , [`Systemd`](#systemd) , ve [`Json`](#json) .

> [!IMPORTANT]
> Daha önce, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat> istenen günlük biçimini seçmeye izin verilen numaralandırma, ya da `Default` olarak da bilinen tek satır olan insanlar okunabilir `Systemd` . Ancak **bunlar özelleştirilemez ve** artık kullanım dışıdır.

Bu makalede, konsol günlüğü formatlayıcıları hakkında bilgi edineceksiniz. Örnek kaynak kodu şunları gösterir:

- Yeni bir biçimlendirici Kaydet
- Kullanılacak kayıtlı bir biçimlendirici seçin
  - Kod ya da [yapılandırma](configuration.md) üzerinden
- Özel biçimlendirici uygulama
  - Yapılandırmayı Güncelleştirme aracılığıyla <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>
  - Özel renk biçimlendirmesini etkinleştir

## <a name="register-formatter"></a>Biçimlendirici Kaydet

[ `Console` Günlüğe kaydetme sağlayıcısında](logging-providers.md#console) birkaç önceden tanımlı biçim vardır ve kendi özel biçimlendiricinizi yazma özelliğini ortaya koyar. Kullanılabilir formatlayıcıları kaydetmek için ilgili `Add{Type}Console` genişletme yöntemini kullanın:

| Kullanılabilir türler | Kayıt türü yöntemi |
|--|--|
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddJsonConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSimpleConsole%2A?displayProperty=nameWithType> |
| <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType> | <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddSystemdConsole%2A?displayProperty=nameWithType> |

### <a name="simple"></a>Basit

`Simple`Konsol biçimlendirici 'yı kullanmak için şunu ile kaydedin `AddSimpleConsole` :

:::code language="csharp" source="snippets/logging/console-formatter-simple/Program.cs" highlight="11-16":::

Önceki örnek kaynak kodunda, <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType> biçimlendirici kaydettirildi. Yalnızca her bir günlük iletisindeki zaman ve günlük düzeyi gibi bilgileri kaydırabilme olanağı sağlar, ancak Ayrıca iletilerin ANSI renk ekleme ve girintileme için de izin verir.

### <a name="systemd"></a>Systemd

<xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>Konsol günlükçüsü:

- "Syslog" günlük düzeyi biçimini ve önem derecelerine kullanır
- İletileri renklerle **biçimlendirmez**
- İletileri her zaman tek bir satırda günlüğe kaydeder

Bu, genellikle konsol günlüğünü kullanan kapsayıcılar için yararlıdır `Systemd` . .NET 5 ile `Simple` konsol günlükçüsü, tek bir satırda oturum açan ve ayrıca daha önceki bir örnekte gösterildiği gibi renklerin devre dışı bırakılmasına izin veren bir Compact sürümü de sağlar.

:::code language="csharp" source="snippets/logging/console-formatter-systemd/Program.cs" highlight="11-15":::

### <a name="json"></a>Json

Günlükleri JSON biçiminde yazmak için `Json` konsol biçimlendiricisi kullanılır. Örnek kaynak kodu bir ASP.NET Core uygulamasının nasıl kaydedebileceğini gösterir. Şablonu kullanarak `webapp` , [DotNet yeni](../tools/dotnet-new.md) komutuyla yeni bir ASP.NET Core uygulaması oluşturun:

```dotnetcli
dotnet new webapp -o Console.ExampleFormatters.Json
```

Uygulamayı çalıştırırken, şablon kodunu kullanarak aşağıdaki varsayılan günlük biçimini alırsınız:

```
info: Microsoft.Hosting.Lifetime[0]
      Now listening on: https://localhost:5001
```

Varsayılan olarak `Simple` konsol günlük biçimlendiricisi varsayılan yapılandırmayla seçilir. Bunu `AddJsonConsole` *program.cs* içinde çağırarak değiştirirsiniz:

:::code language="csharp" source="snippets/logging/console-formatter-json/Program.cs" highlight="17-26":::

Uygulamayı bir daha çalıştırın, yukarıdaki değişiklik ile günlük iletisi artık JSON olarak biçimlendirilir:

:::code language="json" source="snippets/logging/console-formatter-json/example-output.json":::

> [!TIP]
> `Json`Konsol biçimlendiricisi, varsayılan olarak her iletiyi tek bir satırda günlüğe kaydeder. Biçimlendirici yapılandırılırken daha okunaklı olması için, <xref:System.Text.Json.JsonWriterOptions.Indented?displayProperty=nameWithType> olarak ayarlayın `true` .

## <a name="set-formatter-with-configuration"></a>Biçimlendirici yapılandırma ile ayarla

Önceki örneklerde, bir biçimlendirici programlı bir şekilde nasıl kaydedileceği gösterilmektedir. Alternatif olarak, bu [yapılandırma](configuration.md)ile yapılabilir. Önceki Web uygulaması örnek kaynak kodunu göz önünde bulundurun, Program.cs dosyasında çağırmak yerine dosyayı *appsettings.js* güncelleştirirseniz `ConfigureLogging` aynı sonucu elde edebilirsiniz  . Güncelleştirilmiş `appsettings.json` Dosya, biçimlendirici şu şekilde yapılandırılır:

:::code language="json" source="snippets/logging/console-formatter-json/appsettings.json" highlight="14-23":::

Ayarlanması gereken iki anahtar değeri `"FormatterName"` ve ' dir `"FormatterOptions"` . İçin değer kümesine sahip bir biçimlendirici `"FormatterName"` zaten kaydedilmişse, bu biçimlendirici seçilir ve özellikleri düğüm içinde bir anahtar olarak sağlandıkları sürece yapılandırılabilir `"FormatterOptions"` . Önceden tanımlanmış biçimlendirici adları şu şekilde ayrılmıştır <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames> :

- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Json?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Simple?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterNames.Systemd?displayProperty=nameWithType>

## <a name="implement-a-custom-formatter"></a>Özel biçimlendirici uygulama

Özel bir biçimlendirici uygulamak için şunları yapmanız gerekir:

- İçin bir alt sınıf oluşturun <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatter> , bu özel biçimlendiricisi temsil eder
- Özel biçimlendirici hesabınızı kaydetme
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsole%2A?displayProperty=nameWithType>
  - <xref:Microsoft.Extensions.Logging.ConsoleLoggerExtensions.AddConsoleFormatter%60%602(Microsoft.Extensions.Logging.ILoggingBuilder,System.Action{%60%601})?displayProperty=nameWithType>

Bunu sizin için işlemek üzere bir genişletme yöntemi oluşturun:

:::code language="csharp" source="snippets/logging/console-formatter-custom/ConsoleLoggerExtensions.cs" highlight="11-12":::

, `CustomOptions` Aşağıdaki gibi tanımlanır:

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomOptions.cs":::

Yukarıdaki kodda, seçenekleri öğesinin bir alt sınıfıdır <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> .

`AddConsoleFormatter`API:

- Bir alt sınıfını kaydeder `ConsoleFormatter`
- Tanıtıcı yapılandırma:
  - , [Seçenekler düzenine](options.md)ve [ıoptionsmonitor](xref:Microsoft.Extensions.Options.IOptionsMonitor%601) arabirimine göre güncelleştirmeleri eşleştirmek için bir değişiklik belirteci kullanır

:::code language="csharp" source="snippets/logging/console-formatter-custom/Program.cs" highlight="11-12":::

Bir `CustomerFormatter` alt sınıfı tanımlayın `ConsoleFormatter` :

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomFormatter.cs" highlight="24-45":::

Yukarıdaki `CustomFormatter.Write<TState>` API, her günlük iletisi etrafında hangi metnin sarmalanacağını belirler. Bir standart `ConsoleFormatter` , en az kapsam, zaman damgası ve önem düzeyi olan günlüklerin etrafında kaydırabilmelidir. Ayrıca, günlük iletilerinde ANSI renklerini kodlayabilir ve istenen girintileri de sağlayabilirsiniz. Uygulamasının `CustomFormatter.Write<TState>` Bu özellikleri yoktur.

Biçimlendirmeyi daha fazla özelleştirme konusunda daha fazla bilgi için bkz. ad alanındaki mevcut uygulamalar `Microsoft.Extensions.Logging.Console` :

- [Simpleconsoleformatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SimpleConsoleFormatter.cs).
- [SystemdConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/SystemdConsoleFormatter.cs)
- [JsonConsoleFormatter](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.Extensions.Logging.Console/src/JsonConsoleFormatter.cs)

## <a name="implement-custom-color-formatting"></a>Özel renk biçimlendirmesi Uygula

Özel günlük biçimlendiricinizdeki renk yeteneklerini doğru bir şekilde etkinleştirmek için, ' yi, <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> günlüklerde renkleri etkinleştirmek faydalı olabilecek bir özelliğe sahip olacak şekilde genişletebilirsiniz.

Şu `CustomColorOptions` kaynaktan türetilen bir oluştur `SimpleConsoleFormatterOptions` :

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorOptions.cs" highlight="5":::

Daha sonra, `TextWriterExtensions` biçimlendirilen günlük ILETILERINDE ANSI kodlu renkleri kolay bir şekilde katıştırmaya izin veren bir sınıfta bazı uzantı yöntemlerini yazın:

:::code language="csharp" source="snippets/logging/console-formatter-custom/TextWriterExtensions.cs":::

Özel renkleri uygulamayı işleyen özel bir renk biçimlendiricisi aşağıdaki gibi tanımlanabilir:

:::code language="csharp" source="snippets/logging/console-formatter-custom/CustomColorFormatter.cs" highlight="15-18,52-65":::

Uygulamayı çalıştırdığınızda Günlükler olduğunda `CustomPrefix` iletiyi yeşil renkte gösterir `FormatterOptions.ColorBehavior` `Enabled` .

> [!NOTE]
> Ne zaman, <xref:Microsoft.Extensions.Logging.Console.LoggerColorBehavior> `Disabled` günlük iletileri, günlük iletileri IÇINDEKI gömülü ANSI renk kodlarını _yorumlamaz_ . Bunun yerine, ham iletiyi alırlar. Örneğin, aşağıdakileri göz önünde bulundurun:
>
> ```csharp
> logger.LogInformation("Random log \x1B[42mwith green background\x1B[49m message");
> ```
>
> Bu, tam dizeyi çıktılar ve _renklendirilmez_ .
>
> ```output
> Random log \x1B[42mwith green background\x1B[49m message
> ```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET oturumu açma](logging.md)
- [.NET ' te özel bir günlüğe kaydetme sağlayıcısı uygulama](custom-logging-provider.md)
- [.NET 'te yüksek performanslı günlüğe kaydetme](high-performance-logging.md)
