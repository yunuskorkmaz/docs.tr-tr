---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo3:: RequestProfilerDetach yöntemi'
title: ICorProfilerInfo3::RequestProfilerDetach Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
ms.openlocfilehash: 6d37c6df823aaebe4209e45cd459a8815a39852f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687044"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a><span data-ttu-id="a5b2d-103">ICorProfilerInfo3::RequestProfilerDetach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5b2d-103">ICorProfilerInfo3::RequestProfilerDetach Method</span></span>

<span data-ttu-id="a5b2d-104">Çalışma zamanına profil oluşturucuyu ayırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-104">Instructs the runtime to detach the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5b2d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5b2d-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5b2d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5b2d-106">Parameters</span></span>  

 `dwExpectedCompletionMilliseconds`  
 <span data-ttu-id="a5b2d-107">'ndaki Ortak dil çalışma zamanının (CLR), profil oluşturucunun kaldırılması için güvenli olup olmadığını denetlemeden önce beklemesi gereken süre (milisaniye cinsinden).</span><span class="sxs-lookup"><span data-stu-id="a5b2d-107">[in] The length of time, in milliseconds, the common language runtime (CLR) should wait before checking to see whether it is safe to unload the profiler.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5b2d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a5b2d-108">Return Value</span></span>  

 <span data-ttu-id="a5b2d-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a5b2d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5b2d-110">HRESULT</span></span>|<span data-ttu-id="a5b2d-111">Description</span><span class="sxs-lookup"><span data-stu-id="a5b2d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5b2d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5b2d-112">S_OK</span></span>|<span data-ttu-id="a5b2d-113">Ayırma isteği geçerli ve ayırma yordamı artık başka bir iş parçacığında devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-113">The detach request is valid, and the detach procedure is now continuing on another thread.</span></span> <span data-ttu-id="a5b2d-114">Ayırma tam olarak tamamlandığında bir `ProfilerDetachSucceeded` olay verilir.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-114">When the detach is fully complete, a `ProfilerDetachSucceeded` event is issued.</span></span>|  
