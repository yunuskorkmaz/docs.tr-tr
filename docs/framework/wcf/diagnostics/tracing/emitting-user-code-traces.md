---
title: Kullanıcı Kodu İzleri Yayma
ms.date: 03/30/2017
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
ms.openlocfilehash: 18b424139f4c1656193f80cf76c704af2b2887e3
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="emitting-user-code-traces"></a>Kullanıcı Kodu İzleri Yayma
Windows Communication Foundation (WCF) tarafından oluşturulan izleme verileri toplamak için yapılandırma izlemeyi etkinleştirmeye ek olarak, ayrıca program aracılığıyla içinde kullanıcı kodu izleri yayma. Bu şekilde, tanılama amaç için daha sonra tekrar kullanmanıza izleme verileri önceden oluşturabilirsiniz. Bu konuda, bunu yapmak nasıl ele alınmıştır.  
  
 Ayrıca, [genişletme izleme](../../../../../docs/framework/wcf/samples/extending-tracing.md) örnek aşağıdaki bölümlerde gösterilen tüm kod içerir.  
  
## <a name="creating-a-trace-source"></a>İzleme kaynağı oluşturma  
 Bir kullanıcı izleme kaynağı oluşturmak için aşağıdaki kodu kullanabilirsiniz.  
  
```  
TraceSource ts = new TraceSource("myUserTraceSource");  
```  
  
## <a name="creating-activities"></a>Aktivite oluşturma  
 Mantıksal birim işleme etkinliklerdir. Birlikte Gruplanacak izlemeleri istediğiniz her ana işleme birimi için bir etkinlik oluşturabilirsiniz. Örneğin, hizmet için her istek için bir etkinlik oluşturabilirsiniz. Bunu yapmak için aşağıdaki adımları gerçekleştirin.  
  
1.  Etkinlik Kimliği kapsamda kaydedin.  
  
2.  Yeni bir etkinlik kimliği oluşturma  
  
3.  Yeni bir kapsam etkinliğinde aktarmaya, yeni etkinlik kapsamda ayarlayabilir ve bu etkinlik için bir başlangıç izleme yayma.  
  
 Aşağıdaki kod bunun nasıl yapılacağı gösterilmektedir.  
  
```  
Guid oldID = Trace.CorrelationManager.ActivityId;  
Guid traceID = Guid.NewGuid();  
ts.TraceTransfer(0, "transfer", traceID);  
Trace.CorrelationManager.ActivityId = traceID; // Trace is static  
ts.TraceEvent(TraceEventType.Start, 0, "Add request");  
```  
  
## <a name="emitting-traces-within-a-user-activity"></a>Bir kullanıcı etkinliği içinde izleri yayma  
 Aşağıdaki kod, bir kullanıcı etkinliği içinde izlemeleri yayar.  
  
```  
double value1 = 100.00D;  
double value2 = 15.99D;  
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);  
double result = client.Add(value1, value2);  
ts.TraceInformation("Client receives Add response '" + result + "'");  
```  
  
## <a name="stopping-the-activities"></a>Etkinlikler durdurma  
 Etkinlikleri durdurmak için eski etkinliğe Aktarım, geçerli etkinlik kimliğini durdurmak ve eski etkinlik kimliği kapsamında Sıfırla.  
  
 Aşağıdaki kod bunun nasıl yapılacağı gösterilmektedir.  
  
```  
ts.TraceTransfer(0, "transfer", oldID);  
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");  
Trace.CorrelationManager.ActivityId = oldID;  
```  
  
## <a name="propagating-the-activity-id-to-a-service"></a>Bir hizmete etkinlik kimliği yayma  
 Ayarlarsanız `propagateActivity` özniteliğini `true` için `System.ServiceModel` hem istemci hem de hizmet yapılandırmasında izleme kaynak dosyaları, istemci tanımlanmış olanla aynı etkinliğinde ekleme isteği gerçekleştiği için işleme hizmetidir. Hizmet kendi etkinlikleri ve aktarımları tanımlıyorsa, hizmet izlemeleri istemci yayıldığı etkinliğinde görünmez. Bunun yerine, aktarım izlemeleri Kimliğine istemci tarafından yayılır etkinliğine tarafından bağıntılı bir etkinlikte görünür.  
  
> [!NOTE]
>  Varsa `propagateActivity` özniteliği `true` hem istemci hem de hizmet üzerinde hizmet işlemi kapsamında ortam etkinlik WCF tarafından ayarlanır.  
  
 Bir etkinlik kapsamda WCF tarafından ayarlanıp ayarlanmadığını denetlemek için aşağıdaki kodu kullanabilirsiniz.  
  
```  
// Check if an activity was set in scope by WCF, if it was   
// propagated from the client. If not, ( ambient activity is   
// equal to Guid.Empty), create a new one.  
if(Trace.CorrelationManager.ActivityId == Guid.Empty)  
{  
    Guid newGuid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = newGuid;  
}  
// Emit your Start trace.  
ts.TraceEvent(TraceEventType.Start, 0, "Add Activity");  
  
// Emit the processing traces for that request.  
serviceTs.TraceInformation("Service receives Add "   
                            + n1 + ", " + n2);  
// double result = n1 + n2;  
serviceTs.TraceInformation("Service sends Add result" + result);  
  
// Emit the Stop trace and exit the method scope.  
ts.TraceEvent(TraceEventType.Stop, 0, "Add Activity");  
// return result;  
```  
  
## <a name="tracing-exceptions-thrown-in-code"></a>Kod içinde oluşturulan özel durumları izleme  
 Kod içinde bir özel durum, aşağıdaki kodu kullanarak yukarı veya uyarı düzeyinde özel durum da izleyebilirsiniz.  
  
