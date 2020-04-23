---
title: .NET için Azure SDK ile günlüğe kaydetme
description: .NET istemci kitaplıkları için Azure SDK ile oturum açmayı nasıl etkinleştirmenizi öğrenin
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: b277045a60ef5cc065d77dad84878872dedc963e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "82071992"
---
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="f5171-103">.NET için Azure SDK ile günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="f5171-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="f5171-104">.NET istemci kitaplıkları için [Azure SDK](https://azure.microsoft.com/downloads/) istemci kitaplığı işlemlerini günlüğe kaydetme özelliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="f5171-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="f5171-105">Bu, istemci kitaplıklarının Azure hizmetlerine yaptığı G/Ç isteklerini ve yanıtlarını izlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f5171-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="f5171-106">Genellikle, günlükleri hata ayıklamak veya iletişim sorunları tanılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5171-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="f5171-107">Bu makalede, .NET için Azure SDK ile günlüğe kaydetmeyi etkinleştirmek için üç yaklaşım açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f5171-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="f5171-108">Konsol penceresine giriş yap</span><span class="sxs-lookup"><span data-stu-id="f5171-108">Log to the console window</span></span>
- <span data-ttu-id="f5171-109">.NET tanılama izlemelerine giriş yapın</span><span class="sxs-lookup"><span data-stu-id="f5171-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="f5171-110">Özel günlüğe kaydetmeyi yapılandır</span><span class="sxs-lookup"><span data-stu-id="f5171-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5171-111">Bu makale, .NET için Azure SDK'nın en son sürümlerini kullanan istemci kitaplıkları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f5171-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="f5171-112">Kitaplığın desteklenip desteklenmeyip desteklenmeylistesini görmek için [Azure SDK'nın son sürümleri](https://azure.github.io/azure-sdk/releases/latest/index.html)listesine bakın.</span><span class="sxs-lookup"><span data-stu-id="f5171-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="f5171-113">Uygulamanız Azure SDK istemci kitaplıklarının eski bir sürümünü kullanıyorsa, ilgili hizmet belgelerindeki belirli talimatlara bakın.</span><span class="sxs-lookup"><span data-stu-id="f5171-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="f5171-114">Günlük bilgileri</span><span class="sxs-lookup"><span data-stu-id="f5171-114">Log information</span></span>

<span data-ttu-id="f5171-115">SDK, kişisel verileri kaldırmak için parametre sorgusunu ve üstbilgi değerlerini temizleyerek aşağıdaki bilgileri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f5171-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="f5171-116">HTTP istek günlüğü girişi:</span><span class="sxs-lookup"><span data-stu-id="f5171-116">HTTP request log entry:</span></span>

- <span data-ttu-id="f5171-117">Benzersiz Kimlik</span><span class="sxs-lookup"><span data-stu-id="f5171-117">Unique ID</span></span>
- <span data-ttu-id="f5171-118">HTTP yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5171-118">HTTP method</span></span>
- <span data-ttu-id="f5171-119">URI</span><span class="sxs-lookup"><span data-stu-id="f5171-119">URI</span></span>
- <span data-ttu-id="f5171-120">Giden istek üstbilgi</span><span class="sxs-lookup"><span data-stu-id="f5171-120">Outgoing request headers</span></span>

<span data-ttu-id="f5171-121">HTTP yanıt günlüğü girişi:</span><span class="sxs-lookup"><span data-stu-id="f5171-121">HTTP response log entry:</span></span>

- <span data-ttu-id="f5171-122">G/Ç çalışma süresi (geçen süre)</span><span class="sxs-lookup"><span data-stu-id="f5171-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="f5171-123">İstek Kimliği</span><span class="sxs-lookup"><span data-stu-id="f5171-123">Request ID</span></span>
- <span data-ttu-id="f5171-124">HTTP durum kodu</span><span class="sxs-lookup"><span data-stu-id="f5171-124">HTTP status code</span></span>
- <span data-ttu-id="f5171-125">HTTP neden cümlesi</span><span class="sxs-lookup"><span data-stu-id="f5171-125">HTTP reason phrase</span></span>
- <span data-ttu-id="f5171-126">Yanıt üst bilgileri</span><span class="sxs-lookup"><span data-stu-id="f5171-126">Response headers</span></span>
- <span data-ttu-id="f5171-127">Varsa hata bilgileri</span><span class="sxs-lookup"><span data-stu-id="f5171-127">Error information, when applicable</span></span>

<span data-ttu-id="f5171-128">İstek ve yanıt içeriği için:</span><span class="sxs-lookup"><span data-stu-id="f5171-128">For request and response content:</span></span>

