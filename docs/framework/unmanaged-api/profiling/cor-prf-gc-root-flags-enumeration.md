---
title: COR_PRF_GC_ROOT_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: bbc163c71b47e6fee0db89284d6e3fd27e882768
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500901"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a><span data-ttu-id="4158e-102">COR_PRF_GC_ROOT_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4158e-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="4158e-103">Çöp toplama kökünün bir özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4158e-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4158e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4158e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="4158e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4158e-105">Members</span></span>  
  
|<span data-ttu-id="4158e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4158e-106">Member</span></span>|<span data-ttu-id="4158e-107">Description</span><span class="sxs-lookup"><span data-stu-id="4158e-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="4158e-108">Kök bir çöp toplamanın nesneyi taşımasını engeller.</span><span class="sxs-lookup"><span data-stu-id="4158e-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="4158e-109">Kök çöp toplamayı engellemez.</span><span class="sxs-lookup"><span data-stu-id="4158e-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="4158e-110">Kök nesnenin kendisi yerine nesnesinin bir alanına başvurur.</span><span class="sxs-lookup"><span data-stu-id="4158e-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="4158e-111">Nesnenin başvuru sayısı belirli bir değer ise, kök çöp toplamayı önler.</span><span class="sxs-lookup"><span data-stu-id="4158e-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4158e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4158e-112">Remarks</span></span>  
 <span data-ttu-id="4158e-113">`COR_PRF_GC_ROOT_FLAGS`Özel köklerle ilgili ek bilgi sağlayan bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="4158e-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="4158e-114">Ancak, tüm kökler özel değildir.</span><span class="sxs-lookup"><span data-stu-id="4158e-114">However, not all roots are special.</span></span> <span data-ttu-id="4158e-115">Örneğin, bazı köklere zayıf başvurular, iç işaretçiler, sabitlenmiş veya başvuru sayılır.</span><span class="sxs-lookup"><span data-stu-id="4158e-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="4158e-116">Bu tür kökler için, iletmek üzere bayrak yoktur.</span><span class="sxs-lookup"><span data-stu-id="4158e-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="4158e-117">Bu nedenle, [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) yöntemi gibi bu numaralandırmayı kullanan Yöntemler, bayraklar bit maskesi için 0 gönderir ve tüm bayrakların kapalı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4158e-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4158e-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4158e-118">Requirements</span></span>  
 <span data-ttu-id="4158e-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4158e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4158e-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4158e-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4158e-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4158e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4158e-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4158e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4158e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4158e-123">See also</span></span>

- [<span data-ttu-id="4158e-124">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4158e-124">Profiling Enumerations</span></span>](profiling-enumerations.md)
