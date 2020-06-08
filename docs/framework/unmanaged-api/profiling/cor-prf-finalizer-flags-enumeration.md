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
ms.openlocfilehash: b273faafd7abb86ace58bb5c24473406af3ce20e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500981"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="3e001-102">COR_PRF_FINALIZER_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3e001-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="3e001-103">Bir nesne için sonlandırıcıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="3e001-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e001-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e001-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="3e001-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3e001-105">Members</span></span>  
  
|<span data-ttu-id="3e001-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3e001-106">Member</span></span>|<span data-ttu-id="3e001-107">Description</span><span class="sxs-lookup"><span data-stu-id="3e001-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="3e001-108">Sonlandırıcı kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3e001-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e001-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e001-109">Remarks</span></span>  
 <span data-ttu-id="3e001-110">`COR_PRF_FINALIZER_FLAGS`Numaralandırma, bir nesnenin sonlandırıcısını anlatmak Için [ICorProfilerCallback2:: Finalizeableobjectkuyruklanmış](icorprofilercallback2-finalizeableobjectqueued-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e001-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e001-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e001-111">Requirements</span></span>  
 <span data-ttu-id="3e001-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e001-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e001-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3e001-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3e001-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3e001-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e001-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e001-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e001-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e001-116">See also</span></span>

- [<span data-ttu-id="3e001-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="3e001-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
