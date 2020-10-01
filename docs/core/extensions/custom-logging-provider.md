---
title: .NET ' te özel bir günlüğe kaydetme sağlayıcısı uygulama
description: .NET uygulamalarınızda özel bir günlüğe kaydetme sağlayıcısı uygulamayı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 09/25/2020
ms.topic: how-to
ms.openlocfilehash: 3a0af6296c2ade15ff1b75dce5a5f99bfe235ebf
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614734"
---
# <a name="implement-a-custom-logging-provider-in-net"></a>.NET ' te özel bir günlüğe kaydetme sağlayıcısı uygulama

Ortak günlük gereksinimlerine yönelik birçok [günlük sağlayıcısı](logging-providers.md) mevcuttur. <xref:Microsoft.Extensions.Logging.ILoggerProvider>Kullanılabilir sağlayıcılardan biri uygulama gereksinimlerinize uygun olmadığında bir özel uygulamanız gerekebilir. Bu makalede, konsolundaki günlükleri renklendirmeye yönelik olarak kullanılabilecek özel bir günlüğe kaydetme sağlayıcısını nasıl uygulayacağınızı öğreneceksiniz.

### <a name="sample-custom-logger-configuration"></a>Örnek özel günlükçü yapılandırması

Örnek, aşağıdaki yapılandırma türünü kullanarak günlük düzeyi ve olay KIMLIĞI başına farklı renk konsolu girdileri oluşturur:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

Yukarıdaki kod, varsayılan düzeyi olarak `Information` , rengine `Green` ve, `EventId` örtülü olarak ayarlanır `0` .

### <a name="create-the-custom-logger"></a>Özel günlükçü oluşturma

`ILogger`Uygulama kategorisi adı genellikle günlük kaynağıdır. Örneğin, günlükçü 'nin oluşturulduğu tür:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

Yukarıdaki kod:

- Kategori adı başına bir günlükçü örneği oluşturur.
- İade `logLevel == _config.LogLevel` eder `IsEnabled` , her birinin `logLevel` benzersiz bir günlükçü vardır. Günlükçüler aynı zamanda tüm daha yüksek günlük seviyeleri için de etkinleştirilmelidir:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a>Özel günlükçü sağlayıcısı

`ILoggerProvider`Nesne, günlükçü örnekleri oluşturmaktan sorumludur. Kategori başına bir günlükçü örneği oluşturmak gerekli değildir, ancak bu, NLog veya Log4net gibi bazı Günlükçüler için mantıklı olur. Bunu yaptığınızda, gerekirse kategori başına farklı günlüğe kaydetme çıkış hedeflerini de seçebilirsiniz:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

Yukarıdaki kodda, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> Kategori başına adının tek bir örneğini oluşturur `ColorConsoleLogger` ve içinde depolar [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2) .

## <a name="usage-and-registration-of-the-custom-logger"></a>Özel günlükçü kullanımı ve kaydı

Özel günlüğe kaydetme sağlayıcısını ve karşılık gelen günlükçüsü eklemek için, öğesinden bir ile öğesine ekleyin <xref:Microsoft.Extensions.Logging.ILoggerProvider> <xref:Microsoft.Extensions.Logging.ILoggingBuilder> <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType> :

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-39":::

, `ILoggingBuilder` Bir veya daha fazla `ILogger` örnek oluşturur. `ILogger`Örnekler, bilgileri günlüğe kaydetmek için Framework tarafından kullanılır.

Yukarıdaki kod için, için en az bir genişletme yöntemi sağlayın `ILoggerFactory` :

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

Bu basit uygulamayı çalıştırmak, aşağıdaki konsol penceresine benzer şekilde işlenir:

:::image type="content" source="media/color-console-logger.png" alt-text="Renk konsolu günlükçüsü örnek çıkışı":::

## <a name="see-also"></a>Ayrıca bkz.

- [.NET oturumu açılıyor](logging.md).
- [.Net 'Te günlüğe kaydetme sağlayıcıları](logging-providers.md).
- [.Net ' te yüksek performanslı günlük kaydı](high-performance-logging.md).
