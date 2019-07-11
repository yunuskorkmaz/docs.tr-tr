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
ms.openlocfilehash: 208552dd94f587b9326280ad455ca2478ae4ac4d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780258"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="69a7a-102">ICorProfilerInfo::ForceGC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69a7a-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="69a7a-103">Ortak dil çalışma zamanı içinde (CLR) gerçekleşmesi için çöp toplama zorlar.</span><span class="sxs-lookup"><span data-stu-id="69a7a-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69a7a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69a7a-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="69a7a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69a7a-105">Remarks</span></span>  
 <span data-ttu-id="69a7a-106">`ForceGC` Yönetilen kod asla çalıştırıldı ve tüm profil oluşturucu geri aramaları, yığın üzerinde yok. bir iş parçacığından metodu çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69a7a-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="69a7a-107">Çağıran profil oluşturucu içinde ayrı bir iş parçacığı oluşturmak için en kolay uygulamadır `ForceGC` erdiği zaman.</span><span class="sxs-lookup"><span data-stu-id="69a7a-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69a7a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69a7a-108">Requirements</span></span>  
 <span data-ttu-id="69a7a-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69a7a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69a7a-110">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="69a7a-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="69a7a-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69a7a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69a7a-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69a7a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a7a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69a7a-113">See also</span></span>

- [<span data-ttu-id="69a7a-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69a7a-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