|<span data-ttu-id="a5b2d-115">E_CORPROF_E_CALLBACK3_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="a5b2d-115">E_CORPROF_E_CALLBACK3_REQUIRED</span></span>|<span data-ttu-id="a5b2d-116">Profil Oluşturucu, ayırma işlemini desteklemek için uygulanması gereken [ICorProfilerCallback3](icorprofilercallback3-interface.md) arabirimi için [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-116">The profiler failed an [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) attempt for the [ICorProfilerCallback3](icorprofilercallback3-interface.md) interface, which it must implement to support the detach operation.</span></span> <span data-ttu-id="a5b2d-117">Ayırma denenmedi.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-117">Detach was not attempted.</span></span>|  
|<span data-ttu-id="a5b2d-118">CORPROF_E_IMMUTABLE_FLAGS_SET</span><span class="sxs-lookup"><span data-stu-id="a5b2d-118">CORPROF_E_IMMUTABLE_FLAGS_SET</span></span>|<span data-ttu-id="a5b2d-119">Profil Oluşturucu başlangıçta sabit bayraklar ayarlandığı için, kesilmesi olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-119">Detachment is impossible because the profiler set immutable flags at startup.</span></span> <span data-ttu-id="a5b2d-120">Kesilmesi denenmedi; Profil Oluşturucu hala tam olarak iliştirildi.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-120">Detachment was not attempted; the profiler is still fully attached.</span></span>|  
|<span data-ttu-id="a5b2d-121">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span><span class="sxs-lookup"><span data-stu-id="a5b2d-121">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span></span>|<span data-ttu-id="a5b2d-122">Profil Oluşturucu, belgelenmiş Microsoft ara dili (MSIL) kodu veya eklenmiş kancalar tarafından kullanıldığından, bu, kesilmesi olanaksızdır `enter` / `leave` .</span><span class="sxs-lookup"><span data-stu-id="a5b2d-122">Detachment is impossible because the profiler used instrumented Microsoft intermediate language (MSIL) code, or inserted `enter`/`leave` hooks.</span></span> <span data-ttu-id="a5b2d-123">Kesilmesi denenmedi; Profil Oluşturucu hala tam olarak iliştirildi.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-123">Detachment was not attempted; the profiler is still fully attached.</span></span><br /><br /> <span data-ttu-id="a5b2d-124">**Göz önünde** Belgelenmiş MSIL, [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) yöntemi kullanılarak profil oluşturucu tarafından belirtilen koddur.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-124">**Note** Instrumented MSIL is code is code that is provided by the profiler using the [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>|  
|<span data-ttu-id="a5b2d-125">CORPROF_E_RUNTIME_UNINITIALIZED</span><span class="sxs-lookup"><span data-stu-id="a5b2d-125">CORPROF_E_RUNTIME_UNINITIALIZED</span></span>|<span data-ttu-id="a5b2d-126">Çalışma zamanı, yönetilen uygulamada henüz başlatılmadı.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-126">The runtime has not been initialized yet in the managed application.</span></span> <span data-ttu-id="a5b2d-127">(Diğer bir deyişle, çalışma zamanı tam olarak yüklenmemiştir.) Bu hata kodu, profil oluşturucu geri çağrısının [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) yöntemi içinde, bir hastame istendiğinde döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-127">(That is, the runtime has not been fully loaded.) This error code may be returned when detachment is requested inside the profiler callback's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) method.</span></span>|  
|<span data-ttu-id="a5b2d-128">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="a5b2d-128">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span></span>|<span data-ttu-id="a5b2d-129">`RequestProfilerDetach` , desteklenmeyen bir zamanda çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-129">`RequestProfilerDetach` was called at an unsupported time.</span></span> <span data-ttu-id="a5b2d-130">Bu, yöntemi yönetilen bir iş parçacığında çağrılırsa veya bir [ICorProfilerCallback](icorprofilercallback-interface.md) yöntemi içinden ya da bir atık toplamaya tolerans yamayan [ICorProfilerCallback](icorprofilercallback-interface.md) yöntemi içinden çağrıldığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-130">This occurs if the method is called on a managed thread but not from within an [ICorProfilerCallback](icorprofilercallback-interface.md) method or from within an [ICorProfilerCallback](icorprofilercallback-interface.md) method that cannot tolerate a garbage collection.</span></span> <span data-ttu-id="a5b2d-131">Daha fazla bilgi için bkz. [HRESULT corprof_e_unsupported_call_sequence](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="a5b2d-131">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5b2d-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5b2d-132">Remarks</span></span>  

 <span data-ttu-id="a5b2d-133">Ayırma yordamı sırasında, ayırma iş parçacığı (profil oluşturucuyu ayırmak için özel olarak oluşturulan iş parçacığı) zaman zaman, tüm iş parçacıklarının profil oluşturucunun kodundan çıkılmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-133">During the detach procedure, the detach thread (the thread created specifically for detaching the profiler) occasionally checks whether all threads have exited the profiler’s code.</span></span> <span data-ttu-id="a5b2d-134">Profil Oluşturucu, bu parametrenin ne kadar süreceğine ilişkin bir tahmin sağlamalıdır `dwExpectedCompletionMilliseconds` .</span><span class="sxs-lookup"><span data-stu-id="a5b2d-134">The profiler should provide an estimate of how long this should take through the `dwExpectedCompletionMilliseconds` parameter.</span></span> <span data-ttu-id="a5b2d-135">Kullanım için iyi bir değer, profil oluşturucunun verilen herhangi bir yöntem içinde harcadığı tipik süredir `ICorProfilerCallback*` . Bu değer, profil oluşturucunun harcamayı beklediği maksimum sürenin yarısından daha az olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-135">A good value to use is the typical amount of time the profiler spends inside any given `ICorProfilerCallback*` method; this value should not be less than half of the maximum amount of time the profiler expects to spend.</span></span>  
  
 <span data-ttu-id="a5b2d-136">Ayırma iş parçacığı, `dwExpectedCompletionMilliseconds` Profil Oluşturucu geri çağırma kodunun tüm yığınların yapılıp yapılmayacağını denetlemeden önce ne kadar uyku moduna geçmeye karar vermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-136">The detach thread uses `dwExpectedCompletionMilliseconds` to decide how long to sleep before checking whether profiler callback code has been popped off all stacks.</span></span> <span data-ttu-id="a5b2d-137">Aşağıdaki algoritmanın ayrıntıları CLR 'nin gelecek sürümlerinde değişebilir, ancak `dwExpectedCompletionMilliseconds` profil oluşturucunun kaldırılması ne zaman güvenli olduğunun belirlenmesi sırasında bir yol gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-137">Although the details of the following algorithm may change in future releases of the CLR, it illustrates one way `dwExpectedCompletionMilliseconds` can be used when determining when it is safe to unload the profiler.</span></span> <span data-ttu-id="a5b2d-138">Ayırma iş parçacığı ilk olarak milisaniye için uykuya geçer `dwExpectedCompletionMilliseconds` .</span><span class="sxs-lookup"><span data-stu-id="a5b2d-138">The detach thread first sleeps for `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="a5b2d-139">Uyandırma sonrasında, CLR, profil oluşturucu geri çağırma kodunun hala mevcut olduğunu bulur, bu kez bu kez iki kez geçen süreyi ayırın `dwExpectedCompletionMilliseconds` .</span><span class="sxs-lookup"><span data-stu-id="a5b2d-139">If, after awakening from the sleep, the CLR finds that profiler callback code is still present, the detach thread sleeps again, this time for two times `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="a5b2d-140">Bu ikinci Uykudan uyandırma sonra, ayırma iş parçacığı profil oluşturucu geri çağırma kodunun hala mevcut olduğunu belirlerse, yeniden denetlemeden önce 10 dakika boyunca uykuya geçer.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-140">If, after awakening from this second sleep, the detach thread finds that profiler callback code is still present, it sleeps for 10 minutes before checking again.</span></span> <span data-ttu-id="a5b2d-141">Ayırma iş parçacığı her 10 dakikada bir yeniden denetlemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-141">The detach thread continues to recheck every 10 minutes.</span></span>  
  
 <span data-ttu-id="a5b2d-142">Profil Oluşturucu `dwExpectedCompletionMilliseconds` 0 (sıfır) olarak belirtirse, clr varsayılan bir 5000 değeri kullanır. Bu, 5 saniye sonra, 10 saniye sonra ve sonrasında 10 dakikada bir denetim gerçekleştirecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-142">If the profiler specifies `dwExpectedCompletionMilliseconds` as 0 (zero), the CLR uses a default value of 5000, which means that it will perform a check after 5 seconds, again after 10 seconds, and then every 10 minutes thereafter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5b2d-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5b2d-143">Requirements</span></span>  

 <span data-ttu-id="a5b2d-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5b2d-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5b2d-145">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a5b2d-145">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5b2d-146">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a5b2d-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5b2d-147">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5b2d-147">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b2d-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5b2d-148">See also</span></span>

- [<span data-ttu-id="a5b2d-149">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5b2d-149">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a5b2d-150">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a5b2d-150">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a5b2d-151">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5b2d-151">Profiling</span></span>](index.md)
