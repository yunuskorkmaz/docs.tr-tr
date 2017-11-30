---
title: IReferenceAppId Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceAppId
helpviewer_keywords: IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cac4ef63292f1bd342bb94799872b002fdcdf945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="c98ba-102">IReferenceAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c98ba-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="c98ba-103">Geçerli kapsamdaki uygulama için benzersiz tanımlayıcı başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c98ba-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c98ba-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c98ba-104">Methods</span></span>  
  
|<span data-ttu-id="c98ba-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c98ba-105">Method</span></span>|<span data-ttu-id="c98ba-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c98ba-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="c98ba-107">Bu tarafından başvurulan uygulaması için kod tanımlayıcı bir dize gösterimini bir işaretçi alır `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c98ba-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="c98ba-108">Bu tarafından başvurulan uygulama için kod tanımlayıcı ayarlar `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c98ba-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="c98ba-109">Bir arabirim işaretçisi alır bir `IEnumReferenceIdentity` örneğini içeren `IReferenceIdentity` bu üyeleri temsil örnekleri `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c98ba-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="c98ba-110">Bu abonelik için bir işaretçi belirteç tanımlayıcı bir dize gösterimini alır `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c98ba-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="c98ba-111">Bir abonelik için belirteç tanımlayıcı için ayarlar `IReferenceAppId` belirtilen dize değeri.</span><span class="sxs-lookup"><span data-stu-id="c98ba-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c98ba-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c98ba-112">Requirements</span></span>  
 <span data-ttu-id="c98ba-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c98ba-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c98ba-114">**Başlık:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="c98ba-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c98ba-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c98ba-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c98ba-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c98ba-116">See Also</span></span>  
 [<span data-ttu-id="c98ba-117">Fusion arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c98ba-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="c98ba-118">Ienumreferenceıdentity arabirimi</span><span class="sxs-lookup"><span data-stu-id="c98ba-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="c98ba-119">Ireferenceıdentity arabirimi</span><span class="sxs-lookup"><span data-stu-id="c98ba-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
