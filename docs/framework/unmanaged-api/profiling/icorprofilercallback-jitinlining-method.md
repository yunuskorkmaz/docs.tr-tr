---
title: ICorProfilerCallback::JITInlining Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60183291fda551e328ee1def03c02240314a71e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178275"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="44279-102">ICorProfilerCallback::JITInlining Yöntemi</span><span class="sxs-lookup"><span data-stu-id="44279-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="44279-103">Profil Oluşturucu, just-in-time (JIT) derleyici hakkında başka bir işlevi satır içi işlev eklemek için olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="44279-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44279-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44279-104">Syntax</span></span>  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44279-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44279-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="44279-106">[in] Hangi işlev kimliği `calleeId` işlevi eklenir.</span><span class="sxs-lookup"><span data-stu-id="44279-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="44279-107">[in] Eklenecek işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="44279-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="44279-108">[out] `true` oluşmasına; eklemeye izin verecek şekilde Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="44279-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44279-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44279-109">Remarks</span></span>  
 <span data-ttu-id="44279-110">Profil Oluşturucu ayarlayabilirsiniz `pfShouldInline` için `false` önlemek için `calleeId` içine eklenen gelen işlevi `callerId` işlevi.</span><span class="sxs-lookup"><span data-stu-id="44279-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="44279-111">Ayrıca, profil oluşturucu genel olarak satır içi ekleme COR_PRF_DISABLE_INLINING değerini kullanarak devre dışı bırakabilirsiniz [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="44279-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="44279-112">Eklenen işlevler satır içi olmayan olaylar girerek veya bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="44279-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="44279-113">Bu nedenle, profil oluşturucu ayarlamalısınız `pfShouldInline` için `false` doğru bir çağrı grafiği oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="44279-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="44279-114">Ayarı `pfShouldInline` için `false` satır içi ekleme, genellikle hızını artırır ve eklenen yöntemi için ayrı JIT derleme olay sayısını azaltır çünkü performansı etkiler.</span><span class="sxs-lookup"><span data-stu-id="44279-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44279-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44279-115">Requirements</span></span>  
 <span data-ttu-id="44279-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44279-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44279-117">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="44279-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="44279-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44279-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44279-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44279-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44279-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44279-120">See also</span></span>

- [<span data-ttu-id="44279-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44279-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
