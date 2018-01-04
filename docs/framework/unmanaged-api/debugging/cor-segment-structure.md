---
title: "COR_SEGMENT Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_SEGMENT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_SEGMENT
helpviewer_keywords: COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9414aa1c36ba059d9ee1101f6183dc8a669f9e6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corsegment-structure"></a><span data-ttu-id="7a1e1-102">COR_SEGMENT Yapısı</span><span class="sxs-lookup"><span data-stu-id="7a1e1-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="7a1e1-103">Yönetilen yığın bellekte bir bölge hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a1e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a1e1-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="7a1e1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7a1e1-105">Members</span></span>  
  
|<span data-ttu-id="7a1e1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7a1e1-106">Member</span></span>|<span data-ttu-id="7a1e1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a1e1-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="7a1e1-108">Bellek bölge başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="7a1e1-109">Bellek bölge bitiş adresi.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="7a1e1-110">A [cordebuggenerationtypes sabit](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) bellek bölge neslini belirten numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="7a1e1-111">Bellek bölge bulunduğu yığın sayısı.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="7a1e1-112">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a1e1-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a1e1-113">Remarks</span></span>  
 <span data-ttu-id="7a1e1-114">`COR_SEGMENTS` Yapısı Yönetilen yığın bellekte bölgesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="7a1e1-115">`COR_SEGMENTS`nesneleri üyeleri olan [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) çağırarak doldurulur koleksiyon nesnesi[Icordebugprocess5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="7a1e1-116">`heap` Raporlandığını yığın karşılık gelen işlemci numarası bir alandır.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="7a1e1-117">İş istasyonları yalnızca bir atık toplama yığın olduğundan iş istasyonu atık toplayıcıları, değeri sıfır, her zaman olduğu.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="7a1e1-118">Sunucu atık toplayıcıları değerini öbek iliştirildiği işlemci karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="7a1e1-119">Olabileceğini daha fazla veya daha az atık toplama yığınlardaki atık toplayıcı uygulama ayrıntılarını nedeniyle gerçek işlemciler çok dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a1e1-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a1e1-120">Requirements</span></span>  
 <span data-ttu-id="7a1e1-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a1e1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a1e1-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a1e1-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a1e1-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a1e1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a1e1-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a1e1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a1e1-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a1e1-125">See Also</span></span>  
 [<span data-ttu-id="7a1e1-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="7a1e1-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="7a1e1-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7a1e1-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