```  
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");  
```  
  
## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a>Hizmet izleme Görüntüleyicisi aracı kullanıcı izlemeleri görüntüleme  
 Bu bölümde çalıştırarak oluşturulan izlemeleri ekran görüntüleri içeren [genişletme izleme](../../../../../docs/framework/wcf/samples/extending-tracing.md) kullanarak görüntülendiğinde örnek [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Aşağıdaki şemada daha önce oluşturduğunuz "Ekleme isteği" etkinliği sol panelde seçilir. Bu uygulamanın istemci programı oluşturduğunu (, çıkarma, Çarp bölme) üç diğer matematik işlemi etkinliklerle listelenir. Kullanıcı kodu farklı isteklerindeki olası hata oluşum yalıtmak her bir işlemin yeni bir etkinlik tanımlanır.  
  
 Aktarım kullanımını göstermek için [genişletme izleme](../../../../../docs/framework/wcf/samples/extending-tracing.md) örnek, dört işlemi istekleri yalıtır hesaplayıcı etkinlik da oluşturuldu. Her istek için bir aktarımı geri ve İleri hesaplayıcı etkinlik isteği etkinliği yoktur (izleme vurgulanmış şekilde sağ üst panelinde).  
  
 Bir etkinlik Sol paneldeki seçtiğinizde, bu etkinlik tarafından dahil izlemeleri üst Sağdaki panelde gösterilir. Varsa `propagateActivity` olan `true` istek yolu her uç noktada istekte katılan tüm işlemler isteği etkinliği içindeki arasındadır. Bu örnekte, hem istemci hem de hizmet Masası 4 sütununda izlemeleri görebilirsiniz.  
  
 Bu etkinlik işleme aşağıdaki sırayı gösterir:  
  
1.  İstemci Ekle iletisi gönderir.  
  
2.  Hizmet Ekle İstek iletisini alır.  
  
3.  Hizmet Ekle yanıt gönderir.  
  
4.  İstemci Ekle yanıtı alır.  
  
 Bu izlemeler bilgi düzeyinde yayılan. Sağ üst köşede panelinde izleme tıklatarak sağ alt panelinde, izleme ayrıntılarını gösterir.  
  
 Aşağıdaki diyagramda, biz de aktarımı izlemeleri ilk ve son iki başlangıç çiftlerini yanı sıra hesaplayıcı etkinliği ve durdurma izlemeleri isteği etkinliği, istemci için diğeri için hizmet (her izleme kaynağı için bir tane) başına bakın.  
  
 ![İzleme görüntüleyicisini: Kullanıcı yayma&#45;kod izlemeleri](../../../../../docs/framework/wcf/diagnostics/tracing/media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd")  
Oluşturma zamanı (sol paneli) tarafından etkinliklerin listesini ve bunların iç içe etkinlik (sağ üst köşede Masası)  
  
 Hizmet koduna (örneğin istemci kendi isteğinin yanıtı almadığını de,) throw istemciye neden olan bir özel durum oluşturursa, doğrudan bağıntı aynı etkinliği hem hizmet ve istemci uyarı veya hata iletileri oluşur. Aşağıdaki diyagramda, hizmet "kullanıcı kodu bu isteği işlemek hizmet reddediyor." bildiren özel durum oluşturur. İstemci de "sunucu bir iç hata nedeniyle isteği işleyemedi." bildiren bir özel durum oluşturur  
  
 ![Kullanıcı yaymak üzere izleme Görüntüleyicisi'ni kullanarak&#45;kod izlemeleri](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace2.gif "e2eTrace2")  
İstek etkinlik kimliği yayıldığı aynı etkinlik içindeki belirli bir istek için uç hataları görünür  
  
 Çift Çarp ile izlemelerini aşağıdaki grafikte Sol paneldeki etkinliğini gösterir katılan her işlem için etkinlik çarpın. İstek işlenemedi çünkü, istemci üzerinde uyarıları ve hataları tarafından izlenir hizmeti (özel durum oluştu), önce bir uyarı oluştu görebiliriz. Bu nedenle, biz nedensel hata ilişki uç noktalar arasında kapsıyor ve hatasının kök nedenini türetilir.  
  
 ![Kullanıcı yaymak üzere izleme Görüntüleyicisi'ni kullanarak&#45;kod izlemeleri](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace3.gif "e2eTrace3")  
Hata bağıntı grafik görünümü  
  
 Önceki izlemelerini almak için ayarlarız `ActivityTracing` kullanıcı izleme kaynakları için ve `propagateActivity=true` için `System.ServiceModel` izleme kaynağı. Biz ayarlanmamış `ActivityTracing` için `System.ServiceModel` kullanıcı kodunu aktivite yayma kullanıcı kodu etkinleştirmek için izleme kaynağı. (ServiceModel Etkinlik izleme etkin olduğunda, istemcinin tanımlanan etkinlik kimliği bu süreç boyunca tüm hizmet kullanıcı kodu dağıtılmaz; Aktarımları, ancak, istemci ve hizmet kullanıcı kodu etkinlikleri Ara WCF etkinliklerini ilişkilendirmek.)  
  
 Etkinlikleri tanımlama ve etkinlik kimliği yayma bize uç noktalar arasında doğrudan hata bağıntı gerçekleştirmesini sağlar. Bu şekilde, biz hata kök nedenini daha hızlı bir şekilde bulabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlemeyi Genişletme](../../../../../docs/framework/wcf/samples/extending-tracing.md)
