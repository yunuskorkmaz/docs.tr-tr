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
ms.openlocfilehash: 9aa7173d81d84d9080d90b0890769ffeaee6a738
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728621"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="0ccbe-102">IReferenceAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ccbe-102">IReferenceAppId Interface</span></span>

<span data-ttu-id="0ccbe-103">Geçerli kapsamdaki uygulamanın benzersiz tanımlayıcısına yönelik bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ccbe-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ccbe-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0ccbe-104">Methods</span></span>  
  
|<span data-ttu-id="0ccbe-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0ccbe-105">Method</span></span>|<span data-ttu-id="0ccbe-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ccbe-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="0ccbe-107">Bunun başvurduğu uygulamanın kod tanımlayıcısının dize gösterimine yönelik bir işaretçi alır `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="0ccbe-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="0ccbe-108">Bunun başvurduğu uygulamanın kod tanımlayıcısını ayarlar `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="0ccbe-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="0ccbe-109">`IEnumReferenceIdentity` `IReferenceIdentity` Bu öğenin üyelerini temsil eden örnekleri içeren bir örneğe bir arabirim işaretçisi alır `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="0ccbe-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="0ccbe-110">Bu abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="0ccbe-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="0ccbe-111">Bu abonelik için belirteç tanımlayıcısını `IReferenceAppId` belirtilen dize değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0ccbe-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ccbe-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ccbe-112">Requirements</span></span>  

 <span data-ttu-id="0ccbe-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ccbe-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ccbe-114">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="0ccbe-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="0ccbe-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ccbe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccbe-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ccbe-116">See also</span></span>

- [<span data-ttu-id="0ccbe-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0ccbe-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="0ccbe-118">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ccbe-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="0ccbe-119">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ccbe-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
