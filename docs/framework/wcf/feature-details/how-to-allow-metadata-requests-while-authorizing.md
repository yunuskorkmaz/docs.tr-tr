---
title: 'Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 4d549bb953ecdcbddd0ea4730a766538b2205d0f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082678"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="1f7c8-102">Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme</span><span class="sxs-lookup"><span data-stu-id="1f7c8-102">How To: Allow Metadata Requests While Authorizing</span></span>
<span data-ttu-id="1f7c8-103">Özel yetkilendirme sırasında işlenecek meta veri isteği izin vermek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="1f7c8-104">Aşağıdaki konuda bu tür bir istek doğrulamak için adımlarda size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="1f7c8-105">Windows Communication Foundation (WCF) yetkilendirme hakkında daha fazla bilgi için bkz: [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="1f7c8-105">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="1f7c8-106">Yetkilendirme sırasında meta veri isteklerine izin vermek için</span><span class="sxs-lookup"><span data-stu-id="1f7c8-106">To allow metadata requests during authorization</span></span>  
  
1.  <span data-ttu-id="1f7c8-107">Oluşturma uzantısı <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2.  <span data-ttu-id="1f7c8-108">Geçersiz kılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="1f7c8-109">Yöntem döndürür `true` veya `false` yetkilendirme verilip verilmediğine bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="1f7c8-110">Geçerli yordam hakkında bilgi de ulaşabilirsiniz <xref:System.ServiceModel.OperationContext> yönteme parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3.  <span data-ttu-id="1f7c8-111">Geçersiz sözleşme adı, ad alanı ve aşağıdaki örnekte gösterildiği gibi bir eylem denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="1f7c8-112">Koşullar geçerli olduğunda, ardından dönün</span><span class="sxs-lookup"><span data-stu-id="1f7c8-112">If the conditions are valid, then return</span></span> `true.`  
  
4.  <span data-ttu-id="1f7c8-113">Sınıf kullanmak istemiyorsunuz genişletilebilirlik noktası kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-113">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="1f7c8-114">Daha fazla bilgi için [nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="1f7c8-114">For more information, see [How to: Create a Custom Authorization Manager for a Service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f7c8-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f7c8-115">Example</span></span>  
 <span data-ttu-id="1f7c8-116">Aşağıdaki örnek, geçersiz kılma gösterir <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1f7c8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f7c8-117">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="1f7c8-118">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="1f7c8-118">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [<span data-ttu-id="1f7c8-119">Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="1f7c8-119">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
