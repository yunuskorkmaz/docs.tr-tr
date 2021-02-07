---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: One-Way sözleşmesi oluşturma'
title: 'Nasıl yapılır: Tek Yönlü Sözleşme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: 465dc2da20288c918a70743fcbe3ed931620b33b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734730"
---
# <a name="how-to-create-a-one-way-contract"></a><span data-ttu-id="08696-103">Nasıl yapılır: Tek Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="08696-103">How to: Create a One-Way Contract</span></span>

<span data-ttu-id="08696-104">Bu konuda tek yönlü bir sözleşme kullanan Yöntemler oluşturmak için temel adımlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="08696-104">This topic shows the basic steps to create methods that use a one-way contract.</span></span> <span data-ttu-id="08696-105">Bu tür yöntemler bir istemciden Windows Communication Foundation (WCF) hizmetinde işlemleri çağırır ancak yanıt beklemez.</span><span class="sxs-lookup"><span data-stu-id="08696-105">Such methods invoke operations on a Windows Communication Foundation (WCF) service from a client but do not expect a reply.</span></span> <span data-ttu-id="08696-106">Bu tür bir sözleşme, örneğin, birçok aboneye bildirim yayımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08696-106">This type of contract can be used, for example, to publish notifications to many subscribers.</span></span> <span data-ttu-id="08696-107">Ayrıca, bir çift yönlü (çift yönlü) sözleşme oluştururken, istemcilerin ve sunucuların birbirleriyle yapılan çağrıları başlatabilmeleri için birbirinden bağımsız olarak birbirleriyle iletişim kurmasına olanak sağlayan tek yönlü sözleşmeleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08696-107">You can also use one-way contracts when creating a duplex (two-way) contract, which allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="08696-108">Bu, özellikle sunucunun istemci için istemcinin olay olarak kabul edebilir tek yönlü çağrılar yapmasına izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="08696-108">This can allow, in particular, the server to make one-way calls to the client that the client can treat as events.</span></span> <span data-ttu-id="08696-109">Tek yönlü yöntemler belirtme hakkında ayrıntılı bilgi için, bkz <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> . özelliği ve <xref:System.ServiceModel.OperationContractAttribute> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="08696-109">For detailed information about specifying one-way methods, see the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property and the <xref:System.ServiceModel.OperationContractAttribute> class.</span></span>  
  
 <span data-ttu-id="08696-110">Bir çift yönlü sözleşme için istemci uygulaması oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmetlere One-Way ve Request-Reply sözleşmeleri Ile erişme](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="08696-110">For more information about creating a client application for a duplex contract, see [How to: Access Services with One-Way and Request-Reply Contracts](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span></span> <span data-ttu-id="08696-111">Çalışan bir örnek için bkz. [tek yönlü](../samples/one-way.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="08696-111">For a working sample, see the [One-Way](../samples/one-way.md) sample.</span></span>  
  
### <a name="to-create-a-one-way-contract"></a><span data-ttu-id="08696-112">Tek yönlü bir sözleşme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="08696-112">To create a one-way contract</span></span>  
  
1. <span data-ttu-id="08696-113"><xref:System.ServiceModel.ServiceContractAttribute>Sınıfı, hizmetin uygulanacağı yöntemleri tanımlayan arabirime uygulayarak hizmet sözleşmesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="08696-113">Create the service contract by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface that defines the methods the service is to implement.</span></span>  
  
2. <span data-ttu-id="08696-114">Bir istemcinin Arabirim içindeki hangi yöntemlerin bu sınıfa uygulama tarafından çağrılabileceğini belirtin <xref:System.ServiceModel.OperationContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="08696-114">Indicate which methods in the interface a client can invoked by applying the <xref:System.ServiceModel.OperationContractAttribute> class to them.</span></span>  
  
3. <span data-ttu-id="08696-115">Özelliğini olarak ayarlayarak çıkış olmaması gereken (dönüş değeri yok ve out veya ref parametreleri olmayan) işlemleri tek yönlü olarak belirleyin <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="08696-115">Designate operations that must have no output (no return value and no out or ref parameters) as one-way by setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`.</span></span> <span data-ttu-id="08696-116"><xref:System.ServiceModel.OperationContractAttribute>Özelliği varsayılan olarak olduğu için, sınıfı taşıyan işlemlerin varsayılan olarak bir istek-yanıt sözleşmesini karşıladığına unutmayın <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="08696-116">Note that the operations that carry the <xref:System.ServiceModel.OperationContractAttribute> class satisfy a request-reply contract by default because the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property is `false` by default.</span></span> <span data-ttu-id="08696-117">Bu nedenle `true` , yöntemi için tek yönlü bir anlaşma istiyorsanız, öznitelik özelliğinin değerini açıkça belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="08696-117">So you must explicitly specify the value of the attribute property to be `true` if you want a one-way contract for the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08696-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="08696-118">Example</span></span>  

 <span data-ttu-id="08696-119">Aşağıdaki kod örneği, birkaç tek yönlü Yöntem içeren bir hizmet için bir sözleşme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08696-119">The following code example defines a contract for a service that includes several one-way methods.</span></span> <span data-ttu-id="08696-120">Tüm yöntemlerin tek yönlü sözleşmeleri vardır `Equals` ve bu, varsayılan olarak istek-yanıt verir ve bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="08696-120">All of the methods have one-way contracts except `Equals`, which defaults to request-reply and returns a result.</span></span>  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="08696-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08696-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="08696-122">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="08696-122">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="08696-123">Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama</span><span class="sxs-lookup"><span data-stu-id="08696-123">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="08696-124">Oturumuna</span><span class="sxs-lookup"><span data-stu-id="08696-124">Session</span></span>](../samples/session.md)
- [<span data-ttu-id="08696-125">Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="08696-125">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
