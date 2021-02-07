---
description: 'Daha fazla bilgi edinin: COR_SEGMENT Yapısı'
title: COR_SEGMENT Yapısı
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
ms.openlocfilehash: 9bbc452b2c2036d019175ac1be8b9917ffa07b6a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712200"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="db815-103">COR_SEGMENT Yapısı</span><span class="sxs-lookup"><span data-stu-id="db815-103">COR_SEGMENT Structure</span></span>

<span data-ttu-id="db815-104">Yönetilen yığında bir bellek bölgesi hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="db815-104">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db815-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="db815-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;
    CORDB_ADDRESS end;
    CorDebugGenerationTypes gen;
    ULONG heap;
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="db815-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="db815-106">Members</span></span>  
  
|<span data-ttu-id="db815-107">Üye</span><span class="sxs-lookup"><span data-stu-id="db815-107">Member</span></span>|<span data-ttu-id="db815-108">Description</span><span class="sxs-lookup"><span data-stu-id="db815-108">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="db815-109">Bellek bölgesinin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="db815-109">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="db815-110">Bellek bölgesinin bitiş adresi.</span><span class="sxs-lookup"><span data-stu-id="db815-110">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="db815-111">Bellek bölgesinin üretimini gösteren [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) sabit listesi üyesi.</span><span class="sxs-lookup"><span data-stu-id="db815-111">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="db815-112">Bellek bölgesinin bulunduğu yığın numarası.</span><span class="sxs-lookup"><span data-stu-id="db815-112">The heap number in which the memory region resides.</span></span> <span data-ttu-id="db815-113">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="db815-113">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db815-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db815-114">Remarks</span></span>  

 <span data-ttu-id="db815-115">`COR_SEGMENTS`Yapı, yönetilen yığında bir bellek bölgesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="db815-115">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="db815-116">`COR_SEGMENTS`nesneler, [ICorDebugProcess5:: Enumerateheapregion](icordebugprocess5-enumerateheapregions-method.md) yöntemi çağırarak doldurulan [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) koleksiyon nesnesinin üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="db815-116">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="db815-117">`heap`Alan, bildirilen yığına karşılık gelen işlemci numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="db815-117">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="db815-118">İş istasyonları yalnızca bir atık toplama yığınına sahip olduğundan, iş istasyonu atık toplayıcıları için değeri her zaman sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="db815-118">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="db815-119">Sunucu çöp toplayıcıları için, değeri yığının eklendiği işlemciye karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="db815-119">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="db815-120">Çöp toplayıcısının uygulama ayrıntıları nedeniyle gerçek işlemcilerin olduğu daha fazla veya daha az atık toplama yığınlarının olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="db815-120">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db815-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db815-121">Requirements</span></span>  

 <span data-ttu-id="db815-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db815-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db815-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="db815-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db815-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="db815-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db815-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db815-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db815-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db815-126">See also</span></span>

- [<span data-ttu-id="db815-127">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="db815-127">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="db815-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="db815-128">Debugging</span></span>](index.md)
