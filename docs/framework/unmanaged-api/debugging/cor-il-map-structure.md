---
title: "COR_IL_MAP Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_IL_MAP
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_IL_MAP
helpviewer_keywords: COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ffcd4dc32f2f509dd9421b2c24781fb2819418b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="corilmap-structure"></a><span data-ttu-id="6cfac-102">COR_IL_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="6cfac-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="6cfac-103">Değişiklikler bir işlev göreli uzaklığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6cfac-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cfac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cfac-104">Syntax</span></span>  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="6cfac-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6cfac-105">Members</span></span>  
  
|<span data-ttu-id="6cfac-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6cfac-106">Member</span></span>|<span data-ttu-id="6cfac-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cfac-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="6cfac-108">İşlev başına göreli uzaklığı eski Microsoft Ara dili (MSIL).</span><span class="sxs-lookup"><span data-stu-id="6cfac-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="6cfac-109">İşlev başlangıcını göre yeni MSIL uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="6cfac-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="6cfac-110">`true`doğru olması için eşleme biliniyorsa; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="6cfac-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cfac-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6cfac-111">Remarks</span></span>  
 <span data-ttu-id="6cfac-112">Harita biçimi aşağıdaki gibidir: hata ayıklayıcı varsayar `oldOffset` özgün, değiştirilmemiş MSIL kodundaki MSIL uzaklığı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="6cfac-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="6cfac-113">`newOffset` Yeni, Araçlı kod içinde karşılık gelen MSIL uzaklık parametresi başvurur.</span><span class="sxs-lookup"><span data-stu-id="6cfac-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="6cfac-114">Atlama için düzgün çalışması için aşağıdaki gereksinimlerin karşılanması:</span><span class="sxs-lookup"><span data-stu-id="6cfac-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
-   <span data-ttu-id="6cfac-115">Harita artan sırada sıralanması.</span><span class="sxs-lookup"><span data-stu-id="6cfac-115">The map should be sorted in ascending order.</span></span>  
  
-   <span data-ttu-id="6cfac-116">İzleme eklenmiş MSIL kod edilip edilmemesi gerektiğini değil.</span><span class="sxs-lookup"><span data-stu-id="6cfac-116">Instrumented MSIL code should not be reordered.</span></span>  
  
-   <span data-ttu-id="6cfac-117">Özgün MSIL kod kaldırılmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6cfac-117">Original MSIL code should not be removed.</span></span>  
  
-   <span data-ttu-id="6cfac-118">Harita program veritabanı (PDB) dosyasından tüm sıralama noktaları eşlemek için girişleri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="6cfac-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="6cfac-119">Harita eksik girdiler kesinti değil.</span><span class="sxs-lookup"><span data-stu-id="6cfac-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="6cfac-120">Aşağıdaki örnek, bir harita ve sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="6cfac-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="6cfac-121">Eşleyin:</span><span class="sxs-lookup"><span data-stu-id="6cfac-121">Map:</span></span>  
  
-   <span data-ttu-id="6cfac-122">eski uzaklığı 0, 0 yeni uzaklığı</span><span class="sxs-lookup"><span data-stu-id="6cfac-122">0 old offset, 0 new offset</span></span>  
  
-   <span data-ttu-id="6cfac-123">5 eski uzaklığı, 10 yeni uzaklığı</span><span class="sxs-lookup"><span data-stu-id="6cfac-123">5 old offset, 10 new offset</span></span>  
  
-   <span data-ttu-id="6cfac-124">9 eski uzaklığı, 20 yeni uzaklığı</span><span class="sxs-lookup"><span data-stu-id="6cfac-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="6cfac-125">Sonuçları:</span><span class="sxs-lookup"><span data-stu-id="6cfac-125">Results:</span></span>  
  
-   <span data-ttu-id="6cfac-126">0, 1, 2, 3 veya 4 eski uzaklığı yeni uzaklığı 0 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="6cfac-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
-   <span data-ttu-id="6cfac-127">5, 6, 7 veya 8 eski uzaklığı yeni uzaklık 10 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="6cfac-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
-   <span data-ttu-id="6cfac-128">9 veya üzeri eski uzaklığı yeni uzaklık 20 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="6cfac-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
-   <span data-ttu-id="6cfac-129">Yeni bir uzaklığı 0, 1, 2, 3, 4, 5, 6, 7, 8 veya 9 eski uzaklığı 0 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="6cfac-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
-   <span data-ttu-id="6cfac-130">Yeni uzaklığını 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 eski uzaklık 5 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="6cfac-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
-   <span data-ttu-id="6cfac-131">Yeni bir uzaklık 20 veya daha yüksek eski uzaklık 9 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="6cfac-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cfac-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6cfac-132">Requirements</span></span>  
 <span data-ttu-id="6cfac-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cfac-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cfac-134">**Başlık:** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="6cfac-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="6cfac-135">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cfac-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cfac-136">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cfac-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cfac-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6cfac-137">See Also</span></span>  
 [<span data-ttu-id="6cfac-138">Hata ayıklama yapıları</span><span class="sxs-lookup"><span data-stu-id="6cfac-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="6cfac-139">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="6cfac-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
