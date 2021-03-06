---
title: 'Son değişiklik: ConsoleLoggerOptions üzerinde Kullanımdan kaldırılmış Özellikler'
description: ConsoleLoggerFormat türü ve ConsoleLoggerOptions üzerindeki bazı özellikler artık kullanımdan kalkmış olan çekirdek .NET kitaplıklarında .NET 5 ile ilgili önemli değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: c6ee294f90e304cebd517bd0139c58a6c7a41e0c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257316"
---
# <a name="obsolete-properties-on-consoleloggeroptions"></a><span data-ttu-id="15be1-103">ConsoleLoggerOptions üzerinde kullanımdan kaldırılan özellikler</span><span class="sxs-lookup"><span data-stu-id="15be1-103">Obsolete properties on ConsoleLoggerOptions</span></span>

<span data-ttu-id="15be1-104"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType>Türü ve bazı özellikler <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="15be1-104">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and some properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are now obsolete.</span></span>

## <a name="change-description"></a><span data-ttu-id="15be1-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="15be1-105">Change description</span></span>

<span data-ttu-id="15be1-106">.NET 5 ' den başlayarak, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> türü ve çeşitli özellikleri <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="15be1-106">Starting in .NET 5, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and several properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are obsolete.</span></span> <span data-ttu-id="15be1-107">Artık kullanılmayan özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="15be1-107">The obsolete properties are:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

<span data-ttu-id="15be1-108">Yeni formatlara giriş ile bu özellikler artık ayrı biçimlendirme üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="15be1-108">With the introduction of new formatters, these properties are now available on the individual formatters.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="15be1-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="15be1-109">Reason for change</span></span>

<span data-ttu-id="15be1-110"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>Özelliği, özel bir biçimlendirici temsil etmediği bir numaralandırma türüdür.</span><span class="sxs-lookup"><span data-stu-id="15be1-110">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> property is an enumeration type, which cannot represent a custom formatter.</span></span>

<span data-ttu-id="15be1-111">Kalan özellikler, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> konsol günlükleri için yerleşik biçimlerin her ikisine de ayarlandı ve uygulandı.</span><span class="sxs-lookup"><span data-stu-id="15be1-111">The remaining properties were set on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> and applied to both of the built-in formats for console logs.</span></span> <span data-ttu-id="15be1-112">Bununla birlikte, yeni bir biçimlendirici API 'sine giriş ile, biçimlendirme için biçimlendirmelere özgü seçeneklerde temsil edilecek daha mantıklı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="15be1-112">However, with the introduction of a new formatter API, it makes more sense for formatting to be represented on the formatter-specific options.</span></span> <span data-ttu-id="15be1-113">Bu değişiklik, günlükçü ve günlükçü biçimleri arasında daha iyi ayrım sağlar.</span><span class="sxs-lookup"><span data-stu-id="15be1-113">This change provides better separation between the logger and logger formatters.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="15be1-114">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="15be1-114">Version introduced</span></span>

<span data-ttu-id="15be1-115">5.0</span><span class="sxs-lookup"><span data-stu-id="15be1-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="15be1-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="15be1-116">Recommended action</span></span>

- <span data-ttu-id="15be1-117"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType>Özelliği yerine yeni özelliğini kullanın <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="15be1-117">Use the new <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> property in place of the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="15be1-118">Örnek:</span><span class="sxs-lookup"><span data-stu-id="15be1-118">For example:</span></span>

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  <span data-ttu-id="15be1-119">Ve arasında birkaç fark vardır <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> :</span><span class="sxs-lookup"><span data-stu-id="15be1-119">There are several differences between <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>:</span></span>

  - <span data-ttu-id="15be1-120"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> yalnızca iki olası seçeneğe sahiptir: `Default` ve `Systemd` .</span><span class="sxs-lookup"><span data-stu-id="15be1-120"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> has only two possible options: `Default` and `Systemd`.</span></span>
  - <span data-ttu-id="15be1-121"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> büyük/küçük harfe duyarlıdır ve herhangi bir dize olabilir.</span><span class="sxs-lookup"><span data-stu-id="15be1-121"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> is case insensitive and can be any string.</span></span> <span data-ttu-id="15be1-122">Ayrılmış, yerleşik adlar `Simple` , `Systemd` ve `Json` (.NET 5 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="15be1-122">The reserved, built-in names are `Simple`, `Systemd`, and `Json` (.NET 5 and later).</span></span>
  - <span data-ttu-id="15be1-123">`"Format": "Systemd"` ile eşlenir `"FormatterName": "Systemd"` .</span><span class="sxs-lookup"><span data-stu-id="15be1-123">`"Format": "Systemd"` maps to `"FormatterName": "Systemd"`.</span></span>
  - <span data-ttu-id="15be1-124">`"Format": "Default"` ile eşlenir `"FormatterName": "Simple"` .</span><span class="sxs-lookup"><span data-stu-id="15be1-124">`"Format": "Default"` maps to `"FormatterName": "Simple"`.</span></span>

- <span data-ttu-id="15be1-125">,, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes> Ve özellikleri için, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat> <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> bunun yerine yeni, veya türlerinde ilgili özelliği kullanın <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> .</span><span class="sxs-lookup"><span data-stu-id="15be1-125">For the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat>, and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> properties, use the corresponding property on the new <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>, <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions>, or <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> types instead.</span></span> <span data-ttu-id="15be1-126">Örneğin, için karşılık gelen ayarı <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType> <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="15be1-126">For example, the corresponding setting for <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType> is <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions.ColorBehavior?displayProperty=nameWithType>.</span></span>

  <span data-ttu-id="15be1-127">Önceki kod:</span><span class="sxs-lookup"><span data-stu-id="15be1-127">Previous code:</span></span>

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

  <span data-ttu-id="15be1-128">Yeni kod:</span><span class="sxs-lookup"><span data-stu-id="15be1-128">New code:</span></span>

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.ColorBehavior = LoggerColorBehavior.Disabled;
  });
  ```

<span data-ttu-id="15be1-129">Aşağıdaki iki JSON kod parçacığı yapılandırma dosyasının nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="15be1-129">The following two JSON snippets show how the configuration file changes.</span></span> <span data-ttu-id="15be1-130">Eski yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="15be1-130">Old configuration file:</span></span>

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

<span data-ttu-id="15be1-131">Yeni yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="15be1-131">New configuration file:</span></span>

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

## <a name="affected-apis"></a><span data-ttu-id="15be1-132">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="15be1-132">Affected APIs</span></span>

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
