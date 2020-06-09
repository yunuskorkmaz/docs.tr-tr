---
title: Etkinlik
ms.date: 03/30/2017
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
ms.openlocfilehash: 41de6b9458feb4e1898eeac6635b74c4617885d6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602147"
---
# <a name="activity"></a>Etkinlik
Bu konuda Windows Communication Foundation (WCF) izleme modelindeki etkinlik izlemeleri açıklanmaktadır. Etkinlikler, kullanıcının bir hata kapsamını daraltmaya yardımcı olan birimleri işliyor. Aynı etkinlikte oluşan hatalar doğrudan ilgilidir. Örneğin, ileti şifre çözme işlemi başarısız olduğundan bir işlem başarısız olur. Hem işlem hem de ileti şifre çözme hatasının izlemeleri aynı etkinlikte görünür ve şifre çözme hatası ile istek hatası arasında doğrudan bağıntı gösteriliyor.  
  
## <a name="configuring-activity-tracing"></a>Etkinlik Izlemeyi yapılandırma  
 WCF, uygulamaları işlemek için önceden tanımlanmış etkinlikler sağlar (bkz. [etkinlik listesi](activity-list.md)). Ayrıca, Kullanıcı izlemelerini gruplamak için etkinlik programlama yoluyla da tanımlayabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı kodu Izlemelerini yayma](emitting-user-code-traces.md).  
  
 Çalışma zamanında etkinlik izlemelerini yaymak için, `ActivityTracing` `System.ServiceModel` aşağıdaki yapılandırma kodu tarafından gösterildiği gibi izleme kaynağı veya diğer WCF veya özel izleme kaynakları için ayarı kullanın.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Kullanılan yapılandırma öğesi ve öznitelikleri hakkında daha fazla bilgi edinmek için [Izleme yapılandırma](configuring-tracing.md) konusuna bakın.  
  
