---
title: "İleti Akışı İzlemeyi Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8df32a64c07db8a45dfb41a46e7a65a92fbef434
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-message-flow-tracing"></a>İleti Akışı İzlemeyi Yapılandırma
Zaman [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Etkinlik izleme etkin olduğunda, uçtan uca etkinlik kimlikleri, mantıksal etkinlikleri atanır [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] yığını. İçinde [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], izleme için Windows olay (ileti akışı izlemeyi adlı ETW ile) çalışır bu özellik daha yüksek bir performans sürümünün artık yoktur. Etkinleştirildiğinde, uçtan uca etkinlik kimlikleri alınan (veya boş ise atanan) gelen iletileri ve bu yayılan ileti kanal tarafından kodunu çözdü sonra gösterilen tüm izleme olayları. Müşteriler, ileti akışları farklı Hizmetleri'nden izleme günlükleri ile kodunu çözdükten sonra yeniden oluşturmak için bu özelliği kullanabilirsiniz.  
  
 İzleme uygulama ile ilgili bir sorun algıladı sonra etkin ve sorun çözüldükten sonra sonra devre dışı.  
  
## <a name="enabling-tracing"></a>İzlemeyi etkinleştirme  
 .NET Framework 4 ayarlayarak ileti akışı izlemeyi etkinleştirebilirsiniz `messageFlowTracing` yapılandırma öğesi için `true`, aşağıdaki örnekte gösterildiği gibi.  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  Çünkü `endToEndTracing` yapılandırma öğesi bulunan bir Web.config dosyasında, ETW aynı şekilde dinamik olarak yapılandırılamaz. İçin `endToEndTracing` etkili, uygulama yapılandırma öğesi geri dönüştürüldüğünde olmalıdır.  
  
 Etkinlikleri etkinlik kimliğini adlı bir tanımlayıcıyı değişim tarafından bağıntılı Bu tanımlayıcı, bir GUID'dir ve System.Diagnostics.CorrelationManager sınıfı tarafından oluşturulur. System.Diagnostics.Trace.CorrelationManager.ActivityID işlemek, WCF kodu yürütme denetimi ne zaman özgün değeri ayarlandığından emin olun.  Ayrıca, zaman uyumsuz bir WCF programlama modelini kullanırsanız System.Diagnostics.Trace.CorrelationManager.ActivityID iş parçacıkları arasında aktarılan emin olun.  
  
## <a name="message-flow-tracing-and-rest-services"></a>İleti akışı izlemeyi ve REST Hizmetleri  
 İleti akışı izlemeyi isteği uçtan uca izleme sağlar.  SOAP tabanlı Hizmetleri ile bir SOAP ileti üstbilgisinde bir etkinlik kimliği gönderilir. Bunun yerine bir özel HTTP Olay üstbilgisi kullanılmak üzere REST istekleri bu üstbilgiyi içermiyor. Aşağıdaki kod parçacığını, etkinlik kimliği değeri programlı olarak nasıl alabileceğinizi gösterir:  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 Aşağıdaki kodu kullanarak üstbilgi programlı olarak ekleyebilirsiniz:  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
