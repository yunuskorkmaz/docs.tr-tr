---
title: COR_IL_MAP Yapısı
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: c37f039d9636854c464e7981693c573bd60deab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132338"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="12ddd-102">COR_IL_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="12ddd-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="12ddd-103">Bir işlevin göreli uzaklığının değişikliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="12ddd-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ddd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12ddd-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="12ddd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="12ddd-105">Members</span></span>  
  
|<span data-ttu-id="12ddd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="12ddd-106">Member</span></span>|<span data-ttu-id="12ddd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12ddd-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="12ddd-108">İşlevin başlangıcına göre eski Microsoft ara dili (MSIL) uzaklıkları.</span><span class="sxs-lookup"><span data-stu-id="12ddd-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="12ddd-109">İşlevin başlangıcına göre yeni MSIL fark.</span><span class="sxs-lookup"><span data-stu-id="12ddd-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="12ddd-110">eşlemenin doğru olduğu bilindiğinde `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="12ddd-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12ddd-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12ddd-111">Remarks</span></span>  
 <span data-ttu-id="12ddd-112">Haritanın biçimi şu şekildedir: hata ayıklayıcı, `oldOffset` orijinal, değiştirilmemiş MSIL kodu içindeki bir MSIL sapmasını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="12ddd-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="12ddd-113">`newOffset` parametresi, yeni ve belgelenmiş kod içindeki karşılık gelen MSIL sapmasını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="12ddd-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="12ddd-114">Adımların düzgün çalışması için aşağıdaki gereksinimlerin karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="12ddd-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="12ddd-115">Haritanın artan sırada sıralanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="12ddd-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="12ddd-116">Belgelenmiş MSIL kodu yeniden sıralanmaz.</span><span class="sxs-lookup"><span data-stu-id="12ddd-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="12ddd-117">Orijinal MSIL kodu kaldırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="12ddd-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="12ddd-118">Map, program veritabanı (PDB) dosyasındaki tüm sıra noktalarını eşlemek için girdiler içermelidir.</span><span class="sxs-lookup"><span data-stu-id="12ddd-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="12ddd-119">Eşleme, eksik girişleri enterpolamıyor.</span><span class="sxs-lookup"><span data-stu-id="12ddd-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="12ddd-120">Aşağıdaki örnek bir eşlemeyi ve sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="12ddd-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="12ddd-121">Harita</span><span class="sxs-lookup"><span data-stu-id="12ddd-121">Map:</span></span>  
  
- <span data-ttu-id="12ddd-122">0 eski fark, 0 yeni fark</span><span class="sxs-lookup"><span data-stu-id="12ddd-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="12ddd-123">5 eski fark, 10 yeni fark</span><span class="sxs-lookup"><span data-stu-id="12ddd-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="12ddd-124">9 eski fark, 20 yeni fark</span><span class="sxs-lookup"><span data-stu-id="12ddd-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="12ddd-125">Sonucunun</span><span class="sxs-lookup"><span data-stu-id="12ddd-125">Results:</span></span>  
  
- <span data-ttu-id="12ddd-126">0, 1, 2, 3 veya 4 ' ün eski bir kayması, 0 ' ın yeni bir uzaklığa eşlenir.</span><span class="sxs-lookup"><span data-stu-id="12ddd-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="12ddd-127">5, 6, 7 veya 8 ' in eski bir kayması, yeni %10 ' a eşlenir.</span><span class="sxs-lookup"><span data-stu-id="12ddd-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="12ddd-128">Daha eski bir 9 veya üzeri fark, 20. yeni uzaklığa eşlenir.</span><span class="sxs-lookup"><span data-stu-id="12ddd-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="12ddd-129">0, 1, 2, 3, 4, 5, 6, 7, 8 ya da 9 ' un yeni bir kayması, 0 ' dan eski uzaklığa eşlenir.</span><span class="sxs-lookup"><span data-stu-id="12ddd-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="12ddd-130">10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 ' un yeni bir kayması, 5 eski uzaklığa eşlenir.</span><span class="sxs-lookup"><span data-stu-id="12ddd-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="12ddd-131">20 veya üzeri yeni bir konum, eski konum 9 ' A eşlenir.</span><span class="sxs-lookup"><span data-stu-id="12ddd-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12ddd-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12ddd-132">Requirements</span></span>  
 <span data-ttu-id="12ddd-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12ddd-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12ddd-134">**Üst bilgi:** CorDebug. IDL, CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="12ddd-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="12ddd-135">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="12ddd-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12ddd-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12ddd-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ddd-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12ddd-137">See also</span></span>

- [<span data-ttu-id="12ddd-138">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="12ddd-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="12ddd-139">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="12ddd-139">Debugging</span></span>](index.md)
