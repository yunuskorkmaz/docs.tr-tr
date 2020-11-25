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
ms.openlocfilehash: ae8e907d0e0d6ef5030b3e9aa1f1b3dcef50193e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726632"
---
# <a name="cor_field-structure"></a><span data-ttu-id="d1838-102">COR_FIELD Yapısı</span><span class="sxs-lookup"><span data-stu-id="d1838-102">COR_FIELD Structure</span></span>

<span data-ttu-id="d1838-103">Bir nesne içindeki bir alan hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1838-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1838-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1838-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="d1838-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d1838-105">Members</span></span>  
  
|<span data-ttu-id="d1838-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d1838-106">Member</span></span>|<span data-ttu-id="d1838-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1838-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="d1838-108">`mdFieldDef`Alan bilgilerini almak için kullanılabilen bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="d1838-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="d1838-109">Nesnedeki alan verilerine göre bayt cinsinden fark.</span><span class="sxs-lookup"><span data-stu-id="d1838-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="d1838-110">Bu alanın türünü tanımlayan [COR_TYPEID](cor-typeid-structure.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="d1838-110">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="d1838-111">Alanın türünü gösteren bir CorElementType numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="d1838-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1838-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1838-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1838-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1838-113">Requirements</span></span>  

 <span data-ttu-id="d1838-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1838-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1838-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d1838-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1838-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d1838-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1838-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1838-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1838-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1838-118">See also</span></span>

- [<span data-ttu-id="d1838-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="d1838-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="d1838-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d1838-120">Debugging</span></span>](index.md)
