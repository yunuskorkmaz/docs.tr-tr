---
title: ICorProfilerCallback::JITCompilationStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5ba90ce4523fcc55fca3f84a78fa4cfeb6a93f0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782821"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="12df6-102">ICorProfilerCallback::JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12df6-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="12df6-103">Profil Oluşturucu, just-ın-time (JIT) derleyici bir işlevi derlemeye ne başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="12df6-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12df6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12df6-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12df6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12df6-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="12df6-106">[in] Kendisi için derleme başlatılıyor işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="12df6-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="12df6-107">[in] Profil oluşturucuya engelleme olup olmadığını belirten bir değer çalışma zamanı işleyişini etkiler.</span><span class="sxs-lookup"><span data-stu-id="12df6-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="12df6-108">Değer `true` engelleme, bu geri çağrısından; döndürmek çağıran iş parçacığını beklemek çalışma zamanı neden olabilir, aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="12df6-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="12df6-109">Değerini rağmen `true` çalışma zamanı zarar değil, profil oluşturma sonuçlarından eğriltilebilir.</span><span class="sxs-lookup"><span data-stu-id="12df6-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12df6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12df6-110">Remarks</span></span>  
 <span data-ttu-id="12df6-111">Birden fazla çiftinin almak mümkündür `JITCompilationStarted` ve [Icorprofilercallback::jıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) her işlev için şekli nedeniyle çalışma zamanı işleyen sınıf oluşturucuları çağırır.</span><span class="sxs-lookup"><span data-stu-id="12df6-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="12df6-112">Örneğin, çalışma zamanı JIT derleme yöntemine bir başlatmaz, bunun Sınıf B sınıf oluşturucusu çalıştırılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="12df6-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="12df6-113">Bu nedenle, çalışma zamanı JIT derlenir B sınıfı için oluşturucu ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="12df6-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="12df6-114">Oluşturucu çalışırken yöntemi yeniden JIT olarak derlenmiş olması için bir neden olan bir yönteme bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="12df6-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="12df6-115">Bu senaryoda, bir yöntemin ilk JIT derlemesi durdurulur.</span><span class="sxs-lookup"><span data-stu-id="12df6-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="12df6-116">Ancak, her iki JIT derleme yöntemi bir girişimi JIT derlemesi olaylarla raporlanır.</span><span class="sxs-lookup"><span data-stu-id="12df6-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="12df6-117">Profil Oluşturucu çağırarak yöntemi bir Microsoft Ara dili (MSIL) kodu yerine yayınlanıyorsa [Icorprofilerınfo::setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi, her ikisi için bunu gerekir `JITCompilationStarted` olaylar, ancak aynı MSIL bloğundan kullanabilir her ikisi için.</span><span class="sxs-lookup"><span data-stu-id="12df6-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="12df6-118">Profil oluşturucular JIT geri çağırmalar dizisi, burada iki iş parçacığı geri çağırmaları aynı anda çağırıyorsanız durumlarda desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="12df6-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="12df6-119">Örneğin, bir iş parçacığı çağrı `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="12df6-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="12df6-120">Ancak, bir dizi çağrıları önce `JITCompilationFinished`, iş parçacığı B çağrıları [Icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) A'ın iş parçacığından işlevi kimlikli `JITCompilationStarted` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="12df6-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="12df6-121">İşlev kimliği henüz geçerli gerektiğini görünebilir çünkü bir çağrı `JITCompilationFinished` henüz Profil Oluşturucu tarafından almadı.</span><span class="sxs-lookup"><span data-stu-id="12df6-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="12df6-122">Ancak, bunun gibi bir durumda, işlev kimliği geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="12df6-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12df6-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12df6-123">Requirements</span></span>  
 <span data-ttu-id="12df6-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12df6-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12df6-125">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12df6-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12df6-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12df6-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12df6-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12df6-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12df6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12df6-128">See also</span></span>

- [<span data-ttu-id="12df6-129">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12df6-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="12df6-130">JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12df6-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
