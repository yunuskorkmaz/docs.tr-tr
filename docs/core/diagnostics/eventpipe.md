---
title: EventPipe genel bakış
description: EventPipe hakkında bilgi edinin ve performans sorunlarını tanılamak üzere .NET uygulamalarınızı izlemek için nasıl kullanacağınızı öğrenin.
ms.date: 11/09/2020
ms.topic: overview
ms.openlocfilehash: d30cdf02c3ae300401febe2078dfd3431269c73e
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688575"
---
# <a name="eventpipe"></a>EventPipe

EventPipe, ETW veya LTTng 'e benzeyen izleme verilerini toplamak için kullanılabilen bir çalışma zamanı bileşenidir. EventPipe 'ın amacı, .NET geliştiricilerinin ETW veya LTTng gibi platforma özgü işletim sistemi yerel bileşenlerine güvenmeksizin .NET uygulamalarını kolayca izlemesine izin sağlamaktır.

EventPipe, çoğu tanılama aracının arkasındaki mekanizmadır ve çalışma zamanı tarafından oluşturulan olaylar ve [EventSource](xref:System.Diagnostics.Tracing.EventSource)ile yazılmış özel olaylar için de kullanılabilir.

Bu makale, EventPipe 'ın ne zaman ve nasıl kullanılacağını açıklayan EventPipe 'ın ve gereksinimlerinize en uygun şekilde nasıl yapılandırılacağı hakkında üst düzey bir genel bakıştır.

## <a name="eventpipe-basics"></a>EventPipe temelleri

EventPipe, çalışma zamanı bileşenleri tarafından yayılan olayları toplar-Örneğin, tam zamanında derleyici veya çöp toplayıcı ve kitaplıklarda ve Kullanıcı kodundaki [EventSource](xref:System.Diagnostics.Tracing.EventSource) örneklerinden yazılmış olaylar.

Olaylar daha sonra serileştirilir ve doğrudan bir dosyaya yazılabilir veya bir tanılama bağlantı noktası aracılığıyla bir tanesi tarafından tüketilebilir. Windows 'da tanılama bağlantı noktaları s olarak uygulanır `NamedPipe` . Linux veya macOS gibi Windows dışı platformlarda, Unix etki alanı yuvaları kullanılarak uygulanır. Tanılama bağlantı noktası hakkında daha fazla bilgi ve özel işlem arası iletişim protokolü aracılığıyla bununla etkileşim kurma hakkında daha fazla bilgi için bkz. [Tanılama IPC Protokolü belgeleri](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md).

