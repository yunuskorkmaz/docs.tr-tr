---
title: 'Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 0be2400ef3da5f0bbc218032ecd69af23f82cabd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597143"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="a2f91-102">Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2f91-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="a2f91-103">Windows Communication Foundation (WCF) sözleşmesinin oluşturulması için tercih edilen yöntem bir arabirim kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="a2f91-103">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="a2f91-104">Daha fazla bilgi için bkz. [nasıl yapılır: hizmet sözleşmesi tanımlama](../how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a2f91-104">For more information, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="a2f91-105">Burada özetlenen alternatif, bir sınıf oluşturmak ve ardından <xref:System.ServiceModel.ServiceContractAttribute> doğrudan sınıfa ve <xref:System.ServiceModel.OperationContractAttribute> özniteliği, sözleşmenin bir parçası olan sınıftaki yöntemlerin her birine uygular.</span><span class="sxs-lookup"><span data-stu-id="a2f91-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a2f91-106">`[ServiceContract]`ve `[ServiceContractAttribute]` aynı şeyi yapın.</span><span class="sxs-lookup"><span data-stu-id="a2f91-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="a2f91-107">Ve için aynı şey doğrudur `[OperationContract]` `[OperationContractAttribute]` .</span><span class="sxs-lookup"><span data-stu-id="a2f91-107">The same thing is true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="a2f91-108">Her durumda, ilki ikinci için toplu bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="a2f91-108">In each case, the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="a2f91-109">Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a2f91-109">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="a2f91-110">Bir sınıfla Windows Communication Foundation sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2f91-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1. <span data-ttu-id="a2f91-111">Visual Basic, C# veya başka bir ortak dil çalışma zamanı dili kullanarak yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a2f91-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="a2f91-112">Sınıfını <xref:System.ServiceModel.ServiceContractAttribute> sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a2f91-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3. <span data-ttu-id="a2f91-113">Sınıfında yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a2f91-113">Create methods in the class.</span></span>  
  
4. <span data-ttu-id="a2f91-114">Sınıfı, <xref:System.ServiceModel.OperationContractAttribute> genel WCF sözleşmesinin bir parçası olarak kullanıma sunulacak her bir yönteme uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a2f91-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2f91-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2f91-115">Example</span></span>  
 <span data-ttu-id="a2f91-116">Aşağıdaki kod örneği, bir hizmet sözleşmesini tanımlayan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2f91-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="a2f91-117"><xref:System.ServiceModel.OperationContractAttribute>Sınıf uygulanmış Yöntemler varsayılan olarak bir istek-yanıt iletisi model kullanır.</span><span class="sxs-lookup"><span data-stu-id="a2f91-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="a2f91-118">Bu ileti düzeniyle ilgili daha fazla bilgi için bkz. [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a2f91-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="a2f91-119">Ayrıca, özniteliğin özelliklerini ayarlayarak diğer ileti düzenlerini de oluşturabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2f91-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="a2f91-120">Daha fazla örnek için bkz. [nasıl yapılır: tek yönlü sözleşme oluşturma](how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a2f91-120">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2f91-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2f91-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
