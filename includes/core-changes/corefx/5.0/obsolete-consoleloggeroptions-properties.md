---
ms.openlocfilehash: e92fe8364800b1775f0acc31d67aef66a42d0b95
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465898"
---
### <a name="obsolete-properties-on-consoleloggeroptions"></a>ConsoleLoggerOptions üzerinde kullanımdan kalkmış Özellikler

<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType>Türü ve bazı özellikler <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> artık kullanılmıyor.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET 5,0 ' den başlayarak, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> türü ve çeşitli özellikleri <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> artık kullanılmıyor. Artık kullanılmayan özellikler şunlardır:

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

Yeni formatlara giriş ile bu özellikler artık ayrı biçimlendirme üzerinde kullanılabilir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>Özelliği, özel bir biçimlendirici temsil etmediği bir numaralandırma türüdür.

Kalan özellikler, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> konsol günlükleri için yerleşik biçimlerin her ikisine de ayarlandı ve uygulandı. Bununla birlikte, yeni bir biçimlendirici API 'sine giriş ile, biçimlendirme için biçimlendirmelere özgü seçeneklerde temsil edilecek daha mantıklı hale gelir. Bu değişiklik, günlükçü ve günlükçü biçimleri arasında daha iyi ayrım sağlar.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 8

#### <a name="recommended-action"></a>Önerilen eylem

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType>Özelliği yerine yeni özelliğini kullanın <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> . Örneğin:

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  Ve arasında birkaç fark vardır <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> :

  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> yalnızca iki olası seçeneğe sahiptir: `Default` ve `Systemd` .
  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> büyük/küçük harfe duyarlıdır ve herhangi bir dize olabilir. Ayrılmış, yerleşik adlar `Simple` , `Systemd` ve `Json` (.NET 5,0 ve üzeri).
  - `"Format": "Systemd"` ile eşlenir `"FormatterName": "Systemd"` .
  - `"Format": "Default"` ile eşlenir `"FormatterName": "Simple"` .

- ,, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes> Ve özellikleri için, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> bunun yerine yeni, veya türlerinde ilgili özelliği kullanın <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> . Örneğin:

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

Aşağıdaki iki JSON kod parçacığı yapılandırma dosyasının nasıl değiştirileceğini gösterir. Eski yapılandırma dosyası:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "Format": "Systemd",
      "IncludeScopes": true,
      "TimestampFormat": "HH:mm:ss",
      "UseUtcTimestamp": true
    }
  },
  "AllowedHosts": "*"
}
```

Yeni yapılandırma dosyası:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "FormatterName": "Systemd",
      "FormatterOptions": {
        "IncludeScopes": true,
        "TimestampFormat": "HH:mm:ss",
        "UseUtcTimestamp": true
      }
    }
  },
  "AllowedHosts": "*"
}
```

#### <a name="category"></a>Kategori

- Core .NET kitaplıkları
- ASP.NET

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=fullName>

<!--

#### Affected APIs

- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format`

-->
