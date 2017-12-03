---
title: "Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma"
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
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cf3938f96674b07a7938861e217a93babd83101
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="7d221-102">Nasıl yapılır: Sözleşme Arabirimi ile Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d221-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="7d221-103">Oluşturmak için tercih edilen yol bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sözleşmedir bir arabirim kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7d221-103">The preferred way to create a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contract is by using an interface.</span></span> <span data-ttu-id="7d221-104">Bu sözleşme koleksiyon ve işlemleri erişmek için gerekli iletileri yapısını belirtir hizmeti sunar.</span><span class="sxs-lookup"><span data-stu-id="7d221-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="7d221-105">Bu arabirim uygulayarak giriş ve çıkış türlerini tanımlar <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfına ve <xref:System.ServiceModel.OperationContractAttribute> kullanıma sunmak istediğiniz yöntemleri sınıfına.</span><span class="sxs-lookup"><span data-stu-id="7d221-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="7d221-106">Hizmet sözleşmeleri için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7d221-106"> service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="7d221-107">Bir WCF Sözleşmesi ile bir arabirim oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d221-107">Creating a WCF contract with an interface</span></span>  
  
1.  <span data-ttu-id="7d221-108">Kullanarak yeni bir arabirim oluşturmak [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# veya herhangi diğer ortak dil çalışma zamanı dili.</span><span class="sxs-lookup"><span data-stu-id="7d221-108">Create a new interface using [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="7d221-109">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7d221-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3.  <span data-ttu-id="7d221-110">Arabirim yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7d221-110">Define the methods in the interface.</span></span>  
  
4.  <span data-ttu-id="7d221-111">Uygulama <xref:System.ServiceModel.OperationContractAttribute> ortak bir parçası olarak sunulan her yöntemi sınıfına [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sözleşme.</span><span class="sxs-lookup"><span data-stu-id="7d221-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d221-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d221-112">Example</span></span>  
 <span data-ttu-id="7d221-113">Aşağıdaki kod örneği bir hizmet sözleşmesini tanımlayan bir arabirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d221-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="7d221-114">Sahip yöntemleri <xref:System.ServiceModel.OperationContractAttribute> sınıfı uygulanan varsayılan bir istek-yanıt iletisi desen kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d221-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="7d221-115">Bu ileti deseni bkz [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="7d221-115"> this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="7d221-116">Ayrıca, oluşturabilir ve öznitelik özelliklerini ayarlayarak diğer ileti modelleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d221-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="7d221-117">Daha fazla örnek için bkz: [nasıl yapılır: bir One-Way sözleşmesi oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) ve [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="7d221-117">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d221-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d221-118">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
