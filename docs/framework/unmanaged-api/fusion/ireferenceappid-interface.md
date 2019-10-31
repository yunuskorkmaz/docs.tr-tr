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
ms.openlocfilehash: 6f20fb2e9e026253fb02b47dfcd63cf655acc4ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131653"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="22db9-102">IReferenceAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22db9-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="22db9-103">Geçerli kapsamdaki uygulamanın benzersiz tanımlayıcısına yönelik bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="22db9-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="22db9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="22db9-104">Methods</span></span>  
  
|<span data-ttu-id="22db9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="22db9-105">Method</span></span>|<span data-ttu-id="22db9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22db9-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="22db9-107">Bu `IReferenceAppId`başvurduğu uygulamanın kod tanımlayıcısının dize gösterimine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="22db9-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="22db9-108">Bu `IReferenceAppId`başvurduğu uygulamanın kod tanımlayıcısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="22db9-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="22db9-109">Bu `IReferenceAppId`üyelerini temsil eden `IReferenceIdentity` örneklerini içeren bir `IEnumReferenceIdentity` örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="22db9-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="22db9-110">Bu `IReferenceAppId`abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="22db9-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="22db9-111">Bu `IReferenceAppId` abonelik için belirteç tanımlayıcısını belirtilen dize değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="22db9-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22db9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22db9-112">Requirements</span></span>  
 <span data-ttu-id="22db9-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22db9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22db9-114">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="22db9-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="22db9-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22db9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22db9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22db9-116">See also</span></span>

- [<span data-ttu-id="22db9-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="22db9-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="22db9-118">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22db9-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="22db9-119">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22db9-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
