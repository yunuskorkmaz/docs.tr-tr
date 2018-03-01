---
title: "ICorProfilerInfo::ForceGC Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89e0e9534b5e074e5a22ceaec4e04467f752281e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="91521-102">ICorProfilerInfo::ForceGC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91521-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="91521-103">Ortak dil çalışma zamanı içinde (CLR) gerçekleşmesi için atık toplama zorlar.</span><span class="sxs-lookup"><span data-stu-id="91521-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91521-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91521-104">Syntax</span></span>  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="91521-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91521-105">Remarks</span></span>  
 <span data-ttu-id="91521-106">`ForceGC` Yöntemi çağrılır, yönetilen kod çalıştırılmadı ve tüm profil oluşturucu geri aramalar kendi yığında yok bir iş.</span><span class="sxs-lookup"><span data-stu-id="91521-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="91521-107">Çağıran profil oluşturucu içinde ayrı bir iş parçacığı oluşturmak için en uygun uygulamasıdır `ForceGC` erdiği zaman.</span><span class="sxs-lookup"><span data-stu-id="91521-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91521-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91521-108">Requirements</span></span>  
 <span data-ttu-id="91521-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91521-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91521-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91521-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91521-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91521-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91521-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91521-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91521-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91521-113">See Also</span></span>  
 [<span data-ttu-id="91521-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91521-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
