---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: ad155c4efb9f11565eeed8bc0a3540311aca4eb7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866279"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="a0140-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0140-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="a0140-103">Önceden yerel görüntü Oluşturucu (NGen. exe) kullanılarak derlenen bir işlev için bir aramanın tamamlandığını bir profil oluşturucuya bildirir.</span><span class="sxs-lookup"><span data-stu-id="a0140-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0140-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0140-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0140-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0140-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="a0140-106">\[içinde] aramanın gerçekleştirildiği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a0140-106">\[in] The ID of the function for which the search was performed.</span></span>

- `result`

  <span data-ttu-id="a0140-107">\[in] aramanın sonucunu gösteren [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) numaralandırmanın bir değeri.</span><span class="sxs-lookup"><span data-stu-id="a0140-107">\[in] A value of the [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0140-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0140-108">Remarks</span></span>  
 <span data-ttu-id="a0140-109">.NET Framework sürüm 2,0 ' de, [ICorProfilerCallback:: JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) ve `JITCachedFunctionSearchFinished` geri çağırmaları normal Ngen görüntülerinde tüm işlevler için yapılmayacak.</span><span class="sxs-lookup"><span data-stu-id="a0140-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="a0140-110">Yalnızca bir profil Oluşturucu için en iyi duruma getirilmiş NGen görüntüleri görüntüdeki tüm işlevler için geri çağrılar oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="a0140-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="a0140-111">Bununla birlikte, ek yük nedeniyle, profil oluşturucu en iyi duruma getirilmiş NGen görüntülerini yalnızca bir işlevin tam zamanında (JıT) derlenmesi için bu geri çağırmaları kullanmayı amaçladığında istemelidir.</span><span class="sxs-lookup"><span data-stu-id="a0140-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="a0140-112">Aksi takdirde, profil oluşturucunun işlev bilgilerini toplamak için bir yavaş strateji kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0140-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0140-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0140-113">Requirements</span></span>  
 <span data-ttu-id="a0140-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0140-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0140-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a0140-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0140-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a0140-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0140-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0140-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0140-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0140-118">See also</span></span>

- [<span data-ttu-id="a0140-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0140-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
