---
description: 'Daha fazla bilgi edinin: COR_IL_MAP yapısı'
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
ms.openlocfilehash: ff3d636429f51119342baea5d71163eb9d764e03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712330"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="7c139-103">COR_IL_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="7c139-103">COR_IL_MAP Structure</span></span>

<span data-ttu-id="7c139-104">Bir işlevin göreli uzaklığının değişikliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c139-104">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c139-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7c139-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="7c139-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7c139-106">Members</span></span>  
  
|<span data-ttu-id="7c139-107">Üye</span><span class="sxs-lookup"><span data-stu-id="7c139-107">Member</span></span>|<span data-ttu-id="7c139-108">Description</span><span class="sxs-lookup"><span data-stu-id="7c139-108">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="7c139-109">İşlevin başlangıcına göre eski Microsoft ara dili (MSIL) uzaklıkları.</span><span class="sxs-lookup"><span data-stu-id="7c139-109">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="7c139-110">İşlevin başlangıcına göre yeni MSIL fark.</span><span class="sxs-lookup"><span data-stu-id="7c139-110">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="7c139-111">`true` eşlemenin doğru olduğu bilinmektedir; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="7c139-111">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c139-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c139-112">Remarks</span></span>  

 <span data-ttu-id="7c139-113">Haritanın biçimi şu şekildedir: hata ayıklayıcı, `oldOffset` orijinal, DEĞIŞTIRILMEMIŞ MSIL kodu içindeki BIR MSIL sapmasını ifade eden kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7c139-113">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="7c139-114">`newOffset`Parametresi, yeni ve belgelenmiş kod içindeki karşılık gelen MSIL sapmasını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="7c139-114">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="7c139-115">Adımların düzgün çalışması için aşağıdaki gereksinimlerin karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="7c139-115">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="7c139-116">Haritanın artan sırada sıralanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c139-116">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="7c139-117">Belgelenmiş MSIL kodu yeniden sıralanmaz.</span><span class="sxs-lookup"><span data-stu-id="7c139-117">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="7c139-118">Orijinal MSIL kodu kaldırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c139-118">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="7c139-119">Map, program veritabanı (PDB) dosyasındaki tüm sıra noktalarını eşlemek için girdiler içermelidir.</span><span class="sxs-lookup"><span data-stu-id="7c139-119">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="7c139-120">Eşleme, eksik girişleri enterpolamıyor.</span><span class="sxs-lookup"><span data-stu-id="7c139-120">The map does not interpolate missing entries.</span></span> <span data-ttu-id="7c139-121">Aşağıdaki örnek bir eşlemeyi ve sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c139-121">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="7c139-122">Harita</span><span class="sxs-lookup"><span data-stu-id="7c139-122">Map:</span></span>  
  
- <span data-ttu-id="7c139-123">0 eski fark, 0 yeni fark</span><span class="sxs-lookup"><span data-stu-id="7c139-123">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="7c139-124">5 eski fark, 10 yeni fark</span><span class="sxs-lookup"><span data-stu-id="7c139-124">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="7c139-125">9 eski fark, 20 yeni fark</span><span class="sxs-lookup"><span data-stu-id="7c139-125">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="7c139-126">Sonuçlar:</span><span class="sxs-lookup"><span data-stu-id="7c139-126">Results:</span></span>  
  
- <span data-ttu-id="7c139-127">0, 1, 2, 3 veya 4 ' ün eski bir kayması, 0 ' ın yeni bir uzaklığa eşlenir.</span><span class="sxs-lookup"><span data-stu-id="7c139-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="7c139-128">5, 6, 7 veya 8 ' in eski bir kayması, yeni %10 ' a eşlenir.</span><span class="sxs-lookup"><span data-stu-id="7c139-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="7c139-129">Daha eski bir 9 veya üzeri fark, 20. yeni uzaklığa eşlenir.</span><span class="sxs-lookup"><span data-stu-id="7c139-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="7c139-130">0, 1, 2, 3, 4, 5, 6, 7, 8 ya da 9 ' un yeni bir kayması, 0 ' dan eski uzaklığa eşlenir.</span><span class="sxs-lookup"><span data-stu-id="7c139-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="7c139-131">10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 ' un yeni bir kayması, 5 eski uzaklığa eşlenir.</span><span class="sxs-lookup"><span data-stu-id="7c139-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="7c139-132">20 veya üzeri yeni bir konum, eski konum 9 ' A eşlenir.</span><span class="sxs-lookup"><span data-stu-id="7c139-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c139-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c139-133">Requirements</span></span>  

 <span data-ttu-id="7c139-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c139-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c139-135">**Üst bilgi:** CorDebug. IDL, CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="7c139-135">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="7c139-136">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7c139-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c139-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c139-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c139-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c139-138">See also</span></span>

- [<span data-ttu-id="7c139-139">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="7c139-139">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="7c139-140">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7c139-140">Debugging</span></span>](index.md)
