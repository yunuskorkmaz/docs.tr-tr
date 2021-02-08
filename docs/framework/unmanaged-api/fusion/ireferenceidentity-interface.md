---
description: 'Daha fazla bilgi edinin: IReferenceIdentity Arabirimi'
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
ms.openlocfilehash: a29aaa1f4fb928c136af4168619d27900537c779
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800051"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="dd3d9-103">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd3d9-103">IReferenceIdentity Interface</span></span>

<span data-ttu-id="dd3d9-104">Bir kod nesnesinin benzersiz imzasına bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dd3d9-104">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd3d9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dd3d9-105">Methods</span></span>  
  
|<span data-ttu-id="dd3d9-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dd3d9-106">Method</span></span>|<span data-ttu-id="dd3d9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd3d9-107">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="dd3d9-108">`IReferenceIdentity` `IReferenceIdentity` Belirtilen öznitelik değişiklikleri dışında, bu ile özdeş olan yeni bir örneğe bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="dd3d9-108">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="dd3d9-109">`IEnumIDENTITY_ATTRIBUTE`Bu ile ilişkili öznitelikleri içeren bir örneğe bir arabirim işaretçisi alır `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="dd3d9-109">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="dd3d9-110">Belirtilen ad alanındaki özniteliğin değerini belirtilen adla alır.</span><span class="sxs-lookup"><span data-stu-id="dd3d9-110">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="dd3d9-111">Belirtilen ad alanına ve belirtilen ada sahip olan özniteliği belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dd3d9-111">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd3d9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd3d9-112">Requirements</span></span>  

 <span data-ttu-id="dd3d9-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd3d9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd3d9-114">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="dd3d9-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="dd3d9-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd3d9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd3d9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd3d9-116">See also</span></span>

- [<span data-ttu-id="dd3d9-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dd3d9-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="dd3d9-118">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd3d9-118">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