- <span data-ttu-id="f5171-129">İçerik, İçerik Türü üstbilgisine bağlı olarak metin veya bayt olarak akış.</span><span class="sxs-lookup"><span data-stu-id="f5171-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="f5171-130">[! NOT} İçerik günlüğe kaydetme varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="f5171-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="f5171-131">Etkinleştirmek için, `Diagnostics.IsLoggingContentEnabled` `true` 'de `ClientOptions`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f5171-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="f5171-132">Olay günlükleri genellikle şu üç düzeyden birinde çıkar:</span><span class="sxs-lookup"><span data-stu-id="f5171-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="f5171-133">İstek ve yanıt olayları için bilgilendirme</span><span class="sxs-lookup"><span data-stu-id="f5171-133">Informational for request and response events</span></span>
- <span data-ttu-id="f5171-134">Hatalar için uyarı</span><span class="sxs-lookup"><span data-stu-id="f5171-134">Warning for errors</span></span>
- <span data-ttu-id="f5171-135">Ayrıntılı mesajlar ve içerik günlüğü için ayrıntılı bilgi</span><span class="sxs-lookup"><span data-stu-id="f5171-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="f5171-136">Yerleşik yöntemlerle günlüğe kaydetmeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f5171-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="f5171-137">.NET istemci kitaplıkları için Azure SDK, olayları .NET için tipik olan [ `EventSource` sınıf](/dotnet/api/system.diagnostics.tracing.eventsource)üzerinden Windows için Olay İzleme (ETW) olarak günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f5171-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="f5171-138">Olay kaynakları, uygulama kodunuzda en az performans yüküyle yapılandırılmış günlüğe kaydetme yi kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5171-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="f5171-139">Bu etkinlik günlüklerine erişmek için etkinlik dinleyicilerini kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5171-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="f5171-140">SDK, .NET uygulamanız için kapsamlı günlüğe kaydetmeyi basitleştiren iki statik yöntem içeren `Azure.Core.Diagnostics.AzureEventSourceListener` `CreateConsoleLogger` sınıfı `CreateTraceLogger`(Azure.Core NuGet paketinde tanımlanan) içerir: ve.</span><span class="sxs-lookup"><span data-stu-id="f5171-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="f5171-141">Bu yöntemler, günlük düzeyini belirten isteğe bağlı bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="f5171-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="f5171-142">Konsol penceresine giriş yap</span><span class="sxs-lookup"><span data-stu-id="f5171-142">Log to the console window</span></span>

<span data-ttu-id="f5171-143">.NET istemci kitaplıkları için Azure SDK'nın temel ilkelerinden biri, kapsamlı günlükleri gerçek zamanlı olarak görüntüleme olanağını basitleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="f5171-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="f5171-144">Yöntem, `CreateConsoleLogger` tek bir kod satırı yla konsol penceresine günlük göndermenize olanak tanır:</span><span class="sxs-lookup"><span data-stu-id="f5171-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="f5171-145">Tanılama izlerine günlük</span><span class="sxs-lookup"><span data-stu-id="f5171-145">Log to diagnostic traces</span></span>

<span data-ttu-id="f5171-146">İzleme dinleyicileri uygularsanız, `CreateTraceLogger` standart .NET olay izleme mekanizmasına ( ).[`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)</span><span class="sxs-lookup"><span data-stu-id="f5171-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="f5171-147">.NET'te etkinlik izleme hakkında daha fazla bilgi için [Bkz.](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners)</span><span class="sxs-lookup"><span data-stu-id="f5171-147">For more information on event tracing in .NET, see [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span></span> <span data-ttu-id="f5171-148">Bu örnekte bir günlük verbose düzeyi belirtilir:</span><span class="sxs-lookup"><span data-stu-id="f5171-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="f5171-149">Özel günlüğe kaydetmeyi yapılandır</span><span class="sxs-lookup"><span data-stu-id="f5171-149">Configure custom logging</span></span>

<span data-ttu-id="f5171-150">Yukarıda belirtildiği gibi, .NET için Azure SDK'dan günlük iletileri almak için etkinlik dinleyicilerini kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5171-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="f5171-151">Yukarıdaki basitleştirilmiş yöntemlerden birini kullanarak kapsamlı günlüğe kaydetme uygulamak istemiyorsanız, `AzureEventSourceListener` sınıfın bir örneğini oluşturup yazdığınız bir geri arama işlevini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5171-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="f5171-152">Bu yöntem, istediğiniz şekilde işleyebilir günlük iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="f5171-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="f5171-153">Buna ek olarak, örneği oluştursanız, içerecek günlük düzeylerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5171-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="f5171-154">Aşağıdaki örnek, özel bir iletiyle konsola giriş yapan ve düzey ayrıntılı Azure temel olaylarına filtrelenen bir olay dinleyicisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5171-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="f5171-155">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f5171-155">Next steps</span></span>

- [<span data-ttu-id="f5171-156">Azure Uygulama Hizmeti'ndeki uygulamalar için tanılama günlüğe kaydetmeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f5171-156">Enable diagnostics logging for apps in Azure App Service</span></span>](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="f5171-157">[Azure güvenlik günlüğe kaydetme ve denetleme](https://docs.microsoft.com/azure/security/fundamentals/log-audit) seçeneklerini gözden geçirme</span><span class="sxs-lookup"><span data-stu-id="f5171-157">Review [Azure security logging and auditing](https://docs.microsoft.com/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="f5171-158">[Azure platform günlükleriyle](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview) nasıl çalışacağınızı öğrenin</span><span class="sxs-lookup"><span data-stu-id="f5171-158">Learn how to work with [Azure platform logs](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="f5171-159">[.NET Core günlük ve izleme](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing) hakkında daha fazla bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="f5171-159">Read more about [.NET Core logging and tracing](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span></span>
