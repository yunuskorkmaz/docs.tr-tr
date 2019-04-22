---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: faf1be65d308b223490f3ae67eed3d8a2b1688b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223075"
---
# <a name="corsegment-structure"></a><span data-ttu-id="dee7d-102">COR_SEGMENT Yapısı</span><span class="sxs-lookup"><span data-stu-id="dee7d-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="dee7d-103">Bellek yönetilen yığında bir bölge hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="dee7d-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dee7d-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="dee7d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="dee7d-105">Members</span></span>  
  
|<span data-ttu-id="dee7d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="dee7d-106">Member</span></span>|<span data-ttu-id="dee7d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dee7d-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="dee7d-108">Bellek bölgesini başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="dee7d-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="dee7d-109">Bellek bölgesini bitiş adresi.</span><span class="sxs-lookup"><span data-stu-id="dee7d-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="dee7d-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) bellek bölgesini neslini belirten sabit listesi üyesi.</span><span class="sxs-lookup"><span data-stu-id="dee7d-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="dee7d-111">Bellek bölgesini bulunduğu yığın sayısı.</span><span class="sxs-lookup"><span data-stu-id="dee7d-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="dee7d-112">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="dee7d-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dee7d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dee7d-113">Remarks</span></span>  
 <span data-ttu-id="dee7d-114">`COR_SEGMENTS` Yapıyı yönetilen yığında bellek bölgesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dee7d-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="dee7d-115">`COR_SEGMENTS` nesneleri üyeleridir [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) çağırarak doldurulur koleksiyon nesnesine [Icordebugprocess5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dee7d-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="dee7d-116">`heap` Karşılık gelen bildirilen yığın işlemci sayısı bir alandır.</span><span class="sxs-lookup"><span data-stu-id="dee7d-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="dee7d-117">İş istasyonu çöp toplama yığınında yalnızca bir olduğundan iş istasyonu atık toplayıcıları değeri her zaman sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="dee7d-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="dee7d-118">Sunucu atık toplayıcıları, yığın bağlı işlemciye değerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="dee7d-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="dee7d-119">Olabilir, daha fazla veya daha az çöp toplama yığınlardaki atık toplayıcının uygulama ayrıntılarını nedeniyle gerçek işlemci sayısından unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dee7d-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dee7d-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dee7d-120">Requirements</span></span>  
 <span data-ttu-id="dee7d-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dee7d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dee7d-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dee7d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dee7d-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dee7d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dee7d-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dee7d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee7d-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dee7d-125">See also</span></span>

- [<span data-ttu-id="dee7d-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="dee7d-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="dee7d-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="dee7d-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
