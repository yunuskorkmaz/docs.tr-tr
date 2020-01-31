---
title: COR_PRF_SNAPSHOT_INFO Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 97bf3e69a8ea155d53479ba6f61988e56e3bd396
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867031"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="59d68-102">COR_PRF_SNAPSHOT_INFO Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59d68-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="59d68-103">Profil oluşturucunun [StackSnapshotCallback](stacksnapshotcallback-function.md) işlevine yapılan her çağrıda bir yığın anlık görüntüsüne ne kadar veri geçirileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="59d68-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d68-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59d68-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="59d68-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="59d68-105">Members</span></span>  
  
|<span data-ttu-id="59d68-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="59d68-106">Members</span></span>|<span data-ttu-id="59d68-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59d68-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="59d68-108">`context` parametresi dışında tüm `StackSnapshotCallback` parametreleri için değerlerin geçirilmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="59d68-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="59d68-109">`context` parametresi dahil olmak üzere tüm `StackSnapshotCallback` parametreleri için değerlerin geçirilmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="59d68-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="59d68-110">Daha basit, alternatif bir yığın yürüme algoritmasının kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="59d68-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59d68-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59d68-111">Remarks</span></span>  
 <span data-ttu-id="59d68-112">`COR_PRF_SNAPSHOT_INFO` numaralandırması tarafından verilen değerler, [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metoduna parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="59d68-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59d68-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59d68-113">Requirements</span></span>  
 <span data-ttu-id="59d68-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59d68-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59d68-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="59d68-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="59d68-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="59d68-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59d68-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59d68-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59d68-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59d68-118">See also</span></span>

- [<span data-ttu-id="59d68-119">DoStackSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59d68-119">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="59d68-120">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="59d68-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
