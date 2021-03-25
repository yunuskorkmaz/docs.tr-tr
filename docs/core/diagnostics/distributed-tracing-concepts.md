---
title: Dağıtılmış izleme kavramları-.NET
description: .NET dağıtılmış izleme kavramları
ms.date: 03/14/2021
ms.openlocfilehash: 368cb545b9928534766e3005992a7a55571b8dcc
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111573"
---
# <a name="net-distributed-tracing-concepts"></a>.NET dağıtılmış Izleme kavramları

Dağıtılmış izleme, özellikle birden çok makineye veya işleme dağılmış olabilecek uygulamalarda hataları ve performans sorunlarını yerelleştirebilmenizi sağlayan bir tanılama tekniğidir. Dağıtılmış izlemenin yararlı olduğu ve başlamak için örnek kod gibi genel bilgiler için [Dağıtılmış Izlemeye genel bakış](distributed-tracing.md) bölümüne bakın.

### <a name="traces-and-activities"></a>İzlemeler ve Etkinlikler

Bir uygulama tarafından her yeni istek alındığında, bir izleme ile ilişkilendirilebilir. .NET ' te yazılan uygulama bileşenlerinde, bir izlemede iş birimleri, <xref:System.Diagnostics.Activity?displayProperty=nameWithType> Bu etkinliklerin bir bütün olarak, büyük olasılıkla birçok farklı işleme yayılmış olan örnekleri tarafından temsil edilir. Yeni bir istek için oluşturulan ilk etkinlik, izleme ağacının kökünü oluşturur ve isteği işleyen genel süreyi ve başarıyı/başarısızlığını izler. Alt etkinlikler, çalışmayı ayrı ayrı izlenebilecek farklı adımlara alt bölmek için isteğe bağlı olarak oluşturulabilir.
Örneğin, bir Web sunucusunda belirli bir gelen HTTP isteğini izleyen bir etkinlik veriliyorsa, isteği tamamlaması gereken veritabanı sorgularının her birini izlemek için alt etkinlikler oluşturulabilir. Bu, her sorgunun süresini ve başarısını bağımsız olarak kaydetmek için izin verir.
Etkinlikler <xref:System.Diagnostics.Activity.OperationName> , ad-değer çiftleri ve olarak adlandırılan her bir iş birimi için diğer bilgileri kaydedebilir <xref:System.Diagnostics.Activity.Tags> <xref:System.Diagnostics.Activity.Events> . Ad, gerçekleştirilen iş türünü tanımlar, Etiketler çalışmanın açıklayıcı parametrelerini kaydedebilir ve olaylar, zaman damgası alınan tanılama iletilerini kaydetmek için basit bir günlüğe kaydetme mekanizmasıdır.

> [!NOTE]
> Dağıtılmış bir izlemede iş birimleri için başka bir ortak sektör adı ' yaymalar '.
> .NET, bu kavram için ' span ' adının iyi bir şekilde kurulmadan önce, ' Activity ' koşulunu çok yıl önce benimsedi.

### <a name="activity-ids"></a>Etkinlik Kimlikleri

