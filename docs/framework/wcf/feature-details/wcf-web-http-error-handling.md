---
title: WCF Web HTTP Hata İşleme
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 34912bccaefb645541f47d083c5c307b20ff77c5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975952"
---
# <a name="wcf-web-http-error-handling"></a>WCF Web HTTP Hata İşleme
Windows Communication Foundation (WCF) Web HTTP hatası işleme, WCF Web HTTP hizmetlerinden bir HTTP durum kodu belirten hata döndürmenizi ve işlemle aynı biçimi (örneğin, XML veya JSON) kullanarak hata ayrıntılarını döndürmenizi sağlar.  
  
## <a name="wcf-web-http-error-handling"></a>WCF Web HTTP Hata İşleme  
 <xref:System.ServiceModel.Web.WebFaultException> sınıfı, bir HTTP durum kodu belirtmenizi sağlayan bir oluşturucu tanımlar. Bu durum kodu daha sonra istemciye döndürülür. <xref:System.ServiceModel.Web.WebFaultException> sınıfının genel bir sürümü <xref:System.ServiceModel.Web.WebFaultException%601>, oluşan hata hakkında bilgi içeren Kullanıcı tanımlı bir tür döndürmenizi sağlar. Bu özel nesne, işlem tarafından belirtilen biçim kullanılarak serileştirilir ve istemciye döndürülür. Aşağıdaki örnek, bir HTTP durum kodunun nasıl döndürülmesini göstermektedir.  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 Aşağıdaki örnek, bir HTTP durum kodunun ve ek bilgilerin Kullanıcı tanımlı bir tür içinde nasıl döndürülmesini göstermektedir. `MyErrorDetail`, oluşan hata hakkında ek bilgiler içeren Kullanıcı tanımlı bir türdür.  
  
```csharp
public string Operation2()
{
   // Operation logic  
   // ...
   MyErrorDetail detail = new MyErrorDetail()
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 Önceki kod, yasak durum koduna ve `MyErrorDetails` nesnesinin bir örneğini içeren bir gövdeye sahip HTTP yanıtı döndürür. `MyErrorDetails` nesnesinin biçimi tarafından belirlenir:  
  
- Hizmet işleminde belirtilen <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliğinin `ResponseFormat` parametresi değeri.  
  
- <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>değeri.  
  
- <xref:System.ServiceModel.Web.OutgoingWebResponseContext>erişerek <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> özelliğinin değeri.  
  
 Bu değerlerin işlemin biçimlendirmesini nasıl etkilediği hakkında daha fazla bilgi için bkz. [WCF Web http biçimlendirmesi](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException> bir <xref:System.ServiceModel.FaultException> ve bu nedenle, SOAP bitiş noktalarının yanı sıra Web HTTP uç noktaları sunan hizmetler için hata özel durum programlama modeli olarak kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [WCF Web HTTP Biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [Hataları Tanımlama ve Belirtme](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [Özel Durum ve Hataları İşleme](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [Hataları Gönderme ve Alma](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
