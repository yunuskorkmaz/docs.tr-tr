---
title: IReferenceAppId Arabirimi
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25733e459423500352595d6be0eee26ef75ca7e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157202"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="c1bb9-102">IReferenceAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1bb9-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="c1bb9-103">Geçerli kapsam içinde bir uygulama için benzersiz tanımlayıcı bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1bb9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c1bb9-104">Methods</span></span>  
  
|<span data-ttu-id="c1bb9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c1bb9-105">Method</span></span>|<span data-ttu-id="c1bb9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1bb9-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="c1bb9-107">Bu başvuru uygulaması için kod tanımlayıcısı için bir dize gösterimini bir işaretçi alır `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="c1bb9-108">Bu başvuru uygulaması için kod tanımlayıcısı ayarlar `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="c1bb9-109">Bir arabirim işaretçisi alır bir `IEnumReferenceIdentity` örneği içeren `IReferenceIdentity` bu üyeleri temsil eden örnekleri `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="c1bb9-110">Abonelik için bu belirteci tanımlayıcı bir dize gösterimini bir işaretçi alır `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="c1bb9-111">Bir abonelik için belirteç tanımlayıcısı için ayarlar `IReferenceAppId` belirtilen dize değeri.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1bb9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1bb9-112">Requirements</span></span>  
 <span data-ttu-id="c1bb9-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1bb9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1bb9-114">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="c1bb9-114">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="c1bb9-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c1bb9-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c1bb9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-116">See also</span></span>

- [<span data-ttu-id="c1bb9-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c1bb9-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="c1bb9-118">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1bb9-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [<span data-ttu-id="c1bb9-119">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1bb9-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
