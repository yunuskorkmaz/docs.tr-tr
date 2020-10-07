---
title: .NET 'te yüksek performanslı günlüğe kaydetme
author: IEvangelist
description: Yüksek performanslı günlük senaryolarında daha az sayıda nesne ayırması gerektiren önbelleğe alınabilir temsilciler oluşturmak için LoggerMessage kullanmayı öğrenin.
ms.author: dapine
ms.date: 09/25/2020
ms.openlocfilehash: 9111b9553c913cff2937b574250b65e633250f4f
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804763"
---
# <a name="high-performance-logging-in-net"></a>.NET 'te yüksek performanslı günlüğe kaydetme

<xref:Microsoft.Extensions.Logging.LoggerMessage>Sınıfı, ve gibi [günlükçü uzantısı yöntemlerine](xref:Microsoft.Extensions.Logging.LoggerExtensions)kıyasla daha az nesne ayırma ve daha düşük hesaplama yükü gerektiren önbelleğe alınabilir temsilciler oluşturmak için işlevselliği kullanıma sunar <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> . Yüksek performanslı günlük senaryoları için, bu kalıbı kullanın <xref:Microsoft.Extensions.Logging.LoggerMessage> .

<xref:Microsoft.Extensions.Logging.LoggerMessage> Günlükçü uzantı yöntemlerine göre aşağıdaki performans avantajlarını sağlar:

- Günlükçü uzantı yöntemleri, gibi "kutulama" (dönüştürme) değer türlerini gerektirir `int` `object` . Bu <xref:Microsoft.Extensions.Logging.LoggerMessage> model, <xref:System.Action> kesin türü belirtilmiş parametrelerle statik alanlar ve genişletme yöntemleri kullanarak kutulamayı önler.
- Günlükçü uzantısı yöntemlerinin her bir günlük iletisi yazıldığında ileti şablonunu (biçim dizesi olarak adlandırılır) ayrıştırması gerekir. <xref:Microsoft.Extensions.Logging.LoggerMessage> yalnızca ileti tanımlandığında bir şablonu ayrıştırmayı gerektirir.

Örnek uygulama, <xref:Microsoft.Extensions.Logging.LoggerMessage> çalışan hizmeti için bir öncelik kuyruğu işleyen özellikleri gösterir. Uygulama, iş öğelerini öncelik sırasına göre işler. Bu işlemler gerçekleştiğinde, günlük iletileri model kullanılarak oluşturulur <xref:Microsoft.Extensions.Logging.LoggerMessage> .

## <a name="define-a-logger-message"></a>Günlükçü iletisi tanımlama

