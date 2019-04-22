---
title: WCF Web HTTP Hata İşleme
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 834c642e36e1551081dbe1f14529ed7596df1360
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152704"
---
# <a name="wcf-web-http-error-handling"></a>WCF Web HTTP Hata İşleme
Windows Communication Foundation (WCF) Web HTTP hata işleme hataları, HTTP durum kodu belirtin ve dönüş hata ayrıntıları (örneğin, XML veya JSON) işlem olarak aynı biçimi kullanarak WCF Web HTTP hizmetinden döndürmenizi sağlar.  
  
## <a name="wcf-web-http-error-handling"></a>WCF Web HTTP Hata İşleme  
 <xref:System.ServiceModel.Web.WebFaultException> Sınıfı, bir HTTP durum kodu belirtmenizi sağlar bir oluşturucu tanımlar. Bu durum kodu, ardından istemciye döndürülür. Genel bir sürümünü <xref:System.ServiceModel.Web.WebFaultException> sınıfı <xref:System.ServiceModel.Web.WebFaultException%601> oluşan hata hakkında bilgi içeren kullanıcı tanımlı bir tür döndürmenizi sağlar. İstemciye döndürülen ve işlem tarafından belirtilen biçimi kullanarak bu özel nesne seri hale getirilir. Aşağıdaki örnek, bir HTTP durum kodunu döndürmek gösterilmektedir.  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 Aşağıdaki örnek, bir HTTP durum kodu ve ek bilgileri kullanıcı tanımlı bir tür dönmek gösterilmektedir. `MyErrorDetail` gerçekleşen hata hakkında ek bilgi içeren bir kullanıcı tanımlı türdür.  
  
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
  
 Yukarıdaki kod Yasak durum kodunu ve örneği içeren bir gövde ile bir HTTP yanıtı döndürür `MyErrorDetails` nesne. Biçimi `MyErrorDetails` nesnesi tarafından belirlenir:  
  
-   Değerini `ResponseFormat` parametresinin <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> hizmet işlemi belirtilen özniteliği.  
  
-   Değerini <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.  
  
-   Değerini <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> erişerek özelliği <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 Biçimlendirme işlemi bu değerleri nasıl etkilediği hakkında daha fazla bilgi için bkz. [WCF Web HTTP biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException> olan bir <xref:System.ServiceModel.FaultException> ve bu nedenle hata özel durum programlama modeli SOAP uç noktalarını kullanıma yanı sıra HTTP uç noktalarını web hizmetleri için kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [WCF Web HTTP Biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [Hataları Tanımlama ve Belirtme](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [Özel Durum ve Hataları İşleme](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [Hataları Gönderme ve Alma](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
