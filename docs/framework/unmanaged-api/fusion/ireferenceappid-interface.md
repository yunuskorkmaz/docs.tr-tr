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
ms.workload: dotnet
ms.openlocfilehash: 22ac2d75632b3c670d7c185cbbf5081732dcaffc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="6e993-102">IReferenceAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e993-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="6e993-103">Geçerli kapsamdaki uygulama için benzersiz tanımlayıcı başvuru temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e993-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e993-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6e993-104">Methods</span></span>  
  
|<span data-ttu-id="6e993-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6e993-105">Method</span></span>|<span data-ttu-id="6e993-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e993-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="6e993-107">Bu tarafından başvurulan uygulaması için kod tanımlayıcı bir dize gösterimini bir işaretçi alır `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="6e993-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="6e993-108">Bu tarafından başvurulan uygulama için kod tanımlayıcı ayarlar `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="6e993-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="6e993-109">Bir arabirim işaretçisi alır bir `IEnumReferenceIdentity` örneğini içeren `IReferenceIdentity` bu üyeleri temsil örnekleri `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="6e993-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="6e993-110">Bu abonelik için bir işaretçi belirteç tanımlayıcı bir dize gösterimini alır `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="6e993-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="6e993-111">Bir abonelik için belirteç tanımlayıcı için ayarlar `IReferenceAppId` belirtilen dize değeri.</span><span class="sxs-lookup"><span data-stu-id="6e993-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e993-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e993-112">Requirements</span></span>  
 <span data-ttu-id="6e993-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e993-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e993-114">**Başlık:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="6e993-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="6e993-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e993-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e993-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e993-116">See Also</span></span>  
 [<span data-ttu-id="6e993-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6e993-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="6e993-118">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e993-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="6e993-119">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e993-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
