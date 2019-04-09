---
title: Etkinlik
ms.date: 03/30/2017
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
ms.openlocfilehash: b93960d4006499c935c27ee18e066d091632d3d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170215"
---
# <a name="activity"></a>Etkinlik
Bu konu, Windows Communication Foundation (WCF) izleme modelinde etkinlik izlemeleri açıklar. Etkinlikler işlem hata kapsamını daraltmak kullanıcı Yardımı birimleri. Aynı etkinlik içinde oluşan hataları doğrudan ilişkilidir. Örneğin, ileti şifre çözme başarısız olduğundan işlem başarısız olur. Şifre çözme hatası ve istek hatası arasında doğrudan bağıntı gösteren aynı etkinliğinde, hem işlem hem de şifre çözme hatası iletisi izlemelerini görünür.  
  
## <a name="configuring-activity-tracing"></a>Etkinlik izlemeyi yapılandırma  
 WCF işleme uygulamaları için önceden tanımlanmış etkinlikleri sağlar (bkz [etkinlik listesi](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)). Etkinlikler de program aracılığıyla ve grup kullanıcı izlemelere tanımlayabilirsiniz. Daha fazla bilgi için [kullanıcı kodu izlemeleri yayma](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
 Çalışma zamanında etkinlik izlemeleri yayma kullanın `ActivityTracing` ayarını `System.ServiceModel` izleme kaynağına veya diğer WCF veya özel izleme kaynakları, aşağıdaki yapılandırma kodda gösterildiği gibi.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Yapılandırma öğesi ve kullanılan öznitelikler hakkında daha fazla bilgi için bkz: [yapılandırma izleme](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) konu.  
  
## <a name="viewing-activities"></a>Etkinlikleri görüntüleme  
 Etkinlikler ve bunların yardımcı programı görüntüleyebileceğiniz [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). ActivityTracing etkinleştirildiğinde, bu aracı izlemelerini alır ve bunları etkinliklere göre sıralar. İzleme aktarımları da görebilirsiniz. Bir izleme aktarımı nasıl farklı etkinlikleri gösterir birbirleriyle ilişkili. Belirli bir etkinlik başlatmak başka bir neden olduğunu görebilirsiniz. Örneğin, bir güvenli konuşma belirteci almak için bir güvenlik el sıkışması iletisi İsteği başlatıldı.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Hizmet izleme görüntüleyicisini etkinlikleri ilişkilendirme  
 Hizmet izleme Görüntüleyicisi aracı etkinliklerinin iki görünüm sağlar:  
  
-   **Liste** izlemeleri süreçler arasında doğrudan bağıntı kurmak için etkinlik kimliği kullanıldığı görünümü. İzlemeler farklı işlemler, örneğin, istemciyi ve hizmeti ancak aynı etkinlik kimliği ile aynı etkinliğin gruplandırılır. Bu nedenle, ardından istemcide bir hata neden hizmetinde gerçekleşen bir hata her ikisi de aynı aracı etkinlik görünümünde gösterilir.  
  
-   **Graf** nerede etkinlikleri gruplanır işlemler tarafından görünümü. Bu görünümde, bir istemci ve aynı etkinlik kimliği hizmetiyle farklı etkinlikleri, izlemeleri sahip. Etkinlikler farklı işlemlerdeki aynı etkinlik kimliği ile ilişkilendirmek için aracı ileti akışları arasında ilgili etkinlikleri gösterir.  
  
 Daha fazla bilgi ve hizmet izleme Görüntüleyicisi aracı grafik bir görünümünü görmek için bkz. [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ve [ilişkilendirilmiş izlemeleri görüntülemek için hizmet izleme görüntüleyicisini kullanma ve Sorun giderme](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Bir etkinlik kapsamını tanımlama  
 Bir etkinliğin tasarım zamanında tanımlanır ve bir mantıksal birim iş gösterir. Aynı etkinlik tanımlayıcısı yayılan izlemeleri doğrudan ilgili, aynı etkinliğin parçasıdır. Etkinlik bitiş noktası sınırları (istek) aşabileceğinden bir etkinlik için iki kapsamı tanımlanır.  
  
-   `Global` uygulama başına kapsam. Bu kapsamda etkinlik, 128 bit genel olarak benzersiz bir etkinlik tanımlayıcısı, gAId tanımlanır. Uç noktalar genelinde yayılır gAid olur.  
  
-   `Local` uç noktası başına kapsam. Bu kapsamda etkinliğin etkinlik izlemeleri ve işlem kimliği yayma izleme kaynak adı ile birlikte kendi gAId tanımlanır Bu Üçlü düzenlenir, yerel etkinlik kimliği oluşturur. Düzenlenir, bir etkinlik (yerel) sınırlarını tanımlamak için kullanılır.  
  
## <a name="trace-schema"></a>İzleme şeması  
 İzlemeler yayılan herhangi bir şema kullanılarak ve Microsoft platformlarında. "e2e" ("uçtan uca" için) yaygın olarak kullanılan bir şema var. Bu şema 128 bit tanımlayıcı (gAId), izleme kaynak adını ve işlem kimliği içerir. Yönetilen kodda <xref:System.Diagnostics.XmlWriterTraceListener> E2E şema izlemelerinde yayar.  
  
 Geliştiriciler, bir izleme ile ayarlayarak yayıldığını yardımcı ayarlayabilirsiniz <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> özellik üzerinde iş parçacığı yerel depolaması (TLS) GUID. Aşağıdaki örnekte bu gösterir.  
  
```csharp
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```
  
 İzlemeleri bir izleme kaynağı kullanarak aşağıdaki örnekte gösterildiği gibi gönderilir, gAId TLS'ye ayarlama yetkisiz değiştirmeye karşı korumalı hale gelir.  
  
```csharp
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 TLS, izleme kaynağının oluşturucusu ve geçerli işlemin kimliği için bir parametre olarak geçirilen izleme kaynak adı, şu anda gAId yayılan izleme içerir  
  
## <a name="activity-lifetime"></a>Etkinlik yaşam süresi  
 En katı bağlamında, kanıt etkinliğin etkinlik kimliği yayılan bir izlemede kullanılır ve yayılan bir izlemede kullanıldığı son kez sona erer ilk kez başlatır. Önceden tanımlanmış bir izleme türleri kümesi tarafından sağlanan <xref:System.Diagnostics>başlatma ve durdurma, etkinlik yaşam sınırlarını açıkça işaretlemek için dahil olmak üzere.  
  
-   Başlat: Bir etkinlik başlangıcını gösterir. Yeni bir işleme kilometre taşı başlayan bir kayıt "Başlangıç" izleme sağlar. Etkinlik Kimliği uç noktalar genelinde ne zaman dağıtılacağını dışında verilen bir işlem olarak belirtilen izleme kaynağı için yeni bir etkinlik kimliği varsa, bu durumda bir "Başlangıç" uç nokta görüyoruz. Yeni bir etkinlik başlangıç örnekleri, işleme veya yeni bir genel yöntem girmek için yeni bir iş parçacığı oluşturmayı içerir.  
  
-   Durdur: Etkinliğin bitiş gösterir. Bir "Durdur" izleme var olan bir işleme kilometre bitiş kaydını sağlar. Etkinlik Kimliği uç noktalar genelinde ne zaman dağıtılacağını dışında verilen bir işlem olarak belirtilen izleme kaynağı için mevcut bir etkinlik kimliği varsa, bu durumda bir "durak" uç nokta görüyoruz.  Bir etkinlik durdurma örnekleri şunlardır: işlem iş parçacığı Sonlandırıcı ya da devre dışı olan başına "Başlangıç" izleme ile gösterilen bir yönteminden çıkılıyor.  
  
-   Askıya alma: Bir etkinliğin işlenmesini askıya alınması gösterir. Bir "Askıya Al" izleme, işlem daha sonra devam etmek için beklenen var olan bir etkinlik kimliği içerir. İzleme yok, bu kimliği geçerli bir izleme kaynağı askıya alma ve sürdürme olayları arasında gönderilir. Bir etkinlik bir dış kitaplık işleve çağrılırken veya bir g/ç tamamlama bağlantı gibi bir kaynaktaki beklerken duraklatma örneklerindendir.  
  
-   Sürdür: Bir etkinliğin işlemin sürdürülmesini gösterir. "Devam" izleme "Askıya Al" izleme, son yayılan izleme geçerli izleme kaynağına ait olduğu mevcut bir etkinlik kimliği içerir. Bir dış kitaplık işlevine veya bir g/ç tamamlama bağlantı gibi bir kaynak tarafından sinyal işleme devam etmek için bir çağrısından döndürerek örneklerindendir.  
  
-   Aktarın: Bazı etkinlikler başkaları tarafından neden olduğu veya başkalarına ilgili etkinlikleri diğer etkinliklerden izlemeleri "Aktarabilir" ilgili olabilir. Bir etkinlik başka bir yönlendirilmiş arasındaki ilişkiyi bir aktarım kaydeder  
  
 Başlatma ve durdurma izlemelerle bağıntı için kritik değildir. Ancak, bunlar performans, profil oluşturma ve etkinlik kapsam doğrulama artan düzende yardımcı olabilir.  
  
 Araç aktarım izlemeleri izliyorsa olayları etkinlikleri ilgili veya kullanarak bu tür araçların aynı etkinliğin hemen ilgili olayları bulmak için izleme günlüklerini gezinme en iyi duruma getirebilirsiniz. Örneğin, bunlar bir Başlat/Durdur izleme gördüğünüzde belirli bir etkinlik günlüklerini ayrıştırma araçları durdurur.  
  
 Bu izleme türleri, profil oluşturma için de kullanılabilir. Başlatma ve durdurma işaretlerinin arasında tüketilen kaynaklar içerdiği mantıksal etkinlikler dahil olmak üzere etkinliğe ilişkin kapsamlı süre temsil eder. Askıya alma ve sürdürme izlemeleri arasındaki zaman aralıklarının çıkararak gerçek etkinlik süresi sağlar.  
  
 İzlemeyi Durdur de uygulanan etkinlikleri kapsamını doğrulamak için özellikle yararlıdır. Bazı işleme izlemelerini İzlemeyi Durdur yerine belirli bir etkinlik içinde sonra görünüyorsa, bu kod hatası önerir.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Etkinlik izleme kullanma yönergeleri  
 ActivityTracing izlemeleri (Başlangıç, durdurma, askıya alma, sürdürme ve aktarım) kullanarak bir kılavuz aşağıda verilmiştir.  
  
-   İzleme yönlendirilmiş döngüsel bir grafik olan bir ağaç olur. Bir etkinlik için etkinlik kökenli denetim döndürebilir.  
  
-   Bir etkinlik yöneticisine sistemin veya desteklenebilirlik için anlamlı bir işleme sınırı gösterir.  
  
-   Hem istemci ve sunucu üzerindeki her WCF yöntemi sonra başlayan yeni bir etkinlik tarafından (İş tamamlandıktan sonra) sınırlıdır yeni etkinlik bitiş ve ortam etkinlikten döndürüyor.  
  
-   Bağlantıları dinlemeyi veya bekleyen iletileri gibi uzun (sürekli) çalıştıran etkinlikler tarafından karşılık gelen başlangıç/bitiş işaretleri gösterilir.  
  
-   Etkinlikleri ulaşmasından tetiklenen veya ileti işleme izleme sınırları tarafından temsil edilir.  
  
-   Etkinlikler, etkinlikleri, mutlaka nesneleri gösterir. Bir etkinlik olarak yorumlanması gereken "Bu gerçekleştiği zaman. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. (anlamlı izleme Emisyonu oluştu)."  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlemeyi Yapılandırma](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma ](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Uçtan Uca İzleme Senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Kullanıcı Kodu İzleri Yayma](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)
