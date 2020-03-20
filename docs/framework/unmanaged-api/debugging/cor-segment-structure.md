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
ms.openlocfilehash: a5c743064b8ca645cf45d02b8800c88187bf4c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179281"
---
# <a name="cor_segment-structure"></a><span data-ttu-id="e8145-102">COR_SEGMENT Yapısı</span><span class="sxs-lookup"><span data-stu-id="e8145-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="e8145-103">Yönetilen yığındaki bellek bölgesi hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e8145-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8145-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8145-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;
    CORDB_ADDRESS end;
    CorDebugGenerationTypes gen;
    ULONG heap;
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="e8145-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e8145-105">Members</span></span>  
  
|<span data-ttu-id="e8145-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e8145-106">Member</span></span>|<span data-ttu-id="e8145-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8145-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="e8145-108">Bellek bölgesinin başlangıç adresi.</span><span class="sxs-lookup"><span data-stu-id="e8145-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="e8145-109">Bellek bölgesinin bitiş adresi.</span><span class="sxs-lookup"><span data-stu-id="e8145-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="e8145-110">Bellek bölgesinin oluşumunu gösteren [bir CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="e8145-110">A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="e8145-111">Bellek bölgesinin bulunduğu yığın numarası.</span><span class="sxs-lookup"><span data-stu-id="e8145-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="e8145-112">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e8145-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8145-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8145-113">Remarks</span></span>  
 <span data-ttu-id="e8145-114">Yapı, `COR_SEGMENTS` yönetilen yığındaki bellek bölgesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e8145-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="e8145-115">`COR_SEGMENTS`nesneler [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) toplama nesnesi, [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) yöntemi çağırarak doldurulur üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="e8145-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="e8145-116">Alan, `heap` bildirilen yığına karşılık gelen işlemci numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="e8145-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="e8145-117">İş istasyonu çöp toplayıcıları için değeri her zaman sıfırdır, çünkü iş istasyonlarında yalnızca bir çöp toplama yığını vardır.</span><span class="sxs-lookup"><span data-stu-id="e8145-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="e8145-118">Sunucu çöp toplayıcıları için değeri, yığının bağlı olduğu işlemciye karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e8145-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="e8145-119">Çöp toplayıcının uygulama ayrıntıları nedeniyle gerçek işlemcilerden daha fazla veya daha az çöp toplama yığını olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e8145-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8145-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8145-120">Requirements</span></span>  
 <span data-ttu-id="e8145-121">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8145-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8145-122">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8145-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8145-123">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8145-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8145-124">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8145-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8145-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8145-125">See also</span></span>

- [<span data-ttu-id="e8145-126">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="e8145-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="e8145-127">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e8145-127">Debugging</span></span>](index.md)
