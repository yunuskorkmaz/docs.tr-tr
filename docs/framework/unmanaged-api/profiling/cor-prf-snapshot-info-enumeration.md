---
title: "COR_PRF_SNAPSHOT_INFO Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SNAPSHOT_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SNAPSHOT_INFO
helpviewer_keywords: COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a9c854360881426f2fc7fc9e401da1dc93b9bd84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="714e6-102">COR_PRF_SNAPSHOT_INFO Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="714e6-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="714e6-103">Ne kadar veri geçirmek için Profil Oluşturucu'nın her çağrıda yığın anlık görüntüleri geri belirtir [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="714e6-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="714e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="714e6-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="714e6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="714e6-105">Members</span></span>  
  
|<span data-ttu-id="714e6-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="714e6-106">Members</span></span>|<span data-ttu-id="714e6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="714e6-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="714e6-108">Değerleri tüm geçirilmelidir olduğunu gösteren `StackSnapshotCallback` parametreleri dışında `context` parametresi.</span><span class="sxs-lookup"><span data-stu-id="714e6-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="714e6-109">Değerleri tüm geçirilmelidir olduğunu gösteren `StackSnapshotCallback` dahil parametreleri `context` parametresi.</span><span class="sxs-lookup"><span data-stu-id="714e6-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="714e6-110">Bir daha basit, alternatif yığını taramasını algoritması kullanılacak gösterir.</span><span class="sxs-lookup"><span data-stu-id="714e6-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="714e6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="714e6-111">Remarks</span></span>  
 <span data-ttu-id="714e6-112">Tarafından sağlanan değerler `COR_PRF_SNAPSHOT_INFO` numaralandırması için parametre olarak geçirilen [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="714e6-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="714e6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="714e6-113">Requirements</span></span>  
 <span data-ttu-id="714e6-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="714e6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="714e6-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="714e6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="714e6-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="714e6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="714e6-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="714e6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="714e6-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="714e6-118">See Also</span></span>  
 [<span data-ttu-id="714e6-119">DoStackSnapshot yöntemi</span><span class="sxs-lookup"><span data-stu-id="714e6-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="714e6-120">Profil oluşturma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="714e6-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
