---
title: .NET için Azure SDK ile günlüğe kaydetme
description: .NET istemci kitaplıkları için Azure SDK ile günlüğe kaydetmeyi etkinleştirme hakkında bilgi edinin
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: 0b255713bc9c13e0cbdaeb25a3d0fe46e91e815d
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416035"
---
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="25340-103">.NET için Azure SDK ile günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="25340-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="25340-104">.NET için [Azure SDK](https://azure.microsoft.com/downloads/) istemci kitaplıkları, istemci kitaplığı işlemlerini günlüğe kaydetme özelliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="25340-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="25340-105">Bu, istemci kitaplıklarının Azure hizmetlerinde yapmakta olduğu g/ç isteklerini ve yanıtlarını izlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="25340-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="25340-106">Genellikle Günlükler, iletişim sorunlarını ayıklamak veya tanılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25340-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="25340-107">Bu makalede, .NET için Azure SDK ile günlüğe kaydetmeyi etkinleştirmek için üç yaklaşım açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="25340-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="25340-108">Konsol penceresinde günlüğe kaydet</span><span class="sxs-lookup"><span data-stu-id="25340-108">Log to the console window</span></span>
- <span data-ttu-id="25340-109">.NET tanılama izlemelerinde günlüğe kaydet</span><span class="sxs-lookup"><span data-stu-id="25340-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="25340-110">Özel günlüğü yapılandırma</span><span class="sxs-lookup"><span data-stu-id="25340-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25340-111">Bu makale, .NET için Azure SDK 'sının en son sürümlerini kullanan istemci kitaplıkları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="25340-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="25340-112">Bir kitaplığın desteklenip desteklenmediğini görmek için, [Azure SDK 'sının en son sürümleri](https://azure.github.io/azure-sdk/releases/latest/index.html)listesine bakın.</span><span class="sxs-lookup"><span data-stu-id="25340-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="25340-113">Uygulamanız Azure SDK istemci kitaplıklarının eski bir sürümünü kullanıyorsa, geçerli hizmet belgelerindeki belirli yönergelere bakın.</span><span class="sxs-lookup"><span data-stu-id="25340-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="25340-114">Günlük bilgileri</span><span class="sxs-lookup"><span data-stu-id="25340-114">Log information</span></span>

<span data-ttu-id="25340-115">SDK, kişisel verileri kaldırmak için aşağıdaki bilgileri günlüğe kaydeder, parametre sorgusunu ve üst bilgi değerlerini temizler.</span><span class="sxs-lookup"><span data-stu-id="25340-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="25340-116">HTTP istek günlüğü girişi:</span><span class="sxs-lookup"><span data-stu-id="25340-116">HTTP request log entry:</span></span>

- <span data-ttu-id="25340-117">Benzersiz Kimlik</span><span class="sxs-lookup"><span data-stu-id="25340-117">Unique ID</span></span>
- <span data-ttu-id="25340-118">HTTP yöntemi</span><span class="sxs-lookup"><span data-stu-id="25340-118">HTTP method</span></span>
- <span data-ttu-id="25340-119">URI</span><span class="sxs-lookup"><span data-stu-id="25340-119">URI</span></span>
- <span data-ttu-id="25340-120">Giden istek üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="25340-120">Outgoing request headers</span></span>

<span data-ttu-id="25340-121">HTTP yanıt günlüğü girişi:</span><span class="sxs-lookup"><span data-stu-id="25340-121">HTTP response log entry:</span></span>

- <span data-ttu-id="25340-122">G/ç işleminin süresi (geçen süre)</span><span class="sxs-lookup"><span data-stu-id="25340-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="25340-123">Request ID</span><span class="sxs-lookup"><span data-stu-id="25340-123">Request ID</span></span>
- <span data-ttu-id="25340-124">HTTP durum kodu</span><span class="sxs-lookup"><span data-stu-id="25340-124">HTTP status code</span></span>
- <span data-ttu-id="25340-125">HTTP neden tümceciği</span><span class="sxs-lookup"><span data-stu-id="25340-125">HTTP reason phrase</span></span>
- <span data-ttu-id="25340-126">Yanıt üst bilgileri</span><span class="sxs-lookup"><span data-stu-id="25340-126">Response headers</span></span>
- <span data-ttu-id="25340-127">Uygun olduğunda hata bilgileri</span><span class="sxs-lookup"><span data-stu-id="25340-127">Error information, when applicable</span></span>

<span data-ttu-id="25340-128">İstek ve yanıt içeriği için:</span><span class="sxs-lookup"><span data-stu-id="25340-128">For request and response content:</span></span>

- <span data-ttu-id="25340-129">Content-Type üst bilgisine bağlı olarak, metin veya bayt olarak içerik akışı.</span><span class="sxs-lookup"><span data-stu-id="25340-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="25340-130">[! NOTE} Içerik günlüğe kaydetme varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="25340-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="25340-131">Etkinleştirmek için, `Diagnostics.IsLoggingContentEnabled` içinde olarak ayarlayın `true` `ClientOptions` .</span><span class="sxs-lookup"><span data-stu-id="25340-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="25340-132">Olay günlükleri genellikle şu üç düzeyden birinde çıkış olur:</span><span class="sxs-lookup"><span data-stu-id="25340-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="25340-133">İstek ve yanıt olayları için bilgilendirici</span><span class="sxs-lookup"><span data-stu-id="25340-133">Informational for request and response events</span></span>
- <span data-ttu-id="25340-134">Hatalar için uyarı</span><span class="sxs-lookup"><span data-stu-id="25340-134">Warning for errors</span></span>
- <span data-ttu-id="25340-135">Ayrıntılı iletiler ve içerik günlüğü için ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="25340-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="25340-136">Yerleşik yöntemlerle günlüğe kaydetmeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="25340-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="25340-137">.NET istemci kitaplıkları için Azure SDK, .NET için tipik olan [ `EventSource` sınıfı](/dotnet/api/system.diagnostics.tracing.eventsource)aracılığıyla Windows için olay Izleme 'ye (ETW) yönelik olayları günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="25340-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="25340-138">Olay kaynakları, uygulama kodunuzda yapılandırılmış günlük oluşturmayı en düşük performans yüküyle kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="25340-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="25340-139">Bu olay günlüklerine erişim kazanmak için olay dinleyicilerini kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="25340-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="25340-140">SDK, `Azure.Core.Diagnostics.AzureEventSourceListener` .NET uygulamanız için kapsamlı günlüğü kolaylaştıran iki statik yöntem içeren sınıfını (Azure. Core NuGet paketinde tanımlanmıştır) içerir: `CreateConsoleLogger` ve `CreateTraceLogger` .</span><span class="sxs-lookup"><span data-stu-id="25340-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="25340-141">Bu yöntemler, günlük düzeyini belirten isteğe bağlı bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="25340-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="25340-142">Konsol penceresinde günlüğe kaydet</span><span class="sxs-lookup"><span data-stu-id="25340-142">Log to the console window</span></span>

<span data-ttu-id="25340-143">.NET istemci kitaplıkları için Azure SDK 'sının temel bir temel, kapsamlı günlükleri gerçek zamanlı görüntüleme özelliğini basitleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="25340-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="25340-144">`CreateConsoleLogger`Yöntemi, tek bir kod satırıyla günlükleri konsol penceresine göndermenizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="25340-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="25340-145">Tanılama izlemelerinde günlüğe kaydet</span><span class="sxs-lookup"><span data-stu-id="25340-145">Log to diagnostic traces</span></span>

<span data-ttu-id="25340-146">İzleme dinleyicileri uygularsanız, `CreateTraceLogger` Standart .NET olay izleme mekanizmasına () oturum açmak için yöntemini kullanabilirsiniz [`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing) .</span><span class="sxs-lookup"><span data-stu-id="25340-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="25340-147">.NET 'teki olay izleme hakkında daha fazla bilgi için bkz. [Trace dinleyicileri](../framework/debug-trace-profile/trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="25340-147">For more information on event tracing in .NET, see [Trace Listeners](../framework/debug-trace-profile/trace-listeners.md).</span></span> <span data-ttu-id="25340-148">Bu örnek, ayrıntılı bir günlük düzeyi belirtir:</span><span class="sxs-lookup"><span data-stu-id="25340-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="25340-149">Özel günlüğü yapılandırma</span><span class="sxs-lookup"><span data-stu-id="25340-149">Configure custom logging</span></span>

<span data-ttu-id="25340-150">Yukarıda belirtildiği gibi, .NET için Azure SDK 'dan günlük iletilerini almak üzere olay dinleyicilerini kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="25340-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="25340-151">Yukarıdaki Basitleştirilmiş yöntemlerden birini kullanarak kapsamlı günlük uygulamak istemiyorsanız, sınıfının bir örneğini oluşturabilir `AzureEventSourceListener` ve yazdığınız bir geri çağırma işlevi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25340-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="25340-152">Bu yöntem, ihtiyacınız olan ancak yapmanız gereken günlük iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="25340-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="25340-153">Ayrıca, örneği oluşturduğunuzda, dahil edilecek günlük düzeylerini de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25340-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="25340-154">Aşağıdaki örnek, özel bir iletiyle konsola oturum açan bir olay dinleyicisi oluşturur ve ayrıntı düzeyinde Azure Core olaylarına filtrelenir.</span><span class="sxs-lookup"><span data-stu-id="25340-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

```csharp
using AzureEventSourceListener listener = new AzureEventSourceListener((e, message) =>
    {
        // Only log messages from Azure-Core event source
        if (e.EventSource.Name == "Azure-Core")
        {
            Console.WriteLine($"{DateTime.Now} {message}");
        }
    },
    level: EventLevel.Verbose);
```

## <a name="next-steps"></a><span data-ttu-id="25340-155">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="25340-155">Next steps</span></span>

- [<span data-ttu-id="25340-156">Azure App Service uygulamalar için tanılama günlüğünü etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="25340-156">Enable diagnostics logging for apps in Azure App Service</span></span>](/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="25340-157">[Azure Güvenlik günlüğü ve denetim](/azure/security/fundamentals/log-audit) seçeneklerini gözden geçirin</span><span class="sxs-lookup"><span data-stu-id="25340-157">Review [Azure security logging and auditing](/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="25340-158">[Azure platform günlükleriyle](/azure/azure-monitor/platform/platform-logs-overview) nasıl çalışacağınızı öğrenin</span><span class="sxs-lookup"><span data-stu-id="25340-158">Learn how to work with [Azure platform logs](/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="25340-159">[.NET Core günlüğe kaydetme ve izleme](../core/diagnostics/logging-tracing.md) hakkında daha fazla bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="25340-159">Read more about [.NET Core logging and tracing](../core/diagnostics/logging-tracing.md)</span></span>
