---
title: 'Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e56a95bf773e22166297bc153ee3ef88320db0f9
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="35c52-102">Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme</span><span class="sxs-lookup"><span data-stu-id="35c52-102">How To: Allow Metadata Requests While Authorizing</span></span>
<span data-ttu-id="35c52-103">Özel yetkilendirme sırasında işlenmesi için meta veriler için bir istek izin vermek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="35c52-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="35c52-104">Aşağıdaki konu böyle bir istek doğrulamak için adımlarda size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="35c52-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="35c52-105">Hakkında daha fazla bilgi için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yetkilendirme, bkz: [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="35c52-105">For more information about [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="35c52-106">Yetkilendirme sırasında meta veri isteklerine izin vermek için</span><span class="sxs-lookup"><span data-stu-id="35c52-106">To allow metadata requests during authorization</span></span>  
  
1.  <span data-ttu-id="35c52-107">Uzantısı oluşturma <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="35c52-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2.  <span data-ttu-id="35c52-108">Geçersiz kılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35c52-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="35c52-109">Yöntem `true` veya `false` yetkilendirme verilip verilmediğine bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="35c52-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="35c52-110">Geçerli yordam hakkında bilgi içinde bulunan <xref:System.ServiceModel.OperationContext> yönteme parametre olarak geçirilen.</span><span class="sxs-lookup"><span data-stu-id="35c52-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3.  <span data-ttu-id="35c52-111">Geçersiz sözleşme adı, ad alanı ve aşağıdaki örnekte gösterildiği gibi eylem denetleyin.</span><span class="sxs-lookup"><span data-stu-id="35c52-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="35c52-112">Koşullar geçerli olduğunda, ardından Döndür `true.`</span><span class="sxs-lookup"><span data-stu-id="35c52-112">If the conditions are valid, then return `true.`</span></span>  
  
4.  <span data-ttu-id="35c52-113">Sınıf kullanımlar için genişletilebilirlik noktası kullanın.</span><span class="sxs-lookup"><span data-stu-id="35c52-113">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="35c52-114">Daha fazla bilgi için bkz: [nasıl yapılır: Özel Yetkilendirme Yöneticisi için bir hizmet oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="35c52-114">For more information, see [How to: Create a Custom Authorization Manager for a Service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35c52-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="35c52-115">Example</span></span>  
 <span data-ttu-id="35c52-116">Aşağıdaki örnek, bir geçersiz kılma gösterir <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35c52-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="35c52-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35c52-117">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="35c52-118">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="35c52-118">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="35c52-119">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="35c52-119">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
