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
ms.openlocfilehash: 78e34d9d33d34047e3ebd2effb4894bc7b709585
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132353"
---
# <a name="cor_field-structure"></a><span data-ttu-id="5c71d-102">COR_FIELD Yapısı</span><span class="sxs-lookup"><span data-stu-id="5c71d-102">COR_FIELD Structure</span></span>
<span data-ttu-id="5c71d-103">Bir nesne içindeki bir alan hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c71d-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c71d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c71d-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="5c71d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5c71d-105">Members</span></span>  
  
|<span data-ttu-id="5c71d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="5c71d-106">Member</span></span>|<span data-ttu-id="5c71d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c71d-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="5c71d-108">Alan bilgilerini almak için kullanılabilen bir `mdFieldDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="5c71d-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="5c71d-109">Nesnedeki alan verilerine göre bayt cinsinden fark.</span><span class="sxs-lookup"><span data-stu-id="5c71d-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="5c71d-110">Bu alanın türünü tanımlayan bir [COR_TYPEID](cor-typeid-structure.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="5c71d-110">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="5c71d-111">Alanın türünü gösteren bir CorElementType numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="5c71d-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c71d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c71d-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c71d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c71d-113">Requirements</span></span>  
 <span data-ttu-id="5c71d-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c71d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c71d-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5c71d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c71d-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5c71d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c71d-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c71d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c71d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c71d-118">See also</span></span>

- [<span data-ttu-id="5c71d-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="5c71d-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="5c71d-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5c71d-120">Debugging</span></span>](index.md)