Dağıtılmış izleme ağacındaki etkinlikler arasındaki Parent-Child ilişkiler benzersiz kimlikler kullanılarak oluşturulur. . NET ' in dağıtılmış izleme, .NET 5 ' te varsayılan olan W3C standart [TraceContext](https://www.w3.org/TR/trace-context/) ve geriye dönük uyumluluk için kullanılabilen ' sıradüzensel ' adlı eski bir .net kuralı olan iki kimlik şemasını destekler.
<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> Hangi KIMLIK şemasının kullanıldığını denetler. W3C TraceContext Standard 'da her izlemeye, genel olarak benzersiz bir 16 baytlık Trace-ID ( <xref:System.Diagnostics.Activity.TraceId?displayProperty=nameWithType> ) atanır ve izleme içindeki her etkinliğe benzersiz bir 8 baytlık span ID ( <xref:System.Diagnostics.Activity.SpanId?displayProperty=nameWithType> ) atanır. Her etkinlik, izleme kimliği, kendi yayılma kimliği ve üst öğesinin () span ID 'sini kaydeder <xref:System.Diagnostics.Activity.ParentSpanId?displayProperty=nameWithType> . Dağıtılmış izlemeler işlem sınırları genelinde çalışmayı izleyebildiğinden ve alt etkinlikler aynı süreçte bulunmayabilir. Bir izleme kimliği ve üst yayılma kimliği birleşimi, içinde hangi işlemden bağımsız olarak üst etkinliği genel olarak tanımlayabilir.

<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> Yeni izlemeler başlatmak için kullanılan KIMLIK biçimini denetler, ancak varsayılan olarak var olan bir izlemeye yeni bir etkinlik eklendiğinde üst etkinliğin kullandığı biçim kullanılır.
<xref:System.Diagnostics.Activity.ForceDefaultIdFormat?displayProperty=nameWithType>True olarak ayarlamak bu davranışı geçersiz kılar ve üst öğe farklı bır kimlik biçimi kullandığında bile Defaultıdformat ile tüm yeni etkinlikleri oluşturur.

### <a name="starting-and-stopping-activities"></a>Etkinlikleri başlatma ve durdurma

Bir işlemdeki her iş parçacığının, aracılığıyla erişilebilen, bu iş parçacığında iş işlemesini izleyen karşılık gelen bir etkinlik nesnesi olabilir <xref:System.Diagnostics.Activity.Current?displayProperty=nameWithType> . Geçerli etkinlik, iş parçacığı üzerindeki tüm zaman uyumlu çağrıların yanı sıra farklı iş parçacıklarında işlenen zaman uyumsuz çağrıları otomatik olarak akar. A etkinliği bir iş parçacığında geçerli etkinlik ise ve kod yeni bir etkinliği başlattığında b Bu iş parçacığında yeni geçerli etkinlik olur. Varsayılan etkinlik B, etkinlik A 'nın üst öğesi olarak da değerlendirilir. Etkinlik B daha sonra durdurulduğunda, etkinlik iş parçacığında geçerli etkinlik olarak geri yüklenir. Bir etkinlik başlatıldığında, geçerli saati olarak yakalar <xref:System.Diagnostics.Activity.StartTimeUtc?displayProperty=nameWithType> . Durdurulduğunda, <xref:System.Diagnostics.Activity.Duration?displayProperty=nameWithType> geçerli saat ile başlangıç saati arasındaki fark olarak hesaplanır.

### <a name="coordinating-across-process-boundaries"></a>İşlem sınırları genelinde koordine etme

İşlem sınırları genelinde çalışmayı izlemek için, alıcı işlemin bunlara başvuran etkinlikler oluşturabilmesi için üst kimliklerin ağ üzerinden aktarılması gerekir. W3C TraceContext ID biçimi .NET kullanılırken, bu bilgileri aktarmak için [Standart](https://www.w3.org/TR/trace-context/) tarafından önerilen http üst bilgileri de kullanılır. <xref:System.Diagnostics.ActivityIdFormat.Hierarchical>.Net ID biçimi kullanıldığında, kimliği iletmek için özel bir istek KIMLIĞI http üstbilgisi kullanır. Diğer birçok dilin aksine, ASP.NET Web Server ve System .NET gibi .NET yerleşik kitaplıkları. http yerel olarak HTTP iletilerinde etkinlik kimliklerinin kodunu nasıl çözebileceğinizi ve kodlayacağınızı anlayın. Çalışma zamanı ayrıca KIMLIĞI, eşzamanlı ve zaman uyumsuz çağrılar aracılığıyla nasıl akakullanacağınızı de anlamıştır. Bu, HTTP iletilerini alan ve oluşturan .NET uygulamalarının, uygulama geliştiricisi veya üçüncü taraf kitaplığı bağımlılıkları tarafından özel bir kodlama olmadan otomatik olarak akış dağıtılmış izleme kimliklerine katılmasına yol gösterir. 3. taraf kitaplıklar, HTTP olmayan ileti protokolleri üzerinden kimlik iletme veya HTTP için özel kodlama kurallarını destekleme desteği ekleyebilir.

### <a name="collecting-traces"></a>İzlemeleri toplama

Belgelenmiş kod <xref:System.Diagnostics.Activity> , dağıtılmış izlemenin bir parçası olarak nesneler oluşturabilir, ancak tüm izlemenin daha sonra tam olarak gözden geçirilmesi için bu nesnelerdeki bilgilerin merkezi bir persistant deposunda iletilmesi ve serileştirilmesi gerekir. Bu görevi [Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing), [opentelemetri](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md)veya bir 3. taraf telemetri ya da APM satıcısı tarafından sunulan bir kitaplık gibi yapabilen birkaç telemetri toplama kitaplığı vardır. Alternatif geliştiriciler, veya kullanarak kendi özel etkinlik telemetri toplamasını yazabilir <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> <xref:System.Diagnostics.DiagnosticListener?displayProperty=nameWithType> . ActivityListener, geliştiricinin BT hakkında bir öncelik bilgisine sahip olup olmamasına bakılmaksızın tüm etkinlikleri gözlemlerken destekler.
Bu, ActivityListener 'ı basit ve esnek bir genel amaçlı çözüm haline getirir. DiagnosticListener 'ın aksine, açılan kodun çağırarak yerine kullanmasını gerektiren daha karmaşık bir senaryo ve koleksiyon kitaplığı, başlatıldığında izlenen <xref:System.Diagnostics.DiagnosticSource.StartActivity%2A?displayProperty=nameWithType> kodun kullandığı tam adlandırma bilgilerini bilmelidir. DiagnosticSource ve DiagnosticListener kullanmak, Oluşturucu ve dinleyicinin rastgele .NET nesnelerini alışverişi ve özelleştirilmiş bilgi geçirme kuralları oluşturmasını sağlar.

### <a name="sampling"></a>Örnekleme

Yüksek işleme uygulamalarında geliştirilmiş performans için, .NET üzerinde dağıtılmış izleme, tümünü kaydetmek yerine yalnızca izlemelerin bir alt kümesini örneklemeyi destekler. Önerilen API ile oluşturulan faaliyetlerini için <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> telemetri toplama kitaplıkları geri çağırma ile örneklemesi denetleyebilir <xref:System.Diagnostics.ActivityListener.Sample%2A?displayProperty=nameWithType> .
Günlüğe kaydetme kitaplığı, etkinliğin hiç bir şekilde oluşturulmasını, dağıtım izleme kimliklerini yaymak için gereken en az bilgilerle oluşturmayı veya bir bütün tanılama bilgilerini doldurmayı tercih edebilir. Bu seçimler, daha fazla tanılama yardımcı programı için performans yükünü artırmaya yönelik ticareti kapatıyor. ' Nin eski ve çağırma düzeniyle başlatılan etkinlikler, <xref:System.Diagnostics.Activity.%23ctor%2A?displayProperty=nameWithType> <xref:System.Diagnostics.DiagnosticSource.StartActivity%2A?displayProperty=nameWithType> önce çağırarak diagnosticlistener örneklemesi de destekleyebilir <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A?displayProperty=nameWithType> .
Tam tanılama bilgilerini yakalarken bile, .NET uygulamasına yönelik etkili bir toplayıcıyla hızlı bir şekilde bağlanmış olacak şekilde tasarlanan bir etkinlik oluşturulabilir, doldurulabilir ve modern donanımda mikro saniye içinde iletilebilir. Örnekleme, kayıtlı olmayan her etkinlik için 100 nanosaniye 'tan az olan izleme maliyetini azaltabilir.

## <a name="next-steps"></a>Sonraki adımlar

.NET uygulamalarında dağıtılmış izlemeyi kullanmaya başlamak için bkz. [Dağıtılmış Izlemeye genel bakış](distributed-tracing.md) örneğin kod.
