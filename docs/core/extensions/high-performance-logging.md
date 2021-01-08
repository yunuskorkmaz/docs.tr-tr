---
title: .NET 'te yüksek performanslı günlüğe kaydetme
author: IEvangelist
description: Yüksek performanslı günlük senaryolarında daha az sayıda nesne ayırması gerektiren önbelleğe alınabilir temsilciler oluşturmak için LoggerMessage kullanmayı öğrenin.
ms.author: dapine
ms.date: 01/04/2021
ms.openlocfilehash: 0031ff7a9f70cb0cf724fdf6dfa4fbe0a44af7c1
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025446"
---
# <a name="high-performance-logging-in-net"></a><span data-ttu-id="b3d84-103">.NET 'te yüksek performanslı günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="b3d84-103">High-performance logging in .NET</span></span>

<span data-ttu-id="b3d84-104"><xref:Microsoft.Extensions.Logging.LoggerMessage>Sınıfı, ve gibi [günlükçü uzantısı yöntemlerine](xref:Microsoft.Extensions.Logging.LoggerExtensions)kıyasla daha az nesne ayırma ve daha düşük hesaplama yükü gerektiren önbelleğe alınabilir temsilciler oluşturmak için işlevselliği kullanıma sunar <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> .</span><span class="sxs-lookup"><span data-stu-id="b3d84-104">The <xref:Microsoft.Extensions.Logging.LoggerMessage> class exposes functionality to create cacheable delegates that require fewer object allocations and reduced computational overhead compared to [logger extension methods](xref:Microsoft.Extensions.Logging.LoggerExtensions), such as <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> and <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A>.</span></span> <span data-ttu-id="b3d84-105">Yüksek performanslı günlük senaryoları için, bu kalıbı kullanın <xref:Microsoft.Extensions.Logging.LoggerMessage> .</span><span class="sxs-lookup"><span data-stu-id="b3d84-105">For high-performance logging scenarios, use the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

<span data-ttu-id="b3d84-106"><xref:Microsoft.Extensions.Logging.LoggerMessage> Günlükçü uzantı yöntemlerine göre aşağıdaki performans avantajlarını sağlar:</span><span class="sxs-lookup"><span data-stu-id="b3d84-106"><xref:Microsoft.Extensions.Logging.LoggerMessage> provides the following performance advantages over Logger extension methods:</span></span>

- <span data-ttu-id="b3d84-107">Günlükçü uzantı yöntemleri, gibi "kutulama" (dönüştürme) değer türlerini gerektirir `int` `object` .</span><span class="sxs-lookup"><span data-stu-id="b3d84-107">Logger extension methods require "boxing" (converting) value types, such as `int`, into `object`.</span></span> <span data-ttu-id="b3d84-108">Bu <xref:Microsoft.Extensions.Logging.LoggerMessage> model, <xref:System.Action> kesin türü belirtilmiş parametrelerle statik alanlar ve genişletme yöntemleri kullanarak kutulamayı önler.</span><span class="sxs-lookup"><span data-stu-id="b3d84-108">The <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern avoids boxing by using static <xref:System.Action> fields and extension methods with strongly-typed parameters.</span></span>
- <span data-ttu-id="b3d84-109">Günlükçü uzantısı yöntemlerinin her bir günlük iletisi yazıldığında ileti şablonunu (biçim dizesi olarak adlandırılır) ayrıştırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3d84-109">Logger extension methods must parse the message template (named format string) every time a log message is written.</span></span> <span data-ttu-id="b3d84-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> yalnızca ileti tanımlandığında bir şablonu ayrıştırmayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b3d84-110"><xref:Microsoft.Extensions.Logging.LoggerMessage> only requires parsing a template once when the message is defined.</span></span>

