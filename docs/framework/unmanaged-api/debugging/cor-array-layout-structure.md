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
ms.openlocfilehash: ca2d00611a7530dfb0d1c2a27123947bdf69820d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179347"
---
# <a name="cor_array_layout-structure"></a><span data-ttu-id="2c81c-102">COR_ARRAY_LAYOUT Yapısı</span><span class="sxs-lookup"><span data-stu-id="2c81c-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="2c81c-103">Bellekte bir dizi nesnesinin düzeni hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c81c-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c81c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c81c-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="2c81c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2c81c-105">Members</span></span>  
  
|<span data-ttu-id="2c81c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2c81c-106">Member</span></span>|<span data-ttu-id="2c81c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c81c-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="2c81c-108">Dizinin içerdiği nesne türünün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2c81c-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="2c81c-109">Bileşenin çöp toplama başvurusu mu, değer sınıfı mı yoksa ilkel mi olduğunu gösteren bir CorElementType numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="2c81c-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="2c81c-110">Dizideki ilk öğeye ofset.</span><span class="sxs-lookup"><span data-stu-id="2c81c-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="2c81c-111">Her öğenin boyutu.</span><span class="sxs-lookup"><span data-stu-id="2c81c-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="2c81c-112">Dizideki öğe sayısına mahsup.</span><span class="sxs-lookup"><span data-stu-id="2c81c-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="2c81c-113">Rütbenin büyüklüğü, baytlar halinde.</span><span class="sxs-lookup"><span data-stu-id="2c81c-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="2c81c-114">Dizideki rütbe sayısı.</span><span class="sxs-lookup"><span data-stu-id="2c81c-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="2c81c-115">Rütbelerin başladığı ofset.</span><span class="sxs-lookup"><span data-stu-id="2c81c-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c81c-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c81c-116">Remarks</span></span>  
 <span data-ttu-id="2c81c-117">Alan, `rankSize` çok boyutlu bir dizideki bir sıralamanın boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c81c-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="2c81c-118">Tek boyutlu diziler için de doğrudur.</span><span class="sxs-lookup"><span data-stu-id="2c81c-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="2c81c-119">Tek boyutlu `numRanks` bir dizi ve `N` çok boyutlu boyutlar dizisi `N` için değeri 1'dir.</span><span class="sxs-lookup"><span data-stu-id="2c81c-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c81c-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c81c-120">Requirements</span></span>  
 <span data-ttu-id="2c81c-121">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c81c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c81c-122">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c81c-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c81c-123">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c81c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c81c-124">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c81c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c81c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c81c-125">See also</span></span>

- [<span data-ttu-id="2c81c-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="2c81c-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="2c81c-127">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2c81c-127">Debugging</span></span>](index.md)
