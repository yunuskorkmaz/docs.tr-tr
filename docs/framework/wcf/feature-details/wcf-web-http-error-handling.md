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
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="fe0a2-102">WCF Web HTTP Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="fe0a2-102">WCF Web HTTP Error Handling</span></span>
<span data-ttu-id="fe0a2-103">Windows Communication Foundation (WCF) Web HTTP hatası işleme, WCF Web HTTP hizmetlerinden bir HTTP durum kodu belirten hata döndürmenizi ve işlemle aynı biçimi (örneğin, XML veya JSON) kullanarak hata ayrıntılarını döndürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="fe0a2-104">WCF Web HTTP Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="fe0a2-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="fe0a2-105"><xref:System.ServiceModel.Web.WebFaultException> sınıfı, bir HTTP durum kodu belirtmenizi sağlayan bir oluşturucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="fe0a2-106">Bu durum kodu daha sonra istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-106">This status code is then returned to the client.</span></span> <span data-ttu-id="fe0a2-107"><xref:System.ServiceModel.Web.WebFaultException> sınıfının genel bir sürümü <xref:System.ServiceModel.Web.WebFaultException%601>, oluşan hata hakkında bilgi içeren Kullanıcı tanımlı bir tür döndürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="fe0a2-108">Bu özel nesne, işlem tarafından belirtilen biçim kullanılarak serileştirilir ve istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="fe0a2-109">Aşağıdaki örnek, bir HTTP durum kodunun nasıl döndürülmesini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-109">The following example shows how to return an HTTP status code.</span></span>  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 <span data-ttu-id="fe0a2-110">Aşağıdaki örnek, bir HTTP durum kodunun ve ek bilgilerin Kullanıcı tanımlı bir tür içinde nasıl döndürülmesini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="fe0a2-111">`MyErrorDetail`, oluşan hata hakkında ek bilgiler içeren Kullanıcı tanımlı bir türdür.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="fe0a2-112">Önceki kod, yasak durum koduna ve `MyErrorDetails` nesnesinin bir örneğini içeren bir gövdeye sahip HTTP yanıtı döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="fe0a2-113">`MyErrorDetails` nesnesinin biçimi tarafından belirlenir:</span><span class="sxs-lookup"><span data-stu-id="fe0a2-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="fe0a2-114">Hizmet işleminde belirtilen <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliğinin `ResponseFormat` parametresi değeri.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="fe0a2-115"><xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>değeri.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="fe0a2-116"><xref:System.ServiceModel.Web.OutgoingWebResponseContext>erişerek <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> özelliğinin değeri.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="fe0a2-117">Bu değerlerin işlemin biçimlendirmesini nasıl etkilediği hakkında daha fazla bilgi için bkz. [WCF Web http biçimlendirmesi](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="fe0a2-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="fe0a2-118"><xref:System.ServiceModel.Web.WebFaultException> bir <xref:System.ServiceModel.FaultException> ve bu nedenle, SOAP bitiş noktalarının yanı sıra Web HTTP uç noktaları sunan hizmetler için hata özel durum programlama modeli olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0a2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe0a2-119">See also</span></span>

- [<span data-ttu-id="fe0a2-120">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="fe0a2-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="fe0a2-121">WCF Web HTTP Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="fe0a2-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [<span data-ttu-id="fe0a2-122">Hataları Tanımlama ve Belirtme</span><span class="sxs-lookup"><span data-stu-id="fe0a2-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [<span data-ttu-id="fe0a2-123">Özel Durum ve Hataları İşleme</span><span class="sxs-lookup"><span data-stu-id="fe0a2-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="fe0a2-124">Hataları Gönderme ve Alma</span><span class="sxs-lookup"><span data-stu-id="fe0a2-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
