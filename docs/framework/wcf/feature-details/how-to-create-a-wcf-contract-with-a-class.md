---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: sınıf ile Windows Communication Foundation sözleşmesi oluşturma'
title: 'Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 63a5cc4e6a7966af69f2d5f3c7db0c7f4e313faf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756168"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="e92e6-103">Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e92e6-103">How to: Create a Windows Communication Foundation Contract with a Class</span></span>

<span data-ttu-id="e92e6-104">Windows Communication Foundation (WCF) sözleşmesinin oluşturulması için tercih edilen yöntem bir arabirim kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e92e6-104">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="e92e6-105">Daha fazla bilgi için bkz. [nasıl yapılır: hizmet sözleşmesi tanımlama](../how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="e92e6-105">For more information, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="e92e6-106">Burada özetlenen alternatif, bir sınıf oluşturmak ve ardından <xref:System.ServiceModel.ServiceContractAttribute> doğrudan sınıfa ve <xref:System.ServiceModel.OperationContractAttribute> özniteliği, sözleşmenin bir parçası olan sınıftaki yöntemlerin her birine uygular.</span><span class="sxs-lookup"><span data-stu-id="e92e6-106">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="e92e6-107">`[ServiceContract]` ve `[ServiceContractAttribute]` aynı şeyi yapın.</span><span class="sxs-lookup"><span data-stu-id="e92e6-107">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="e92e6-108">Ve için aynı şey doğrudur `[OperationContract]` `[OperationContractAttribute]` .</span><span class="sxs-lookup"><span data-stu-id="e92e6-108">The same thing is true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="e92e6-109">Her durumda, ilki ikinci için toplu bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e92e6-109">In each case, the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="e92e6-110">Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e92e6-110">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="e92e6-111">Bir sınıfla Windows Communication Foundation sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e92e6-111">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1. <span data-ttu-id="e92e6-112">Visual Basic, C# veya başka bir ortak dil çalışma zamanı dili kullanarak yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e92e6-112">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="e92e6-113">Sınıfını <xref:System.ServiceModel.ServiceContractAttribute> sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e92e6-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3. <span data-ttu-id="e92e6-114">Sınıfında yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e92e6-114">Create methods in the class.</span></span>  
  
4. <span data-ttu-id="e92e6-115">Sınıfı, <xref:System.ServiceModel.OperationContractAttribute> genel WCF sözleşmesinin bir parçası olarak kullanıma sunulacak her bir yönteme uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e92e6-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e92e6-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="e92e6-116">Example</span></span>  

 <span data-ttu-id="e92e6-117">Aşağıdaki kod örneği, bir hizmet sözleşmesini tanımlayan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e92e6-117">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="e92e6-118"><xref:System.ServiceModel.OperationContractAttribute>Sınıf uygulanmış Yöntemler varsayılan olarak bir istek-yanıt iletisi model kullanır.</span><span class="sxs-lookup"><span data-stu-id="e92e6-118">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="e92e6-119">Bu ileti düzeniyle ilgili daha fazla bilgi için bkz. [nasıl yapılır: Request-Reply sözleşmesi oluşturma](how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="e92e6-119">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="e92e6-120">Ayrıca, özniteliğin özelliklerini ayarlayarak diğer ileti düzenlerini de oluşturabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e92e6-120">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="e92e6-121">Daha fazla örnek için bkz. [nasıl yapılır: One-Way sözleşmesi oluşturma](how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="e92e6-121">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e92e6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e92e6-122">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
