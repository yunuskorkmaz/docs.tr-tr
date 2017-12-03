---
title: "WCF Web HTTP Hata İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 156960a6594f5475e339b36e5dabf46f26d13d62
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-web-http-error-handling"></a>WCF Web HTTP Hata İşleme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Web HTTP hata işleme hatalarını döndürülecek etkinleştirir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir HTTP durum belirtin Web HTTP Hizmetleri kod ve işlem olarak (örneğin, XML veya JSON) ile aynı biçimi kullanarak hata ayrıntılarını döndürür.  
  
## <a name="wcf-web-http-error-handling"></a>WCF Web HTTP Hata İşleme  
 <xref:System.ServiceModel.Web.WebFaultException> Sınıfı, bir HTTP durum kodunu belirtmek izin veren bir oluşturucu tanımlar. Bu durum kodu ardından istemciye döndürülür. Genel bir sürümü <xref:System.ServiceModel.Web.WebFaultException> sınıfı, <xref:System.ServiceModel.Web.WebFaultException%601> dönüş oluşan hata hakkında bilgi içeren kullanıcı tarafından tanımlanan bir türü olanak tanır. Bu özel nesne işlem tarafından belirtilen ve istemciye döndürülen biçimini kullanarak serileştirilir. Aşağıdaki örnek, bir HTTP durum kodu döndürülecek gösterilmiştir.  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 Aşağıdaki örnek, bir HTTP durum kodu ve ek bilgileri kullanıcı tanımlı bir tür döndürür gösterilmektedir. `MyErrorDetail`gerçekleşen hata hakkında ek bilgi içeren bir kullanıcı tarafından tanımlanan türüdür.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu değerleri biçimlendirme çalışmasını etkileyen bkz [WCF Web HTTP biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException>olan bir <xref:System.ServiceModel.FaultException> ve bu nedenle SOAP uç noktalarını kullanıma sunar yanı sıra HTTP uç noktaları web hizmetleri için hataya özel durum programlama modeli kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [WCF Web HTTP biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [Hataları tanımlama ve belirtme](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [Özel durumlar ve hataları işleme](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Hataları gönderme ve alma](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
