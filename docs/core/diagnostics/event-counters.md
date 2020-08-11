---
title: .NET Core 'da EventCounters
description: Bu makalede, olaylarınızın ne olduğunu, nasıl uygulanacağını ve bunları nasıl kullanacağınızı öğreneceksiniz.
ms.date: 08/07/2020
ms.openlocfilehash: fc2f945e3de732a81b9ce3fd82eff10e455cae87
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062970"
---
# <a name="eventcounters-in-net-core"></a>.NET Core 'da EventCounters

**Bu makale şu şekilde geçerlidir: ✔️** .net Core 3,0 SDK ve sonraki sürümleri

EventCounters, hafif, platformlar arası ve neredeyse gerçek zamanlı performans ölçümü koleksiyonu için kullanılan .NET Core API 'larıdır. EventCounters, Windows üzerindeki .NET Framework "performans sayaçları" için platformlar arası bir alternatif olarak eklenmiştir. Bu makalede, olaylarınızın ne olduğunu, nasıl uygulanacağını ve bunları nasıl kullanacağınızı öğreneceksiniz.

.NET Core çalışma zamanı ve birkaç .NET kitaplığı, .NET Core 3,0 ' den başlayarak EventCounters kullanarak temel tanılama bilgilerini yayımlar. .NET çalışma zamanı tarafından sunulan EventCounters dışında, kendi Eventsayaçlarınızı uygulamayı seçebilirsiniz. EventCounters, çeşitli ölçümleri izlemek için kullanılabilir.

EventCounters, bir parçası olarak bulunur <xref:System.Diagnostics.Tracing.EventSource> ve otomatik olarak dinleyici araçlarına düzenli olarak gönderilir. İçindeki tüm diğer olaylar gibi <xref:System.Diagnostics.Tracing.EventSource> , bunlar hem işlem içi hem de işlem dışı <xref:System.Diagnostics.Tracing.EventListener> ve eventpipe ile tüketilebilir. Bu makale, EventCounters 'in platformlar arası özelliklerine odaklanmaktadır ve özellikle PerfView ve ETW (Windows için olay Izleme) özelliğini dışlar, ancak her ikisi de EventCounters ile kullanılabilir.

![-Proc ve proc dışı diyagram görüntüsü EventCounters](media/event-counters.svg)

[!INCLUDE [available-counters](includes/available-counters.md)]

## <a name="eventcounter-api-overview"></a>EventCounter API 'sine genel bakış

Sayaçların iki birincil kategorisi vardır. Bazı sayaçlar, toplam özel durum sayısı, toplam GB sayısı ve toplam istek sayısı gibi "ücret" değerleri için kullanılır. Diğer sayaçlar, yığın kullanımı, CPU kullanımı ve çalışma kümesi boyutu gibi "Snapshot" değerleridir. Bu sayaçların her bir kategorisi içinde, değerlerini alma yoluyla değişen iki tür sayaç vardır. Yoklama sayaçları, bir geri çağırma yoluyla değerlerini alır ve yoklamasız sayaçların değerleri doğrudan sayaç örneğinde ayarlanır.

Sayaçlar aşağıdaki uygulamalarla temsil edilir:

* <xref:System.Diagnostics.Tracing.EventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingEventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>
* <xref:System.Diagnostics.Tracing.PollingCounter>

Bir olay dinleyicisi, ölçüm aralıklarının ne kadar süreyle olduğunu belirtir. Her bir aralığın sonunda, her sayaç için dinleyiciye bir değer iletilir. Bir sayacın uygulamaları, her aralığa değer üretmek için hangi API 'Lerin ve hesaplamaların kullanılacağını tespit edilir.

1. <xref:System.Diagnostics.Tracing.EventCounter>Bir değer kümesini kaydeder. <xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType>Yöntemi, kümesine yeni bir değer ekler. Her aralığa göre, en az, en fazla ve ortalama gibi, küme için istatistiksel bir Özet hesaplanır. [DotNet-Counters](dotnet-counters.md) aracı her zaman ortalama değeri görüntüler. , <xref:System.Diagnostics.Tracing.EventCounter> Ayrı bir işlem kümesini tanımlamaya yarar. Yaygın kullanım, son GÇ işlemlerinin bayt cinsinden ortalama boyutunu veya bir dizi mali işlemin ortalama parasal değerini izlemeyi içerebilir.

1. <xref:System.Diagnostics.Tracing.IncrementingEventCounter>Her zaman aralığı için çalışan bir toplam kaydeder. <xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType>Yöntemi toplam 'a ekler. Örneğin, `Increment()` ve değerlerini içeren bir Aralık sırasında üç kez çağrılırsa, `1` `2` `5` çalışma toplamı `8` Bu Aralık için sayaç değeri olarak raporlanır. [DotNet-Counters](dotnet-counters.md) Aracı, kaydedilen toplam/saat olarak oranı görüntüler. , <xref:System.Diagnostics.Tracing.IncrementingEventCounter> Saniye başına işlenen istek sayısı gibi bir eylemin ne sıklıkla oluştuğunu ölçmek için yararlıdır.

