---
title: 'Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: c7d4bce174790b97db6b95aa5d15af455f261f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597169"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="d9847-102">Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9847-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="d9847-103">Windows Communication Foundation (WCF) sözleşmesinin oluşturulması için tercih edilen yol, bir arabirim kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d9847-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="d9847-104">Bu sözleşme, hizmet sunduğu işlemlere erişmek için gereken iletilerin toplanmasını ve yapısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9847-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="d9847-105">Bu arabirim, <xref:System.ServiceModel.ServiceContractAttribute> sınıfının arabirime ve sınıfına sınıfını uygulayarak giriş ve çıkış türlerini, <xref:System.ServiceModel.OperationContractAttribute> göstermek istediğiniz yöntemlere tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d9847-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="d9847-106">Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="d9847-106">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="d9847-107">Arabirim ile WCF sözleşmesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9847-107">Creating a WCF contract with an interface</span></span>  
  
1. <span data-ttu-id="d9847-108">Visual Basic, C# veya başka bir ortak dil çalışma zamanı dili kullanarak yeni bir arabirim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d9847-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="d9847-109"><xref:System.ServiceModel.ServiceContractAttribute>Sınıfı arabirime uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d9847-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3. <span data-ttu-id="d9847-110">Arabirimindeki yöntemleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d9847-110">Define the methods in the interface.</span></span>  
  
4. <span data-ttu-id="d9847-111">Sınıfı, <xref:System.ServiceModel.OperationContractAttribute> genel WCF sözleşmesinin bir parçası olarak kullanıma sunulacak her bir yönteme uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d9847-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9847-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9847-112">Example</span></span>  
 <span data-ttu-id="d9847-113">Aşağıdaki kod örneğinde, bir hizmet sözleşmesini tanımlayan bir arabirim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d9847-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="d9847-114"><xref:System.ServiceModel.OperationContractAttribute>Sınıf uygulanmış Yöntemler varsayılan olarak bir istek-yanıt iletisi model kullanır.</span><span class="sxs-lookup"><span data-stu-id="d9847-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="d9847-115">Bu ileti düzeniyle ilgili daha fazla bilgi için bkz. [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="d9847-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="d9847-116">Ayrıca, özniteliğin özelliklerini ayarlayarak diğer ileti düzenlerini de oluşturabilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9847-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="d9847-117">Daha fazla örnek için bkz. [nasıl yapılır: tek yönlü sözleşme oluşturma](how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="d9847-117">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9847-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9847-118">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
