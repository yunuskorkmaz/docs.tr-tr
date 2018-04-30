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
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="dc2c8-102">WCF Web HTTP Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="dc2c8-102">WCF Web HTTP Error Handling</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="dc2c8-103"> Web HTTP hata işleme hatalarını döndürülecek etkinleştirir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir HTTP durum belirtin Web HTTP Hizmetleri kod ve işlem olarak (örneğin, XML veya JSON) ile aynı biçimi kullanarak hata ayrıntılarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-103"> Web HTTP error handling enables you to return errors from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="dc2c8-104">WCF Web HTTP Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="dc2c8-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="dc2c8-105"><xref:System.ServiceModel.Web.WebFaultException> Sınıfı, bir HTTP durum kodunu belirtmek izin veren bir oluşturucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="dc2c8-106">Bu durum kodu ardından istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-106">This status code is then returned to the client.</span></span> <span data-ttu-id="dc2c8-107">Genel bir sürümü <xref:System.ServiceModel.Web.WebFaultException> sınıfı, <xref:System.ServiceModel.Web.WebFaultException%601> dönüş oluşan hata hakkında bilgi içeren kullanıcı tarafından tanımlanan bir türü olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="dc2c8-108">Bu özel nesne işlem tarafından belirtilen ve istemciye döndürülen biçimini kullanarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="dc2c8-109">Aşağıdaki örnek, bir HTTP durum kodu döndürülecek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-109">The following example shows how to return an HTTP status code.</span></span>  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="dc2c8-110">Aşağıdaki örnek, bir HTTP durum kodu ve ek bilgileri kullanıcı tanımlı bir tür döndürür gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="dc2c8-111">`MyErrorDetail` gerçekleşen hata hakkında ek bilgi içeren bir kullanıcı tarafından tanımlanan türüdür.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="dc2c8-112">Önceki kod yasaklanmış durum kodunu ve örneği içeren bir gövde sahip bir HTTP yanıtı döndürür `MyErrorDetails` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="dc2c8-113">Biçimi `MyErrorDetails` nesnesi tarafından belirlenir:</span><span class="sxs-lookup"><span data-stu-id="dc2c8-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
-   <span data-ttu-id="dc2c8-114">Değeri `ResponseFormat` parametresinin <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute> özniteliği hizmet işlemi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
-   <span data-ttu-id="dc2c8-115">Değeri <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
-   <span data-ttu-id="dc2c8-116">Değeri <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> erişerek özelliği <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="dc2c8-117">Bu değerleri biçimlendirme işlemini nasıl etkilediği hakkında daha fazla bilgi için bkz: [WCF Web HTTP biçimlendirme](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="dc2c8-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="dc2c8-118"><xref:System.ServiceModel.Web.WebFaultException> olan bir <xref:System.ServiceModel.FaultException> ve bu nedenle SOAP uç noktalarını kullanıma sunar yanı sıra HTTP uç noktaları web hizmetleri için hataya özel durum programlama modeli kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc2c8-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc2c8-119">See Also</span></span>  
 [<span data-ttu-id="dc2c8-120">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="dc2c8-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="dc2c8-121">WCF Web HTTP Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="dc2c8-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [<span data-ttu-id="dc2c8-122">Hataları Tanımlama ve Belirtme</span><span class="sxs-lookup"><span data-stu-id="dc2c8-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [<span data-ttu-id="dc2c8-123">Özel Durum ve Hataları İşleme</span><span class="sxs-lookup"><span data-stu-id="dc2c8-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [<span data-ttu-id="dc2c8-124">Hataları Gönderme ve Alma</span><span class="sxs-lookup"><span data-stu-id="dc2c8-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
