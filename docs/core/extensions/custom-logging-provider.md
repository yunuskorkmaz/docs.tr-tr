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
# <a name="implement-a-custom-logging-provider-in-net"></a><span data-ttu-id="c354d-103">.NET ' te özel bir günlüğe kaydetme sağlayıcısı uygulama</span><span class="sxs-lookup"><span data-stu-id="c354d-103">Implement a custom logging provider in .NET</span></span>

<span data-ttu-id="c354d-104">Ortak günlük gereksinimlerine yönelik birçok [günlük sağlayıcısı](logging-providers.md) mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c354d-104">There are many [logging providers](logging-providers.md) available for common logging needs.</span></span> <span data-ttu-id="c354d-105"><xref:Microsoft.Extensions.Logging.ILoggerProvider>Kullanılabilir sağlayıcılardan biri uygulama gereksinimlerinize uygun olmadığında bir özel uygulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c354d-105">You may need to implement a custom <xref:Microsoft.Extensions.Logging.ILoggerProvider> when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="c354d-106">Bu makalede, konsolundaki günlükleri renklendirmeye yönelik olarak kullanılabilecek özel bir günlüğe kaydetme sağlayıcısını nasıl uygulayacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c354d-106">In this article, you'll learn how to implement a custom logging provider that can be used to colorize logs in the console.</span></span>

### <a name="sample-custom-logger-configuration"></a><span data-ttu-id="c354d-107">Örnek özel günlükçü yapılandırması</span><span class="sxs-lookup"><span data-stu-id="c354d-107">Sample custom logger configuration</span></span>

<span data-ttu-id="c354d-108">Örnek, aşağıdaki yapılandırma türünü kullanarak günlük düzeyi ve olay KIMLIĞI başına farklı renk konsolu girdileri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c354d-108">The sample creates different color console entries per log level and event ID using the following configuration type:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

<span data-ttu-id="c354d-109">Yukarıdaki kod, varsayılan düzeyi olarak `Information` , rengine `Green` ve, `EventId` örtülü olarak ayarlanır `0` .</span><span class="sxs-lookup"><span data-stu-id="c354d-109">The preceding code sets the default level to `Information`, the color to `Green`, and the `EventId` is implicitly `0`.</span></span>

### <a name="create-the-custom-logger"></a><span data-ttu-id="c354d-110">Özel günlükçü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c354d-110">Create the custom logger</span></span>

<span data-ttu-id="c354d-111">`ILogger`Uygulama kategorisi adı genellikle günlük kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="c354d-111">The `ILogger` implementation category name is typically the logging source.</span></span> <span data-ttu-id="c354d-112">Örneğin, günlükçü 'nin oluşturulduğu tür:</span><span class="sxs-lookup"><span data-stu-id="c354d-112">For example, the type where the logger is created:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

<span data-ttu-id="c354d-113">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="c354d-113">The preceding code:</span></span>

- <span data-ttu-id="c354d-114">Kategori adı başına bir günlükçü örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c354d-114">Creates a logger instance per category name.</span></span>
- <span data-ttu-id="c354d-115">İade `logLevel == _config.LogLevel` eder `IsEnabled` , her birinin `logLevel` benzersiz bir günlükçü vardır.</span><span class="sxs-lookup"><span data-stu-id="c354d-115">Checks `logLevel == _config.LogLevel` in `IsEnabled`, so each `logLevel` has a unique logger.</span></span> <span data-ttu-id="c354d-116">Günlükçüler aynı zamanda tüm daha yüksek günlük seviyeleri için de etkinleştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="c354d-116">Loggers should also be enabled for all higher log levels:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a><span data-ttu-id="c354d-117">Özel günlükçü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="c354d-117">Custom logger provider</span></span>

<span data-ttu-id="c354d-118">`ILoggerProvider`Nesne, günlükçü örnekleri oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="c354d-118">The `ILoggerProvider` object is responsible for creating logger instances.</span></span> <span data-ttu-id="c354d-119">Kategori başına bir günlükçü örneği oluşturmak gerekli değildir, ancak bu, NLog veya Log4net gibi bazı Günlükçüler için mantıklı olur.</span><span class="sxs-lookup"><span data-stu-id="c354d-119">Maybe it is not needed to create a logger instance per category, but this makes sense for some loggers, like NLog or log4net.</span></span> <span data-ttu-id="c354d-120">Bunu yaptığınızda, gerekirse kategori başına farklı günlüğe kaydetme çıkış hedeflerini de seçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c354d-120">Doing this you are also able to choose different logging output targets per category if needed:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

<span data-ttu-id="c354d-121">Yukarıdaki kodda, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> Kategori başına adının tek bir örneğini oluşturur `ColorConsoleLogger` ve içinde depolar [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2) .</span><span class="sxs-lookup"><span data-stu-id="c354d-121">In the preceding code, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> creates a single instance of the `ColorConsoleLogger` per category name and stores it in the [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2).</span></span>

## <a name="usage-and-registration-of-the-custom-logger"></a><span data-ttu-id="c354d-122">Özel günlükçü kullanımı ve kaydı</span><span class="sxs-lookup"><span data-stu-id="c354d-122">Usage and registration of the custom logger</span></span>

<span data-ttu-id="c354d-123">Özel günlüğe kaydetme sağlayıcısını ve karşılık gelen günlükçüsü eklemek için, öğesinden bir ile öğesine ekleyin <xref:Microsoft.Extensions.Logging.ILoggerProvider> <xref:Microsoft.Extensions.Logging.ILoggingBuilder> <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="c354d-123">To add the custom logging provider and corresponding logger, add an <xref:Microsoft.Extensions.Logging.ILoggerProvider> with <xref:Microsoft.Extensions.Logging.ILoggingBuilder> from the <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-39":::

<span data-ttu-id="c354d-124">, `ILoggingBuilder` Bir veya daha fazla `ILogger` örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c354d-124">The `ILoggingBuilder` creates one or more `ILogger` instances.</span></span> <span data-ttu-id="c354d-125">`ILogger`Örnekler, bilgileri günlüğe kaydetmek için Framework tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c354d-125">The `ILogger` instances are used by the framework to log the information.</span></span>

<span data-ttu-id="c354d-126">Yukarıdaki kod için, için en az bir genişletme yöntemi sağlayın `ILoggerFactory` :</span><span class="sxs-lookup"><span data-stu-id="c354d-126">For the preceding code, provide at least one extension method for the `ILoggerFactory`:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

<span data-ttu-id="c354d-127">Bu basit uygulamayı çalıştırmak, aşağıdaki konsol penceresine benzer şekilde işlenir:</span><span class="sxs-lookup"><span data-stu-id="c354d-127">Running this simple application will render similar to the following console window:</span></span>

:::image type="content" source="media/color-console-logger.png" alt-text="Renk konsolu günlükçüsü örnek çıkışı":::

## <a name="see-also"></a><span data-ttu-id="c354d-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c354d-129">See also</span></span>

- <span data-ttu-id="c354d-130">[.NET oturumu açılıyor](logging.md).</span><span class="sxs-lookup"><span data-stu-id="c354d-130">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="c354d-131">[.Net 'Te günlüğe kaydetme sağlayıcıları](logging-providers.md).</span><span class="sxs-lookup"><span data-stu-id="c354d-131">[Logging providers in .NET](logging-providers.md).</span></span>
- <span data-ttu-id="c354d-132">[.Net ' te yüksek performanslı günlük kaydı](high-performance-logging.md).</span><span class="sxs-lookup"><span data-stu-id="c354d-132">[High-performance logging in .NET](high-performance-logging.md).</span></span>
