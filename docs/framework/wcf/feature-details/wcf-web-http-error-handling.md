---
title: WCF Web HTTP Hata İşleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bcd0e6d1e6318404eb47741dc61ccf2ff9358b47
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-web-http-error-handling"></a>WCF Web HTTP Hata İşleme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP hata işleme hatalarını döndürülecek etkinleştirir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir HTTP durum belirtin Web HTTP Hizmetleri kod ve işlem olarak (örneğin, XML veya JSON) ile aynı biçimi kullanarak hata ayrıntılarını döndürür.  
  
## <a name="wcf-web-http-error-handling"></a>WCF Web HTTP Hata İşleme  
 <xref:System.ServiceModel.Web.WebFaultException> Sınıfı, bir HTTP durum kodunu belirtmek izin veren bir oluşturucu tanımlar. Bu durum kodu ardından istemciye döndürülür. Genel bir sürümü <xref:System.ServiceModel.Web.WebFaultException> sınıfı, <xref:System.ServiceModel.Web.WebFaultException%601> dönüş oluşan hata hakkında bilgi içeren kullanıcı tarafından tanımlanan bir türü olanak tanır. Bu özel nesne işlem tarafından belirtilen ve istemciye döndürülen biçimini kullanarak serileştirilir. Aşağıdaki örnek, bir HTTP durum kodu döndürülecek gösterilmiştir.  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 Aşağıdaki örnek, bir HTTP durum kodu ve ek bilgileri kullanıcı tanımlı bir tür döndürür gösterilmektedir. `MyErrorDetail` gerçekleşen hata hakkında ek bilgi içeren bir kullanıcı tarafından tanımlanan türüdür.  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 Önceki kod yasaklanmış durum kodunu ve örneği içeren bir gövde sahip bir HTTP yanıtı döndürür `MyErrorDetails` nesnesi. Biçimi `MyErrorDetails` nesnesi tarafından belirlenir:  
  
-   Değeri `ResponseFormat` parametresinin <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliği hizmet işlemi belirtildi.  
  
-   Değeri <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.  
  
-   Değeri <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> erişerek özelliği <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 Bu değerleri biçimlendirme işlemini nasıl etkilediği hakkında daha fazla bilgi için bkz: [WCF Web HTTP biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException> olan bir <xref:System.ServiceModel.FaultException> ve bu nedenle SOAP uç noktalarını kullanıma sunar yanı sıra HTTP uç noktaları web hizmetleri için hataya özel durum programlama modeli kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [WCF Web HTTP Biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [Hataları Tanımlama ve Belirtme](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [Özel Durum ve Hataları İşleme](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Hataları Gönderme ve Alma](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
