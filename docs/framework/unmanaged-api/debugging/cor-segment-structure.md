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
ms.openlocfilehash: aabf3ac4e51280bd847d145e15ad804d514ede2c
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274004"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="011cb-102">COR_SEGMENT Yapısı</span><span class="sxs-lookup"><span data-stu-id="011cb-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="011cb-103">Yönetilen yığında bir bellek bölgesi hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="011cb-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="011cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="011cb-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="011cb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="011cb-105">Members</span></span>  
  
|<span data-ttu-id="011cb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="011cb-106">Member</span></span>|<span data-ttu-id="011cb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="011cb-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="011cb-108">Bellek bölgesinin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="011cb-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="011cb-109">Bellek bölgesinin bitiş adresi.</span><span class="sxs-lookup"><span data-stu-id="011cb-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="011cb-110">Bellek bölgesinin üretimini gösteren [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) sabit listesi üyesi.</span><span class="sxs-lookup"><span data-stu-id="011cb-110">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="011cb-111">Bellek bölgesinin bulunduğu yığın numarası.</span><span class="sxs-lookup"><span data-stu-id="011cb-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="011cb-112">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="011cb-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="011cb-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="011cb-113">Remarks</span></span>  
 <span data-ttu-id="011cb-114">`COR_SEGMENTS` Yapı, yönetilen yığında bir bellek bölgesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="011cb-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="011cb-115">`COR_SEGMENTS`nesneler, [ICorDebugProcess5:: Enumerateheapregion](icordebugprocess5-enumerateheapregions-method.md) yöntemi çağırarak doldurulan [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) koleksiyon nesnesinin üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="011cb-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="011cb-116">`heap` Alan, bildirilen yığına karşılık gelen işlemci numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="011cb-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="011cb-117">İş istasyonları yalnızca bir atık toplama yığınına sahip olduğundan, iş istasyonu atık toplayıcıları için değeri her zaman sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="011cb-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="011cb-118">Sunucu çöp toplayıcıları için, değeri yığının eklendiği işlemciye karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="011cb-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="011cb-119">Çöp toplayıcısının uygulama ayrıntıları nedeniyle gerçek işlemcilerin olduğu daha fazla veya daha az atık toplama yığınlarının olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="011cb-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="011cb-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="011cb-120">Requirements</span></span>  
 <span data-ttu-id="011cb-121">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="011cb-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="011cb-122">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="011cb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="011cb-123">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="011cb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="011cb-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="011cb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="011cb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="011cb-125">See also</span></span>

- [<span data-ttu-id="011cb-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="011cb-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="011cb-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="011cb-127">Debugging</span></span>](index.md)
