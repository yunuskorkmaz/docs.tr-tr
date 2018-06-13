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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d6713a7f54f6a6d8dbf261ad45304e6ddbe24c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450723"
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="03af4-102">COR_PRF_SNAPSHOT_INFO Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="03af4-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="03af4-103">Ne kadar veri geçirmek için Profil Oluşturucu'nın her çağrıda yığın anlık görüntüleri geri belirtir [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="03af4-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03af4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03af4-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="03af4-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="03af4-105">Members</span></span>  
  
|<span data-ttu-id="03af4-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="03af4-106">Members</span></span>|<span data-ttu-id="03af4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03af4-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="03af4-108">Değerleri tüm geçirilmelidir olduğunu gösteren `StackSnapshotCallback` parametreleri dışında `context` parametresi.</span><span class="sxs-lookup"><span data-stu-id="03af4-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="03af4-109">Değerleri tüm geçirilmelidir olduğunu gösteren `StackSnapshotCallback` dahil parametreleri `context` parametresi.</span><span class="sxs-lookup"><span data-stu-id="03af4-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="03af4-110">Bir daha basit, alternatif yığını taramasını algoritması kullanılacak gösterir.</span><span class="sxs-lookup"><span data-stu-id="03af4-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03af4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03af4-111">Remarks</span></span>  
 <span data-ttu-id="03af4-112">Tarafından sağlanan değerler `COR_PRF_SNAPSHOT_INFO` numaralandırması için parametre olarak geçirilen [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03af4-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03af4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03af4-113">Requirements</span></span>  
 <span data-ttu-id="03af4-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03af4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03af4-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="03af4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="03af4-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03af4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03af4-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03af4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03af4-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03af4-118">See Also</span></span>  
 [<span data-ttu-id="03af4-119">DoStackSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03af4-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="03af4-120">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="03af4-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