İletiyi günlüğe kaydetmek için bir temsilci oluşturmak üzere [define (LogLevel, EventID, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) kullanın <xref:System.Action> . <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> Aşırı Yüklemeler, adlandırılmış biçim dizesine (şablon) altı tür parametre geçişine izin verir.

Yöntemine girilen dize, <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> enterpolasyonlu bir dize değil, bir şablondur. Yer tutucular, türlerin belirtilme sırasına göre doldurulur. Şablondaki yer tutucu adları, şablonlar genelinde açıklayıcı ve tutarlı olmalıdır. Bunlar, yapılandırılmış günlük verileri içinde özellik adı olarak görev yapar. Yer tutucu adları için [Pascal büyük harfleri](../../standard/design-guidelines/capitalization-conventions.md) öneririz. Örneğin,, `{Item}` `{DateTime}` .

Her günlük iletisi, <xref:System.Action> [Loggermessage. define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A)tarafından oluşturulan statik bir alanda tutulur. Örneğin, örnek uygulama iş öğelerinin işlenmesine yönelik bir günlük iletisini tanımlayacak bir alan oluşturur:

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

İçin <xref:System.Action> şunu belirtin:

- Günlük düzeyi.
- <xref:Microsoft.Extensions.Logging.EventId>Statik Uzantı yönteminin adı ile benzersiz bir olay tanımlayıcısı ().
- İleti şablonu (biçim dizesi olarak adlandırılır).

İş öğeleri çalışan Hizmeti uygulamasının işlenmesine karşı sıraya alındığından, şunları ayarlar:

- Günlük düzeyi `Critical` .
- `13`Yöntemin adı ile olay kimliği `FailedToProcessWorkItem` .
- Bir dizeye ileti şablonu (biçim dizesi olarak adlandırılır).

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

Yapılandırılmış günlük depoları, olay kimliği ile birlikte verileri zenginleştirmek için sağlandığında olay adını kullanabilir. Örneğin, [Serilog](https://github.com/serilog/serilog-extensions-logging) olay adını kullanır.

, <xref:System.Action> Türü kesin belirlenmiş bir uzantı yöntemiyle çağrılır. `FailedToProcessWorkItem`Yöntemi bir iş öğesi işlendiği her seferinde bir ileti kaydeder:

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

`FailedToProcessWorkItem` , `ExecuteAsync` bir hata oluştuğunda *Worker.cs* içindeki yönteminde günlükçü üzerinde çağrılır:

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="15-18":::

Uygulamanın konsol çıkışını inceleyin:

```console
crit: WorkerServiceOptions.Example.Worker[13]
      Epic failure processing item!
      System.Exception: Failed to verify communications.
         at WorkerServiceOptions.Example.Worker.ExecuteAsync(CancellationToken stoppingToken) in
         ..\Worker.cs:line 27
```

Parametreleri bir günlük iletisine geçirmek için, statik alanı oluştururken en fazla altı tür tanımlayın. Örnek uygulama, alan için bir tür tanımlayarak öğeleri işlerken iş öğesi ayrıntılarını günlüğe kaydeder `WorkItem` <xref:System.Action> :

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemField":::

Temsilcinin günlük iletisi şablonu, belirtilen türlerden yer tutucu değerlerini alır. Örnek uygulama, quote parametresinin bir tırnak işareti eklemek için bir temsilci tanımlar `WorkItem` :

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemAssignment":::

Bir iş öğesinin işlendiği statik genişletme yöntemi, `PriorityItemProcessed` iş öğesi bağımsız değişken değerini alır ve <xref:System.Action> temsilciye geçirir:

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemMethod":::

Çalışan hizmeti `ExecuteAsync` yönteminde, `PriorityItemProcessed` iletiyi günlüğe kaydetmek için çağrılır:

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="12":::

Uygulamanın konsol çıkışını inceleyin:

```console
info: WorkerServiceOptions.Example.Worker[1]
      Processing priority item: Priority-Extreme (50db062a-9732-4418-936d-110549ad79e4): 'Verify communications'
```

## <a name="define-logger-message-scope"></a>Günlükçü ileti kapsamını tanımlama

[DefineScope (String)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) yöntemi, <xref:System.Func%601> [günlük kapsamını](logging.md#log-scopes)tanımlamak için bir temsilci oluşturur. <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> Aşırı Yüklemeler, adlandırılmış biçim dizesine (şablon) üç tür parametrenin geçirilmesine izin verir.

Yönteminde olduğu gibi <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> , yöntemi için girilen dize, ilişkili <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> dize değil, bir şablondur. Yer tutucular, türlerin belirtilme sırasına göre doldurulur. Şablondaki yer tutucu adları, şablonlar genelinde açıklayıcı ve tutarlı olmalıdır. Bunlar, yapılandırılmış günlük verileri içinde özellik adı olarak görev yapar. Yer tutucu adları için [Pascal büyük harfleri](../../standard/design-guidelines/capitalization-conventions.md) öneririz. Örneğin,, `{Item}` `{DateTime}` .

Yöntemini kullanarak bir dizi günlük mesajı için uygulanacak [günlük kapsamını](logging.md#log-scopes) tanımlayın <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> .

Örnek uygulamanın, veritabanındaki tüm teklifleri silmek için **Tümünü Temizle** düğmesi vardır. Tırnak işaretleri tek seferde kaldırılarak silinir. Bir teklifin her silindiği her seferinde `QuoteDeleted` yöntemi günlükçü üzerinde çağrılır. Bu günlük iletilerine bir günlük kapsamı eklenir.

`IncludeScopes` *Üzerindeappsettings.js*konsol günlükçüsü bölümünde etkinleştirin:

:::code language="json" source="snippets/configuration/worker-service-options/appsettings.json" highlight="3-5":::

Bir günlük kapsamı oluşturmak için, kapsam için bir temsilci tutacak bir alan ekleyin <xref:System.Func%601> . Örnek uygulama `_allQuotesDeletedScope` (*Iç/LoggerExtensions. cs*) adlı bir alan oluşturur:

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

<xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A>Temsilciyi oluşturmak için kullanın. Temsilci çağrıldığında Şablon bağımsız değişkenleri olarak kullanmak için en fazla üç tür belirlenebilir. Örnek uygulama, silinen tekliflerin sayısını (bir tür) içeren bir ileti şablonu kullanır `int` :

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

Günlük iletisi için bir statik genişletme yöntemi sağlayın. İleti şablonunda görünen adlandırılmış özellikler için herhangi bir tür parametresi ekleyin. Örnek uygulama, `DateTime` günlüğe kaydedilecek ve döndüren özel bir zaman damgası için bir kullanır `_processingWorkScope` :

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

Kapsam, oturum açma uzantısı çağrılarını bir [using](../../csharp/language-reference/keywords/using-statement.md) bloğunda sarmalar:

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="4":::

Uygulamanın konsol çıkışında günlük iletilerini inceleyin. Aşağıdaki sonuç, günlük kapsamı iletisi dahil olmak üzere silinen üç tırnak gösterir:

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

## <a name="see-also"></a>Ayrıca bkz.

- [.NET oturumu açma](logging.md)
