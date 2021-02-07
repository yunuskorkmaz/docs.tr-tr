---
description: ': ICorProfilerInfo:: ForceGC yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1abed09450b72730a11a168223b6da05e9baf9be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737551"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="14286-103">ICorProfilerInfo::ForceGC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14286-103">ICorProfilerInfo::ForceGC Method</span></span>

<span data-ttu-id="14286-104">Çöp toplamayı ortak dil çalışma zamanı (CLR) içinde gerçekleşmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="14286-104">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14286-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="14286-105">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="14286-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14286-106">Remarks</span></span>  

 <span data-ttu-id="14286-107">`ForceGC`Yöntemi yalnızca yönetilen kodu çalıştırmayan bir iş parçacığından çağrılmalıdır ve yığınında hiçbir profil oluşturucu geri çağırmaları yok.</span><span class="sxs-lookup"><span data-stu-id="14286-107">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="14286-108">En uygun uygulama, zaman Oluşturucu içinde, sinyal edildiğinde çağıran ayrı bir iş parçacığı oluşturmaktır `ForceGC` .</span><span class="sxs-lookup"><span data-stu-id="14286-108">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14286-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14286-109">Requirements</span></span>  

 <span data-ttu-id="14286-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14286-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14286-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="14286-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="14286-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="14286-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14286-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14286-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14286-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14286-114">See also</span></span>

- [<span data-ttu-id="14286-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14286-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
