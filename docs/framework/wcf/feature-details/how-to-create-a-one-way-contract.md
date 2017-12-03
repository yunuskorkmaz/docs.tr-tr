---
title: "Nasıl yapılır: Tek Yönlü Sözleşme Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f93247a96501359bcda8d2956308e6570c597f93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-one-way-contract"></a><span data-ttu-id="a93dc-102">Nasıl yapılır: Tek Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a93dc-102">How to: Create a One-Way Contract</span></span>
<span data-ttu-id="a93dc-103">Bu konuda, tek yönlü sözleşme kullanan yöntemleri oluşturmak için temel adımlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a93dc-103">This topic shows the basic steps to create methods that use a one-way contract.</span></span> <span data-ttu-id="a93dc-104">Üzerinde operations tür yöntem çağırma bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet bir istemciden ancak bir yanıt bekliyorsunuz değil.</span><span class="sxs-lookup"><span data-stu-id="a93dc-104">Such methods invoke operations on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service from a client but do not expect a reply.</span></span> <span data-ttu-id="a93dc-105">Bu tür bir sözleşme, örneğin, birçok abonelere bildirimleri yayımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a93dc-105">This type of contract can be used, for example, to publish notifications to many subscribers.</span></span> <span data-ttu-id="a93dc-106">Tek yönlü sözleşmeler, istemcilerin ve sunucuların ya da diğer çağrıları başlatmak için birbiriyle bağımsız olarak iletişim kurması verir çift yönlü bir (iki yönlü) sözleşme oluştururken de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a93dc-106">You can also use one-way contracts when creating a duplex (two-way) contract, which allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="a93dc-107">Bu, özellikle, sunucunun istemci olayları olarak davranabilirsiniz istemci tek yönlü çağrı yapmak izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a93dc-107">This can allow, in particular, the server to make one-way calls to the client that the client can treat as events.</span></span> <span data-ttu-id="a93dc-108">Tek yönlü yöntemleri belirtme hakkında ayrıntılı bilgi için bkz: <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği ve <xref:System.ServiceModel.OperationContractAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a93dc-108">For detailed information about specifying one-way methods, see the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property and the <xref:System.ServiceModel.OperationContractAttribute> class.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a93dc-109">bkz. çift yönlü bir sözleşme için bir istemci uygulaması oluşturma [nasıl yapılır: Erişim Hizmetleri tek yönlü ve istek-yanıt sözleşmeleriyle](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a93dc-109"> creating a client application for a duplex contract, see [How to: Access Services with One-Way and Request-Reply Contracts](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span></span> <span data-ttu-id="a93dc-110">Çalışma örnek için bkz: [tek yönlü](../../../../docs/framework/wcf/samples/one-way.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="a93dc-110">For a working sample, see the [One-Way](../../../../docs/framework/wcf/samples/one-way.md) sample.</span></span>  
  
### <a name="to-create-a-one-way-contract"></a><span data-ttu-id="a93dc-111">Tek yönlü sözleşme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a93dc-111">To create a one-way contract</span></span>  
  
1.  <span data-ttu-id="a93dc-112">Hizmet sözleşmesi uygulayarak oluşturma <xref:System.ServiceModel.ServiceContractAttribute> hizmetidir uygulanacak yöntemleri tanımlar arabirimi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a93dc-112">Create the service contract by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface that defines the methods the service is to implement.</span></span>  
  
2.  <span data-ttu-id="a93dc-113">Hangi yöntemlerin arabiriminde bir istemci uygulama tarafından çağrılan belirtebilirsiniz <xref:System.ServiceModel.OperationContractAttribute> bunlara sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a93dc-113">Indicate which methods in the interface a client can invoked by applying the <xref:System.ServiceModel.OperationContractAttribute> class to them.</span></span>  
  
3.  <span data-ttu-id="a93dc-114">Hiçbir çıktı olmalıdır işlemleri belirleyin (dönüş değeri yok ve hiçbir çıkış veya başvuru parametreleri) olarak ayarlayarak tek yönlü <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="a93dc-114">Designate operations that must have no output (no return value and no out or ref parameters) as one-way by setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`.</span></span> <span data-ttu-id="a93dc-115">İşlemleri yürütmek Not <xref:System.ServiceModel.OperationContractAttribute> sınıfı çünkü bu bir istek-yanıt sözleşmesi varsayılan karşılamak <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliği `false` varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="a93dc-115">Note that the operations that carry the <xref:System.ServiceModel.OperationContractAttribute> class satisfy a request-reply contract by default because the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property is `false` by default.</span></span> <span data-ttu-id="a93dc-116">Öznitelik özelliğini değerini açıkça belirtmeniz gerekir böylece `true` yöntemi için tek yönlü sözleşme istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="a93dc-116">So you must explicitly specify the value of the attribute property to be `true` if you want a one-way contract for the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a93dc-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="a93dc-117">Example</span></span>  
 <span data-ttu-id="a93dc-118">Aşağıdaki kod örneğinde tek yönlü için birkaç yöntem içerir bir hizmet için bir sözleşmede tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a93dc-118">The following code example defines a contract for a service that includes several one-way methods.</span></span> <span data-ttu-id="a93dc-119">Tüm yöntemleri dışında tek yönlü sözleşmeler sahip `Equals`, varsayılan olarak istek-yanıt ve bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="a93dc-119">All of the methods have one-way contracts except `Equals`, which defaults to request-reply and returns a result.</span></span>  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a93dc-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a93dc-120">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="a93dc-121">Hizmetleri Tasarlama ve uygulama</span><span class="sxs-lookup"><span data-stu-id="a93dc-121">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="a93dc-122">Nasıl yapılır: bir hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="a93dc-122">How to: Define a Service Contract</span></span>](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="a93dc-123">Oturumu</span><span class="sxs-lookup"><span data-stu-id="a93dc-123">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)  
 [<span data-ttu-id="a93dc-124">Nasıl yapılır: çift yönlü sözleşme oluşturma</span><span class="sxs-lookup"><span data-stu-id="a93dc-124">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
