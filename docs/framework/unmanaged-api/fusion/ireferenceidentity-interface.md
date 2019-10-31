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
ms.openlocfilehash: 8f6a117d1e2fe76c271b0b014e6079370c8b4fe4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127061"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="1c532-102">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c532-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="1c532-103">Bir kod nesnesinin benzersiz imzasına bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1c532-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c532-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1c532-104">Methods</span></span>  
  
|<span data-ttu-id="1c532-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1c532-105">Method</span></span>|<span data-ttu-id="1c532-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c532-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="1c532-107">Belirtilen öznitelik değişiklikleri dışında, bu `IReferenceIdentity`özdeş olan yeni bir `IReferenceIdentity` örneğine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="1c532-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="1c532-108">Bu `IReferenceIdentity`ilişkili öznitelikleri içeren `IEnumIDENTITY_ATTRIBUTE` örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="1c532-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="1c532-109">Belirtilen ad alanındaki özniteliğin değerini belirtilen adla alır.</span><span class="sxs-lookup"><span data-stu-id="1c532-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="1c532-110">Belirtilen ad alanına ve belirtilen ada sahip olan özniteliği belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1c532-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c532-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c532-111">Requirements</span></span>  
 <span data-ttu-id="1c532-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c532-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c532-113">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="1c532-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="1c532-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c532-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c532-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c532-115">See also</span></span>

- [<span data-ttu-id="1c532-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1c532-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="1c532-117">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c532-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
