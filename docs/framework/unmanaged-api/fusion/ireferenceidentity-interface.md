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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796361"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="816b5-102">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="816b5-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="816b5-103">Bir kod nesnesinin benzersiz imzasına bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="816b5-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="816b5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="816b5-104">Methods</span></span>  
  
|<span data-ttu-id="816b5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="816b5-105">Method</span></span>|<span data-ttu-id="816b5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="816b5-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="816b5-107">Belirtilen öznitelik değişiklikleri dışında, bu `IReferenceIdentity` `IReferenceIdentity`ile özdeş olan yeni bir örneğe bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="816b5-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="816b5-108">`IEnumIDENTITY_ATTRIBUTE` Bu`IReferenceIdentity`ile ilişkili öznitelikleri içeren bir örneğe bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="816b5-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="816b5-109">Belirtilen ad alanındaki özniteliğin değerini belirtilen adla alır.</span><span class="sxs-lookup"><span data-stu-id="816b5-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="816b5-110">Belirtilen ad alanına ve belirtilen ada sahip olan özniteliği belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="816b5-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="816b5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="816b5-111">Requirements</span></span>  
 <span data-ttu-id="816b5-112">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="816b5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="816b5-113">**Üst bilgi** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="816b5-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="816b5-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="816b5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816b5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="816b5-115">See also</span></span>

- [<span data-ttu-id="816b5-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="816b5-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="816b5-117">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="816b5-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
