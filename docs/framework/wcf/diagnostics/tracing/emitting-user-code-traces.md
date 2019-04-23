---
title: Kullanıcı Kodu İzleri Yayma
ms.date: 03/30/2017
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
ms.openlocfilehash: 93da2eb74705a0581923d0317315e628f374be3e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222763"
---
# <a name="emitting-user-code-traces"></a>Kullanıcı Kodu İzleri Yayma

Windows Communication Foundation (WCF) tarafından oluşturulan izleme verilerini toplamak için yapılandırma izleme etkinleştirmeye ek olarak, kullanıcı kodunda programlı olarak izlemeleri gönderebilir. Bu şekilde, tanılama amacıyla daha sonra tekrar kullanmanıza ölçümlü izleme verilerini proaktif bir şekilde oluşturabilirsiniz. Bu konuda, bunu nasıl yapabileceğiniz açıklanır.

Ayrıca, [genişletme izleme](../../../../../docs/framework/wcf/samples/extending-tracing.md) aşağıdaki bölümlerde gösterilen tüm kod örneği içerir.

## <a name="creating-a-trace-source"></a>Bir izleme kaynağı oluşturma

Bir kullanıcı izleme kaynağı oluşturmak için aşağıdaki kodu kullanabilirsiniz.

```csharp
TraceSource ts = new TraceSource("myUserTraceSource");
```

## <a name="creating-activities"></a>Etkinlik oluşturma

Mantıksal birim işleme etkinliklerdir. Birlikte gruplanması izlemeleri istediğiniz her bir ana işleme birimi için bir etkinlik oluşturabilirsiniz. Örneğin, hizmete her istek için bir etkinlik oluşturabilirsiniz. Bunu yapmak için aşağıdaki adımları gerçekleştirin.

1. Etkinlik Kimliği kapsamda kaydedin.

2. Yeni bir etkinlik kimliği oluşturma

3. Yeni bir tane kapsam etkinliğinde aktarmaya kapsamda yeni etkinliği ayarlayabilir ve bu etkinlik için bir başlangıç izleme yayma.

Aşağıdaki kod, bunun nasıl yapılacağı gösterilmektedir.

```csharp
Guid oldID = Trace.CorrelationManager.ActivityId;
Guid traceID = Guid.NewGuid();
ts.TraceTransfer(0, "transfer", traceID);
Trace.CorrelationManager.ActivityId = traceID; // Trace is static
ts.TraceEvent(TraceEventType.Start, 0, "Add request");
```

## <a name="emitting-traces-within-a-user-activity"></a>Bir kullanıcı etkinliği içinde izlemeleri yayma

Aşağıdaki kod, bir kullanıcı etkinliği içinde izlemeleri yayar.

```csharp
double value1 = 100.00D;
double value2 = 15.99D;
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);
double result = client.Add(value1, value2);
ts.TraceInformation("Client receives Add response '" + result + "'");
```

## <a name="stopping-the-activities"></a>Etkinlikleri durduruluyor

Etkinlikleri durdurmak için eski etkinliğine Aktarım, geçerli etkinlik kimliği durdurun ve sıfırlama kapsamda eski etkinlik kimliği.

Aşağıdaki kod, bunun nasıl yapılacağı gösterilmektedir.

```csharp
ts.TraceTransfer(0, "transfer", oldID);
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");
Trace.CorrelationManager.ActivityId = oldID;
```

## <a name="propagating-the-activity-id-to-a-service"></a>Bir hizmete etkinlik kimliği yayma

Ayarlarsanız `propagateActivity` özniteliğini `true` için `System.ServiceModel` izleme kaynağı hem istemci hem de hizmet yapılandırma dosyaları, aynı etkinliğinde istemci tanımlı bir ekleme isteği gerçekleştiği için işleme hizmetidir. Hizmet kendi etkinlikleri ve aktarımları tanımlıyorsa, hizmet izlemeleri istemci yayılan etkinliğinde görünmez. Bunun yerine, etkinlik kimliği, istemci tarafından yayılan etkinliğine aktarımı izlemeleri tarafından bağıntılı görünürler.

> [!NOTE]
> Varsa `propagateActivity` özniteliği `true` hem istemci hem de hizmet, ortam etkinlik hizmet işlemi kapsamında WCF tarafından ayarlanır.

Bir etkinlik kapsamda WCF tarafından ayarlanıp ayarlanmadığını kontrol etmek için aşağıdaki kodu kullanabilirsiniz.

