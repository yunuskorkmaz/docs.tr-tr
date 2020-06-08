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
ms.openlocfilehash: 6168c5b27868a261871b292e17ca02b04ae89917
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500786"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="fc19c-102">COR_PRF_SNAPSHOT_INFO Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fc19c-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="fc19c-103">Profil oluşturucunun [StackSnapshotCallback](stacksnapshotcallback-function.md) işlevine yapılan her çağrıda bir yığın anlık görüntüsüne ne kadar veri geçirileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc19c-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc19c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc19c-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="fc19c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fc19c-105">Members</span></span>  
  
|<span data-ttu-id="fc19c-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fc19c-106">Members</span></span>|<span data-ttu-id="fc19c-107">Description</span><span class="sxs-lookup"><span data-stu-id="fc19c-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="fc19c-108">Parametresi dışında tüm parametrelerin değerlerinin geçirilmesi gerektiğini gösterir `StackSnapshotCallback` `context` .</span><span class="sxs-lookup"><span data-stu-id="fc19c-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="fc19c-109">Parametresi dahil tüm parametrelerin değerlerinin geçirilmesi gerektiğini gösterir `StackSnapshotCallback` `context` .</span><span class="sxs-lookup"><span data-stu-id="fc19c-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="fc19c-110">Daha basit, alternatif bir yığın yürüme algoritmasının kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc19c-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc19c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc19c-111">Remarks</span></span>  
 <span data-ttu-id="fc19c-112">Numaralandırma tarafından verilen değerler, `COR_PRF_SNAPSHOT_INFO` [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metoduna parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fc19c-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc19c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc19c-113">Requirements</span></span>  
 <span data-ttu-id="fc19c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc19c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc19c-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fc19c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc19c-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fc19c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc19c-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc19c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc19c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc19c-118">See also</span></span>

- [<span data-ttu-id="fc19c-119">DoStackSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc19c-119">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="fc19c-120">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fc19c-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
