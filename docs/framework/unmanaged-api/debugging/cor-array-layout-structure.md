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
ms.openlocfilehash: 2ca6c89a671c4d7882e7cefdb820d07ac5636530
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727412"
---
# <a name="cor_array_layout-structure"></a><span data-ttu-id="32084-102">COR_ARRAY_LAYOUT Yapısı</span><span class="sxs-lookup"><span data-stu-id="32084-102">COR_ARRAY_LAYOUT Structure</span></span>

<span data-ttu-id="32084-103">Bellekte bir dizi nesnesinin yerleşimi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="32084-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32084-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="32084-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="32084-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="32084-105">Members</span></span>  
  
|<span data-ttu-id="32084-106">Üye</span><span class="sxs-lookup"><span data-stu-id="32084-106">Member</span></span>|<span data-ttu-id="32084-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32084-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="32084-108">Dizinin içerdiği nesne türünün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="32084-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="32084-109">Bileşenin bir çöp toplama başvurusu, bir değer sınıfı veya temel öğe olup olmadığını gösteren bir CorElementType numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="32084-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="32084-110">Dizideki ilk öğenin boşluğu.</span><span class="sxs-lookup"><span data-stu-id="32084-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="32084-111">Her öğenin boyutu.</span><span class="sxs-lookup"><span data-stu-id="32084-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="32084-112">Dizideki öğe sayısının boşluğu.</span><span class="sxs-lookup"><span data-stu-id="32084-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="32084-113">Derecenin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="32084-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="32084-114">Dizideki derecelendirmelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="32084-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="32084-115">Derecelendirmelerinin başlayacağı fark.</span><span class="sxs-lookup"><span data-stu-id="32084-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32084-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32084-116">Remarks</span></span>  

 <span data-ttu-id="32084-117">`rankSize`Alan, çok boyutlu bir dizideki bir derece boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="32084-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="32084-118">Tek boyutlu diziler için de doğrudur.</span><span class="sxs-lookup"><span data-stu-id="32084-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="32084-119">Değeri, `numRanks` tek boyutlu bir dizi için ve `N` çok boyutlu bir boyut dizisi için 1 ' dir `N` .</span><span class="sxs-lookup"><span data-stu-id="32084-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32084-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32084-120">Requirements</span></span>  

 <span data-ttu-id="32084-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32084-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32084-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32084-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32084-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="32084-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32084-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32084-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32084-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32084-125">See also</span></span>

- [<span data-ttu-id="32084-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="32084-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="32084-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="32084-127">Debugging</span></span>](index.md)