```csharp
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

Kodda bir özel durum, özel durum uyarısı düzeyinde veya oluşturan aşağıdaki kodu kullanarak da izleyebilirsiniz.

```csharp
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");
```

## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a>Hizmet izleme Görüntüleyicisi Aracı ' kullanıcı izlemeleri görüntüleme

Bu bölümde çalıştırılarak oluşturulan izlemeleri ekran görüntüleri içeren [genişletme izleme](../../../../../docs/framework/wcf/samples/extending-tracing.md) kullanarak görüntülendiğinde, örnek [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).

Aşağıdaki diyagramda, daha önce oluşturduğunuz "Ekleme isteği" etkinliği sol panelde seçilir. Uygulama istemci programı oluşturan (, çıkarma, birden çok kez bölme) üç diğer matematiksel işlem etkinliklerle listelenir. Kullanıcı kodu farklı isteklerinde olası hataları ayırmak her işlem için yeni bir etkinlik tanımladı.

Aktarımlarında kullanımını göstermek için [genişletme izleme](../../../../../docs/framework/wcf/samples/extending-tracing.md) dört işlem istekleri kapsülleyen bir hesap makinesi etkinlik örneği de oluşturulur. Her istek için hesaplayıcı etkinliğinden İleri ve geri bir aktarım isteği etkinliği yok (şekildeki üst sağ panelde izleme vurgulanır).

Bir etkinlik Sol paneldeki seçtiğinizde, bu etkinliği tarafından bulunan izlemeleri üst Sağdaki panelde görüntülenir. Varsa `propagateActivity` olduğu `true` istek yolu, her bir uç noktada istekte katılan tüm işlemler istek etkinliği izlemelerinde arasındadır. Bu örnekte, hem istemci hem de hizmet Masası 4 sütununda izlemelerinden görebilirsiniz.

Bu etkinlik aşağıdaki işlenme sırasını gösterir:

1. İstemci Ekle iletisi gönderir.

2. Hizmet Ekle İstek iletisini alır.

3. Hizmet Ekle yanıt gönderir.

4. İstemci Ekle yanıtı alır.

Bu izlemeler bilgi düzeyinde yayılan. Sağ panelde bir izleme tıklayarak sağ panelde, izleme ayrıntılarını gösterir.

Aşağıdaki diyagramda, ayrıca aktarım izlemeleri ilk ve son iki başlangıç çiftlerini yanı sıra, hesaplayıcı etkinliği ve istemci biri diğeri (her bir izleme kaynağı için bir tane) hizmeti isteği etkinliği başına durdurma izlemeleri görüyoruz.

![İzleme görüntüleyicisini: Kullanıcı yayma&#45;kodu izlemeleri](../../../../../docs/framework/wcf/diagnostics/tracing/media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd") oluşturulma zamanı (sol paneli) ile etkinlikleri ve iç içe geçmiş etkinliklerini (sağ paneli) listesi

Hizmet kodu (örneğin istemci isteğine yanıt almadı yanı,) throw istemciye neden olan bir özel durum oluşturursa, hem hizmet ve istemci uyarı veya hata iletileri aynı etkinlik için doğrudan bağıntı oluşur. Aşağıdaki görüntüde hizmet, "kullanıcı kodunda bu isteği işlemek hizmet reddeder." bildiren bir özel durum oluşturur. İstemci de "sunucu bir iç hata nedeniyle isteği işleyemedi." bildiren bir özel durum oluşturur.

Aşağıdaki resimlerde isteğin etkinlik kimliği yayıldığı, hataları belirli bir istek için uç noktalar arasında aynı etkinliğin göründüğünü gösterir:

![Belirli bir istek için uç noktalar arasında hataları gösteren ekran görüntüsü.](./media/emitting-user-code-traces/trace-viewer-endpoint-errors.gif)

Çift birden çok kez izlemelerini ile aşağıdaki grafikte Sol paneldeki etkinliği gösterir katılan her işlem için etkinlik çarpın. Bir uyarı olduğu için istek işlenemedi istemcide ardından uyarıları ve hataları hizmeti (özel durum oluştu), ilk oluştu görebiliriz. Bu nedenle, biz uç noktalar arasında nedensel hata ilişkisine işaret ve hatanın nedenini türetilir.

Aşağıdaki görüntüde bağıntı hata bir grafik görünümü gösterilmektedir:

![Graf görünümünü hata bağıntı gösteren ekran görüntüsü.](./media/emitting-user-code-traces/trace-viewer-error-correlation.gif)

Önceki izlemeleri almak için ayarladığımız `ActivityTracing` kullanıcı izleme kaynakları için ve `propagateActivity=true` için `System.ServiceModel` izleme kaynağı. Biz ayarlanmamış `ActivityTracing` için `System.ServiceModel` kullanıcı kodu Etkinlik yayma kullanıcı kodu etkinleştirmek için izleme kaynağı. (ServiceModel Etkinlik izleme etkin olduğunda, istemci tanımlanan etkinlik kimliği tüm hizmet kullanıcı koduna dağıtılmaz; Aktarımları, Bununla birlikte, hizmet ve istemci kullanıcı kodu etkinlikleri Ara WCF etkinliklere ilişkilendirin.)

Etkinlikleri tanımlama ve etkinlik kimliği yayma uç noktalar genelinde doğrudan hata bağıntısı gerçekleştirme sağlıyor. Bu şekilde, biz hata nedenini daha hızlı bir şekilde bulabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlemeyi Genişletme](../../../../../docs/framework/wcf/samples/extending-tracing.md)
