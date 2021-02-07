---
description: 'Daha fazla bilgi edinin: nasıl yapılır: yetkilendirirken meta veri Isteklerine Izin verme'
title: 'Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: a9f5ab7db73aaa8a2a420a60c3172f1b1a738fb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742751"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a><span data-ttu-id="02efa-103">Nasıl yapılır: Yetkilendirirken Meta Veri İsteklerine İzin Verme</span><span class="sxs-lookup"><span data-stu-id="02efa-103">How To: Allow Metadata Requests While Authorizing</span></span>

<span data-ttu-id="02efa-104">Özel yetkilendirme sırasında, meta verilerin işlenmesine yönelik bir isteğin işlenmesine izin vermek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="02efa-104">During custom authorization, it may be necessary to allow a request for metadata to be processed.</span></span> <span data-ttu-id="02efa-105">Aşağıdaki konu, bu tür bir isteği doğrulamaya yönelik adımları adım adım göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="02efa-105">The following topic walks through the steps to validate such a request.</span></span>  
  
 <span data-ttu-id="02efa-106">Windows Communication Foundation (WCF) yetkilendirmesi hakkında daha fazla bilgi için bkz. [Yetkilendirme](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="02efa-106">For more information about Windows Communication Foundation (WCF) authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
### <a name="to-allow-metadata-requests-during-authorization"></a><span data-ttu-id="02efa-107">Yetkilendirme sırasında meta veri isteklerine izin vermek için</span><span class="sxs-lookup"><span data-stu-id="02efa-107">To allow metadata requests during authorization</span></span>  
  
1. <span data-ttu-id="02efa-108">Sınıfın bir uzantısını oluşturun <xref:System.ServiceModel.ServiceAuthorizationManager> .</span><span class="sxs-lookup"><span data-stu-id="02efa-108">Create an extension of the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
2. <span data-ttu-id="02efa-109">Yöntemini geçersiz kılın <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> .</span><span class="sxs-lookup"><span data-stu-id="02efa-109">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="02efa-110">Yöntemi, `true` `false` yetkilendirime izin verilip verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02efa-110">The method returns `true` or `false` depending on whether authorization is allowed.</span></span> <span data-ttu-id="02efa-111">Geçerli yordam hakkındaki bilgiler, <xref:System.ServiceModel.OperationContext> metoduna bir parametre olarak geçirilmiş içinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="02efa-111">Information about the current procedure is found in the <xref:System.ServiceModel.OperationContext> passed as a parameter to the method.</span></span>  
  
3. <span data-ttu-id="02efa-112">Geçersiz kılma ' da, aşağıdaki örnekte gösterildiği gibi sözleşme adını, ad alanını ve eylemi kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="02efa-112">In the override, check the contract name, namespace, and the action as shown in the following example.</span></span> <span data-ttu-id="02efa-113">Koşullar geçerliyse, dön `true.`</span><span class="sxs-lookup"><span data-stu-id="02efa-113">If the conditions are valid, then return `true.`</span></span>  
  
4. <span data-ttu-id="02efa-114">Sınıfı kullanmak için genişletilebilirlik noktasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="02efa-114">Use the extensibility point to employ the class.</span></span> <span data-ttu-id="02efa-115">Daha fazla bilgi için bkz. [nasıl yapılır: bir hizmet Için özel Yetkilendirme Yöneticisi oluşturma](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="02efa-115">For more information, see [How to: Create a Custom Authorization Manager for a Service](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02efa-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="02efa-116">Example</span></span>  

 <span data-ttu-id="02efa-117">Aşağıdaki örnek yöntemi geçersiz kılmayı gösterir <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> .</span><span class="sxs-lookup"><span data-stu-id="02efa-117">The following example shows an override of the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span>  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="02efa-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02efa-118">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="02efa-119">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="02efa-119">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="02efa-120">Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="02efa-120">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
