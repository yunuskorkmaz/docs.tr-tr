---
title: 'Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 296f500532040aaebf0f6d7d37a7a9aae99a3451
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491819"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="9df66-102">Nasıl yapılır: Sınıf ile Windows Communication Foundation Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9df66-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="9df66-103">Windows Communication Foundation (WCF) sözleşme oluşturma tercih edilen bir arabirim kullanılarak yoludur.</span><span class="sxs-lookup"><span data-stu-id="9df66-103">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="9df66-104">Daha fazla bilgi için bkz: [nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="9df66-104">For more information, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="9df66-105">Bir alternatif, Anahatlı burada olan bir sınıf oluşturun ve ardından uygulamak için <xref:System.ServiceModel.ServiceContractAttribute> sınıfa öznitelik doğrudan ve <xref:System.ServiceModel.OperationContractAttribute> özniteliği her sözleşmenin parçası sınıftaki yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="9df66-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="9df66-106">`[ServiceContract]` ve `[ServiceContractAttribute]` aynı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="9df66-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="9df66-107">True için aynı şeyi `[OperationContract]` ve `[OperationContractAttribute]`.</span><span class="sxs-lookup"><span data-stu-id="9df66-107">The same thing it true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="9df66-108">Her durumda, ikinci için toplu eski özelliktir.</span><span class="sxs-lookup"><span data-stu-id="9df66-108">In each case the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="9df66-109">Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9df66-109">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="9df66-110">Bir sınıf ile Windows Communication Foundation sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9df66-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1.  <span data-ttu-id="9df66-111">Visual Basic, C# veya herhangi diğer ortak dil çalışma zamanı dil kullanarak yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9df66-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="9df66-112">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> sınıfı için sınıf.</span><span class="sxs-lookup"><span data-stu-id="9df66-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3.  <span data-ttu-id="9df66-113">Yöntemleri sınıfında oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9df66-113">Create methods in the class.</span></span>  
  
4.  <span data-ttu-id="9df66-114">Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel WCF sözleşmesinin bir parçası olarak sunulan her yönteme sınıf.</span><span class="sxs-lookup"><span data-stu-id="9df66-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9df66-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="9df66-115">Example</span></span>  
 <span data-ttu-id="9df66-116">Aşağıdaki kod örneği bir hizmet sözleşmesini tanımlayan bir sınıf gösterir.</span><span class="sxs-lookup"><span data-stu-id="9df66-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="9df66-117">Sahip yöntemleri <xref:System.ServiceModel.OperationContractAttribute> sınıfı uygulanan varsayılan bir istek-yanıt iletisi desen kullanın.</span><span class="sxs-lookup"><span data-stu-id="9df66-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="9df66-118">Bu ileti deseni hakkında daha fazla bilgi için bkz: [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="9df66-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="9df66-119">Ayrıca, oluşturabilir ve öznitelik özelliklerini ayarlayarak diğer ileti modelleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="9df66-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="9df66-120">Daha fazla örnek için bkz: [nasıl yapılır: bir One-Way sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="9df66-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9df66-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9df66-121">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
