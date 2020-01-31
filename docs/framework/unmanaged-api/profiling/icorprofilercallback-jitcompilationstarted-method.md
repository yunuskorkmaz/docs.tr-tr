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
ms.openlocfilehash: e05cb944ea4f3a9ca718dc22c6cd726b6a516ea9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866240"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="66082-102">ICorProfilerCallback::JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66082-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="66082-103">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi derlemek için başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="66082-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66082-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66082-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66082-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66082-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="66082-106">'ndaki Derlemenin başladığı işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="66082-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="66082-107">'ndaki Profiler 'ın çalışma zamanının işlemini etkilemesinin ne olmayacağını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="66082-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="66082-108">Engelleme, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini neden olabileceğinden `true`. Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="66082-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="66082-109">`true` değeri çalışma zamanına zarar verse de, profil oluşturma sonuçlarını çarpıtmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="66082-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66082-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66082-110">Remarks</span></span>  
 <span data-ttu-id="66082-111">Çalışma zamanının sınıf oluşturucularını işleme biçimi nedeniyle her bir işlev için birden fazla `JITCompilationStarted` ve [ICorProfilerCallback:: JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) çağrısı almak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="66082-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="66082-112">Örneğin, çalışma zamanı JıT-Compile yöntemine başlar, ancak B sınıfı için sınıf oluşturucusunun çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="66082-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="66082-113">Bu nedenle, çalışma zamanı JıT-oluşturucuyu B sınıfı için derler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="66082-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="66082-114">Oluşturucu çalışırken, a yöntemine bir çağrı yapar ve bu, yönteminin JıT olarak derlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="66082-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="66082-115">Bu senaryoda, A yönteminin ilk JıT derlemesi durdurulur.</span><span class="sxs-lookup"><span data-stu-id="66082-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="66082-116">Ancak, JIT-Compile yöntemine her ikisi de JıT derleme olayları ile bildirilir.</span><span class="sxs-lookup"><span data-stu-id="66082-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="66082-117">Profil Oluşturucu, [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) metodunu çağırarak bir yöntem için Microsoft ara DILI (MSIL) kodu ' nu değiştirmek için, her iki `JITCompilationStarted` olayına de bunu yapması gerekir, ancak her ikisi için de aynı MSIL bloğunu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="66082-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="66082-118">Profil oluşturucular, iki iş parçacığının aynı anda geri çağırma yapmakta olduğu durumlarda JıT geri çağırmaları dizisini desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="66082-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="66082-119">Örneğin, iş parçacığı bir çağrı `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="66082-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="66082-120">Ancak, iş parçacığından bir çağrı `JITCompilationFinished`önce, B iş parçacığı [ICorProfilerCallback:: ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) ' i Iş parçacığı A 'nın `JITCompilationStarted` geri ÇAĞRıSıNıN işlev kimliğiyle çağırır.</span><span class="sxs-lookup"><span data-stu-id="66082-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="66082-121">Bir `JITCompilationFinished` çağrısı henüz profil oluşturucu tarafından alınmadığından, işlev KIMLIĞININ henüz geçerli olmaması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="66082-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="66082-122">Ancak, bunun gibi bir durumda, işlev KIMLIĞI geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="66082-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66082-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66082-123">Requirements</span></span>  
 <span data-ttu-id="66082-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66082-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66082-125">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="66082-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66082-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="66082-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66082-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66082-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66082-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66082-128">See also</span></span>

- [<span data-ttu-id="66082-129">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66082-129">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="66082-130">JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66082-130">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
