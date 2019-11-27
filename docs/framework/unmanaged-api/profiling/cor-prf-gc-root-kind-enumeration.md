---
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
ms.openlocfilehash: 2fe4735b7f218e89577702cde04d8d4f4de2a971
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447361"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="cc0fd-102">COR_PRF_GC_ROOT_KIND Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cc0fd-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="cc0fd-103">[ICorProfilerCallback2:: RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) geri çağırması tarafından sunulan çöp toplama kökünün türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc0fd-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc0fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc0fd-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="cc0fd-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="cc0fd-105">Members</span></span>  
  
|<span data-ttu-id="cc0fd-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="cc0fd-106">Member</span></span>|<span data-ttu-id="cc0fd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc0fd-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="cc0fd-108">Kök, yığındaki bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="cc0fd-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="cc0fd-109">Kök, Sonlandırıcı sırasındaki bir giriştir.</span><span class="sxs-lookup"><span data-stu-id="cc0fd-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="cc0fd-110">Kök bir atık toplama tanıtıcıdır.</span><span class="sxs-lookup"><span data-stu-id="cc0fd-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="cc0fd-111">Kök türü belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="cc0fd-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc0fd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc0fd-112">Requirements</span></span>  
 <span data-ttu-id="cc0fd-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc0fd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc0fd-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cc0fd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc0fd-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cc0fd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc0fd-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc0fd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc0fd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc0fd-117">See also</span></span>

- [<span data-ttu-id="cc0fd-118">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="cc0fd-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
