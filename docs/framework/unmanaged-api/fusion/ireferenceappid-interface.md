---
description: 'Şu konuda daha fazla bilgi edinin: IReferenceAppId arabirimi'
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
ms.openlocfilehash: 66838d6ae66aa7de05d899e9fa980308718e2a38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800077"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="b87f5-103">IReferenceAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b87f5-103">IReferenceAppId Interface</span></span>

<span data-ttu-id="b87f5-104">Geçerli kapsamdaki uygulamanın benzersiz tanımlayıcısına yönelik bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b87f5-104">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b87f5-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b87f5-105">Methods</span></span>  
  
|<span data-ttu-id="b87f5-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b87f5-106">Method</span></span>|<span data-ttu-id="b87f5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b87f5-107">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="b87f5-108">Bunun başvurduğu uygulamanın kod tanımlayıcısının dize gösterimine yönelik bir işaretçi alır `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="b87f5-108">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="b87f5-109">Bunun başvurduğu uygulamanın kod tanımlayıcısını ayarlar `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="b87f5-109">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="b87f5-110">`IEnumReferenceIdentity` `IReferenceIdentity` Bu öğenin üyelerini temsil eden örnekleri içeren bir örneğe bir arabirim işaretçisi alır `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="b87f5-110">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="b87f5-111">Bu abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="b87f5-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="b87f5-112">Bu abonelik için belirteç tanımlayıcısını `IReferenceAppId` belirtilen dize değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b87f5-112">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b87f5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b87f5-113">Requirements</span></span>  

 <span data-ttu-id="b87f5-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b87f5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b87f5-115">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="b87f5-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b87f5-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b87f5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b87f5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b87f5-117">See also</span></span>

- [<span data-ttu-id="b87f5-118">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b87f5-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="b87f5-119">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b87f5-119">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="b87f5-120">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b87f5-120">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
