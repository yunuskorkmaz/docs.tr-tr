---
description: Daha fazla bilgi için bkz. WCF Web HTTP hatası Işleme
title: WCF Web HTTP Hata İşleme
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 88483c249bc1b6b866517ca10b348c0885fc34fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779490"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="7c877-103">WCF Web HTTP Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="7c877-103">WCF Web HTTP Error Handling</span></span>

<span data-ttu-id="7c877-104">Windows Communication Foundation (WCF) Web HTTP hatası işleme, WCF Web HTTP hizmetlerinden bir HTTP durum kodu belirten hata döndürmenizi ve işlemle aynı biçimi (örneğin, XML veya JSON) kullanarak hata ayrıntılarını döndürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c877-104">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="7c877-105">WCF Web HTTP Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="7c877-105">WCF Web HTTP Error Handling</span></span>  

 <span data-ttu-id="7c877-106"><xref:System.ServiceModel.Web.WebFaultException>Sınıfı, BIR http durum kodu belirtmenizi sağlayan bir oluşturucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7c877-106">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="7c877-107">Bu durum kodu daha sonra istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7c877-107">This status code is then returned to the client.</span></span> <span data-ttu-id="7c877-108">Sınıfının genel bir sürümü <xref:System.ServiceModel.Web.WebFaultException> , <xref:System.ServiceModel.Web.WebFaultException%601> oluşan hata hakkında bilgi içeren Kullanıcı tanımlı bir tür döndürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c877-108">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="7c877-109">Bu özel nesne, işlem tarafından belirtilen biçim kullanılarak serileştirilir ve istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7c877-109">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="7c877-110">Aşağıdaki örnek, bir HTTP durum kodunun nasıl döndürülmesini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7c877-110">The following example shows how to return an HTTP status code.</span></span>  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 <span data-ttu-id="7c877-111">Aşağıdaki örnek, bir HTTP durum kodunun ve ek bilgilerin Kullanıcı tanımlı bir tür içinde nasıl döndürülmesini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7c877-111">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="7c877-112">`MyErrorDetail` , oluşan hata hakkında ek bilgi içeren bir Kullanıcı tanımlı türdür.</span><span class="sxs-lookup"><span data-stu-id="7c877-112">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="7c877-113">Önceki kod, yasak durum koduna ve nesnenin bir örneğini içeren bir gövdeye sahip HTTP yanıtı döndürür `MyErrorDetails` .</span><span class="sxs-lookup"><span data-stu-id="7c877-113">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="7c877-114">Nesnenin biçimi şu şekilde `MyErrorDetails` belirlenir:</span><span class="sxs-lookup"><span data-stu-id="7c877-114">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="7c877-115">`ResponseFormat` <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> Hizmet işleminde belirtilen veya özniteliği parametresinin değeri.</span><span class="sxs-lookup"><span data-stu-id="7c877-115">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="7c877-116">Değeri <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> .</span><span class="sxs-lookup"><span data-stu-id="7c877-116">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="7c877-117"><xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>Öğesine erişerek özelliğinin değeri <xref:System.ServiceModel.Web.OutgoingWebResponseContext> .</span><span class="sxs-lookup"><span data-stu-id="7c877-117">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="7c877-118">Bu değerlerin işlemin biçimlendirmesini nasıl etkilediği hakkında daha fazla bilgi için bkz. [WCF Web http biçimlendirmesi](wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="7c877-118">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="7c877-119"><xref:System.ServiceModel.Web.WebFaultException> , <xref:System.ServiceModel.FaultException> ve bu nedenle, soap bitiş noktaları ve Web HTTP uç noktaları sunan hizmetler için hata özel durum programlama modeli olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c877-119"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c877-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c877-120">See also</span></span>

- [<span data-ttu-id="7c877-121">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="7c877-121">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="7c877-122">WCF Web HTTP Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="7c877-122">WCF Web HTTP Formatting</span></span>](wcf-web-http-formatting.md)
- [<span data-ttu-id="7c877-123">Hataları Tanımlama ve Belirtme</span><span class="sxs-lookup"><span data-stu-id="7c877-123">Defining and Specifying Faults</span></span>](../defining-and-specifying-faults.md)
- [<span data-ttu-id="7c877-124">Özel Durum ve Hataları İşleme</span><span class="sxs-lookup"><span data-stu-id="7c877-124">Handling Exceptions and Faults</span></span>](../extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="7c877-125">Hataları Gönderme ve Alma</span><span class="sxs-lookup"><span data-stu-id="7c877-125">Sending and Receiving Faults</span></span>](../sending-and-receiving-faults.md)