EventPipe daha sonra seri hale getirilmiş olayları `.nettrace` , tanılama bağlantı noktaları aracılığıyla ya da doğrudan bir dosyaya dosya biçiminde yazar. EventPipe serileştirme biçimi hakkında daha fazla bilgi edinmek için [Eventpipe biçim belgelerine](https://github.com/microsoft/perfview/blob/master/src/TraceEvent/EventPipe/EventPipeFormat.md)bakın.

## <a name="eventpipe-vs-etwlttng"></a>EventPipe ve ETW/LTTng karşılaştırması

EventPipe, .NET çalışma zamanının (CoreCLR) bir parçasıdır ve .NET Core 'un desteklediği tüm platformlarda aynı şekilde çalışacak şekilde tasarlanmıştır. Bu,, ve gibi EventPipe tabanlı izleme araçlarının `dotnet-counters` `dotnet-gcdump` `dotnet-trace` platformlar arasında sorunsuz bir şekilde çalışmasını sağlar.

Ancak, EventPipe bir çalışma zamanı yerleşik bileşeni olduğundan, kapsamı yönetilen kodla ve çalışma zamanının kendisi ile sınırlıdır. EventPipe, yerel kod yığınını çözümleme veya çeşitli çekirdek olayları alma gibi bazı alt düzey olayları izlemek için kullanılamaz. Uygulamanızda C/C++ birlikte çalışabiliri veya çalışma zamanının kendisini (C++ dilinde yazılmış) izlemek isterseniz ya da bir uygulamanın, çekirdek olayları gerektiren (yani, yerel iş parçacığı bağlamı değiştirme olayları) uygulama davranışına daha derin tanılama yapmak istiyorsanız, ETW veya [perf/LTTng](./trace-perfcollect-lttng.md)kullanmanız gerekir.

EventPipe ile ETW/LTTng arasındaki diğer önemli fark, yönetici/kök ayrıcalık gereksinimidir. ETW veya LTTng kullanarak bir uygulamayı izlemek için yönetici/kök olmanız gerekir. EventPipe kullanarak, izleyici (örneğin, `dotnet-trace` ) uygulamayı başlatan kullanıcıyla aynı kullanıcı olarak çalıştırıldığı sürece uygulamaları izleyebilirsiniz.

Aşağıdaki tabloda EventPipe ile ETW/LTTng arasındaki farkların bir özeti verilmiştir.

|Öne çıkan özelliği|EventPipe|ETW|Lttng kullanılabilir|
|-------|---------|---|-----------|
|Platformlar arası|Yes|Hayır (yalnızca Windows üzerinde)|Hayır (yalnızca desteklenen Linux 'ları destekler)|
|Yönetici/kök ayrıcalığı iste|Hayır|Yes|Yes|
|İşletim sistemi/çekirdek olayları alabilir|Hayır|Yes|Yes|
|Yerel çağrı yığınlarını çözümleyebilir|Hayır|Yes|Yes|

## <a name="use-eventpipe-to-trace-your-net-application"></a>.NET uygulamanızı izlemek için EventPipe 'ı kullanma

.NET uygulamanızı birçok şekilde izlemek için EventPipe kullanabilirsiniz:

* EventPipe 'ın üzerine inşa edilen [tanılama araçlarından](#tools-using-eventpipe) birini kullanın.

* EventPipe oturumlarını kendiniz yapılandırmak ve başlatmak için kendi aracınızı yazmak üzere [Microsoft. Diagnostics. NETCore. Client](https://github.com/dotnet/diagnostics/blob/master/documentation/diagnostics-client-library-instructions.md) kitaplığını kullanın.

* EventPipe 'ı başlatmak için [ortam değişkenlerini](#trace-using-environment-variables) kullanın.

`nettrace`EventPipe olaylarınızı içeren bir dosya oluşturduktan sonra, dosyayı [`PerfView`](https://github.com/Microsoft/perfview#perfview-overview) veya Visual Studio 'yu görüntüleyebilirsiniz. Windows dışı platformlarda, `nettrace` `speedscope` komutunu kullanarak dosyayı bir veya `Chromium` izleme biçimine dönüştürebilir [`dotnet-trace convert`](./dotnet-trace.md#dotnet-trace-convert) ve [`speedscope`](https://www.speedscope.app/) ya da Chrome DevTools ile görüntüleyebilirsiniz.

Ayrıca, EventPipe izlemelerini [TraceEvent](https://github.com/Microsoft/perfview/blob/master/documentation/TraceEvent/TraceEventLibrary.md)ile programlı bir şekilde çözümleyebilirsiniz.

### <a name="tools-that-use-eventpipe"></a>EventPipe kullanan araçlar

Bu, uygulamanızı izlemek için EventPipe kullanmanın en kolay yoludur. Bu araçların her birini kullanma hakkında daha fazla bilgi edinmek için, her aracın belgelerine bakın.

* [DotNet sayaçları](./dotnet-counters.md) , .NET çalışma zamanı ve çekirdek kitaplıkları tarafından yayılan çeşitli ölçümleri izlemenize ve toplamanıza olanak sağlar.

* [DotNet-gcdump](./dotnet-gcdump.md) , uygulamanın yönetilen yığınını çözümlemek için canlı işlemlerin GC yığın dökümünü toplamanıza olanak tanır.

* [DotNet-Trace](./dotnet-trace.md) , performans için analiz edilecek uygulama izlemelerini toplamanıza olanak tanır.

## <a name="trace-using-environment-variables"></a>Ortam değişkenlerini kullanarak izleme

EventPipe kullanımı için tercih edilen mekanizma, `dotnet-trace` veya `Microsoft.Diagnostics.NETCore.Client` kitaplığını kullanmaktır.

Ancak, bir uygulamada EventPipe oturumu ayarlamak ve izlemeyi doğrudan bir dosyaya yazmak için aşağıdaki ortam değişkenlerini kullanabilirsiniz. İzlemeyi durdurmak için uygulamadan çıkın.

* `COMPlus_EnableEventPipe`: `1` Doğrudan bir dosyaya yazan bir EventPipe oturumu başlatmak için bunu olarak ayarlayın. `0` varsayılan değerdir.

* `COMPlus_EventPipeOutputPath`: Üzerinden çalışacak şekilde yapılandırıldığında çıkış EventPipe izleme dosyasının yolu `COMPlus_EnableEventPipe` . Varsayılan değer `trace.nettrace` , uygulamanın üzerinde çalıştığı aynı dizinde oluşturulacak olur.

* `COMPlus_CircularBufferMB`: İle çalışacak şekilde yapılandırıldığında EventPipe tarafından kullanılan iç arabelleğin boyutu `COMPlus_EnableEventPipe` .

* `COMPlus_EventPipeConfig`: EventPipe oturumu başlatılırken EventPipe oturum yapılandırmasını ayarlar `COMPlus_EnableEventPipe` .

  Söz dizimi şu şekildedir:

  `<provider>:<keyword>:<level>`

  Ayrıca, birden çok sağlayıcıyı virgülle ayırarak belirtebilirsiniz:

  `<provider1>:<keyword1>:<level1>,<provider2>:<keyword2>:<level2>`

  Bu ortam değişkeni ayarlanmamışsa ancak EventPipe tarafından etkinleştirilmişse, aşağıdaki aşağıdaki `COMPlus_EnableEventPipe` anahtar sözcükler ve Düzeyler ile aşağıdaki sağlayıcıları etkinleştirerek izleme başlatılır:

  - `Microsoft-Windows-DotNETRuntime:4c14fccbd:5`
  - `Microsoft-Windows-DotNETRuntimePrivate:4002000b:5`
  - `Microsoft-DotNETCore-SampleProfiler:0:5`
