---
title: COR_PRF_FINALIZER_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
ms.openlocfilehash: 5e718d05f033cc46fa460a81f6816a13ec32476d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428353"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="760c4-102">COR_PRF_FINALIZER_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="760c4-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="760c4-103">Bir nesne için sonlandırıcıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="760c4-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="760c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="760c4-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="760c4-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="760c4-105">Members</span></span>  
  
|<span data-ttu-id="760c4-106">Üye</span><span class="sxs-lookup"><span data-stu-id="760c4-106">Member</span></span>|<span data-ttu-id="760c4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="760c4-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="760c4-108">Sonlandırıcı kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="760c4-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="760c4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="760c4-109">Remarks</span></span>  
 <span data-ttu-id="760c4-110">`COR_PRF_FINALIZER_FLAGS` numaralandırması, bir nesnenin sonlandırıcısını anlatmak için [ICorProfilerCallback2:: Finalizeableobjectkuyruklanmış](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="760c4-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="760c4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="760c4-111">Requirements</span></span>  
 <span data-ttu-id="760c4-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="760c4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="760c4-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="760c4-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="760c4-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="760c4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="760c4-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="760c4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="760c4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="760c4-116">See also</span></span>

- [<span data-ttu-id="760c4-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="760c4-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
