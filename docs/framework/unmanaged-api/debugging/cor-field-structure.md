---
title: COR_FIELD Yapısı
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 691041632312bf8ac7c82a11724dcd725e14a420
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231064"
---
# <a name="corfield-structure"></a><span data-ttu-id="5de0d-102">COR_FIELD Yapısı</span><span class="sxs-lookup"><span data-stu-id="5de0d-102">COR_FIELD Structure</span></span>
<span data-ttu-id="5de0d-103">Bir alan bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5de0d-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5de0d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5de0d-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="5de0d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5de0d-105">Members</span></span>  
  
|<span data-ttu-id="5de0d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="5de0d-106">Member</span></span>|<span data-ttu-id="5de0d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5de0d-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="5de0d-108">Bir `mdFieldDef` alan bilgilerini almak için kullanılan belirteç.</span><span class="sxs-lookup"><span data-stu-id="5de0d-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="5de0d-109">Nesne yer alan verilere bayt cinsinden uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="5de0d-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="5de0d-110">A [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bu alanın türünü tanımlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="5de0d-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="5de0d-111">Alan türünü belirten bir CorElementType sabit listesi değer.</span><span class="sxs-lookup"><span data-stu-id="5de0d-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5de0d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5de0d-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5de0d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5de0d-113">Requirements</span></span>  
 <span data-ttu-id="5de0d-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5de0d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5de0d-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5de0d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5de0d-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5de0d-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5de0d-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="5de0d-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5de0d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5de0d-118">See also</span></span>

- [<span data-ttu-id="5de0d-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="5de0d-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="5de0d-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5de0d-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
