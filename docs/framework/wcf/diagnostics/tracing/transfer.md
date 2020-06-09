---
title: Aktarma
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 52b0cf35a2f8bab17252d3711f3143738c2bc39c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587775"
---
# <a name="transfer"></a>Aktarma
Bu konu, Windows Communication Foundation (WCF) etkinliği izleme modelinde aktarımı açıklamaktadır.  
  
## <a name="transfer-definition"></a>Aktarım tanımı  
 Etkinlikler arasındaki aktarımlar, uç noktalar içindeki ilgili etkinliklerdeki olaylar arasındaki causal ilişkilerini temsil eder. İki etkinlik, bu etkinlikler arasındaki denetim akışı, örneğin etkinlik sınırlarını geçen bir yöntem çağrısı gibi aktarımlarla ilişkilidir. WCF 'de, baytların hizmette geliş durumunda dinleme etkinliği ileti nesnesinin oluşturulduğu bayt alma etkinliğine aktarılır. Uçtan uca izleme senaryolarına ve bunların ilgili etkinliklerini ve izleme tasarımına yönelik bir liste için bkz. [uçtan uca Izleme senaryoları](end-to-end-tracing-scenarios.md).  
  
 Aktarım izlemelerini yaymak için, `ActivityTracing` izleme kaynağı üzerindeki ayarı aşağıdaki yapılandırma kodu ile gösterildiği gibi kullanın.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Uç noktalar Içindeki etkinlikleri Ilişkilendirmek için aktarımı kullanma  
 Etkinlikler ve aktarımlar, kullanıcının bir hatanın kök nedenini bilsel bulmasına izin verir. Örneğin, a ve N bileşenlerinde sırasıyla a ve N etkinlikleri arasında geri ve ileri aktarıldığımızda ve bir kilitlenme, d 'ye geri aktarıldıktan sonra n doğru olursa, büyük olasılıkla N 'nin verileri d 'ye geri geçirmesinin nedeni çizebiliriz.  
  
 A ve N arasında bir denetim akışı olduğunda, bir aktarım izlemesi etkinlik d 'den etkinlik N 'ye yayılır. Örneğin, N, etkinliğin sınırlarını geçen bir yöntem çağrısı nedeniyle h için biraz iş gerçekleştirir. N zaten var veya oluşturulmuş olabilir. N, k için bazı işler gerçekleştiren yeni bir etkinlikse, n tarafından oluşturulur.  
  
 A 'dan N 'ye bir aktarım, N 'den d 'ye geri aktarım ile izlenebilir. Bunun nedeni, N 'nin bazı işleri N 'de üretme ve işi ne zaman tamamladığını izlememe nedeni. Aslında, h işini tamamlanmadan önce son verebilir. Bu durum, NS dinleyicisi etkinliklerini (N) ve ardından sonlandırmakta olan "açık ServiceHost" etkinliğinde (e) oluşur. N 'den d 'ye geri aktarma işlemi, N ile ilgili çalışmanın tamamlandığını gösterir.  
  
 N, farklı oturum açma etkinliklerinden oturum açma istekleri (M) almaya devam eden, mevcut bir kimlik doğrulayıcı etkinliği (N) ile ilişkili diğer işlemleri gerçekleştirmeye devam edebilir.  
  
 İç içe geçmiş ilişki, a ve N etkinlikleri arasında olmamalıdır. Bu, iki nedenden dolayı oluşabilir. İlk olarak, etkinlik M, M tarafından başlatılan N ' de gerçekleştirilen gerçek işlemeyi izlemez. İkinci olarak, N zaten var.  
  
## <a name="example-of-transfers"></a>Aktarım örnekleri  
 Aşağıda iki aktarım örneği listelenmektedir.  
  
- Bir hizmet ana bilgisayarı oluşturduğunuzda, Oluşturucu çağıran koddan denetimi kazanır veya çağıran kod oluşturucuya aktarır. Oluşturucunun yürütülmesi bittiğinde, çağıran koda denetim döndürür veya Oluşturucu çağıran koda geri aktarır. Bu, iç içe geçmiş bir ilişki durumunda olur.  
  
- Bir dinleyici aktarım verilerini işlemeye başladığında, yeni bir iş parçacığı oluşturur ve alma bayt etkinliğine yönelik uygun bağlam işleme, denetim ve verileri geçirme Bu iş parçacığı isteği işlemeyi tamamladığında, alma baytları etkinliği dinleyiciye hiçbir şey geri geçirir. Bu durumda, ' de bir aktarım yaptık, ancak yeni iş parçacığı etkinliğinden aktarım yok. İki etkinlik ilişkili ancak iç içe değil.  
  
## <a name="activity-transfer-sequence"></a>Etkinlik aktarma sırası  
 İyi biçimlendirilmiş bir etkinlik aktarma sırası aşağıdaki adımları içerir.  
  
1. Yeni bir gAId seçip seçmekten oluşan yeni bir etkinlik başlatın.  
  
2. Geçerli etkinlik KIMLIĞINDEN bu yeni bir gAId 'ye bir aktarım izlemesi yay  
  
3. Yeni KIMLIĞI TLS 'de ayarlama  
  
4. Yeni etkinliğin başlangıcını tarafından göstermek için bir başlangıç izlemeyi yay.  
  
5. Özgün etkinliğe geri dönme aşağıdakilerden oluşur:  
  
6. Bir aktarım izlemesini özgün gAId 'ye yay  
  
7. Yeni etkinliğin sonunu belirtmek için bir durdurma izi yay  
  
8. TLS 'yi eski gAId olarak ayarlayın.  
  
 Aşağıdaki kod örneği bunun nasıl yapılacağını göstermektedir. Bu örnek, yeni etkinliğe aktarılırken bir engelleme çağrısının yapıldığını varsayar ve askıya alma/sürdürülme izlemelerini içerir.  
  
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

- [İzlemeyi Yapılandırma](configuring-tracing.md)
- [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma ](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Uçtan Uca İzleme Senaryoları](end-to-end-tracing-scenarios.md)
- [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
