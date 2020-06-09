---
title: Yayma
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 732ae5cb1ce311b78728f8d5de0fd9102bf32499
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578961"
---
# <a name="propagation"></a>Yayma
Bu konu, Windows Communication Foundation (WCF) izleme modelinde etkinlik yaymayı açıklamaktadır.  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Uç noktalar genelinde etkinlikleri Ilişkilendirmek için yayılmayı kullanma  
 Yayma, kullanıcıya, örneğin bir istek gibi uygulama uç noktaları genelinde aynı işleme birimi için hata izlemelerinin doğrudan bağıntısını sağlar. Aynı işleme birimi için farklı uç noktalara yayılan hatalar, uygulama etki alanları arasında bile aynı etkinlik halinde gruplandırılır. Bu, ileti üst bilgilerindeki etkinlik KIMLIĞI yayması aracılığıyla yapılır. Bu nedenle, sunucuda bir iç hata nedeniyle istemci zaman aşımına uğrarsa, her iki hata da doğrudan bağıntı için aynı etkinlikte görünür.  
  
 Bunu yapmak için, `ActivityTracing` Önceki örnekte gösterildiği gibi ayarını kullanın. Ayrıca, `propagateActivity` `System.ServiceModel` tüm uç noktalarında izleme kaynağı için özniteliğini ayarlayın.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 Etkinlik yayma, WCF 'nin, TLS üzerindeki etkinlik KIMLIĞINI içeren giden iletilere üst bilgi eklemesine neden olan yapılandırılabilir bir özelliktir. Bunu sunucu tarafındaki izleyen izlemelere ekleyerek, istemci ve sunucu etkinliklerini ilişkilendirebiliriz.  
  
## <a name="propagation-definition"></a>Yayma tanımı  
 Aşağıdaki koşulların tümü geçerliyse, etkinliğin gAId 'si etkinlik N 'ye yayılır.  
  
- N, d nedeniyle oluşturuldu  
  
- E 'nin gAId 'si N olarak bilinir  
  
- N 'nin gAId 'si, 8 ' in gAId değerine eşit.  
  
 GAId, aşağıdaki XML şemasında gösterildiği gibi ActivityId ileti üst bilgisi aracılığıyla dağıtılır.  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 Aşağıda ileti üstbilgisinin bir örneği verilmiştir.  
  
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
  
## <a name="propagation-and-activity-boundaries"></a>Yayma ve etkinlik sınırları  
 Etkinlik KIMLIĞI uç noktalar arasında yayıldığında, ileti alıcısı bu (yayılan) etkinlik KIMLIĞIYLE bir başlangıç ve durdurma izlemeleri yayar. Bu nedenle, her bir izleme kaynağından bu gAId ile bir başlatma ve durdurma izlemesi vardır. Uç noktalar aynı işlemden ve aynı izleme kaynağı adını kullanıyorsa aynı şekilde aynı (aynı gAId, aynı izleme kaynağı, aynı işleme) ile birden çok başlatma ve durdurma oluşturulur.  
  
## <a name="synchronization"></a>Eşitleme  
 Olayları farklı makinelerde çalışan uç noktalar arasında senkronize etmek için, ileti içine yayılan ActivityId üstbilgisine bir Bağıntıkimliği eklenir. Araçlar, saat tutarsızlığı olan makineler arasında olayları eşleştirmek için bu KIMLIĞI kullanabilir. Özellikle, hizmet Izleme Görüntüleyicisi Aracı, uç noktalar arasındaki ileti akışlarını göstermek için bu KIMLIĞI kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlemeyi Yapılandırma](configuring-tracing.md)
- [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma ](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Uçtan Uca İzleme Senaryoları](end-to-end-tracing-scenarios.md)
- [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