<span data-ttu-id="b3d84-111">Örnek uygulama, <xref:Microsoft.Extensions.Logging.LoggerMessage> çalışan hizmeti için bir öncelik kuyruğu işleyen özellikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3d84-111">The sample app demonstrates <xref:Microsoft.Extensions.Logging.LoggerMessage> features with a priority queue processing worker service.</span></span> <span data-ttu-id="b3d84-112">Uygulama, iş öğelerini öncelik sırasına göre işler.</span><span class="sxs-lookup"><span data-stu-id="b3d84-112">The app processes work items in priority order.</span></span> <span data-ttu-id="b3d84-113">Bu işlemler gerçekleştiğinde, günlük iletileri model kullanılarak oluşturulur <xref:Microsoft.Extensions.Logging.LoggerMessage> .</span><span class="sxs-lookup"><span data-stu-id="b3d84-113">As these operations occur, log messages are generated using the <xref:Microsoft.Extensions.Logging.LoggerMessage> pattern.</span></span>

## <a name="define-a-logger-message"></a><span data-ttu-id="b3d84-114">Günlükçü iletisi tanımlama</span><span class="sxs-lookup"><span data-stu-id="b3d84-114">Define a logger message</span></span>

<span data-ttu-id="b3d84-115">İletiyi günlüğe kaydetmek için bir temsilci oluşturmak üzere [define (LogLevel, EventID, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) kullanın <xref:System.Action> .</span><span class="sxs-lookup"><span data-stu-id="b3d84-115">Use [Define(LogLevel, EventId, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) to create an <xref:System.Action> delegate for logging a message.</span></span> <span data-ttu-id="b3d84-116"><xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> Aşırı Yüklemeler, adlandırılmış biçim dizesine (şablon) altı tür parametre geçişine izin verir.</span><span class="sxs-lookup"><span data-stu-id="b3d84-116"><xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> overloads permit passing up to six type parameters to a named format string (template).</span></span>

<span data-ttu-id="b3d84-117">Yöntemine girilen dize, <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> enterpolasyonlu bir dize değil, bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="b3d84-117">The string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="b3d84-118">Yer tutucular, türlerin belirtilme sırasına göre doldurulur.</span><span class="sxs-lookup"><span data-stu-id="b3d84-118">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="b3d84-119">Şablondaki yer tutucu adları, şablonlar genelinde açıklayıcı ve tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3d84-119">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="b3d84-120">Bunlar, yapılandırılmış günlük verileri içinde özellik adı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="b3d84-120">They serve as property names within structured log data.</span></span> <span data-ttu-id="b3d84-121">Yer tutucu adları için [Pascal büyük harfleri](../../standard/design-guidelines/capitalization-conventions.md) öneririz.</span><span class="sxs-lookup"><span data-stu-id="b3d84-121">We recommend [Pascal casing](../../standard/design-guidelines/capitalization-conventions.md) for placeholder names.</span></span> <span data-ttu-id="b3d84-122">Örneğin,, `{Item}` `{DateTime}` .</span><span class="sxs-lookup"><span data-stu-id="b3d84-122">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="b3d84-123">Her günlük iletisi, <xref:System.Action> [Loggermessage. define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A)tarafından oluşturulan statik bir alanda tutulur.</span><span class="sxs-lookup"><span data-stu-id="b3d84-123">Each log message is an <xref:System.Action> held in a static field created by [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A).</span></span> <span data-ttu-id="b3d84-124">Örneğin, örnek uygulama iş öğelerinin işlenmesine yönelik bir günlük iletisini tanımlayacak bir alan oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b3d84-124">For example, the sample app creates a field to describe a log message for the processing of work items:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingField":::

<span data-ttu-id="b3d84-125">İçin <xref:System.Action> şunu belirtin:</span><span class="sxs-lookup"><span data-stu-id="b3d84-125">For the <xref:System.Action>, specify:</span></span>

- <span data-ttu-id="b3d84-126">Günlük düzeyi.</span><span class="sxs-lookup"><span data-stu-id="b3d84-126">The log level.</span></span>
- <span data-ttu-id="b3d84-127"><xref:Microsoft.Extensions.Logging.EventId>Statik Uzantı yönteminin adı ile benzersiz bir olay tanımlayıcısı ().</span><span class="sxs-lookup"><span data-stu-id="b3d84-127">A unique event identifier (<xref:Microsoft.Extensions.Logging.EventId>) with the name of the static extension method.</span></span>
- <span data-ttu-id="b3d84-128">İleti şablonu (biçim dizesi olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="b3d84-128">The message template (named format string).</span></span>

<span data-ttu-id="b3d84-129">İş öğeleri çalışan Hizmeti uygulamasının işlenmesine karşı sıraya alındığından, şunları ayarlar:</span><span class="sxs-lookup"><span data-stu-id="b3d84-129">As work items are dequeued for processing the worker service app sets the:</span></span>

- <span data-ttu-id="b3d84-130">Günlük düzeyi <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b3d84-130">Log level to <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="b3d84-131">`13`Yöntemin adı ile olay kimliği `FailedToProcessWorkItem` .</span><span class="sxs-lookup"><span data-stu-id="b3d84-131">Event id to `13` with the name of the `FailedToProcessWorkItem` method.</span></span>
- <span data-ttu-id="b3d84-132">Bir dizeye ileti şablonu (biçim dizesi olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="b3d84-132">Message template (named format string) to a string.</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingAssignment":::

<span data-ttu-id="b3d84-133">Yapılandırılmış günlük depoları, olay kimliği ile birlikte verileri zenginleştirmek için sağlandığında olay adını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b3d84-133">Structured logging stores may use the event name when it's supplied with the event id to enrich logging.</span></span> <span data-ttu-id="b3d84-134">Örneğin, [Serilog](https://github.com/serilog/serilog-extensions-logging) olay adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b3d84-134">For example, [Serilog](https://github.com/serilog/serilog-extensions-logging) uses the event name.</span></span>

<span data-ttu-id="b3d84-135">, <xref:System.Action> Türü kesin belirlenmiş bir uzantı yöntemiyle çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b3d84-135">The <xref:System.Action> is invoked through a strongly-typed extension method.</span></span> <span data-ttu-id="b3d84-136">`PriorityItemProcessed`Yöntemi bir iş öğesi işlendiği her seferinde bir ileti kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b3d84-136">The `PriorityItemProcessed` method logs a message every time a work item is being processed.</span></span> <span data-ttu-id="b3d84-137">Ancak, `FailedToProcessWorkItem` (ve ise) bir özel durum oluştuğunda çağrılır:</span><span class="sxs-lookup"><span data-stu-id="b3d84-137">Whereas, `FailedToProcessWorkItem` is called when (and if) an exception occurs:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="15-18":::

<span data-ttu-id="b3d84-138">Uygulamanın konsol çıkışını inceleyin:</span><span class="sxs-lookup"><span data-stu-id="b3d84-138">Inspect the app's console output:</span></span>

```console
crit: WorkerServiceOptions.Example.Worker[13]
      Epic failure processing item!
      System.Exception: Failed to verify communications.
         at WorkerServiceOptions.Example.Worker.ExecuteAsync(CancellationToken stoppingToken) in
         ..\Worker.cs:line 27
```

<span data-ttu-id="b3d84-139">Parametreleri bir günlük iletisine geçirmek için, statik alanı oluştururken en fazla altı tür tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b3d84-139">To pass parameters to a log message, define up to six types when creating the static field.</span></span> <span data-ttu-id="b3d84-140">Örnek uygulama, alan için bir tür tanımlayarak öğeleri işlerken iş öğesi ayrıntılarını günlüğe kaydeder `WorkItem` <xref:System.Action> :</span><span class="sxs-lookup"><span data-stu-id="b3d84-140">The sample app logs the work item details when processing items by defining a `WorkItem` type for the <xref:System.Action> field:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemField":::

<span data-ttu-id="b3d84-141">Temsilcinin günlük iletisi şablonu, belirtilen türlerden yer tutucu değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="b3d84-141">The delegate's log message template receives its placeholder values from the types provided.</span></span> <span data-ttu-id="b3d84-142">Örnek uygulama, öğe parametresinin bir iş öğesi eklemek için bir temsilci tanımlar `WorkItem` :</span><span class="sxs-lookup"><span data-stu-id="b3d84-142">The sample app defines a delegate for adding a work item where the item parameter is a `WorkItem`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemAssignment":::

<span data-ttu-id="b3d84-143">Bir iş öğesinin işlendiği statik genişletme yöntemi, `PriorityItemProcessed` iş öğesi bağımsız değişken değerini alır ve <xref:System.Action> temsilciye geçirir:</span><span class="sxs-lookup"><span data-stu-id="b3d84-143">The static extension method for logging that a work item is being processed, `PriorityItemProcessed`, receives the work item argument value and passes it to the <xref:System.Action> delegate:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemMethod":::

<span data-ttu-id="b3d84-144">Çalışan hizmeti `ExecuteAsync` yönteminde, `PriorityItemProcessed` iletiyi günlüğe kaydetmek için çağrılır:</span><span class="sxs-lookup"><span data-stu-id="b3d84-144">In the worker service's `ExecuteAsync` method, `PriorityItemProcessed` is called to log the message:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="12":::

<span data-ttu-id="b3d84-145">Uygulamanın konsol çıkışını inceleyin:</span><span class="sxs-lookup"><span data-stu-id="b3d84-145">Inspect the app's console output:</span></span>

```console
info: WorkerServiceOptions.Example.Worker[1]
      Processing priority item: Priority-Extreme (50db062a-9732-4418-936d-110549ad79e4): 'Verify communications'
```

## <a name="define-logger-message-scope"></a><span data-ttu-id="b3d84-146">Günlükçü ileti kapsamını tanımlama</span><span class="sxs-lookup"><span data-stu-id="b3d84-146">Define logger message scope</span></span>

<span data-ttu-id="b3d84-147">[DefineScope (String)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) yöntemi, <xref:System.Func%601> [günlük kapsamını](logging.md#log-scopes)tanımlamak için bir temsilci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b3d84-147">The [DefineScope(string)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) method creates a <xref:System.Func%601> delegate for defining a [log scope](logging.md#log-scopes).</span></span> <span data-ttu-id="b3d84-148"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> Aşırı Yüklemeler, adlandırılmış biçim dizesine (şablon) üç tür parametrenin geçirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="b3d84-148"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> overloads permit passing up to three type parameters to a named format string (template).</span></span>

<span data-ttu-id="b3d84-149">Yönteminde olduğu gibi <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> , yöntemi için girilen dize, ilişkili <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> dize değil, bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="b3d84-149">As is the case with the <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> method, the string provided to the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method is a template and not an interpolated string.</span></span> <span data-ttu-id="b3d84-150">Yer tutucular, türlerin belirtilme sırasına göre doldurulur.</span><span class="sxs-lookup"><span data-stu-id="b3d84-150">Placeholders are filled in the order that the types are specified.</span></span> <span data-ttu-id="b3d84-151">Şablondaki yer tutucu adları, şablonlar genelinde açıklayıcı ve tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3d84-151">Placeholder names in the template should be descriptive and consistent across templates.</span></span> <span data-ttu-id="b3d84-152">Bunlar, yapılandırılmış günlük verileri içinde özellik adı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="b3d84-152">They serve as property names within structured log data.</span></span> <span data-ttu-id="b3d84-153">Yer tutucu adları için [Pascal büyük harfleri](../../standard/design-guidelines/capitalization-conventions.md) öneririz.</span><span class="sxs-lookup"><span data-stu-id="b3d84-153">We recommend [Pascal casing](../../standard/design-guidelines/capitalization-conventions.md) for placeholder names.</span></span> <span data-ttu-id="b3d84-154">Örneğin,, `{Item}` `{DateTime}` .</span><span class="sxs-lookup"><span data-stu-id="b3d84-154">For example, `{Item}`, `{DateTime}`.</span></span>

<span data-ttu-id="b3d84-155">Yöntemini kullanarak bir dizi günlük mesajı için uygulanacak [günlük kapsamını](logging.md#log-scopes) tanımlayın <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> .</span><span class="sxs-lookup"><span data-stu-id="b3d84-155">Define a [log scope](logging.md#log-scopes) to apply to a series of log messages using the <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> method.</span></span> <span data-ttu-id="b3d84-156">`IncludeScopes` *Üzerindeappsettings.js* konsol günlükçüsü bölümünde etkinleştirin:</span><span class="sxs-lookup"><span data-stu-id="b3d84-156">Enable `IncludeScopes` in the console logger section of *appsettings.json*:</span></span>

:::code language="json" source="snippets/configuration/worker-service-options/appsettings.json" highlight="3-5":::

<span data-ttu-id="b3d84-157">Bir günlük kapsamı oluşturmak için, kapsam için bir temsilci tutacak bir alan ekleyin <xref:System.Func%601> .</span><span class="sxs-lookup"><span data-stu-id="b3d84-157">To create a log scope, add a field to hold a <xref:System.Func%601> delegate for the scope.</span></span> <span data-ttu-id="b3d84-158">Örnek uygulama `_processingWorkScope` (*Iç/LoggerExtensions. cs*) adlı bir alan oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b3d84-158">The sample app creates a field called `_processingWorkScope` (*Internal/LoggerExtensions.cs*):</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

<span data-ttu-id="b3d84-159"><xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A>Temsilciyi oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3d84-159">Use <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> to create the delegate.</span></span> <span data-ttu-id="b3d84-160">Temsilci çağrıldığında Şablon bağımsız değişkenleri olarak kullanmak için en fazla üç tür belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b3d84-160">Up to three types can be specified for use as template arguments when the delegate is invoked.</span></span> <span data-ttu-id="b3d84-161">Örnek uygulama, işlemin başladığı tarih ve saati içeren bir ileti şablonu kullanır:</span><span class="sxs-lookup"><span data-stu-id="b3d84-161">The sample app uses a message template that includes the date time in which processing started:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

<span data-ttu-id="b3d84-162">Günlük iletisi için bir statik genişletme yöntemi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="b3d84-162">Provide a static extension method for the log message.</span></span> <span data-ttu-id="b3d84-163">İleti şablonunda görünen adlandırılmış özellikler için herhangi bir tür parametresi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d84-163">Include any type parameters for named properties that appear in the message template.</span></span> <span data-ttu-id="b3d84-164">Örnek uygulama, `DateTime` günlüğe kaydedilecek ve döndüren özel bir zaman damgası için bir kullanır `_processingWorkScope` :</span><span class="sxs-lookup"><span data-stu-id="b3d84-164">The sample app takes in a `DateTime` for a custom time stamp to log and returns `_processingWorkScope`:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

<span data-ttu-id="b3d84-165">Kapsam, oturum açma uzantısı çağrılarını bir [using](../../csharp/language-reference/keywords/using-statement.md) bloğunda sarmalar:</span><span class="sxs-lookup"><span data-stu-id="b3d84-165">The scope wraps the logging extension calls in a [using](../../csharp/language-reference/keywords/using-statement.md) block:</span></span>

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="4":::

<span data-ttu-id="b3d84-166">Uygulamanın konsol çıkışında günlük iletilerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d84-166">Inspect the log messages in the app's console output.</span></span> <span data-ttu-id="b3d84-167">Aşağıdaki sonuç, günlük kapsamı iletisi dahil olmak üzere günlük iletilerinin öncelik sıralamasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="b3d84-167">The following result shows priority ordering of log messages with the log scope message included:</span></span>

```console
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Extreme (f5090ede-a337-4041-b914-f6bc0db5ae64): 'Verify communications'
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: ..\worker-service-options
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-High (496d440f-2007-4391-b179-09d75ab52373): 'Validate collection'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (dea9e3f4-d7df-46d2-b7cd-5e0232eb98a5): 'Propagate selections'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (089d7f0d-da72-4b55-92fe-57b147838056): 'Enter pooling [contention]'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Low (6e68c4be-089f-4450-9080-1ea63fcbb686): 'Health check network'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (6f324134-6bb6-455f-81d4-553ab307c421): 'Ping weather service'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (37bf736c-7a26-4a2a-9e56-e89bcf3b8f35): 'Set process state'
```

## <a name="see-also"></a><span data-ttu-id="b3d84-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3d84-168">See also</span></span>

- [<span data-ttu-id="b3d84-169">.NET oturumu açma</span><span class="sxs-lookup"><span data-stu-id="b3d84-169">Logging in .NET</span></span>](logging.md)
