---
title: 'Nasıl yapılır: Sınıf ile Windows Communication Foundation sözleşmesi oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 2cd757107d9f62ce749d98db1d4968c02a09c5d2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988741"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="7b758-102">Nasıl yapılır: Sınıf ile Windows Communication Foundation sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b758-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="7b758-103">Windows Communication Foundation (WCF) sözleşmesinin oluşturulması için tercih edilen yöntem bir arabirim kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7b758-103">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="7b758-104">Daha fazla bilgi için [nasıl yapılır: Bir hizmet sözleşmesi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7b758-104">For more information, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="7b758-105">Burada özetlenen alternatif, bir sınıf oluşturmak ve ardından doğrudan sınıfa <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> ve özniteliği, sözleşmenin bir parçası olan sınıftaki yöntemlerin her birine uygular.</span><span class="sxs-lookup"><span data-stu-id="7b758-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="7b758-106">`[ServiceContract]`ve `[ServiceContractAttribute]` aynı şeyi yapın.</span><span class="sxs-lookup"><span data-stu-id="7b758-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="7b758-107">`[OperationContract]` Ve`[OperationContractAttribute]`için aynı şey doğrudur.</span><span class="sxs-lookup"><span data-stu-id="7b758-107">The same thing is true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="7b758-108">Her durumda, ilki ikinci için toplu bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="7b758-108">In each case, the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="7b758-109">Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7b758-109">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="7b758-110">Bir sınıfla Windows Communication Foundation sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b758-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1. <span data-ttu-id="7b758-111">Visual Basic, C#veya diğer tüm ortak dil çalışma zamanı dilini kullanarak yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b758-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="7b758-112"><xref:System.ServiceModel.ServiceContractAttribute> Sınıfını sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="7b758-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3. <span data-ttu-id="7b758-113">Sınıfında yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b758-113">Create methods in the class.</span></span>  
  
4. <span data-ttu-id="7b758-114"><xref:System.ServiceModel.OperationContractAttribute> Sınıfı, genel WCF sözleşmesinin bir parçası olarak kullanıma sunulacak her bir yönteme uygulayın.</span><span class="sxs-lookup"><span data-stu-id="7b758-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b758-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b758-115">Example</span></span>  
 <span data-ttu-id="7b758-116">Aşağıdaki kod örneği, bir hizmet sözleşmesini tanımlayan bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b758-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="7b758-117"><xref:System.ServiceModel.OperationContractAttribute> Sınıf uygulanmış Yöntemler varsayılan olarak bir istek-yanıt iletisi model kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b758-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="7b758-118">Bu ileti düzeniyle ilgili daha fazla bilgi için bkz [. nasıl yapılır: Istek-yanıt Sözleşmesi](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b758-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="7b758-119">Ayrıca, özniteliğin özelliklerini ayarlayarak diğer ileti düzenlerini de oluşturabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b758-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="7b758-120">Daha fazla örnek için bkz [. nasıl yapılır: Tek yönlü bir sözleşme](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) oluşturun ve [şunları yapın: Çift yönlü sözleşme](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7b758-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b758-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b758-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
