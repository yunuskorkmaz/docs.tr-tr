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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74f515626f5001cbea1a25e8268338c588524bde
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740539"
---
# <a name="corilmap-structure"></a><span data-ttu-id="372d7-102">COR_IL_MAP Yapısı</span><span class="sxs-lookup"><span data-stu-id="372d7-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="372d7-103">Değişiklikleri, bir işlevin göreli uzaklığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="372d7-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="372d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="372d7-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="372d7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="372d7-105">Members</span></span>  
  
|<span data-ttu-id="372d7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="372d7-106">Member</span></span>|<span data-ttu-id="372d7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="372d7-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="372d7-108">İşlevin başlangıcına göre uzaklığı eski Microsoft Ara dilini (MSIL).</span><span class="sxs-lookup"><span data-stu-id="372d7-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="372d7-109">İşlevin başlangıcına göre yeni MSIL uzaklık.</span><span class="sxs-lookup"><span data-stu-id="372d7-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="372d7-110">`true` eşleme doğru olarak bilinir Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="372d7-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="372d7-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="372d7-111">Remarks</span></span>  
 <span data-ttu-id="372d7-112">Eşleme biçimi aşağıdaki gibidir: Hata ayıklayıcı varsayar `oldOffset` özgün, değiştirilmemiş MSIL kodu içinde bir MSIL uzaklığı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="372d7-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="372d7-113">`newOffset` Yeni, izleme eklenmiş kod içinde karşılık gelen MSIL uzaklık parametresi başvurur.</span><span class="sxs-lookup"><span data-stu-id="372d7-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="372d7-114">Düzgün çalışması için atlamak için aşağıdaki gereksinimlerin karşılanması:</span><span class="sxs-lookup"><span data-stu-id="372d7-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="372d7-115">Harita, artan düzende sıralanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="372d7-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="372d7-116">İzleme eklenmiş MSIL kodu edilip edilmemesi gerektiğini değil.</span><span class="sxs-lookup"><span data-stu-id="372d7-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="372d7-117">Özgün MSIL kodu kaldırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="372d7-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="372d7-118">Eşleme girişleri program veritabanı (PDB) dosyasındaki dizi noktalarını eşlemek için içermelidir.</span><span class="sxs-lookup"><span data-stu-id="372d7-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="372d7-119">Harita eksik girdiler enterpolasyon değil.</span><span class="sxs-lookup"><span data-stu-id="372d7-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="372d7-120">Aşağıdaki örnek, bir harita ve sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="372d7-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="372d7-121">Eşleme:</span><span class="sxs-lookup"><span data-stu-id="372d7-121">Map:</span></span>  
  
- <span data-ttu-id="372d7-122">0 eski uzaklığı, 0 yeni uzaklık</span><span class="sxs-lookup"><span data-stu-id="372d7-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="372d7-123">5 eski uzaklığı, 10 yeni uzaklık</span><span class="sxs-lookup"><span data-stu-id="372d7-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="372d7-124">9 eski uzaklığı, 20 yeni uzaklık</span><span class="sxs-lookup"><span data-stu-id="372d7-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="372d7-125">Sonuçları:</span><span class="sxs-lookup"><span data-stu-id="372d7-125">Results:</span></span>  
  
- <span data-ttu-id="372d7-126">0, 1, 2, 3 veya 4 eski uzaklığı 0'ın yeni bir uzaklık eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="372d7-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="372d7-127">Eski bir uzaklık 5, 6, 7 veya 8, 10 yeni uzaklık eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="372d7-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="372d7-128">9 veya daha eski bir uzaklık yeni uzaklık 20 eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="372d7-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="372d7-129">Yeni bir uzaklığı 0, 1, 2, 3, 4, 5, 6, 7, 8 veya 9 eski uzaklığı 0 eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="372d7-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="372d7-130">Yeni bir uzaklık 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 eski uzaklığı 5 eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="372d7-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="372d7-131">20 veya üzeri bir yeni uzaklığı eski uzaklığı 9 eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="372d7-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="372d7-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="372d7-132">Requirements</span></span>  
 <span data-ttu-id="372d7-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="372d7-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="372d7-134">**Üst bilgi:** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="372d7-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="372d7-135">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="372d7-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="372d7-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="372d7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372d7-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="372d7-137">See also</span></span>

- [<span data-ttu-id="372d7-138">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="372d7-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="372d7-139">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="372d7-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
