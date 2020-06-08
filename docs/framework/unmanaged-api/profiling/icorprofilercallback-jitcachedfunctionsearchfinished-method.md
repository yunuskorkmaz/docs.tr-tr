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
ms.openlocfilehash: 6efc9d407bb95f75a79252b2dfad85b396d2164a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500084"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="13f62-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13f62-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="13f62-103">Önceden yerel görüntü Oluşturucu (NGen. exe) kullanılarak derlenen bir işlev için bir aramanın tamamlandığını bir profil oluşturucuya bildirir.</span><span class="sxs-lookup"><span data-stu-id="13f62-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f62-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="13f62-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13f62-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13f62-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="13f62-106">\[' de] aramanın gerçekleştirildiği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="13f62-106">\[in] The ID of the function for which the search was performed.</span></span>

- `result`

  <span data-ttu-id="13f62-107">\[içinde] aramanın sonucunu gösteren [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="13f62-107">\[in] A value of the [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>

## <a name="remarks"></a><span data-ttu-id="13f62-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13f62-108">Remarks</span></span>  
 <span data-ttu-id="13f62-109">.NET Framework sürüm 2,0 ' de, [ICorProfilerCallback:: JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) ve `JITCachedFunctionSearchFinished` geri çağrılar normal Ngen görüntülerinde tüm işlevler için yapılmayacak.</span><span class="sxs-lookup"><span data-stu-id="13f62-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="13f62-110">Yalnızca bir profil Oluşturucu için en iyi duruma getirilmiş NGen görüntüleri görüntüdeki tüm işlevler için geri çağrılar oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="13f62-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="13f62-111">Bununla birlikte, ek yük nedeniyle, profil oluşturucu en iyi duruma getirilmiş NGen görüntülerini yalnızca bir işlevin tam zamanında (JıT) derlenmesi için bu geri çağırmaları kullanmayı amaçladığında istemelidir.</span><span class="sxs-lookup"><span data-stu-id="13f62-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="13f62-112">Aksi takdirde, profil oluşturucunun işlev bilgilerini toplamak için bir yavaş strateji kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="13f62-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13f62-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13f62-113">Requirements</span></span>  
 <span data-ttu-id="13f62-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13f62-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13f62-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="13f62-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13f62-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="13f62-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13f62-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13f62-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f62-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13f62-118">See also</span></span>

- [<span data-ttu-id="13f62-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13f62-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
