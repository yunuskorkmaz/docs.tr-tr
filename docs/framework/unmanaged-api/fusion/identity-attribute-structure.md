---
title: IDENTITY_ATTRIBUTE Yapısı
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb970d31fb5158adc7dbcbb7cc0175cc91c83c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698050"
---
# <a name="identityattribute-structure"></a><span data-ttu-id="2d2b0-102">IDENTITY_ATTRIBUTE Yapısı</span><span class="sxs-lookup"><span data-stu-id="2d2b0-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="2d2b0-103">Hakkında meta veri özniteliğinin bilgilerini içeren bir [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="2d2b0-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d2b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d2b0-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="2d2b0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2d2b0-105">Members</span></span>  
  
|<span data-ttu-id="2d2b0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2d2b0-106">Member</span></span>|<span data-ttu-id="2d2b0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d2b0-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="2d2b0-108">Ad uzayını içeren null ile sonlandırılmış dizeye bir işaretçi olarak özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="2d2b0-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="2d2b0-109">Özniteliğin adını içeren null ile sonlandırılmış dizeye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2d2b0-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="2d2b0-110">Öznitelik değerini içeren null ile sonlandırılmış dizeye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2d2b0-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d2b0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d2b0-111">Remarks</span></span>  
 <span data-ttu-id="2d2b0-112">`IDENTITY_ATTRIBUTE` Yapısı null ile sonlandırılmış dizeleri üç işaretçileri içerir.</span><span class="sxs-lookup"><span data-stu-id="2d2b0-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="2d2b0-113">Bu üç dizeleri bir öznitelik açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2d2b0-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="2d2b0-114">Örneği bir `IDENTITY_ATTRIBUTE` yapısı örneği ile ilişkili bir [ıdentıty_attrıbute_blob](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="2d2b0-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="2d2b0-115">`IDENTITY_ATTRIBUTE` Yapısı içeren gerçek dizeleri ve karşılık gelen `IDENTITY_ATTRIBUTE_BLOB` yapısı listeler listelenen üç dizelere uzaklıkları `IDENTITY_ATTRIBUTE` yapısı.</span><span class="sxs-lookup"><span data-stu-id="2d2b0-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d2b0-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d2b0-116">Requirements</span></span>  
 <span data-ttu-id="2d2b0-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d2b0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d2b0-118">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="2d2b0-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="2d2b0-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d2b0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d2b0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d2b0-120">See also</span></span>

- [<span data-ttu-id="2d2b0-121">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d2b0-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [<span data-ttu-id="2d2b0-122">IDENTITY_ATTRIBUTE_BLOB Yapısı</span><span class="sxs-lookup"><span data-stu-id="2d2b0-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [<span data-ttu-id="2d2b0-123">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="2d2b0-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