1. , <xref:System.Diagnostics.Tracing.PollingCounter> Bildirilen değeri belirlemekte bir geri çağırma kullanır. Her zaman aralığı ile, Kullanıcı tarafından girilen geri çağırma işlevi çağrılır ve dönüş değeri sayaç değeri olarak kullanılır. Bir <xref:System.Diagnostics.Tracing.PollingCounter> dış kaynaktan bir ölçümü sorgulamak için, örneğin, bir diskteki geçerli boş baytları almak için kullanılabilir. Ayrıca, bir uygulama tarafından talep üzerine hesaplanmayan özel istatistikleri raporlamak için de kullanılabilir. Örnekler arasında, son istek gecikmelerinin 95. Yüzdeliğini veya bir Önbelleğin geçerli isabet veya isabetsizlik oranını raporlama sayılabilir.

1. , <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> Bildirilen artış değerini tespit etmek için bir geri çağırma kullanır. Her zaman aralığı ile geri çağırma çağrılır ve sonra geçerli çağrı ve son çağırma değeri bildirilen değerdir. [DotNet-Counters](dotnet-counters.md) aracı her zaman bir hız, bildirilen değer/saat olarak farkı görüntüler. Bu sayaç, her bir yerde API çağrısı yapmak uygun olmadığında yararlıdır, ancak toplam oluşum sayısını sorgulamak mümkündür. Örneğin, bir bayt her yazıldığında bir bildirime gerek kalmadan, dosyaya yazılan bayt sayısını rapor edebilirsiniz.

## <a name="implement-an-eventsource"></a>EventSource uygulama

Aşağıdaki kod, <xref:System.Diagnostics.Tracing.EventSource> adlandırılmış sağlayıcı olarak kullanıma sunulan bir örnek uygular `"Sample.EventCounter.Minimal"` . Bu kaynak, bir <xref:System.Diagnostics.Tracing.EventCounter> temsil eden istek işleme süresini içerir. Bu tür bir sayaç, her ikisi de [DotNet-Counter](dotnet-counters.md)gibi dinleyici araçları tarafından kullanılan bir ada (yani, KAYNAKTAKI benzersiz kimliği) ve görünen ada sahiptir.

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

`dotnet-counters ps`İzlenebilecek .net işlemlerinin bir listesini göstermek için kullanırsınız:

```console
dotnet-counters ps
   1398652 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399072 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399112 dotnet     C:\Program Files\dotnet\dotnet.exe
   1401880 dotnet     C:\Program Files\dotnet\dotnet.exe
   1400180 sample-counters C:\sample-counters\bin\Debug\netcoreapp3.1\sample-counters.exe
```

<xref:System.Diagnostics.Tracing.EventSource> `counter_list` Sayaçlarınızı izlemeye başlamak için adı anahtara geçirin:

```console
dotnet-counters monitor --process-id 1400180 Sample.EventCounter.Minimal
```

Aşağıdaki örnek izleme çıkışını gösterir:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Samples-EventCounterDemos-Minimal]
    Request Processing Time (ms)                            0.445
