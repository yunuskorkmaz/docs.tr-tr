---
title: 'Son değişiklik: ConsoleLoggerOptions üzerinde Kullanımdan kaldırılmış Özellikler'
description: ConsoleLoggerFormat türünün ve ConsoleLoggerOptions üzerindeki bazı özelliklerin artık kullanım dışı olduğu çekirdek .NET kitaplıklarında .NET 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: bd039dfa84ae3399d7fb36f992010a9a3c9f6ddf
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548399"
---
# <a name="obsolete-properties-on-consoleloggeroptions"></a>ConsoleLoggerOptions üzerinde kullanımdan kaldırılan özellikler

<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType>Türü ve bazı özellikler <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> artık kullanılmıyor.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5,0 ' den başlayarak, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> türü ve çeşitli özellikleri <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> artık kullanılmıyor. Artık kullanılmayan özellikler şunlardır:

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

Yeni formatlara giriş ile bu özellikler artık ayrı biçimlendirme üzerinde kullanılabilir.

## <a name="reason-for-change"></a>Değişiklik nedeni

<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>Özelliği, özel bir biçimlendirici temsil etmediği bir numaralandırma türüdür.

Kalan özellikler, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> konsol günlükleri için yerleşik biçimlerin her ikisine de ayarlandı ve uygulandı. Bununla birlikte, yeni bir biçimlendirici API 'sine giriş ile, biçimlendirme için biçimlendirmelere özgü seçeneklerde temsil edilecek daha mantıklı hale gelir. Bu değişiklik, günlükçü ve günlükçü biçimleri arasında daha iyi ayrım sağlar.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

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

- ,, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes> Ve özellikleri için, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> bunun yerine yeni, veya türlerinde ilgili özelliği kullanın <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> . Örneğin, için karşılık gelen ayarı <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType> <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> .

  Önceki kod:

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

  Yeni kod:

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.ColorBehavior = LoggerColorBehavior.Disabled;
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

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- ASP.NET

### Affected APIs

- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format`

-->
