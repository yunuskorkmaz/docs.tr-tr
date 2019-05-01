---
title: İleti Akışı İzlemeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
ms.openlocfilehash: 02c43b152cb1aef1684185e56eb7f172036ac46b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999524"
---
# <a name="configuring-message-flow-tracing"></a>İleti Akışı İzlemeyi Yapılandırma
Windows Communication Foundation (WCF) Etkinlik izleme etkin olduğunda, uçtan uca etkinlik kimlikleri WCF yığın boyunca mantıksal etkinlikleri atanır. İçinde [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], olay izleme için Windows (ileti akışı izlemeyi adlı ETW ile) çalışır. Bu özellik daha yüksek bir performans sürümü artık yoktur. Etkin olduğunda, uçtan uca etkinlik kimlikleri alınan (veya boşsa atanan) gelen iletileri ve bu yayılan ileti kanalı tarafından kodu çözülen sonra yayılan tüm izleme olayları. Müşteriler, ileti akışları ile farklı Hizmetleri izleme günlüklerinden kod çözüldükten sonra yeniden oluşturmak için bu özelliği kullanabilirsiniz.  
  
 İzleme, uygulama ile ilgili bir sorun algılandığında sonra etkin ve ardından sorun çözüldükten sonra devre dışı.  
  
## <a name="enabling-tracing"></a>İzlemeyi etkinleştirme  
 .NET Framework 4 ayarlayarak ileti akışı izlemeyi etkinleştirebilirsiniz `messageFlowTracing` yapılandırma öğesine `true`, aşağıdaki örnekte gösterildiği gibi.  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  Çünkü `endToEndTracing` yapılandırma öğesi, Web.config dosyasında bulunan, ETW aynı şekilde dinamik olarak yapılandırılamaz. İçin `endToEndTracing` etkili uygulama yapılandırma öğesi geri dönüştürülmüş olmalıdır.  
  
 Etkinlikleri tarafından etkinlik kimliğini adlı bir tanımlayıcının değişim bağıntılı olan Bu tanımlayıcı, bir GUID'dir ve System.Diagnostics.CorrelationManager sınıfı tarafından oluşturulur. System.Diagnostics.Trace.CorrelationManager.ActivityID işlemek, WCF kod yürütme denetimi aktarırken özgün değeri ayarlandığından emin olun.  Ayrıca, zaman uyumsuz bir WCF programlama modeli kullandığınız System.Diagnostics.Trace.CorrelationManager.ActivityID iş parçacıkları arasında aktarılan emin olun.  
  
## <a name="message-flow-tracing-and-rest-services"></a>İleti akışı izlemeyi ve REST Hizmetleri  
 İleti akışı izlemeyi bir istek uçtan uca izleme sağlar.  SOAP tabanlı hizmetler ile bir SOAP ileti üstbilgisinde bir etkinlik kimliği gönderilir. Bunun yerine özel bir HTTP olay başlığı kullanılmak üzere REST istekleri bu üst bilgi içermez. Aşağıdaki kod parçacığı, etkinlik kimliği değeri program aracılığıyla nasıl alabileceğinizi gösterir:  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 Aşağıdaki kodu kullanarak üstbilgi program aracılığıyla ekleyebilirsiniz:  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
