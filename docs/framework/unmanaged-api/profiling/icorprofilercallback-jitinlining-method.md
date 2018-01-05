---
title: "ICorProfilerCallback::JITInlining Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITInlining
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3990fdf1bcf76592288aac35b47b15f42cf77bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="1b1ce-102">ICorProfilerCallback::JITInlining Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b1ce-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="1b1ce-103">Profil Oluşturucu tam zamanında (JIT) derleyici hakkında başka bir işlev uygun olarak bir işlev eklemek için olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1b1ce-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b1ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b1ce-104">Syntax</span></span>  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b1ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b1ce-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="1b1ce-106">[in] İşlevdeki Kimliğini `calleeId` işlevi eklenecek.</span><span class="sxs-lookup"><span data-stu-id="1b1ce-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="1b1ce-107">[in] Eklenecek işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="1b1ce-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="1b1ce-108">[out] `true` oluşmasına; eklemeye izin verecek şekilde Aksi halde, `false`.</span><span class="sxs-lookup"><span data-stu-id="1b1ce-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b1ce-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b1ce-109">Remarks</span></span>  
 <span data-ttu-id="1b1ce-110">Profil Oluşturucu ayarlayabilirsiniz `pfShouldInline` için `false` önlemek için `calleeId` içine eklenen gelen işlevi `callerId` işlevi.</span><span class="sxs-lookup"><span data-stu-id="1b1ce-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="1b1ce-111">Ayrıca, profil oluşturucu genel satır içi ekleme COR_PRF_DISABLE_INLINING değerini kullanarak devre dışı bırakabilirsiniz [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="1b1ce-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="1b1ce-112">Eklenen işlevler satır içi değil bırakarak veya girmek için olaylar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="1b1ce-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="1b1ce-113">Bu nedenle, profil oluşturucu ayarlamalısınız `pfShouldInline` için `false` doğru callgraph üretmek için.</span><span class="sxs-lookup"><span data-stu-id="1b1ce-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="1b1ce-114">Ayarı `pfShouldInline` için `false` çünkü satır içi ekleme genellikle hızını artırır ve eklenen yöntemi için ayrı JIT derleme olayları sayısını azaltan performansı etkiler.</span><span class="sxs-lookup"><span data-stu-id="1b1ce-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b1ce-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b1ce-115">Requirements</span></span>  
 <span data-ttu-id="1b1ce-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1ce-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1ce-117">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1b1ce-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b1ce-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b1ce-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b1ce-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1ce-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1ce-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b1ce-120">See Also</span></span>  
 [<span data-ttu-id="1b1ce-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b1ce-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
