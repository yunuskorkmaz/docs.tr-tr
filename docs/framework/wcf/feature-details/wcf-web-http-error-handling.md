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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3366ab851c6e6b66a5df94bdb24baad4ae0c8d14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="4e5b5-102">WCF Web HTTP Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="4e5b5-102">WCF Web HTTP Error Handling</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="4e5b5-103">Web HTTP hata işleme hatalarını döndürülecek etkinleştirir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir HTTP durum belirtin Web HTTP Hizmetleri kod ve işlem olarak (örneğin, XML veya JSON) ile aynı biçimi kullanarak hata ayrıntılarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-103"> Web HTTP error handling enables you to return errors from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="4e5b5-104">WCF Web HTTP Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="4e5b5-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="4e5b5-105"><xref:System.ServiceModel.Web.WebFaultException> Sınıfı, bir HTTP durum kodunu belirtmek izin veren bir oluşturucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="4e5b5-106">Bu durum kodu ardından istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-106">This status code is then returned to the client.</span></span> <span data-ttu-id="4e5b5-107">Genel bir sürümü <xref:System.ServiceModel.Web.WebFaultException> sınıfı, <xref:System.ServiceModel.Web.WebFaultException%601> dönüş oluşan hata hakkında bilgi içeren kullanıcı tarafından tanımlanan bir türü olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="4e5b5-108">Bu özel nesne işlem tarafından belirtilen ve istemciye döndürülen biçimini kullanarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="4e5b5-109">Aşağıdaki örnek, bir HTTP durum kodu döndürülecek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-109">The following example shows how to return an HTTP status code.</span></span>  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="4e5b5-110">Aşağıdaki örnek, bir HTTP durum kodu ve ek bilgileri kullanıcı tanımlı bir tür döndürür gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="4e5b5-111">`MyErrorDetail`gerçekleşen hata hakkında ek bilgi içeren bir kullanıcı tarafından tanımlanan türüdür.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="4e5b5-112">Önceki kod yasaklanmış durum kodunu ve örneği içeren bir gövde sahip bir HTTP yanıtı döndürür `MyErrorDetails` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="4e5b5-113">Biçimi `MyErrorDetails` nesnesi tarafından belirlenir:</span><span class="sxs-lookup"><span data-stu-id="4e5b5-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
-   <span data-ttu-id="4e5b5-114">Değeri `ResponseFormat` parametresinin <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliği hizmet işlemi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
-   <span data-ttu-id="4e5b5-115">Değeri <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
-   <span data-ttu-id="4e5b5-116">Değeri <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> erişerek özelliği <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4e5b5-117">Bu değerleri biçimlendirme çalışmasını etkileyen bkz [WCF Web HTTP biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="4e5b5-117"> how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="4e5b5-118"><xref:System.ServiceModel.Web.WebFaultException>olan bir <xref:System.ServiceModel.FaultException> ve bu nedenle SOAP uç noktalarını kullanıma sunar yanı sıra HTTP uç noktaları web hizmetleri için hataya özel durum programlama modeli kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e5b5-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e5b5-119">See Also</span></span>  
 [<span data-ttu-id="4e5b5-120">WCF Web HTTP programlama modeli</span><span class="sxs-lookup"><span data-stu-id="4e5b5-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="4e5b5-121">WCF Web HTTP biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="4e5b5-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [<span data-ttu-id="4e5b5-122">Hataları tanımlama ve belirtme</span><span class="sxs-lookup"><span data-stu-id="4e5b5-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [<span data-ttu-id="4e5b5-123">Özel durumlar ve hataları işleme</span><span class="sxs-lookup"><span data-stu-id="4e5b5-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [<span data-ttu-id="4e5b5-124">Hataları gönderme ve alma</span><span class="sxs-lookup"><span data-stu-id="4e5b5-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