## <a name="viewing-activities"></a>Etkinlikleri görüntüleme  
 Etkinlikleri ve yardımcı programını [hizmet Izleme Görüntüleyicisi aracında (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)görebilirsiniz. ActivityTracing etkinleştirildiğinde, bu araç izlemeleri alır ve bunları etkinliğe göre sıralar. İzleme aktarımlarını de görebilirsiniz. Bir izleme aktarımı, farklı etkinliklerin birbirleriyle nasıl ilişkili olduğunu gösterir. Belirli bir etkinliğin bir diğerinin başlamasını neden olduğunu görebilirsiniz. Örneğin, bir ileti isteği güvenli konuşma belirteci almak için bir güvenlik anlaşmasını başlattı.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Hizmet Izleme görüntüleyicisinde etkinlikleri ilişkilendirme  
 Hizmet Izleme Görüntüleyicisi aracı iki etkinlik görünümü sağlar:  
  
- Etkinlik KIMLIĞININ süreçler genelinde izlemeleri doğrudan ilişkilendirmek için kullanıldığı **liste** görünümü. Farklı süreçlerden (örneğin, istemci ve hizmet) izler, ancak aynı etkinlik kimliği ile aynı etkinlik kimliğine sahip bir şekilde gruplandırılır. Bu nedenle, hizmette oluşan bir hata, bu durumda istemcide bir hata oluşmasına neden olur ve araç içinde aynı etkinlik görünümünde görünür.  
  
- Etkinliklerin işlemlere göre gruplandırıldığı **grafik** görünümü. Bu görünümde, aynı etkinlik KIMLIĞINE sahip bir istemci ve hizmetin izlemeleri farklı etkinliklerde vardır. Farklı işlemlerdeki aynı etkinlik KIMLIĞINE sahip etkinlikleri ilişkilendirmek için, araç ilgili etkinliklerin tamamında ileti akışlarını gösterir.  
  
 Daha fazla bilgi edinmek ve hizmet Izleme Görüntüleyicisi aracının grafik bir görünümünü görmek için, bkz. [hizmet izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md) ve [bağıntılı Izlemeleri ve sorun gidermeyi görüntülemek Için hizmet Izleme Görüntüleyicisi 'ni kullanma](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Etkinliğin kapsamını tanımlama  
 Bir etkinlik tasarım zamanında tanımlanır ve mantıksal bir iş birimi gösterir. Aynı etkinlik tanımlayıcısına sahip olan izlemeler doğrudan ilgili olarak aynı etkinliğin bir parçasıdır. Bir etkinlik uç nokta sınırlarını (bir istek) çapraz bir şekilde sağladığından, bir etkinliğin iki kapsamı tanımlanmıştır.  
  
- `Global`kapsam, uygulama başına. Bu kapsamda etkinlik, 128 bitlik genel benzersiz etkinlik tanımlayıcısı, gAId tarafından tanımlanır. GAId, uç noktalar genelinde yayılmış şeydir.  
  
- `Local`kapsam, uç nokta başına. Bu kapsamda etkinlik, gAId ile tanımlanır ve etkinlik izlemelerini ve işlem kimliğini yayan izleme kaynak adı ile birlikte kullanılır. Bu, yerel etkinlik kimliğini oluşturur, düzenlenir. Bu, bir etkinliğin (yerel) sınırlarını tanımlamak için kullanılır.  
  
## <a name="trace-schema"></a>İzleme şeması  
 İzlemeler, herhangi bir şema kullanılarak ve Microsoft platformları arasında dağıtılabilir. "e2e" ("uçtan uca" için), yaygın olarak kullanılan bir şemadır. Bu şema, 128 bitlik bir tanımlayıcı (gAId), izleme kaynağı adı ve işlem KIMLIĞI içerir. Yönetilen kodda, <xref:System.Diagnostics.XmlWriterTraceListener> e2e şemasında izlemeleri yayar.  
  
 Geliştiriciler, <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> Iş parçacığı yerel depolama (TLS) üzerinde bir GUID ile özelliği ayarlayarak, bir izleme ile YAYıLAN yardımı ayarlayabilir. Aşağıdaki örnek bunu gösterir.  
  
```csharp
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```
  
 Aşağıdaki örnekte gösterildiği gibi, izlemeler bir izleme kaynağı kullanılarak yayıldığınızda, TLS 'de gAId 'nin ayarlanması de görünmez.  
  
```csharp
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 Bu izleme, şu anda TLS 'de bulunan gAId 'yi, izleme kaynağının oluşturucusuna parametre olarak geçirilen izleme kaynağı adını ve geçerli işlemin KIMLIĞINI içerecektir.  
  
## <a name="activity-lifetime"></a>Etkinlik ömrü  
 En katı koşullarında, bir etkinliğin kanıtı, etkinlik kimliği, yayımlanan bir izlemede ilk kez kullanıldığında başlar ve bu, yayımlanan bir izlemede son kullanıldığı zamanı sonlandırır. <xref:System.Diagnostics>Etkinlik ömrü sınırlarını açıkça işaretlemek için, başlangıç ve durdurma dahil olmak üzere, tarafından önceden tanımlanmış bir izleme türleri kümesi sağlanır.  
  
- Başlat: bir etkinliğin başlangıcını gösterir. "Başlat" izlemesi, yeni bir işleme kilometre taşını başlangıç kaydını sağlar. Etkinlik KIMLIĞININ uç noktalara yayıldığı durumlar dışında, belirli bir işlemde belirli bir izleme kaynağı için yeni bir etkinlik KIMLIĞI içerir. Bu durumda, uç nokta başına bir "başlangıç" görüyoruz. Yeni bir etkinlik başlatma örnekleri, işlenmek üzere yeni bir iş parçacığı oluşturmayı veya yeni bir ortak yöntemi girmeyi içerir.  
  
- Durdur: bir etkinliğin sonunu gösterir. "Durdur" izlemesi, var olan bir işlem kilometre taşını sona erdirme kaydı sağlar. Etkinlik KIMLIĞININ uç noktalara yayıldığı durumlar dışında, belirli bir işlemde belirli bir izleme kaynağı için var olan bir etkinlik KIMLIĞI içerir. Bu durumda, uç nokta başına bir "Durdur" görüyoruz.  Bir etkinliği durdurma örnekleri bir işleme iş parçacığını sonlandırarak veya başlangıcı "Başlat" izleme ile belirtilen bir yöntemden çıkmadan oluşur.  
  
- Askıya al: bir etkinliğin işlenmesinin askıya alınma durumunu gösterir. "Askıya alma" izlemesi, işlemenin daha sonra sürdürülmesi beklenen mevcut bir etkinlik KIMLIĞINI içerir. Geçerli izleme kaynağından askıda kalma ve sürdürülme olayları arasında bu KIMLIKLE hiçbir izleme yok. Örneğin, bir dış kitaplık işlevine çağrı yaparken veya g/ç tamamlama bağlantı noktası gibi bir kaynakta beklerken bir etkinliğin duraklatılması sayılabilir.  
  
- Özgeçmişi: bir etkinliğin işleme sürdürme gösterir. "Özgeçmişi" izlemesi, geçerli izleme kaynağından son yayınlanan izleme "askıya al" iziydi. Örnek olarak, bir dış kitaplık işlevine yapılan çağrıdan veya g/ç tamamlama bağlantı noktası gibi bir kaynak tarafından işlemeyi sürdürecek şekilde sinyallerden geri dönme sayılabilir.  
  
- Aktarım: bazı etkinliklere başkaları neden olduğu veya diğer kullanıcılarla ilişkili olduğu için, etkinlikler "aktarım" izlemeleriyle diğer etkinliklerle ilgili olabilir. Aktarım, bir etkinliğin bir diğer öğesine yönlendirilmiş ilişkisini kaydeder  
  
 Bağıntı için başlatma ve durdurma izlemeleri önemli değildir. Bununla birlikte, performans, profil oluşturma ve etkinlik kapsamı doğrulamasının artması konusunda yardımcı olabilirler.  
  
 Araçlar, bu türleri kullanarak, aynı etkinliğin anında ilgili olaylarını veya araç aktarım izlemelerinizi izliyorsa ilgili etkinliklerdeki olayları bulmak için izleme günlüklerinde gezinmeyi en uygun hale getirebilir. Örneğin, araçlar bir Başlat/Durdur izlemesi görtiklerinde belirli bir etkinliğin günlüklerini ayrıştırmayı durdurur.  
  
 Bu izleme türleri, profil oluşturma için de kullanılabilir. Başlangıç ve durdurma işaretçileri arasında tüketilen kaynaklar, içerilen mantıksal etkinlikler dahil olmak üzere etkinliğin dahil edilen süresini temsil eder. Askıya alma ve özgeçmişi izlemeleri arasındaki zaman aralıklarını çıkarmak gerçek etkinlik süresini sağlar.  
  
 Durdurma izlemesi, uygulanan etkinliklerin kapsamını doğrulamak için de özellikle yararlıdır. Belirli bir etkinlik yerine durdurma izlemesinden sonra bazı işleme izlemeleri görünürse, bu kod hata durumunda olabilir.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Etkinlik Izlemeyi kullanmaya yönelik yönergeler  
 Aşağıda, ActivityTracing izlemelerinin (başlatma, durdurma, askıya alma, özgeçmişi ve aktarım) kullanımı hakkında bir kılavuz verilmiştir.  
  
- İzleme, ağaç değil, yönlendirilmiş bir döngüsel grafiktir. Bir etkinliği oluşturan bir etkinliğe denetim getirebilirsiniz.  
  
- Bir etkinlik, sistemin yöneticisine veya desteklenebilirliği açısından anlamlı olabilen bir işleme sınırını gösterir.  
  
- Hem istemci hem de sunucu üzerinde her bir WCF Yöntemi yeni bir etkinlik başlatarak, sonra (çalışma yapıldıktan sonra) yeni etkinliği sonlandırarak çevresel etkinliğe geri dönerek sınırlanır.  
  
- Bağlantı dinlemek veya ileti bekleniyor gibi uzun süre çalışan (devam eden) Etkinlikler, ilgili başlatma/durdurma işaretçileri tarafından temsil edilir.  
  
- Bir iletinin alınması veya işlenmesi tarafından tetiklenen etkinlikler, izleme sınırları ile temsil edilir.  
  
- Etkinlikler, nesneleri değil, etkinlikleri temsil eder. Etkinlik "Bu oluştu. . . (anlamlı izleme egörev gerçekleşti). "  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlemeyi Yapılandırma](configuring-tracing.md)
- [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma ](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Uçtan Uca İzleme Senaryoları](end-to-end-tracing-scenarios.md)
- [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
- [Kullanıcı Kodu İzleri Yayma](emitting-user-code-traces.md)
