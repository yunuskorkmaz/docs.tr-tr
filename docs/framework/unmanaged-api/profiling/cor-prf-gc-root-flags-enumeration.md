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
ms.openlocfilehash: 263c22a07f363c2752afb50779515de043976e93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207714"
---
# <a name="corprfgcrootflags-enumeration"></a><span data-ttu-id="6f0d7-102">COR_PRF_GC_ROOT_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6f0d7-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="6f0d7-103">Bir çöp toplama kök özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f0d7-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f0d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f0d7-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6f0d7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6f0d7-105">Members</span></span>  
  
|<span data-ttu-id="6f0d7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6f0d7-106">Member</span></span>|<span data-ttu-id="6f0d7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f0d7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="6f0d7-108">Kök nesnenin taşınmasını çöp toplama engeller.</span><span class="sxs-lookup"><span data-stu-id="6f0d7-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="6f0d7-109">Kök çöp toplama engellemez.</span><span class="sxs-lookup"><span data-stu-id="6f0d7-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="6f0d7-110">Kök nesnenin kendisi yerine Nesne bir alana başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="6f0d7-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="6f0d7-111">Kök çöp toplama, nesnenin başvuru sayısının belirli bir değer ise engeller.</span><span class="sxs-lookup"><span data-stu-id="6f0d7-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f0d7-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f0d7-112">Remarks</span></span>  
 `COR_PRF_GC_ROOT_FLAGS` <span data-ttu-id="6f0d7-113">Özel kökleri hakkında ek bilgi sağlayan bir bit maskesi olur.</span><span class="sxs-lookup"><span data-stu-id="6f0d7-113">is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="6f0d7-114">Ancak, tüm kökleri özeldir.</span><span class="sxs-lookup"><span data-stu-id="6f0d7-114">However, not all roots are special.</span></span> <span data-ttu-id="6f0d7-115">Örneğin, bazı kökleri zayıf başvurular, sabitlenmiş veya başvuru sayılan iç işaretçiler değildir.</span><span class="sxs-lookup"><span data-stu-id="6f0d7-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="6f0d7-116">Bu tür kökleri iletmek için hiçbir bayrak vardır.</span><span class="sxs-lookup"><span data-stu-id="6f0d7-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="6f0d7-117">Bu nedenle, bu numaralandırma gibi kullandığınız yöntemleri [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) yöntemi, tüm bayraklar belirten bayrak bit maskesi için gönderme 0 kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f0d7-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f0d7-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f0d7-118">Requirements</span></span>  
 <span data-ttu-id="6f0d7-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f0d7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f0d7-120">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f0d7-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f0d7-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f0d7-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6f0d7-122">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6f0d7-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6f0d7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f0d7-123">See also</span></span>

- [<span data-ttu-id="6f0d7-124">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="6f0d7-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
