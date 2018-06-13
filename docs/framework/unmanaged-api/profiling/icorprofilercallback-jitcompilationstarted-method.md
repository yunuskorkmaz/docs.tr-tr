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
ms.openlocfilehash: 1fa1081afc77c8116d8858c187401555409b4dcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453987"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="e5b38-102">ICorProfilerCallback::JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5b38-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="e5b38-103">Profil Oluşturucu tam zamanında (JIT) derleyici bir işlev derlemek başlatıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="e5b38-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b38-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5b38-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5b38-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5b38-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e5b38-106">[in] Derleme başlatılıyor işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="e5b38-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="e5b38-107">[in] Profil Oluşturucu için engelleme olup olmadığını belirten bir değer çalışma zamanının işlemi etkiler.</span><span class="sxs-lookup"><span data-stu-id="e5b38-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="e5b38-108">Değer `true` engelleme bu geri aramasından; döndürülecek çağıran iş parçacığı beklemek çalışma zamanı yaratabilir, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="e5b38-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="e5b38-109">Değerini rağmen `true` çalışma zamanı zarar değil, profil oluşturma sonuçlarını eğme.</span><span class="sxs-lookup"><span data-stu-id="e5b38-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5b38-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5b38-110">Remarks</span></span>  
 <span data-ttu-id="e5b38-111">Birden fazla Çifti almak mümkündür `JITCompilationStarted` ve [Icorprofilercallback::jıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) için her işlevi nedeniyle şekilde çalışma zamanı tanıtıcıları sınıf oluşturucuları çağırır.</span><span class="sxs-lookup"><span data-stu-id="e5b38-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="e5b38-112">Örneğin, çalışma zamanı JIT derleme yöntemi A başlatır, ancak sınıf B sınıf oluşturucusu çalıştırılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="e5b38-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="e5b38-113">Bu nedenle, çalışma zamanı JIT derlerken Sınıf B oluşturucusu ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e5b38-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="e5b38-114">Oluşturucusu çalışırken, yöntem yeniden JIT derlenmiş olması için bir neden olan bir yöntemine bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="e5b38-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="e5b38-115">Bu senaryoda, A yönteminin ilk JIT derleme durdurulur.</span><span class="sxs-lookup"><span data-stu-id="e5b38-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="e5b38-116">Ancak, her iki JIT derleme yöntemi A girişimleri JIT derleme olaylarla raporlanır.</span><span class="sxs-lookup"><span data-stu-id="e5b38-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="e5b38-117">Profil Oluşturucu çağırarak yönteminin bir Microsoft Ara dili (MSIL) kodunu değiştirmek için edecekse [Icorprofilerınfo::setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi, bunu her ikisi için bunu gerekir `JITCompilationStarted` olayları, ancak aynı MSIL blok kullanabilir her ikisi için.</span><span class="sxs-lookup"><span data-stu-id="e5b38-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="e5b38-118">Profil oluşturucular JIT geri aramalar dizisini iki iş parçacığı aynı anda yapıyor geri aramalar olduğu durumlarda desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5b38-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="e5b38-119">Örneğin, iş parçacığı A çağırır `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="e5b38-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="e5b38-120">Ancak, iş parçacığı A çağrıları önce `JITCompilationFinished`, iş parçacığı B çağrıları [Icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) iş parçacığı A'ın işlevi Kimliğinden ile `JITCompilationStarted` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="e5b38-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="e5b38-121">İşlev kimliği henüz geçerli olmamalıdır, görünebilir için yapılan bir çağrı `JITCompilationFinished` henüz Profil Oluşturucu tarafından almadı.</span><span class="sxs-lookup"><span data-stu-id="e5b38-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="e5b38-122">Ancak, bunun gibi bir durumda, işlev kimliği geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e5b38-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5b38-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5b38-123">Requirements</span></span>  
 <span data-ttu-id="e5b38-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5b38-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5b38-125">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e5b38-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5b38-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5b38-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5b38-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5b38-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b38-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5b38-128">See Also</span></span>  
 [<span data-ttu-id="e5b38-129">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5b38-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="e5b38-130">JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5b38-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