```

İzleme komutunu durdurmak için <kbd>q</kbd> tuşuna basın.

#### <a name="conditional-counters"></a>Koşullu sayaçlar

Bir uygularken <xref:System.Diagnostics.Tracing.EventSource> , <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> Yöntem değeri ile çağrıldığında kapsayan sayaçlar koşullu olarak oluşturulabilir <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> `EventCommand.Enable` . Yalnızca bir sayaç örneğinin güvenli bir şekilde örneğini oluşturmak için `null` , [null birleşim atama işlecini](../../csharp/language-reference/operators/null-coalescing-operator.md)kullanın. Ayrıca, özel yöntemler <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> geçerli olay kaynağının etkinleştirilip etkinleştirilmediğini belirleme yöntemini değerlendirebilir.

:::code language="csharp" source="snippets/EventCounters/ConditionalEventCounterSource.cs":::

> [!TIP]
> Koşullu sayaçlar, mikro iyileştirmede koşullu olarak oluşturulan sayaçlardır. Çalışma zamanı, bir milisaniyenin bir bölümünü kaydetmek için sayaçların normalde kullanılmayan senaryolar için bu stili benimseyen.

### <a name="net-core-runtime-example-counters"></a>.NET Core çalışma zamanı örnek sayaçları

.NET Core çalışma zamanı 'nda çok sayıda harika örnek uygulama vardır. Uygulamanın çalışma kümesi boyutunu izleyen sayaca yönelik çalışma zamanı uygulaması aşağıda verilmiştir.

```csharp
var workingSetCounter = new PollingCounter(
    "working-set",
    this,
    () => (double)(Environment.WorkingSet / 1_000_000))
{
    DisplayName = "Working Set",
    DisplayUnits = "MB"
};
```

, <xref:System.Diagnostics.Tracing.PollingCounter> Bir ölçüm zaman içinde yakalandığından, uygulamanın işlem (çalışma kümesi) ile eşlenen geçerli fiziksel bellek miktarını raporlar. Bir değeri yoklamak için geri çağırma, yalnızca API çağrısı olan, belirtilen lambda ifadesidir <xref:System.Environment.WorkingSet?displayProperty=fullName> . <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName>ve, <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> sayacın Tüketici tarafında değeri daha net bir şekilde görüntüleme konusunda yardımcı olmak üzere ayarlanabilir, isteğe bağlı özelliklerdir. Örneğin, [DotNet sayaçları](dotnet-counters.md) , sayaç adlarının daha kolay görünen bir sürümünü göstermek için bu özellikleri kullanır.

> [!IMPORTANT]
> `DisplayName`Özellikler yerelleştirilmemiş.

, Ve için, <xref:System.Diagnostics.Tracing.PollingCounter> <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> başka hiçbir şeyin gerçekleştirilmesi gerekmez. Bunlar her ikisi de, tüketicinin istediği bir aralıkta değerleri yoklalar.

Kullanılarak uygulanan bir çalışma zamanı sayacı örneği aşağıda verilmiştir <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> .

```csharp
var monitorContentionCounter = new IncrementingPollingCounter(
    "monitor-lock-contention-count",
    this,
    () => Monitor.LockContentionCount
)
{
    DisplayName = "Monitor Lock Contention Count",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

, <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> Toplam kilit çekişmesi sayısı artışını raporlamak için API 'yi kullanır. <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale>Özelliği isteğe bağlıdır, ancak kullanıldığında sayacın en iyi gösterileceği zaman aralığı için bir ipucu sağlayabilir. Örneğin, kilit çakışması sayısı en iyi _sayı_olarak, <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> bir saniye olarak ayarlanır. Görüntüleme ücreti, farklı türlerde hız sayaçlarına göre ayarlanabilir.

> [!NOTE]
> , <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> [DotNet sayaçları](dotnet-counters.md)tarafından kullanılmaz ve olay dinleyicileri bunu kullanmak için gerekli değildir. _not_

[.NET çalışma zamanı](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) deposunda başvuru olarak kullanılacak daha fazla sayaç uygulaması vardır.

## <a name="concurrency"></a>Eşzamanlılık

> [!TIP]
> EventCounters API 'SI iş parçacığı güvenliğini garanti etmez. <xref:System.Diagnostics.Tracing.PollingCounter>Veya örneklerine geçirilen temsilciler <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> birden çok iş parçacığı tarafından çağrıldığında, temsilcilerin iş parçacığı güvenliğini güvence altına almak sizin sorumluluğunuzdadır.

Örneğin, istekleri izlemek için aşağıdakileri göz önünde bulundurun <xref:System.Diagnostics.Tracing.EventSource> .

:::code language="csharp" source="snippets/EventCounters/RequestEventSource.cs":::

`AddRequest()`Yöntemi bir istek işleyicisinden çağrılabilir ve `RequestRateCounter` sayaç tüketicisi tarafından belirtilen aralıktaki değeri yoklar. Ancak, `AddRequest()` yöntemi aynı anda birden çok iş parçacığı tarafından çağrılabilir ve üzerinde bir yarış durumu yerleştirilerek `_requestCount` . İş parçacığı açısından güvenli bir alternatif yöntem `_requestCount` kullanmaktır <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> .

```csharp
public void AddRequest() => Interlocked.Increment(ref _requestCount);
```

## <a name="consume-eventcounters"></a>EventCounters kullanma

EventCounters, işlem içi veya proc dışı kullanmanın iki birincil yolu vardır. EventCounters 'in tüketimi, çeşitli teknolojilerin üç katmanında ayırt edilebilir.

- Etkinlikleri ETW veya EventPipe aracılığıyla ham akışta taşıma:
  - ETW API 'Leri, Windows işletim sistemi ile birlikte gelir ve EventPipe bir [.NET API 'si](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console)veya Diagnostic [IPC Protokolü](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md)olarak erişilebilir.
- İkili olay akışını olaylara çözme:
  - [TraceEvent kitaplığı](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent) hem ETW hem de eventpipe akış biçimlerini işler.
- Komut satırı ve GUI araçları:
  - PerfView (ETW veya EventPipe), DotNet-sayaçlar (yalnızca EventPipe) ve DotNet-Monitor gibi araçlar (yalnızca EventPipe).

