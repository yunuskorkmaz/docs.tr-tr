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
ms.openlocfilehash: dd46ea26532074c9ea42da4d07a38ed583aad076
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220169"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="6f525-102">IReferenceIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f525-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="6f525-103">Kod nesnesi benzersiz imzası bir başvuruyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6f525-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f525-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6f525-104">Methods</span></span>  
  
|<span data-ttu-id="6f525-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6f525-105">Method</span></span>|<span data-ttu-id="6f525-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f525-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="6f525-107">Yeni bir arabirim işaretçisi alır `IReferenceIdentity` için aynı olan örneği `IReferenceIdentity`, belirtilen öznitelik değişiklikleri dışında.</span><span class="sxs-lookup"><span data-stu-id="6f525-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="6f525-108">Bir arabirim işaretçisi alır bir `IEnumIDENTITY_ATTRIBUTE` bununla ilişkili öznitelikleri içeren örneğini `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="6f525-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="6f525-109">Belirtilen ada sahip belirtilen ad alanı özniteliğinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="6f525-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="6f525-110">Belirtilen ad alanı ve belirtilen değere belirtilen ada sahip özniteliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6f525-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f525-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f525-111">Requirements</span></span>  
 <span data-ttu-id="6f525-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f525-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f525-113">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="6f525-113">**Header:** Isolation.h</span></span>  
  
 **<span data-ttu-id="6f525-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6f525-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6f525-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f525-115">See also</span></span>

- [<span data-ttu-id="6f525-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6f525-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="6f525-117">IEnumIDENTITY_ATTRIBUTE Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f525-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
