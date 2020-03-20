---
title: Aktarma
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: e0ebfff97cd33e7a588a1ab92399a97a0fbec039
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185699"
---
# <a name="transfer"></a>Aktarma
Bu konu, Windows Communication Foundation (WCF) etkinlik izleme modelinde aktarım açıklar.  
  
## <a name="transfer-definition"></a>Aktarım Tanımı  
 Etkinlikler arasındaki aktarımlar, uç noktalardaki ilgili etkinliklerdeki olaylar arasındaki nedensel ilişkileri temsil eder. İki etkinlik, bu etkinlikler arasında denetim akışı olduğunda aktarımlarla ilişkilidir, örneğin, bir yöntem geçiş etkinlik sınırları çağırır. WCF'de, hizmete baytlar geldiğinde, At'ı Dinle etkinliği ileti nesnesinin oluşturulduğu Bayt Al etkinliğine aktarılır. Uçtan uca izleme senaryolarının ve bunların ilgili etkinlik ve izleme tasarımlarının listesi için [bkz.](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
  
 Aktarım izlemelerini yalamak için, aşağıdaki yapılandırma kodunda gösterildiği gibi izleme kaynağındaki `ActivityTracing` ayarı kullanın.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Son Noktalardaki Etkinlikleri Ilişkilendirmek için Aktarım Kullanma  
 Etkinlikler ve aktarımlar, kullanıcının bir hatanın temel nedenini probabilistically olarak bulmasına izin verir. Örneğin, M ve N bileşenlerindeki m ve n etkinlikleri arasında ileri geri aktarırsak ve M'e aktarıldıktan hemen sonra N'de bir çökme meydana gelirse, bunun N'nin verileri M'e aktarması ndan kaynaklandığı sonucuna varabiliriz.  
  
 M ve N arasında bir kontrol akışı olduğunda, bir aktarım izi M aktivitesinden N aktivitesine yayılır. Örneğin, N, etkinliklerin sınırlarını aşma yı çağırma yöntemi nedeniyle M için bazı işler gerçekleştirir. N zaten var olabilir veya oluşturulmuştur. N, M için bazı işler gerçekleştiren yeni bir etkinlik olduğunda N, M tarafından ortaya çıkar.  
  
 M'den N'ye geçiş, N'den M'ye geri aktarılmasıyla takip edilemez. Bunun nedeni, M'nin N'de bazı işler ortaya çıkarabiliyor ve N bu çalışmayı tamamladığında izlenmiyor olmasıdır. Aslında, M, N görevini tamamlamadan önce sonlandırılabilir. Bu, Dinleyici etkinliklerini (N) oluşturan ve sonra sona erdiren "Open ServiceHost" etkinliğinde (M) gerçekleşir. N'den M'ye geçiş, N'nin M ile ilgili çalışmayı tamamladığı anlamına gelir.  
  
 N, m ile ilgisi olmayan diğer işlemleri gerçekleştirmeye devam edebilir, örneğin, farklı oturum açma etkinliklerinden oturum açma istekleri (M) almaya devam eden varolan bir kimlik doğrulayıcı etkinliği (N).  
  
 M ve N etkinlikleri arasında iç içe geçme ilişkisi olmak zorunda değildir. Bu iki nedenden dolayı olabilir. İlk olarak, M etkinliği N'de gerçekleştirilen gerçek işlemeyi izlemediğinde, M'yi başlatan N.'ye rağmen. İkincisi, N zaten var olduğunda.  
  
## <a name="example-of-transfers"></a>Aktarım Örneği  
 Aşağıda iki aktarım örneği listelenin.  
  
- Bir hizmet ana bilgisayarı oluşturduğunuzda, oluşturucu çağrı kodundan denetim kazanır veya çağrı kodu oluşturucuya aktarır. Oluşturucu yürütmeyi tamamladığında, denetimi arama koduna döndürür veya oluşturucu arama koduna geri aktarır. Bu iç içe bir ilişki durumudur.  
  
- Bir dinleyici aktarım verilerini işlemeye başladığında, yeni bir iş parçacığı oluşturur ve Yeni Bir Elek oluşturma Bytes etkinliği işleme, denetim ve veri aktarmak için uygun bağlamı alır. Bu iş parçacığı isteği işleme yi bitirdiğinde, Bayt Al etkinliği dinleyiciye hiçbir şey geri aktaramaz. Bu durumda, yeni iş parçacığı etkinliğinden bir aktarım var, ancak aktarım yok. İki etkinlik ilişkilidir, ancak iç içe geçmez.  
  
## <a name="activity-transfer-sequence"></a>Etkinlik Aktarım Sırası  
 İyi biçimlendirilmiş bir etkinlik aktarım sırası aşağıdaki adımları içerir.  
  
1. Yeni bir gAId seçmekte oluşan yeni bir etkinlik başlatın.  
  
2. Geçerli etkinlik kimliğinden bu yeni gAId'ye aktarım izi yayı  
  
3. TLS'de yeni kimliği ayarlama  
  
4. Yeni etkinliğin başlangıcını göstermek için bir başlangıç izi yayan.  
  
5. Özgün faaliyete dönüş aşağıdakilerden oluşur:  
  
6. Orijinal gAId bir transfer izi yayan  
  
7. Yeni etkinliğin sonunu belirtmek için bir Dur izi yontun  
  
8. TLS'yi eski gAId'e ayarlayın.  
  
 Aşağıdaki kod örneği, bunun nasıl yapılacağını gösterir. Bu örnek, yeni faaliyete aktarılırken engelleme çağrısı yapıldığını varsayar ve askıya alma/devam izlemelerini içerir.  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlemeyi Yapılandırma](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma ](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Uçtan Uca İzleme Senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
