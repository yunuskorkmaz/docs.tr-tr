---
title: İleti Akışı İzlemeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
ms.openlocfilehash: b01a06a50fbb5962fe87c3426957b3294b1bf3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917927"
---
# <a name="configuring-message-flow-tracing"></a>İleti Akışı İzlemeyi Yapılandırma
Windows Communication Foundation (WCF) etkinlik izleme etkinleştirildiğinde, WCF yığını genelinde mantıksal etkinliklere uçtan uca etkinlik kimlikleri atanır. ' [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]De artık bu özelliğin, ileti akışı izleme adlı Windows için olay izleme (ETW) ile birlikte çalışarak daha yüksek bir performans sürümü bulunmaktadır. Etkinleştirildiğinde, uçtan uca etkinlik kimlikleri, gelen iletiler üzerinden alınır (veya boş bırakılırsa atanır) ve ileti kanal tarafından kodu oluşturulduktan sonra yayınlanan tüm izleme olaylarına dağıtılır. Müşteriler, kod çözdükten sonra farklı hizmetlerden izleme günlükleriyle ileti akışlarını yeniden oluşturmak için bu özelliği kullanabilir.  
  
 İzleme, uygulama ile ilgili bir sorun algılandıktan sonra etkinleştirilebilir ve sorun çözümlendikten sonra devre dışı bırakılır.  
  
## <a name="enabling-tracing"></a>Izlemeyi etkinleştirme  
 Aşağıdaki örnekte gösterildiği gibi, .NET Framework 4 `messageFlowTracing` yapılandırma öğesini olarak `true`ayarlayarak ileti akışı izlemeyi etkinleştirebilirsiniz.  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
> `endToEndTracing` Yapılandırma öğesi bir Web. config dosyasında bulunduğundan, bu, ETW ile aynı şekilde dinamik olarak yapılandırılamaz. `endToEndTracing` Yapılandırma öğesinin etkili olabilmesi için, uygulamanın geri dönüştürülmesi gerekir.  
  
 Etkinlikler, etkinlik KIMLIĞI adlı bir tanımlayıcının değişimi ile bağıntılı. Bu tanımlayıcı bir GUID 'dir ve System. Diagnostics. CorrelationManager sınıfı tarafından oluşturulur. System. Diagnostics. Trace. CorrelationManager. ActivityId 'yi işlersiniz, yürütme denetimi WCF koduna geri aktarırken değerin özgün olarak ayarlandığından emin olun.  Ayrıca, zaman uyumsuz bir WCF programlama modeli kullanıyorsanız, System. Diagnostics. Trace. CorrelationManager. ActivityId 'nin iş parçacıkları arasında aktarılmasını sağlayabilirsiniz.  
  
## <a name="message-flow-tracing-and-rest-services"></a>İleti akışı Izleme ve REST Hizmetleri  
 İleti akışı izleme isteği uçtan uca izlemenize olanak sağlar.  SOAP tabanlı hizmetlerle bir etkinlik KIMLIĞI bir SOAP ileti üstbilgisinde gönderilir. Bunun yerine özel bir HTTP olay üst bilgisi kullanıldığı için REST istekleri bu üstbilgiyi içermez. Aşağıdaki kod parçacığı, etkinlik KIMLIĞI değerini programlı bir şekilde nasıl alabileceğiniz gösterilmektedir:  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 Aşağıdaki kodu kullanarak üstbilgiyi programlı olarak ekleyebilirsiniz:  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
