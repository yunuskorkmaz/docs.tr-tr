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
ms.openlocfilehash: daca2849908a7798b588ff06f6e117d412db1b33
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867275"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="8ccdd-102">COR_PRF_FINALIZER_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8ccdd-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="8ccdd-103">Bir nesne için sonlandırıcıyı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ccdd-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ccdd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ccdd-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="8ccdd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8ccdd-105">Members</span></span>  
  
|<span data-ttu-id="8ccdd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8ccdd-106">Member</span></span>|<span data-ttu-id="8ccdd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ccdd-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="8ccdd-108">Sonlandırıcı kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8ccdd-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ccdd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ccdd-109">Remarks</span></span>  
 <span data-ttu-id="8ccdd-110">`COR_PRF_FINALIZER_FLAGS` numaralandırması, bir nesnenin sonlandırıcısını anlatmak için [ICorProfilerCallback2:: Finalizeableobjectkuyruklanmış](icorprofilercallback2-finalizeableobjectqueued-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ccdd-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ccdd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ccdd-111">Requirements</span></span>  
 <span data-ttu-id="8ccdd-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ccdd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ccdd-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8ccdd-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ccdd-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8ccdd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ccdd-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ccdd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccdd-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ccdd-116">See also</span></span>

- [<span data-ttu-id="8ccdd-117">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="8ccdd-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
