---
title: 'Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 796870b80ed72db2353e79db3e4e3fc164c22875
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489800"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="97422-102">Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="97422-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="97422-103">Windows Communication Foundation (WCF) sözleşme oluşturmak için tercih edilen bir arabirim kullanılarak yoludur.</span><span class="sxs-lookup"><span data-stu-id="97422-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="97422-104">Bu sözleşme koleksiyon ve işlemleri erişmek için gerekli iletileri yapısını belirtir hizmeti sunar.</span><span class="sxs-lookup"><span data-stu-id="97422-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="97422-105">Bu arabirim uygulayarak giriş ve çıkış türlerini tanımlar <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfına ve <xref:System.ServiceModel.OperationContractAttribute> kullanıma sunmak istediğiniz yöntemleri sınıfına.</span><span class="sxs-lookup"><span data-stu-id="97422-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="97422-106">Hizmet sözleşmeleri hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="97422-106">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="97422-107">Bir WCF Sözleşmesi ile bir arabirim oluşturma</span><span class="sxs-lookup"><span data-stu-id="97422-107">Creating a WCF contract with an interface</span></span>  
  
1.  <span data-ttu-id="97422-108">Visual Basic, C# veya herhangi diğer ortak dil çalışma zamanı dil kullanarak yeni bir arabirim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97422-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="97422-109">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="97422-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3.  <span data-ttu-id="97422-110">Arabirim yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97422-110">Define the methods in the interface.</span></span>  
  
4.  <span data-ttu-id="97422-111">Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel WCF sözleşmesinin bir parçası olarak sunulan her yönteme sınıf.</span><span class="sxs-lookup"><span data-stu-id="97422-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97422-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="97422-112">Example</span></span>  
 <span data-ttu-id="97422-113">Aşağıdaki kod örneği bir hizmet sözleşmesini tanımlayan bir arabirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="97422-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="97422-114">Sahip yöntemleri <xref:System.ServiceModel.OperationContractAttribute> sınıfı uygulanan varsayılan bir istek-yanıt iletisi desen kullanın.</span><span class="sxs-lookup"><span data-stu-id="97422-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="97422-115">Bu ileti deseni hakkında daha fazla bilgi için bkz: [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="97422-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="97422-116">Ayrıca, oluşturabilir ve öznitelik özelliklerini ayarlayarak diğer ileti modelleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="97422-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="97422-117">Daha fazla örnek için bkz: [nasıl yapılır: bir One-Way sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="97422-117">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97422-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97422-118">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
