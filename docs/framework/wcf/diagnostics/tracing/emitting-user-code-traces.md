---
title: Kullanıcı Kodu İzleri Yayma
ms.date: 03/30/2017
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
ms.openlocfilehash: e8b2031165a83e24ba15a2fcf847a170f47e696a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589298"
---
# <a name="emitting-user-code-traces"></a>Kullanıcı Kodu İzleri Yayma

Yapılandırmada izlemeyi Windows Communication Foundation (WCF) tarafından oluşturulan izleme verilerini toplamak üzere etkinleştirmenin yanı sıra, izlemeleri Kullanıcı kodunda programlı bir şekilde de getirebilirsiniz. Bu şekilde, daha sonra tanılama amacıyla kullanabileceğiniz izleme verilerini önceden oluşturabilirsiniz. Bu konu, bunu nasıl yapabileceğinizi anlatmaktadır.

Ayrıca, [genişletme izleme](../../samples/extending-tracing.md) örneği aşağıdaki bölümlerde gösterilen tüm kodu içerir.

## <a name="creating-a-trace-source"></a>Izleme kaynağı oluşturma

Bir kullanıcı izleme kaynağı oluşturmak için aşağıdaki kodu kullanabilirsiniz.

```csharp
TraceSource ts = new TraceSource("myUserTraceSource");
```

## <a name="creating-activities"></a>Etkinlik oluşturma

Etkinlikler mantıksal işleme birimidir. İzlemelerin birlikte gruplandırılmasına istediğiniz her önemli işlem birimi için bir etkinlik oluşturabilirsiniz. Örneğin, hizmete her istek için bir etkinlik oluşturabilirsiniz. Bunu yapmak için aşağıdaki adımları gerçekleştirin.

1. Etkinlik KIMLIĞINI kapsama alanına kaydedin.

2. Yeni bir etkinlik KIMLIĞI oluşturun.

3. Kapsamdaki etkinlikten yeni bir öğesine aktarın, kapsamdaki yeni etkinliği ayarlayın ve bu etkinlik için bir başlangıç izlemesi yapın.

Aşağıdaki kod bunun nasıl yapılacağını göstermektedir.

```csharp
Guid oldID = Trace.CorrelationManager.ActivityId;
Guid traceID = Guid.NewGuid();
ts.TraceTransfer(0, "transfer", traceID);
Trace.CorrelationManager.ActivityId = traceID; // Trace is static
ts.TraceEvent(TraceEventType.Start, 0, "Add request");
```

## <a name="emitting-traces-within-a-user-activity"></a>Bir kullanıcı etkinliği içinde Izlemeleri yayma

Aşağıdaki kod, izlemeleri bir kullanıcı etkinliği içinde yayar.

```csharp
double value1 = 100.00D;
double value2 = 15.99D;
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);
double result = client.Add(value1, value2);
ts.TraceInformation("Client receives Add response '" + result + "'");
```

## <a name="stopping-the-activities"></a>Etkinlikler durduruluyor

Etkinlikleri durdurmak için eski etkinliğe geri aktarın, geçerli etkinlik kimliğini durdurun ve kapsamdaki eski etkinlik kimliğini sıfırlayın.

Aşağıdaki kod bunun nasıl yapılacağını göstermektedir.

```csharp
ts.TraceTransfer(0, "transfer", oldID);
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");
Trace.CorrelationManager.ActivityId = oldID;
```

## <a name="propagating-the-activity-id-to-a-service"></a>Etkinlik KIMLIĞI bir hizmete yayılıyor

`propagateActivity` `true` `System.ServiceModel` Öğesini hem istemci hem de hizmet yapılandırma dosyalarında izleme kaynağı için olarak ayarlarsanız, ekleme isteği için hizmet işleme, istemcide tanımlananla aynı etkinlikte oluşur. Hizmet kendi etkinliklerini ve aktarımlarını tanımlıyorsa, hizmet izlemeleri istemci tarafından yayılan etkinlikte görünmez. Bunun yerine, aktarım izlemelerinden bağıntılı bir etkinlikte, KIMLIĞI istemci tarafından yayılan etkinliğe görünürler.

> [!NOTE]
> `propagateActivity`Özniteliği `true` hem istemci hem de hizmette olarak ayarlandıysa, hizmetin işlem kapsamındaki çevresel etkinlik WCF tarafından ayarlanır.

Bir etkinliğin WCF tarafından kapsamda ayarlanmış olup olmadığını denetlemek için aşağıdaki kodu kullanabilirsiniz.

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

## <a name="tracing-exceptions-thrown-in-code"></a>Kodda oluşturulan özel durumlar izleniyor

Kodda bir özel durum oluşturduğunuzda, özel durumu uyarı düzeyinde veya aşağıdaki kodu kullanarak da izleyebilirsiniz.

```csharp
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");
```

## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a>Hizmet Izleme Görüntüleyicisi aracında Kullanıcı Izlemelerini görüntüleme

