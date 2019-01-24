---
title: 'Nasıl yapılır: Yetkilendirirken meta veri isteklerine izin verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 820725e22c8f07c10212f434e377d5b039cc75e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591917"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="e6125-102">Nasıl yapılır: Yetkilendirirken meta veri isteklerine izin verme</span><span class="sxs-lookup"><span data-stu-id="e6125-102">How To: Allow Metadata Requests While Authorizing</span></span>
<span data-ttu-id="e6125-103">Özel yetkilendirme sırasında işlenecek meta veri isteği izin vermek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6125-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="e6125-104">Aşağıdaki konuda bu tür bir istek doğrulamak için adımlarda size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6125-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="e6125-105">Windows Communication Foundation (WCF) yetkilendirme hakkında daha fazla bilgi için bkz: [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="e6125-105">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="e6125-106">Yetkilendirme sırasında meta veri isteklerine izin vermek için</span><span class="sxs-lookup"><span data-stu-id="e6125-106">To allow metadata requests during authorization</span></span>  
  
1.  <span data-ttu-id="e6125-107">Oluşturma uzantısı <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e6125-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2.  <span data-ttu-id="e6125-108">Geçersiz kılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e6125-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="e6125-109">Yöntem döndürür `true` veya `false` yetkilendirme verilip verilmediğine bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="e6125-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="e6125-110">Geçerli yordam hakkında bilgi de ulaşabilirsiniz <xref:System.ServiceModel.OperationContext> yönteme parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="e6125-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3.  <span data-ttu-id="e6125-111">Geçersiz sözleşme adı, ad alanı ve aşağıdaki örnekte gösterildiği gibi bir eylem denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e6125-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="e6125-112">Koşullar geçerli olduğunda, ardından dönün `true.`</span><span class="sxs-lookup"><span data-stu-id="e6125-112">If the conditions are valid, then return `true.`</span></span>  
  
4.  <span data-ttu-id="e6125-113">Sınıf kullanmak istemiyorsunuz genişletilebilirlik noktası kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6125-113">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="e6125-114">Daha fazla bilgi için [nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="e6125-114">For more information, see [How to: Create a Custom Authorization Manager for a Service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6125-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6125-115">Example</span></span>  
 <span data-ttu-id="e6125-116">Aşağıdaki örnek, geçersiz kılma gösterir <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e6125-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e6125-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6125-117">See also</span></span>
- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="e6125-118">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="e6125-118">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [<span data-ttu-id="e6125-119">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="e6125-119">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
