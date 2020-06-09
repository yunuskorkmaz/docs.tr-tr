---
title: 'Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 6d172f9b659804179d23fb382376f83f4898edc5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601315"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="a130a-102">Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme</span><span class="sxs-lookup"><span data-stu-id="a130a-102">How To: Allow Metadata Requests While Authorizing</span></span>
<span data-ttu-id="a130a-103">Özel yetkilendirme sırasında, meta verilerin işlenmesine yönelik bir isteğin işlenmesine izin vermek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="a130a-103">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="a130a-104">Aşağıdaki konu, bu tür bir isteği doğrulamaya yönelik adımları adım adım göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a130a-104">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="a130a-105">Windows Communication Foundation (WCF) yetkilendirmesi hakkında daha fazla bilgi için bkz. [Yetkilendirme](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="a130a-105">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="a130a-106">Yetkilendirme sırasında meta veri isteklerine izin vermek için</span><span class="sxs-lookup"><span data-stu-id="a130a-106">To allow metadata requests during authorization</span></span>  
  
1. <span data-ttu-id="a130a-107">Sınıfın bir uzantısını oluşturun <xref:System.ServiceModel.ServiceAuthorizationManager> .</span><span class="sxs-lookup"><span data-stu-id="a130a-107">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2. <span data-ttu-id="a130a-108">Yöntemini geçersiz kılın <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> .</span><span class="sxs-lookup"><span data-stu-id="a130a-108">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="a130a-109">Yöntemi, `true` `false` yetkilendirime izin verilip verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a130a-109">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="a130a-110">Geçerli yordam hakkındaki bilgiler, <xref:System.ServiceModel.OperationContext> metoduna bir parametre olarak geçirilmiş içinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a130a-110">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3. <span data-ttu-id="a130a-111">Geçersiz kılma ' da, aşağıdaki örnekte gösterildiği gibi sözleşme adını, ad alanını ve eylemi kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="a130a-111">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="a130a-112">Koşullar geçerliyse, dön`true.`</span><span class="sxs-lookup"><span data-stu-id="a130a-112">If the conditions are valid, then return `true.`</span></span>  
  
4. <span data-ttu-id="a130a-113">Sınıfı kullanmak için genişletilebilirlik noktasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a130a-113">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="a130a-114">Daha fazla bilgi için bkz. [nasıl yapılır: bir hizmet Için özel Yetkilendirme Yöneticisi oluşturma](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="a130a-114">For more information, see [How to: Create a Custom Authorization Manager for a Service](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a130a-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a130a-115">Example</span></span>  
 <span data-ttu-id="a130a-116">Aşağıdaki örnek yöntemi geçersiz kılmayı gösterir <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> .</span><span class="sxs-lookup"><span data-stu-id="a130a-116">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a130a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a130a-117">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="a130a-118">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="a130a-118">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="a130a-119">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="a130a-119">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
