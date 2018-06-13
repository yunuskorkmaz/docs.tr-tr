---
title: ICorProfilerInfo::ForceGC Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06601b1aa675dd9ecf023a9f83d881ba1591ac52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454479"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="0280a-102">ICorProfilerInfo::ForceGC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0280a-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="0280a-103">Ortak dil çalışma zamanı içinde (CLR) gerçekleşmesi için atık toplama zorlar.</span><span class="sxs-lookup"><span data-stu-id="0280a-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0280a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0280a-104">Syntax</span></span>  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0280a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0280a-105">Remarks</span></span>  
 <span data-ttu-id="0280a-106">`ForceGC` Yöntemi çağrılır, yönetilen kod çalıştırılmadı ve tüm profil oluşturucu geri aramalar kendi yığında yok bir iş.</span><span class="sxs-lookup"><span data-stu-id="0280a-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="0280a-107">Çağıran profil oluşturucu içinde ayrı bir iş parçacığı oluşturmak için en uygun uygulamasıdır `ForceGC` erdiği zaman.</span><span class="sxs-lookup"><span data-stu-id="0280a-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0280a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0280a-108">Requirements</span></span>  
 <span data-ttu-id="0280a-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0280a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0280a-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0280a-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0280a-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0280a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0280a-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0280a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0280a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0280a-113">See Also</span></span>  
 [<span data-ttu-id="0280a-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0280a-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
