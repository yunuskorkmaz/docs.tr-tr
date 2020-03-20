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
ms.openlocfilehash: 4c79d0e4e37f3f884651e49c8fff6db72fac4f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179299"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="ed357-102">COR_IL_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="ed357-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="ed357-103">Bir işlevin göreli mahsup değişiklikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed357-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed357-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed357-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="ed357-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ed357-105">Members</span></span>  
  
|<span data-ttu-id="ed357-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ed357-106">Member</span></span>|<span data-ttu-id="ed357-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed357-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="ed357-108">Eski Microsoft ara dili (MSIL) işlevin başına göre ofset.</span><span class="sxs-lookup"><span data-stu-id="ed357-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="ed357-109">Yeni MSIL ofset fonksiyonun başına göre.</span><span class="sxs-lookup"><span data-stu-id="ed357-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="ed357-110">`true`haritalamanın doğru olduğu biliniyorsa; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="ed357-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed357-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed357-111">Remarks</span></span>  
 <span data-ttu-id="ed357-112">Haritanın biçimi aşağıdaki gibidir: Hata ayıklayıcı, `oldOffset` özgün, değiştirilmemiş MSIL kodu içinde bir MSIL mahsup anlamına gelir varsayar.</span><span class="sxs-lookup"><span data-stu-id="ed357-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="ed357-113">Parametre, `newOffset` yeni, araçlı kod içinde ilgili MSIL mahsup anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ed357-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="ed357-114">Düzgün çalışmaya adım atmak için aşağıdaki gereksinimlerin karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="ed357-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="ed357-115">Harita artan sırada sıralanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed357-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="ed357-116">İşletilmiş MSIL kodu yeniden sıralanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed357-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="ed357-117">Özgün MSIL kodu kaldırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed357-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="ed357-118">Harita, program veritabanı (PDB) dosyasındaki tüm sıra noktalarını eşlemek için girişleri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="ed357-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="ed357-119">Harita, eksik girişleri interpolate etmez.</span><span class="sxs-lookup"><span data-stu-id="ed357-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="ed357-120">Aşağıdaki örnekte bir harita ve sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed357-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="ed357-121">Harita:</span><span class="sxs-lookup"><span data-stu-id="ed357-121">Map:</span></span>  
  
- <span data-ttu-id="ed357-122">0 eski ofset, 0 yeni ofset</span><span class="sxs-lookup"><span data-stu-id="ed357-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="ed357-123">5 eski ofset, 10 yeni ofset</span><span class="sxs-lookup"><span data-stu-id="ed357-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="ed357-124">9 eski ofset, 20 yeni ofset</span><span class="sxs-lookup"><span data-stu-id="ed357-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="ed357-125">Sonuçlar:</span><span class="sxs-lookup"><span data-stu-id="ed357-125">Results:</span></span>  
  
- <span data-ttu-id="ed357-126">0, 1, 2, 3 veya 4'lü eski bir ofset, 0'ın yeni bir mahsup'una eşlenir.</span><span class="sxs-lookup"><span data-stu-id="ed357-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="ed357-127">5, 6, 7 veya 8'lik eski bir ofset, yeni ofset 10'a eşlenir.</span><span class="sxs-lookup"><span data-stu-id="ed357-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="ed357-128">9 veya daha yüksek eski bir ofset yeni ofset 20 eşlenir.</span><span class="sxs-lookup"><span data-stu-id="ed357-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="ed357-129">0, 1, 2, 3, 4, 5, 6, 7, 8 veya 9'un yeni bir mahsup hakkı eski ofset 0'a eşlenir.</span><span class="sxs-lookup"><span data-stu-id="ed357-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="ed357-130">10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19'luk yeni bir ofset, eski ofset 5'e eşlenir.</span><span class="sxs-lookup"><span data-stu-id="ed357-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="ed357-131">20 veya daha yüksek yeni bir ofset eski ofset 9 eşlenir.</span><span class="sxs-lookup"><span data-stu-id="ed357-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed357-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed357-132">Requirements</span></span>  
 <span data-ttu-id="ed357-133">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed357-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed357-134">**Üstbilgi:** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ed357-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="ed357-135">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed357-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed357-136">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed357-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed357-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed357-137">See also</span></span>

- [<span data-ttu-id="ed357-138">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="ed357-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ed357-139">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ed357-139">Debugging</span></span>](index.md)
