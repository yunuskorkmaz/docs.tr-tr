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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f179e3b01d6c3b34dfa765565a0fc38d0ba867c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753689"
---
# <a name="corprfgcrootflags-enumeration"></a><span data-ttu-id="13b10-102">COR_PRF_GC_ROOT_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="13b10-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="13b10-103">Bir çöp toplama kök özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="13b10-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13b10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13b10-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="13b10-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="13b10-105">Members</span></span>  
  
|<span data-ttu-id="13b10-106">Üye</span><span class="sxs-lookup"><span data-stu-id="13b10-106">Member</span></span>|<span data-ttu-id="13b10-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13b10-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="13b10-108">Kök nesnenin taşınmasını çöp toplama engeller.</span><span class="sxs-lookup"><span data-stu-id="13b10-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="13b10-109">Kök çöp toplama engellemez.</span><span class="sxs-lookup"><span data-stu-id="13b10-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="13b10-110">Kök nesnenin kendisi yerine Nesne bir alana başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="13b10-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="13b10-111">Kök çöp toplama, nesnenin başvuru sayısının belirli bir değer ise engeller.</span><span class="sxs-lookup"><span data-stu-id="13b10-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13b10-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13b10-112">Remarks</span></span>  
 <span data-ttu-id="13b10-113">`COR_PRF_GC_ROOT_FLAGS` Özel kökleri hakkında ek bilgi sağlayan bir bit maskesi olur.</span><span class="sxs-lookup"><span data-stu-id="13b10-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="13b10-114">Ancak, tüm kökleri özeldir.</span><span class="sxs-lookup"><span data-stu-id="13b10-114">However, not all roots are special.</span></span> <span data-ttu-id="13b10-115">Örneğin, bazı kökleri zayıf başvurular, sabitlenmiş veya başvuru sayılan iç işaretçiler değildir.</span><span class="sxs-lookup"><span data-stu-id="13b10-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="13b10-116">Bu tür kökleri iletmek için hiçbir bayrak vardır.</span><span class="sxs-lookup"><span data-stu-id="13b10-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="13b10-117">Bu nedenle, bu numaralandırma gibi kullandığınız yöntemleri [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) yöntemi, tüm bayraklar belirten bayrak bit maskesi için gönderme 0 kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="13b10-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13b10-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13b10-118">Requirements</span></span>  
 <span data-ttu-id="13b10-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13b10-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13b10-120">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="13b10-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13b10-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13b10-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13b10-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13b10-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13b10-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13b10-123">See also</span></span>

- [<span data-ttu-id="13b10-124">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="13b10-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