### <a name="consume-out-of-proc"></a>İşlem dışı tüketme

İşlem dışı olay sayaçlarını tüketen çok yaygın bir yaklaşım vardır. Bir EventPipe aracılığıyla bunları platformlar arası bir şekilde kullanmak için [DotNet-Counters](dotnet-counters.md) kullanabilirsiniz. `dotnet-counters`Araç, sayaç değerlerini izlemek için kullanılabilen bir platformlar arası DotNet CLI genel aracıdır. `dotnet-counters`Sayaçlarınızı izlemek için ' nin nasıl kullanılacağını öğrenmek için, bkz. [DotNet-Counters](dotnet-counters.md)veya [eventcounters aracılığıyla ölçüm performansı](event-counter-perf.md) aracılığıyla çalışma.

#### <a name="dotnet-trace"></a>dotnet-trace

`dotnet-trace`Araç, bir EventPipe aracılığıyla sayaç verilerini tüketmek için kullanılabilir. Aşağıda, `dotnet-trace` sayaç verilerini toplamak için kullanılan bir örnek verilmiştir.

```console
dotnet-trace collect --process-id <pid> Sample.EventCounter.Minimal:0:0:EventCounterIntervalSec=1
```

Zaman içinde sayaç değerlerini toplama hakkında daha fazla bilgi için bkz. [DotNet-Trace](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time) belgeleri.

#### <a name="azure-application-insights"></a>Azure Application Insights

EventCounters Azure Izleyici tarafından, özellikle Azure Application Insights tüketilebilir. Sayaçlar eklenebilir ve kaldırılabilir ve özel sayaçlar veya iyi bilinen sayaçlar belirtebilirsiniz. Daha fazla bilgi için bkz. [sayaçların toplanmasını sağlamak](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected).

#### <a name="dotnet-monitor"></a>DotNet-izleyici

`dotnet-monitor`Araç, bir .net işlemindeki tanılama bilgilerine erişimi daha kolay hale getiren deneysel bir araçtır. Araç, tüm tanılama araçlarının bir üst kümesi olarak görev yapar. İzlemelere ek olarak, ölçümleri izleyebilir, bellek dökümlerini toplayabilir ve GC dökümlerini toplayabilirler. Hem CLı aracı hem de Docker görüntüsü olarak dağıtılır. Bir REST API sunar ve tanılama yapıtlarının toplanması REST çağrıları aracılığıyla oluşur.

Daha fazla bilgi için bkz. [deneysel bir araç olan DotNet-Monitor](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor).

### <a name="consume-in-proc"></a>İşlem içi tüketme

Sayaç değerlerini API aracılığıyla kullanabilirsiniz <xref:System.Diagnostics.Tracing.EventListener> . <xref:System.Diagnostics.Tracing.EventListener>, Uygulamanızdaki tüm örnekleri tarafından yazılmış olayları kullanmanın işlem içi bir yoludur <xref:System.Diagnostics.Tracing.EventSource> . API 'yi kullanma hakkında daha fazla bilgi için `EventListener` bkz <xref:System.Diagnostics.Tracing.EventListener> ..

İlk olarak, <xref:System.Diagnostics.Tracing.EventSource> sayaç değerini üreten değerin etkinleştirilmesi gerekir. <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType>Oluşturulduğunda bildirim almak için yöntemi geçersiz kılın <xref:System.Diagnostics.Tracing.EventSource> ve bu, <xref:System.Diagnostics.Tracing.EventSource> eventsayaçlarınız ile doğruysa, üzerinde arama yapabilirsiniz <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> . Örnek bir geçersiz kılma aşağıda verilmiştir:

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs" range="16-27":::

#### <a name="sample-code"></a>Örnek kod

Burada <xref:System.Diagnostics.Tracing.EventListener> .NET çalışma zamanının tüm sayaç adlarını ve değerlerini, <xref:System.Diagnostics.Tracing.EventSource> iç sayaçlarını () yayımlamak için bir aralıkta yazdıran örnek bir sınıf verilmiştir `System.Runtime` .

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs":::

Yukarıda gösterildiği gibi, çağrılırken bağımsız değişkenin bağımsız değişkeninde ayarlandığından emin _olmanız gerekir_ `"EventCounterIntervalSec"` `filterPayload` <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A> . Aksi takdirde sayaçlar, hangi zaman boşaltıyoruz olduğunu bilmediğinden, değerleri temizleyemiyor.

## <a name="see-also"></a>Ayrıca bkz.

- [dotnet-counters](dotnet-counters.md)
- [dotnet-trace](dotnet-trace.md)
- <xref:System.Diagnostics.Tracing.EventCounter>
- <xref:System.Diagnostics.Tracing.EventListener>
- <xref:System.Diagnostics.Tracing.EventSource>
