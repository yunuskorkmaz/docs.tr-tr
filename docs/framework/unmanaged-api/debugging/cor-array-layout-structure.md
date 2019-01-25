---
title: COR_ARRAY_LAYOUT Yapısı
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6fee91146e99ba1f63ecafcbbdaae9d42675848
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731146"
---
# <a name="corarraylayout-structure"></a><span data-ttu-id="052d6-102">COR_ARRAY_LAYOUT Yapısı</span><span class="sxs-lookup"><span data-stu-id="052d6-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="052d6-103">Bir dizi nesnesinin bellek düzeni hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="052d6-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="052d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="052d6-104">Syntax</span></span>  
  
```  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="052d6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="052d6-105">Members</span></span>  
  
|<span data-ttu-id="052d6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="052d6-106">Member</span></span>|<span data-ttu-id="052d6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="052d6-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="052d6-108">Dizinin içerdiği nesnelerin türü tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="052d6-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="052d6-109">Bileşen bir çöp toplama başvuru, değer sınıfı veya basit bir tür olup olmadığını belirten bir CorElementType sabit listesi değeri.</span><span class="sxs-lookup"><span data-stu-id="052d6-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="052d6-110">Dizideki ilk öğe için olan uzaklık.</span><span class="sxs-lookup"><span data-stu-id="052d6-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="052d6-111">Her öğe boyutu.</span><span class="sxs-lookup"><span data-stu-id="052d6-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="052d6-112">Dizideki öğelerin sayısını uzaklık.</span><span class="sxs-lookup"><span data-stu-id="052d6-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="052d6-113">Boyut, bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="052d6-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="052d6-114">Dizideki sıralamalara sahip sayısı.</span><span class="sxs-lookup"><span data-stu-id="052d6-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="052d6-115">Başlangıçtan sıralamalara sahip başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="052d6-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="052d6-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="052d6-116">Remarks</span></span>  
 <span data-ttu-id="052d6-117">`rankSize` Alanı, çok boyutlu bir dizi sırası boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="052d6-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="052d6-118">Tek boyutlu diziler için de doğrudur.</span><span class="sxs-lookup"><span data-stu-id="052d6-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="052d6-119">Değerini `numRanks` tek boyutlu bir dizi için 1'dir ve `N` çok boyutlu bir dizi için `N` boyutları.</span><span class="sxs-lookup"><span data-stu-id="052d6-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="052d6-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="052d6-120">Requirements</span></span>  
 <span data-ttu-id="052d6-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="052d6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="052d6-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="052d6-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="052d6-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="052d6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="052d6-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="052d6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="052d6-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="052d6-125">See also</span></span>
- [<span data-ttu-id="052d6-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="052d6-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="052d6-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="052d6-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
