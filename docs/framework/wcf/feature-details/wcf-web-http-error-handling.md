---
title: WCF Web HTTP Hata İşleme
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: c331d70a69740a9830cafb5cafdfcf1de14b541b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499255"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="4f402-102">WCF Web HTTP Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="4f402-102">WCF Web HTTP Error Handling</span></span>
<span data-ttu-id="4f402-103">Windows Communication Foundation (WCF) Web HTTP hata işleme hataları, HTTP durum kodu belirtin ve dönüş hata ayrıntıları (örneğin, XML veya JSON) işlem olarak aynı biçimi kullanarak WCF Web HTTP hizmetinden döndürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f402-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="4f402-104">WCF Web HTTP Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="4f402-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="4f402-105"><xref:System.ServiceModel.Web.WebFaultException> Sınıfı, bir HTTP durum kodu belirtmenizi sağlar bir oluşturucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f402-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="4f402-106">Bu durum kodu, ardından istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4f402-106">This status code is then returned to the client.</span></span> <span data-ttu-id="4f402-107">Genel bir sürümünü <xref:System.ServiceModel.Web.WebFaultException> sınıfı <xref:System.ServiceModel.Web.WebFaultException%601> oluşan hata hakkında bilgi içeren kullanıcı tanımlı bir tür döndürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f402-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="4f402-108">İstemciye döndürülen ve işlem tarafından belirtilen biçimi kullanarak bu özel nesne seri hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="4f402-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="4f402-109">Aşağıdaki örnek, bir HTTP durum kodunu döndürmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4f402-109">The following example shows how to return an HTTP status code.</span></span>  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="4f402-110">Aşağıdaki örnek, bir HTTP durum kodu ve ek bilgileri kullanıcı tanımlı bir tür dönmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4f402-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="4f402-111">`MyErrorDetail` gerçekleşen hata hakkında ek bilgi içeren bir kullanıcı tanımlı türdür.</span><span class="sxs-lookup"><span data-stu-id="4f402-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="4f402-112">Yukarıdaki kod Yasak durum kodunu ve örneği içeren bir gövde ile bir HTTP yanıtı döndürür `MyErrorDetails` nesne.</span><span class="sxs-lookup"><span data-stu-id="4f402-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="4f402-113">Biçimi `MyErrorDetails` nesnesi tarafından belirlenir:</span><span class="sxs-lookup"><span data-stu-id="4f402-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
-   <span data-ttu-id="4f402-114">Değerini `ResponseFormat` parametresinin <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> hizmet işlemi belirtilen özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4f402-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
-   <span data-ttu-id="4f402-115">Değerini <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f402-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
-   <span data-ttu-id="4f402-116">Değerini <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> erişerek özelliği <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="4f402-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="4f402-117">Biçimlendirme işlemi bu değerleri nasıl etkilediği hakkında daha fazla bilgi için bkz. [WCF Web HTTP biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="4f402-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="4f402-118"><xref:System.ServiceModel.Web.WebFaultException> olan bir <xref:System.ServiceModel.FaultException> ve bu nedenle hata özel durum programlama modeli SOAP uç noktalarını kullanıma yanı sıra HTTP uç noktalarını web hizmetleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4f402-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f402-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f402-119">See also</span></span>
- [<span data-ttu-id="4f402-120">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="4f402-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="4f402-121">WCF Web HTTP Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="4f402-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [<span data-ttu-id="4f402-122">Hataları Tanımlama ve Belirtme</span><span class="sxs-lookup"><span data-stu-id="4f402-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [<span data-ttu-id="4f402-123">Özel Durum ve Hataları İşleme</span><span class="sxs-lookup"><span data-stu-id="4f402-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="4f402-124">Hataları Gönderme ve Alma</span><span class="sxs-lookup"><span data-stu-id="4f402-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
