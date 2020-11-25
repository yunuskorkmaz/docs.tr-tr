---
title: IReferenceIdentity Arabirimi
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
ms.openlocfilehash: 867c09caa3bd3aed50de21c2ef91a02782830be2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704558"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="caddf-102">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="caddf-102">IReferenceIdentity Interface</span></span>

<span data-ttu-id="caddf-103">Bir kod nesnesinin benzersiz imzasına bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="caddf-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="caddf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="caddf-104">Methods</span></span>  
  
|<span data-ttu-id="caddf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="caddf-105">Method</span></span>|<span data-ttu-id="caddf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="caddf-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="caddf-107">`IReferenceIdentity` `IReferenceIdentity` Belirtilen öznitelik değişiklikleri dışında, bu ile özdeş olan yeni bir örneğe bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="caddf-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="caddf-108">`IEnumIDENTITY_ATTRIBUTE`Bu ile ilişkili öznitelikleri içeren bir örneğe bir arabirim işaretçisi alır `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="caddf-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="caddf-109">Belirtilen ad alanındaki özniteliğin değerini belirtilen adla alır.</span><span class="sxs-lookup"><span data-stu-id="caddf-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="caddf-110">Belirtilen ad alanına ve belirtilen ada sahip olan özniteliği belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="caddf-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="caddf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="caddf-111">Requirements</span></span>  

 <span data-ttu-id="caddf-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caddf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caddf-113">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="caddf-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="caddf-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caddf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caddf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="caddf-115">See also</span></span>

- [<span data-ttu-id="caddf-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="caddf-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="caddf-117">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="caddf-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
