---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_GC_ROOT_KIND numaralandırması'
title: COR_PRF_GC_ROOT_KIND Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: 148d48458c906974d76b9e0ec0cb6b4d15ee49ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648785"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="2a3e8-103">COR_PRF_GC_ROOT_KIND Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2a3e8-103">COR_PRF_GC_ROOT_KIND Enumeration</span></span>

<span data-ttu-id="2a3e8-104">[ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) geri çağırması tarafından sunulan çöp toplama kökünün türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a3e8-104">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a3e8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a3e8-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="2a3e8-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2a3e8-106">Members</span></span>  
  
|<span data-ttu-id="2a3e8-107">Üye</span><span class="sxs-lookup"><span data-stu-id="2a3e8-107">Member</span></span>|<span data-ttu-id="2a3e8-108">Description</span><span class="sxs-lookup"><span data-stu-id="2a3e8-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="2a3e8-109">Kök, yığındaki bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="2a3e8-109">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="2a3e8-110">Kök, Sonlandırıcı sırasındaki bir giriştir.</span><span class="sxs-lookup"><span data-stu-id="2a3e8-110">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="2a3e8-111">Kök bir atık toplama tanıtıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2a3e8-111">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="2a3e8-112">Kök türü belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="2a3e8-112">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a3e8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a3e8-113">Requirements</span></span>  

 <span data-ttu-id="2a3e8-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a3e8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a3e8-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2a3e8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a3e8-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2a3e8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a3e8-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a3e8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a3e8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a3e8-118">See also</span></span>

- [<span data-ttu-id="2a3e8-119">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="2a3e8-119">Profiling Enumerations</span></span>](profiling-enumerations.md)
