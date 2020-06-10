---
title: WCF Web HTTP Hata İşleme
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: b1d41bebafa2795d390b120ad84475417389479b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598651"
---
# <a name="wcf-web-http-error-handling"></a>WCF Web HTTP Hata İşleme
Windows Communication Foundation (WCF) Web HTTP hatası işleme, WCF Web HTTP hizmetlerinden bir HTTP durum kodu belirten hata döndürmenizi ve işlemle aynı biçimi (örneğin, XML veya JSON) kullanarak hata ayrıntılarını döndürmenizi sağlar.  
  
## <a name="wcf-web-http-error-handling"></a>WCF Web HTTP Hata İşleme  
 <xref:System.ServiceModel.Web.WebFaultException>Sınıfı, BIR http durum kodu belirtmenizi sağlayan bir oluşturucu tanımlar. Bu durum kodu daha sonra istemciye döndürülür. Sınıfının genel bir sürümü <xref:System.ServiceModel.Web.WebFaultException> , <xref:System.ServiceModel.Web.WebFaultException%601> oluşan hata hakkında bilgi içeren Kullanıcı tanımlı bir tür döndürmenizi sağlar. Bu özel nesne, işlem tarafından belirtilen biçim kullanılarak serileştirilir ve istemciye döndürülür. Aşağıdaki örnek, bir HTTP durum kodunun nasıl döndürülmesini göstermektedir.  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 Aşağıdaki örnek, bir HTTP durum kodunun ve ek bilgilerin Kullanıcı tanımlı bir tür içinde nasıl döndürülmesini göstermektedir. `MyErrorDetail`, oluşan hata hakkında ek bilgi içeren bir Kullanıcı tanımlı türdür.  
  
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
  
 Önceki kod, yasak durum koduna ve nesnenin bir örneğini içeren bir gövdeye sahip HTTP yanıtı döndürür `MyErrorDetails` . Nesnenin biçimi şu şekilde `MyErrorDetails` belirlenir:  
  
- `ResponseFormat` <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> Hizmet işleminde belirtilen veya özniteliği parametresinin değeri.  
  
- Değeri <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> .  
  
- <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>Öğesine erişerek özelliğinin değeri <xref:System.ServiceModel.Web.OutgoingWebResponseContext> .  
  
 Bu değerlerin işlemin biçimlendirmesini nasıl etkilediği hakkında daha fazla bilgi için bkz. [WCF Web http biçimlendirmesi](wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException>, <xref:System.ServiceModel.FaultException> ve bu nedenle, soap bitiş noktaları ve Web HTTP uç noktaları sunan hizmetler için hata özel durum programlama modeli olarak kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](wcf-web-http-programming-model.md)
- [WCF Web HTTP Biçimlendirme](wcf-web-http-formatting.md)
- [Hataları Tanımlama ve Belirtme](../defining-and-specifying-faults.md)
- [Özel Durum ve Hataları İşleme](../extending/handling-exceptions-and-faults.md)
- [Hataları Gönderme ve Alma](../sending-and-receiving-faults.md)
