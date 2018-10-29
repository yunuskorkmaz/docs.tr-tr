---
title: Yayma
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 1d5ac743e94edd845650a1b550b3e982929d1b32
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198256"
---
# <a name="propagation"></a>Yayma
Bu konu, Windows Communication Foundation (WCF) izleme modelinde Etkinlik yayma açıklar.  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Uç noktalar genelinde etkinliklerini ilişkilendirmek için yayma kullanma  
 Hata doğrudan bağıntı kullanıcıyla aynı işlem birimini için uygulama uç noktalar genelinde, örneğin, bir istek izler yayılmasını sağlar. Farklı uç noktada aynı işlem birimini için yayılan hataları bile uygulama etki alanları arasında aynı etkinliğinde gruplandırılır. Bu, ileti üst bilgilerinde etkinlik kimliği yayma aracılığıyla gerçekleştirilir. Bu nedenle, sunucu bir iç hata nedeniyle istemci zaman aşımına uğrarsa, her iki hata doğrudan bağıntı aynı etkinliği görüntülenir.  
  
 Bunu yapmak için `ActivityTracing` önceki örnekte gösterildiği gibi ayarlar. Buna ek olarak, `propagateActivity` özniteliğini `System.ServiceModel` tüm uç noktaları, izleme kaynağı.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 Etkinlik yayma TLS üzerinde etkinlik kimliği içeren giden iletiler için bir başlık eklemek WCF neden olan yapılandırılabilir bir özelliktir. Bu sunucu tarafında sonraki izlemeleri üzerinde dahil ederek, istemci ve sunucu etkinlikleri ilişkilendirebilirsiniz.  
  
## <a name="propagation-definition"></a>Yayma tanımı  
 Aşağıdaki koşulların tümü uygularsanız N etkinliği için etkinlik M'ın gAId yayılır.  
  
-   N, M nedeniyle oluşturulur  
  
-   N-M'ın gAId bilinir  
  
-   N'ın gAId M'ın gAId için eşittir.  
  
 Aşağıdaki XML şemada gösterildiği gibi gAId ActivityID ileti üst bilgisi dağıtılır.  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 İleti üst bilgisi bir örnek verilmiştir.  
  
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
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
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
  
## <a name="propagation-and-activity-boundaries"></a>Doldurma ve etkinlik sınırları  
 Etkinlik Kimliği uç noktalar genelinde yayıldığında, ileti alıcısı yayan bir başlatma ve durdurma izler, (yayılan) etkinlik kimliği ile Bu nedenle, her izleme kaynağından o gAId ile başlatma ve durdurma bir izleme yoktur. Uç noktalar aynı işlem içinde ve izleme kaynak adının aynısını kullanın, birden fazla başlatma ve durdurma aynı düzenlenir (aynı gAId, aynı izleme kaynağı, aynı işlemde) ile oluşturulur.  
  
## <a name="synchronization"></a>Eşitleme  
 Olaylar farklı makinelerde çalışan uç noktalar arasında eşitlemek için bir bağıntı kimliği iletilerinde yayılır ActivityID üst bilgi eklenir. Araçları olayları makineler arasında saat tutarsızlık ile eşitlemek için bu kodu kullanabilirsiniz. Özellikle, hizmet izleme Görüntüleyicisi aracı, uç noktalar arasında ileti akışları göstermek için bu kimliği kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlemeyi Yapılandırma](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Uçtan Uca İzleme Senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
