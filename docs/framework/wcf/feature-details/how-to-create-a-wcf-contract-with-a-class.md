---
title: "Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma"
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
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bf32559f9b5a1040390562cc8492646288494638
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="9fac8-102">Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9fac8-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="9fac8-103">Oluşturma tercih edilen yol bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sözleşmedir bir arabirim kullanarak.</span><span class="sxs-lookup"><span data-stu-id="9fac8-103">The preferred way of creating a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="9fac8-104">[Nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="9fac8-104"> [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="9fac8-105">Bir alternatif, Anahatlı burada olan bir sınıf oluşturun ve ardından uygulamak için <xref:System.ServiceModel.ServiceContractAttribute> sınıfa öznitelik doğrudan ve <xref:System.ServiceModel.OperationContractAttribute> özniteliği her sözleşmenin parçası sınıftaki yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="9fac8-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="9fac8-106">`[ServiceContract]`ve `[ServiceContractAttribute]` aynı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="9fac8-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="9fac8-107">True için aynı şeyi `[OperationContract]` ve `[OperationContractAttribute]`.</span><span class="sxs-lookup"><span data-stu-id="9fac8-107">The same thing it true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="9fac8-108">Her durumda, ikinci için toplu eski özelliktir.</span><span class="sxs-lookup"><span data-stu-id="9fac8-108">In each case the former is shorthand for the latter.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9fac8-109">Hizmet sözleşmeleri için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9fac8-109"> service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="9fac8-110">Bir sınıf ile Windows Communication Foundation sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9fac8-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1.  <span data-ttu-id="9fac8-111">Kullanarak yeni bir sınıf oluşturmak [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# veya herhangi diğer ortak dil çalışma zamanı dili.</span><span class="sxs-lookup"><span data-stu-id="9fac8-111">Create a new class using [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="9fac8-112">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> sınıfı için sınıf.</span><span class="sxs-lookup"><span data-stu-id="9fac8-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3.  <span data-ttu-id="9fac8-113">Yöntemleri sınıfında oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9fac8-113">Create methods in the class.</span></span>  
  
4.  <span data-ttu-id="9fac8-114">Uygulama <xref:System.ServiceModel.OperationContractAttribute> ortak bir parçası olarak sunulan her yöntemi sınıfına [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sözleşme.</span><span class="sxs-lookup"><span data-stu-id="9fac8-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fac8-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fac8-115">Example</span></span>  
 <span data-ttu-id="9fac8-116">Aşağıdaki kod örneği bir hizmet sözleşmesini tanımlayan bir sınıf gösterir.</span><span class="sxs-lookup"><span data-stu-id="9fac8-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="9fac8-117">Sahip yöntemleri <xref:System.ServiceModel.OperationContractAttribute> sınıfı uygulanan varsayılan bir istek-yanıt iletisi desen kullanın.</span><span class="sxs-lookup"><span data-stu-id="9fac8-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9fac8-118">Bu ileti deseni bkz [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="9fac8-118"> this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="9fac8-119">Ayrıca, oluşturabilir ve öznitelik özelliklerini ayarlayarak diğer ileti modelleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="9fac8-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="9fac8-120">Daha fazla örnek için bkz: [nasıl yapılır: bir One-Way sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="9fac8-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fac8-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fac8-121">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
