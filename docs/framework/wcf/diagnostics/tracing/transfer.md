---
title: Aktarma
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 360367803fc014c83ae377309b9029dafa3040bd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202900"
---
# <a name="transfer"></a>Aktarma
Bu konu, Windows Communication Foundation (WCF) Etkinlik izleme modelinde aktarımı açıklar.  
  
## <a name="transfer-definition"></a>Aktarım tanımı  
 Etkinlikler arasında aktarımları uç noktaları içindeki ilgili etkinlikleri olaylar arasında nedensel ilişkileri temsil eder. Denetim etkinliği sınırlarını geçmesini bir yöntem çağrısının bu etkinlikler arasında Örneğin, akışlarınız çalıştığında iki etkinliği aktarımları ile ilgilidir. Bayt hizmette gelen olduğunda WCF'de, dinleme, etkinlik ileti nesnesi oluşturulduğu için bayt alma etkinlik aktarılır. Uçtan uca izleme senaryoları ve ilgili etkinlikler ve tasarım izleme listesi için bkz. [uçtan uca izleme senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
 Aktarım izlemeleri yayma kullanın `ActivityTracing` yapılandırma aşağıdaki kodda gösterildiği gibi izleme kaynak ayarlama.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Uç noktaları içindeki etkinliklerini ilişkilendirmek için Aktarım kullanma  
 Etkinlikleri ve aktarımları probabilistically hata nedenini bulmak için kullanıcıya izin verir. Örneğin, biz etkinlikler arasında M ve N sırasıyla M ve bileşenleri N İleri ve geri aktarmak ve aktarımı M sonra N hemen bir kilitlenme olur, biz Bunun nedeni büyük olasılıkla n'nin-m arası veri geçirme sonuç çizebilirsiniz.  
  
 Bir denetim n ile M arasındaki akışını olduğunda bir aktarım izleme etkinliğini N M etkinliğinden yayıldığını Örneğin, bazı çalışma N etkinliklerin sınırlarını geçmesini bir yöntem çağrısının nedeniyle milyon gerçekleştirir. N zaten var olabilir veya oluşturuldu. N, M, N, M için bazı işlemler gerçekleştiren yeni bir etkinlik olduğunda tarafından üretilmedi.  
  
 Bir milyon aktarımı n aktarımı tarafından geri N için M ardından değil. M, n bazı işler oluşturabilir ve N o iş tamamlandığında izlemez olmasıdır. Aslında, N, görev tamamlanmadan önce M sonlandırabilirsiniz. Bu, dinleyici etkinlikleri (N) olarak çoğaltılır ve sonra sona erer "Açık ServiceHost" etkinlik (M) gerçekleşir. Bir aktarımı geri N-M, N, M için ilgili iş tamamlandığı anlamına gelir.  
  
 N, m, örneğin, oturum açma isteklerinin (M) farklı bir oturum açma etkinliklerini alan tutar mevcut authenticator etkinlik (N) ilgisi olmayan başka bir işlem gerçekleştirmeye devam edebilir.  
  
 İç içe geçme ilişkisini etkinlikler arasında M ve N. mevcut değil Bu, iki nedenden kaynaklanabilir. Etkinlik M değil izlerken M başlatıldı ancak ilk olarak, gerçek işleme N gerçekleştirilen n Saniye, ne zaman N'ı zaten mevcut.  
  
## <a name="example-of-transfers"></a>Aktarımları örneği  
 Aşağıdaki liste iki aktarımı örnekler.  
  
-   Bir hizmet konağı oluşturduğunuzda, çağıran kod denetiminden Oluşturucu kazanır veya çağıran kod oluşturucuya aktarır. Oluşturucu yürütme sona erdiğinde, çağrıldığı koda denetimini döndürür veya Oluşturucu çağıran koda geri aktarır. İç içe geçmiş bir ilişkinin durum budur.  
  
-   Dinleyici aktarım veri işlemeye başladığında, yeni bir iş parçacığı oluşturur ve işleme, Denetim ve veri geçirme için uygun içerik için bayt alma etkinlik uygulamalı. İş parçacığı istek işlemeyi tamamlandığında, bayt Al etkinliği hiçbir şey dinleyici için geçirir. Bu durumda, bir aktarımı ancak yeni iş parçacığı etkinliği dışında hiçbir aktarım sahibiz. İki etkinliği ilgili ancak iç içe yerleştirilmiş.  
  
## <a name="activity-transfer-sequence"></a>Etkinlik aktarım dizisi  
 İyi biçimlendirilmiş bir etkinlik aktarım dizisi, aşağıdaki adımları içerir.  
  
1.  Yeni bir gAId seçerek oluşan yeni bir etkinlik başlar.  
  
2.  Aktarım izleme için bu yeni gAId geçerli etkinlik kimliği yayma  
  
3.  TLS yeni kimlik  
  
4.  Yeni etkinlik tarafından belirtmek için bir başlangıç izleme gösterin.  
  
5.  Özgün etkinlik dön aşağıdakilerden oluşur:  
  
6.  Özgün gAId bir aktarım izleme yayma  
  
7.  Yeni Etkinlik sonunu belirtmek için İzlemeyi Durdur yayma  
  
8.  TLS için eski gAId ayarlayın.  
  
 Aşağıdaki kod örneği, bunun nasıl yapılacağı gösterilmektedir. Bu örnek, bir engelleme çağrısının yeni etkinliği aktarırken yapılır ve askıya alma/sürdürme izlemeleri içerir varsayar.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlemeyi Yapılandırma](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Uçtan Uca İzleme Senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
