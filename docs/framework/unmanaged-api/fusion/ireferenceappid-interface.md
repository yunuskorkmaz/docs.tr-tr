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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789694"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="fcf12-102">IReferenceAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcf12-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="fcf12-103">Geçerli kapsam içinde bir uygulama için benzersiz tanımlayıcı bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fcf12-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fcf12-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fcf12-104">Methods</span></span>  
  
|<span data-ttu-id="fcf12-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fcf12-105">Method</span></span>|<span data-ttu-id="fcf12-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcf12-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="fcf12-107">Bu başvuru uygulaması için kod tanımlayıcısı için bir dize gösterimini bir işaretçi alır `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="fcf12-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="fcf12-108">Bu başvuru uygulaması için kod tanımlayıcısı ayarlar `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="fcf12-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="fcf12-109">Bir arabirim işaretçisi alır bir `IEnumReferenceIdentity` örneği içeren `IReferenceIdentity` bu üyeleri temsil eden örnekleri `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="fcf12-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="fcf12-110">Abonelik için bu belirteci tanımlayıcı bir dize gösterimini bir işaretçi alır `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="fcf12-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="fcf12-111">Bir abonelik için belirteç tanımlayıcısı için ayarlar `IReferenceAppId` belirtilen dize değeri.</span><span class="sxs-lookup"><span data-stu-id="fcf12-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fcf12-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcf12-112">Requirements</span></span>  
 <span data-ttu-id="fcf12-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcf12-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcf12-114">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="fcf12-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="fcf12-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcf12-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf12-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcf12-116">See also</span></span>

- [<span data-ttu-id="fcf12-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fcf12-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="fcf12-118">IEnumReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcf12-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [<span data-ttu-id="fcf12-119">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcf12-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
