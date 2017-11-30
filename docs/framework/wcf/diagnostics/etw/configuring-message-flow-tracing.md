---
title: "İleti Akışı İzlemeyi Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77a7148a0fc96c4a043a06fbfac7b139c7720d4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-message-flow-tracing"></a><span data-ttu-id="6686f-102">İleti Akışı İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6686f-102">Configuring Message Flow Tracing</span></span>
<span data-ttu-id="6686f-103">Zaman [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Etkinlik izleme etkin olduğunda, uçtan uca etkinlik kimlikleri, mantıksal etkinlikleri atanır [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] yığını.</span><span class="sxs-lookup"><span data-stu-id="6686f-103">When [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] activity tracing is enabled, End-To-End Activity IDs are assigned to logical activities throughout the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stack.</span></span> <span data-ttu-id="6686f-104">İçinde [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], izleme için Windows olay (ileti akışı izlemeyi adlı ETW ile) çalışır bu özellik daha yüksek bir performans sürümünün artık yoktur.</span><span class="sxs-lookup"><span data-stu-id="6686f-104">In [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], there is now a higher performance version of this feature that works with Event Tracing for Windows (ETW) called message flow tracing.</span></span> <span data-ttu-id="6686f-105">Etkinleştirildiğinde, uçtan uca etkinlik kimlikleri alınan (veya boş ise atanan) gelen iletileri ve bu yayılan ileti kanal tarafından kodunu çözdü sonra gösterilen tüm izleme olayları.</span><span class="sxs-lookup"><span data-stu-id="6686f-105">When enabled, End-To-End activity IDs are taken from (or assigned to if empty) incoming messages and are propagated to all tracing events that are emitted after the message has been decoded by the channel.</span></span> <span data-ttu-id="6686f-106">Müşteriler, ileti akışları farklı Hizmetleri'nden izleme günlükleri ile kodunu çözdükten sonra yeniden oluşturmak için bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6686f-106">Customers can use this feature to reconstruct message flows with trace logs from different services after decoding.</span></span>  
  
 <span data-ttu-id="6686f-107">İzleme uygulama ile ilgili bir sorun algıladı sonra etkin ve sorun çözüldükten sonra sonra devre dışı.</span><span class="sxs-lookup"><span data-stu-id="6686f-107">Tracing can be enabled after a problem is detected with the application and then disabled once the problem is resolved.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="6686f-108">İzlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="6686f-108">Enabling Tracing</span></span>  
 <span data-ttu-id="6686f-109">.NET Framework 4 ayarlayarak ileti akışı izlemeyi etkinleştirebilirsiniz `messageFlowTracing` yapılandırma öğesi için `true`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="6686f-109">You can enable message flow tracing by setting the .NET Framework 4 `messageFlowTracing` configuration element to `true`, as shown in the following example.</span></span>  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="6686f-110">Çünkü `endToEndTracing` yapılandırma öğesi bulunan bir Web.config dosyasında, ETW aynı şekilde dinamik olarak yapılandırılamaz.</span><span class="sxs-lookup"><span data-stu-id="6686f-110">Because the `endToEndTracing` configuration element resides in a Web.config file, it cannot be dynamically configured in the same way as ETW.</span></span> <span data-ttu-id="6686f-111">İçin `endToEndTracing` etkili, uygulama yapılandırma öğesi geri dönüştürüldüğünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6686f-111">For the `endToEndTracing` configuration element to take effect, the application must be recycled.</span></span>  
  
 <span data-ttu-id="6686f-112">Etkinlikleri etkinlik kimliğini adlı bir tanımlayıcıyı değişim tarafından bağıntılı</span><span class="sxs-lookup"><span data-stu-id="6686f-112">Activities are correlated by the interchange of an identifier called the activity ID.</span></span> <span data-ttu-id="6686f-113">Bu tanımlayıcı, bir GUID'dir ve System.Diagnostics.CorrelationManager sınıfı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6686f-113">This identifier is a GUID, and is generated by the System.Diagnostics.CorrelationManager class.</span></span> <span data-ttu-id="6686f-114">System.Diagnostics.Trace.CorrelationManager.ActivityID işlemek, WCF kodu yürütme denetimi ne zaman özgün değeri ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="6686f-114">If you manipulate System.Diagnostics.Trace.CorrelationManager.ActivityID, ensure that the value is set to original when execution control transfers back to WCF code.</span></span>  <span data-ttu-id="6686f-115">Ayrıca, zaman uyumsuz bir WCF programlama modelini kullanırsanız System.Diagnostics.Trace.CorrelationManager.ActivityID iş parçacıkları arasında aktarılan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6686f-115">Also, if you use an asynchronous WCF programming model ensure that System.Diagnostics.Trace.CorrelationManager.ActivityID is transferred between the threads.</span></span>  
  
## <a name="message-flow-tracing-and-rest-services"></a><span data-ttu-id="6686f-116">İleti akışı izlemeyi ve REST Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="6686f-116">Message Flow Tracing and REST Services</span></span>  
 <span data-ttu-id="6686f-117">İleti akışı izlemeyi isteği uçtan uca izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="6686f-117">Message flow tracing allows you to trace a request end to end.</span></span>  <span data-ttu-id="6686f-118">SOAP tabanlı Hizmetleri ile bir SOAP ileti üstbilgisinde bir etkinlik kimliği gönderilir.</span><span class="sxs-lookup"><span data-stu-id="6686f-118">With SOAP-based services an Activity ID is sent in a SOAP message header.</span></span> <span data-ttu-id="6686f-119">Bunun yerine bir özel HTTP Olay üstbilgisi kullanılmak üzere REST istekleri bu üstbilgiyi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="6686f-119">REST requests do not contain this header so a special HTTP event header is used instead.</span></span> <span data-ttu-id="6686f-120">Aşağıdaki kod parçacığını, etkinlik kimliği değeri programlı olarak nasıl alabileceğinizi gösterir:</span><span class="sxs-lookup"><span data-stu-id="6686f-120">The following code snippet shows how you can programmatically retrieve the Activity ID value:</span></span>  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 <span data-ttu-id="6686f-121">Aşağıdaki kodu kullanarak üstbilgi programlı olarak ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6686f-121">You can programmatically add the header using the following code:</span></span>  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
