---
title: Yayma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bfe861d6b535c7158ae930d4f31ac0ad4bae6721
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="propagation"></a>Yayma
Bu konu, Etkinlik yayma açıklar [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] izleme modeli.  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Uç noktalar arasında etkinliklerini ilişkilendirmek için yayma kullanma  
 Yayma hatasının doğrudan bağıntı kullanıcıyla aynı işleme birimi için uygulama uç noktalar arasında Örneğin, bir istek izler sağlar. Farklı uç noktada aynı işleme birimi için gösterilen hatalar bile uygulama etki alanları arasında aynı etkinlik içindeki gruplandırılır. Bu ileti üstbilgisinde etkinlik kimliği yayma yoluyla yapılır. Bu nedenle, sunucu bir iç hata nedeniyle bir istemci zaman aşımına uğrarsa, her iki hata doğrudan bağıntı aynı etkinliği görünür.  
  
 Bunu yapmak için kullanın `ActivityTracing` önceki örnekte gösterildiği gibi ayarlar. Buna ek olarak, `propagateActivity` için öznitelik `System.ServiceModel` tüm uç noktaları adresindeki izleme kaynağı.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 Etkinlik yayma neden olan yapılandırılabilir bir özelliği olan [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] TLS üzerinde etkinlik kimliği içeren giden iletiler için bir başlık eklemek için. Bu sunucu tarafında sonraki izlemeleri üzerinde dahil ederek, istemci ve sunucu etkinlikleri ilişkilendirebilirsiniz.  
  
## <a name="propagation-definition"></a>Yayma tanımı  
 Aşağıdaki koşulların tümü uygularsanız etkinlik M'ın gAId etkinlik N yayılır.  
  
-   N, M nedeniyle oluşturulur  
  
-   M'ın gAId N bilinir  
  
-   N'ın gAId M'ın gAId eşittir.  
  
 Aşağıdaki XML Şeması gösterildiği gibi gAId ActivityID ileti üstbilgisi dağıtılır.  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 İleti üstbilgisinin bir örnek verilmiştir.  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"     
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"   
  
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous  
          </a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a>Yayma ve etkinlik sınırları  
 Etkinlik Kimliği uç noktalar arasında yayılır, ileti alıcısı bir başlangıç yayar ve bu (yayılan) etkinlik kimliğine Dur izler Bu nedenle, bu gAId her izleme kaynağından ile başlatma ve durdurma bir izleme yoktur. Uç noktalar aynı işlem içinde olan ve aynı izleme kaynağı adı kullanırsanız, birden çok başlatma ve durdurma aynı yerleştirilmiş (aynı gAId, aynı izleme kaynağı, aynı işlemi) ile oluşturulur.  
  
## <a name="synchronization"></a>Eşitleme  
 Farklı makinelerde çalıştırma uç olayları eşitlemek için bir correlationıd değeri iletilerinde yayılır ActivityID üstbilgi eklenir. Araçları olayları ile saat tutarsızlık makineler arasında eşitlemek için bu kodu kullanabilirsiniz. Özellikle, hizmet izleme Görüntüleyicisi aracı, ileti akışlarının uç noktalar arasında göstermek için bu kimliği kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlemeyi Yapılandırma](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [İzlemeleri görüntüleme bağıntılı için hizmet izleme görüntüleyicisini kullanma ve sorun giderme](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Uçtan uca izleme senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