Bu bölüm, [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenirken, [genişletme izleme](../../samples/extending-tracing.md) örneği çalıştırılarak oluşturulan izlemelerin ekran görüntülerini içerir.

Aşağıdaki diyagramda, daha önce oluşturulan "istek ekle" etkinliği sol bölmede seçilidir. Uygulama istemci programını oluşturan üç farklı matematik işlemi etkinliği (Böl, çıkart, çarpma) ile listelenir. Kullanıcı kodu, farklı isteklerindeki olası hata oluşumlarını yalıtmak için her işlem için bir yeni etkinlik tanımladı.

[Genişletme izleme](../../samples/extending-tracing.md) örneğinde aktarımların kullanımını göstermek için, dört işlem isteğini kapsülleyen bir hesap makinesi etkinliği de oluşturulur. Her istek için, hesap makinesi etkinliğinden istek etkinliğine geri ve geriye doğru bir aktarım vardır (izleme, şekildeki sağ üst bölmede vurgulanır).

Sol panelde bir etkinlik seçtiğinizde, bu etkinliğin içerdiği izlemeler sağ üst bölmede gösterilir. `propagateActivity` `true` İstek yolundaki her uç noktada, istek etkinliğindeki izlemeler, isteğe katılan tüm işlemlerden alınır. Bu örnekte, paneldeki 4 sütununda hem istemci hem de hizmetten izlemeleri görebilirsiniz.

Bu etkinlik aşağıdaki işleme sırasını gösterir:

1. İstemci eklemek için ileti gönderir.

2. Hizmet, ekleme isteği iletisi alır.

3. Hizmet, Add yanıtı gönderir.

4. İstemci, ekleme yanıtı alır.

Tüm bu izlemeler bilgi düzeyine yayılmıştı. Sağ üst panelde bir izlemeye tıkladığınızda sağ alt panelde bu izlemenin ayrıntıları gösterilir.

Aşağıdaki diyagramda Ayrıca, hesap ve hizmet için bir tane olmak üzere (her izleme kaynağı için bir tane) bir tane olmak üzere, bir veya daha fazla istek için izleme ve durdurma ve hesaplama etkinliklerini de görtik.

![Izleme Görüntüleyicisi: kullanıcı&#45;kod Izlemelerini yayma](media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475A-4BAF-83f3-4227aa942fcd") Oluşturma zamanına göre etkinlik listesi (sol panel) ve iç içe geçmiş Etkinlikleri (sağ üst panel)

Hizmet kodu, istemcinin oluşturmasına neden olan bir özel durum oluşturursa (örneğin, istemci isteğine yanıt alamazsanız), hem hizmet hem de istemci uyarısı veya hata iletileri doğrudan bağıntı için aynı etkinlikte oluşur. Aşağıdaki görüntüde hizmet, "hizmet bu isteği Kullanıcı kodunda işlemeye reddediyor" durumunu belirten bir özel durum oluşturur. İstemci Ayrıca "sunucu bir iç hata nedeniyle isteği işleyemedi" adlı bir özel durum oluşturur.

Aşağıdaki görüntüler, istek etkinlik kimliği yayıldığında, belirli bir istek için uç noktalar arasındaki hataların aynı etkinlikte göründüğünü gösterir:

![Belirli bir istek için uç noktalar arasındaki hataları gösteren ekran görüntüsü.](./media/emitting-user-code-traces/trace-viewer-endpoint-errors.gif)

Sol paneldeki çarpma etkinliğine çift tıklamak, ilgili her bir işlemin çarpılacağı izlemeleri içeren aşağıdaki grafiği gösterir. Hizmette (özel durum oluştu) bir uyarı görüyoruz, bu, isteğin işlenemediği için istemcideki uyarılar ve hatalar tarafından izlenir. Bu nedenle, uç noktalar arasındaki causal hata ilişkisini belirleyebilir ve hatanın kök nedenini türetebiliriz.

Aşağıdaki görüntüde hata bağıntısı grafik görünümü gösterilmektedir:

![Hatanın bağıntı grafik görünümünü gösteren ekran görüntüsü.](./media/emitting-user-code-traces/trace-viewer-error-correlation.gif)

Önceki izlemeleri almak için `ActivityTracing` Kullanıcı izleme kaynakları ve izleme kaynağı için ayarlandık `propagateActivity=true` `System.ServiceModel` . Kullanıcı kodu `ActivityTracing` `System.ServiceModel` etkinlik yayılmaya kullanıcı kodunun etkinleştirilmesi için izleme kaynağı için ayarlanmadınız. (ServiceModel etkinlik izleme açık olduğunda, istemcide tanımlanan etkinlik KIMLIĞI, hizmet kullanıcı koduna tüm şekilde yayılmaz; Ancak, istemci ve hizmet Kullanıcı kodu etkinliklerini ara WCF etkinlikleriyle ilişkilendirmenize karşın aktarır.)

Etkinlikleri tanımlama ve etkinlik KIMLIĞI yaymaya bitiş noktaları arasında doğrudan hata bağıntısı gerçekleştirmemizi sağlar. Bu şekilde, hatanın kök nedenini daha hızlı bulabiliriz.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlemeyi Genişletme](../../samples/extending-tracing.md)
