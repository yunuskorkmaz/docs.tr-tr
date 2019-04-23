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
ms.openlocfilehash: fa85fb2cebb47ecbd7b0f091cb79f6ea0936b1cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177846"
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="0f8c2-102">COR_PRF_SNAPSHOT_INFO Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0f8c2-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="0f8c2-103">Ne kadar profil oluşturucunun her çağrıda bir yığın anlık görüntüsü ile geçirilecek veriler geri belirtir [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="0f8c2-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f8c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f8c2-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="0f8c2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0f8c2-105">Members</span></span>  
  
|<span data-ttu-id="0f8c2-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0f8c2-106">Members</span></span>|<span data-ttu-id="0f8c2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f8c2-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="0f8c2-108">Değerleri tüm geçirilmesi gerektiğini belirten `StackSnapshotCallback` parametreleri dışında `context` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0f8c2-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="0f8c2-109">Değerleri tüm geçirilmesi gerektiğini belirten `StackSnapshotCallback` parametreleri de dahil olmak üzere, `context` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0f8c2-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="0f8c2-110">Bir daha basit, alternatif yığın walking algoritmasının kullanılması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f8c2-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f8c2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f8c2-111">Remarks</span></span>  
 <span data-ttu-id="0f8c2-112">Tarafından sağlanan değerleri `COR_PRF_SNAPSHOT_INFO` numaralandırma için parametre olarak geçirilen [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0f8c2-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f8c2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f8c2-113">Requirements</span></span>  
 <span data-ttu-id="0f8c2-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f8c2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f8c2-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0f8c2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f8c2-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f8c2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f8c2-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f8c2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f8c2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f8c2-118">See also</span></span>

- [<span data-ttu-id="0f8c2-119">DoStackSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f8c2-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="0f8c2-120">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="0f8c2-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
