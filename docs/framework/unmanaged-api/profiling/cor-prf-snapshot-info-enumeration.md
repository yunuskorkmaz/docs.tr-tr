---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_SNAPSHOT_INFO numaralandırması'
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
ms.openlocfilehash: fcdaeeb6170cb9998281100c5628b3d95f9e9326
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753347"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="ab5bf-103">COR_PRF_SNAPSHOT_INFO Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ab5bf-103">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>

<span data-ttu-id="ab5bf-104">Profil oluşturucunun [StackSnapshotCallback](stacksnapshotcallback-function.md) işlevine yapılan her çağrıda bir yığın anlık görüntüsüne ne kadar veri geçirileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-104">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab5bf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ab5bf-105">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="ab5bf-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ab5bf-106">Members</span></span>  
  
|<span data-ttu-id="ab5bf-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ab5bf-107">Members</span></span>|<span data-ttu-id="ab5bf-108">Description</span><span class="sxs-lookup"><span data-stu-id="ab5bf-108">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="ab5bf-109">Parametresi dışında tüm parametrelerin değerlerinin geçirilmesi gerektiğini gösterir `StackSnapshotCallback` `context` .</span><span class="sxs-lookup"><span data-stu-id="ab5bf-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="ab5bf-110">Parametresi dahil tüm parametrelerin değerlerinin geçirilmesi gerektiğini gösterir `StackSnapshotCallback` `context` .</span><span class="sxs-lookup"><span data-stu-id="ab5bf-110">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="ab5bf-111">Daha basit, alternatif bir yığın yürüme algoritmasının kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-111">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab5bf-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab5bf-112">Remarks</span></span>  

 <span data-ttu-id="ab5bf-113">Numaralandırma tarafından verilen değerler, `COR_PRF_SNAPSHOT_INFO` [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metoduna parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-113">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab5bf-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab5bf-114">Requirements</span></span>  

 <span data-ttu-id="ab5bf-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab5bf-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab5bf-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ab5bf-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab5bf-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ab5bf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab5bf-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab5bf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5bf-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-119">See also</span></span>

- [<span data-ttu-id="ab5bf-120">DoStackSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab5bf-120">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="ab5bf-121">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="ab5bf-121">Profiling Enumerations</span></span>](profiling-enumerations.md)
