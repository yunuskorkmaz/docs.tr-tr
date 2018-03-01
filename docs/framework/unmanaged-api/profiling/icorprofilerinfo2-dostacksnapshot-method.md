---
title: "ICorProfilerInfo2::DoStackSnapshot Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5548254eb160547643a874fd2e31a085ec6f3ecb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a><span data-ttu-id="f3ee7-102">ICorProfilerInfo2::DoStackSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3ee7-102">ICorProfilerInfo2::DoStackSnapshot Method</span></span>
<span data-ttu-id="f3ee7-103">Belirtilen iş parçacığı için yığında yönetilen çerçeveler anlatılmaktadır ve profil oluşturucu bir geri çağırma aracılığıyla bilgi gönderir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-103">Walks the managed frames on the stack for the specified thread, and sends information to the profiler through a callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ee7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3ee7-104">Syntax</span></span>  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3ee7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3ee7-105">Parameters</span></span>  
 `thread`  
 <span data-ttu-id="f3ee7-106">[in] Hedef iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-106">[in] The ID of the target thread.</span></span>  
  
 <span data-ttu-id="f3ee7-107">Null geçirme `thread` bir anlık görüntü geçerli iş parçacığının verir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-107">Passing null in `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="f3ee7-108">Varsa bir `ThreadID` , farklı bir iş parçacığı geçirilir, ortak dil çalışma zamanı (CLR) o iş parçacığı askıya alır, anlık görüntü gerçekleştirir ve sürdürür.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-108">If a `ThreadID` of a different thread is passed, the common language runtime (CLR) suspends that thread, performs the snapshot, and resumes.</span></span>  
  
 `callback`  
 <span data-ttu-id="f3ee7-109">[in] Uygulaması için bir işaretçi [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) profil oluşturucu her yönetilen çerçeve ve yönetilmeyen çerçeve her çalıştırma hakkında bilgi sağlamak için CLR tarafından çağrılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-109">[in] A pointer to the implementation of the [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) method, which is called by the CLR to provide the profiler with information on each managed frame and each run of unmanaged frames.</span></span>  
  
 <span data-ttu-id="f3ee7-110">`StackSnapshotCallback` Yöntemi profil oluşturucu yazıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-110">The `StackSnapshotCallback` method is implemented by the profiler writer.</span></span>  
  
 `infoFlags`  
 <span data-ttu-id="f3ee7-111">[in] Değerini [cor_prf_snapshot_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) tarafından her çerçeve için geri geçirilmesi veri miktarını belirtir numaralandırma `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-111">[in] A value of the [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) enumeration, which specifies the amount of data to be passed back for each frame by `StackSnapshotCallback`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="f3ee7-112">[in] Düz aracılığıyla geçirilir, istemci verilerini gösteren bir işaretçi `StackSnapshotCallback` geri çağırma işlevi.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-112">[in] A pointer to the client data, which is passed straight through to the `StackSnapshotCallback` callback function.</span></span>  
  
 `context`  
 <span data-ttu-id="f3ee7-113">[in] Bir işaretçi bir Win32 `CONTEXT` yığın ilerlemesi oluşturmak için kullanılan yapısı.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-113">[in] A pointer to a Win32 `CONTEXT` structure, which is used to seed the stack walk.</span></span> <span data-ttu-id="f3ee7-114">Win32 `CONTEXT` yapısı CPU yazmaçların değerleri içeren ve zaman içinde belirli bir anda CPU durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-114">The Win32 `CONTEXT` structure contains values of the CPU registers and represents the state of the CPU at a particular moment in time.</span></span>  
  
 <span data-ttu-id="f3ee7-115">Çekirdek yığının üst yönetilmeyen yardımcı kodu ise yığın ilerlemesi başlamak nereye belirlemek CLR yardımcı olur; Aksi takdirde, çekirdek göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-115">The seed helps the CLR determine where to begin the stack walk, if the top of the stack is unmanaged helper code; otherwise, the seed is ignored.</span></span> <span data-ttu-id="f3ee7-116">Çekirdek için zaman uyumsuz bir ilerlemesi sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-116">A seed must be supplied for an asynchronous walk.</span></span> <span data-ttu-id="f3ee7-117">Zaman uyumlu ilerlemesi yapıyorsanız, hiçbir çekirdek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-117">If you are doing a synchronous walk, no seed is necessary.</span></span>  
  
 <span data-ttu-id="f3ee7-118">`context` Parametredir COR_PRF_SNAPSHOT_CONTEXT bayrağı yalnızca geçildi geçerli `infoFlags` parametresi.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-118">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in the `infoFlags` parameter.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="f3ee7-119">[in] Boyutunu `CONTEXT` tarafından başvurulan yapısı `context` parametresi.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-119">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3ee7-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3ee7-120">Remarks</span></span>  
 <span data-ttu-id="f3ee7-121">İçin null geçirme `thread` bir anlık görüntü geçerli iş parçacığının verir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-121">Passing null for `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="f3ee7-122">Hedef iş parçacığı aynı anda yalnızca askıya alınırsa anlık görüntüleri diğer iş parçacıklarının alınabilir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-122">Snapshots can be taken of other threads only if the target thread is suspended at the time.</span></span>  
  
 <span data-ttu-id="f3ee7-123">Profil Oluşturucu yığının yol istediğinde, çağıran `DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-123">When the profiler wants to walk the stack, it calls `DoStackSnapshot`.</span></span> <span data-ttu-id="f3ee7-124">Bu çağrısından CLR döndürmeden önce çağrıları, `StackSnapshotCallback` birkaç kez kez her biri için çerçeve (veya yönetilmeyen çerçeveler çalışması) yığında yönetilen.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-124">Before the CLR returns from that call, it calls your `StackSnapshotCallback` several times, once for each managed frame (or run of unmanaged frames) on the stack.</span></span> <span data-ttu-id="f3ee7-125">Yönetilmeyen çerçeveler karşılaştığında, bunları kendiniz yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-125">When unmanaged frames are encountered, you must walk them yourself.</span></span>  
  
 <span data-ttu-id="f3ee7-126">Çerçeveler yığına nasıl iletilmesini tersi yığın gitti sırasıdır: (son gönderilir) ilk, ana (ilk gönderilir) kareler son yaprak.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-126">The order in which the stack is walked is the reverse of how the frames were pushed onto the stack: leaf (last-pushed) frame first, main (first-pushed) frame last.</span></span>  
  
 <span data-ttu-id="f3ee7-127">Yönetilen yığın yürütmek için profil oluşturucu programı hakkında daha fazla bilgi için bkz: [profil oluşturucu yığınının taramasını, .NET Framework 2.0: temel kavramları ve ötesine](http://go.microsoft.com/fwlink/?LinkId=73638).</span><span class="sxs-lookup"><span data-stu-id="f3ee7-127">For more information about how to program the profiler to walk managed stacks, see [Profiler Stack Walking in the .NET Framework 2.0: Basics and Beyond](http://go.microsoft.com/fwlink/?LinkId=73638).</span></span>  
  
 <span data-ttu-id="f3ee7-128">Yığın ilerlemesi, zaman uyumlu veya zaman uyumsuz, aşağıdaki bölümlerde açıklandığı gibi olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-128">A stack walk can be synchronous or asynchronous, as explained in the following sections.</span></span>  
  
## <a name="synchronous-stack-walk"></a><span data-ttu-id="f3ee7-129">Zaman uyumlu yığın ilerlemesi</span><span class="sxs-lookup"><span data-stu-id="f3ee7-129">Synchronous Stack Walk</span></span>  
 <span data-ttu-id="f3ee7-130">Zaman uyumlu yığın ilerlemesi yanıt olarak bir geri çağırma yığını geçerli iş parçacığının taramasını içerir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-130">A synchronous stack walk involves walking the stack of the current thread in response to a callback.</span></span> <span data-ttu-id="f3ee7-131">Dengeli veya askıya gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-131">It does not require seeding or suspending.</span></span>  
  
 <span data-ttu-id="f3ee7-132">Bir zaman uyumlu yaptığınız zaman, yanıt oluşturucunuz 's birini çağırma CLR olarak çağrı [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (veya [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) yöntemlerini çağırırsınız `DoStackSnapshot` yığınını yürütmek için Geçerli iş parçacığının.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-132">You make a synchronous call when, in response to the CLR calling one of your profiler's [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (or [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) methods, you call `DoStackSnapshot` to walk the stack of the current thread.</span></span> <span data-ttu-id="f3ee7-133">Yığın nasıl bir bildirim gibi göründüğünü görmek istediğinizde yararlıdır [Icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="f3ee7-133">This is useful when you want to see what the stack looks like at a notification such as [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).</span></span> <span data-ttu-id="f3ee7-134">Yalnızca çağrısı `DoStackSnapshot` içinden, `ICorProfilerCallback` null geçirerek yöntemini `context` ve `thread` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-134">You just call `DoStackSnapshot` from within your `ICorProfilerCallback` method, passing null in the `context` and `thread` parameters.</span></span>  
  
## <a name="asynchronous-stack-walk"></a><span data-ttu-id="f3ee7-135">Zaman uyumsuz yığın ilerlemesi</span><span class="sxs-lookup"><span data-stu-id="f3ee7-135">Asynchronous Stack Walk</span></span>  
 <span data-ttu-id="f3ee7-136">Zaman uyumsuz yığın ilerlemesi farklı bir iş parçacığı yığınını taramasını veya yanıt için bir geri çağırma ancak geçerli iş parçacığının yönerge işaretçisi ele geçirme tarafından değil, geçerli iş parçacığının yığınını taramasını kapsar.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-136">An asynchronous stack walk entails walking the stack of a different thread, or walking the stack of the current thread, not in response to a callback, but by hijacking the current thread's instruction pointer.</span></span> <span data-ttu-id="f3ee7-137">Zaman uyumsuz bir ilerlemesi yığının üst bir platform parçası olmayan yönetilmeyen kodu ise çekirdek çağırma (PInvoke) gerektirir veya COM çağrısı ancak CLR yardımcı kodu.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-137">An asynchronous walk requires a seed if the top of the stack is unmanaged code that is not part of a platform invoke (PInvoke) or COM call, but helper code in the CLR itself.</span></span> <span data-ttu-id="f3ee7-138">Örneğin, tam zamanında (JIT) derleme veya atık toplama yapan yardımcı kodu kodudur.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-138">For example, code that does just-in-time (JIT) compiling or garbage collection is helper code.</span></span>  
  
 <span data-ttu-id="f3ee7-139">Doğrudan hedef iş parçacığı askıya alma çekirdek almak ve kendi yığını taramasını kendiniz, üstteki bulana kadar çerçeve yönetilir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-139">You obtain a seed by directly suspending the target thread and walking its stack yourself, until you find the topmost managed frame.</span></span> <span data-ttu-id="f3ee7-140">Hedef iş parçacığı askıya sonra hedef iş parçacığının geçerli kayıt bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-140">After the target thread is suspended, get the target thread's current register context.</span></span> <span data-ttu-id="f3ee7-141">Ardından, çağırarak kayıt bağlam yönetilmeyen koda işaret edip etmediğini belirlemek [Icorprofilerınfo::getfunctionfromıp](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — döndürürse bir `FunctionID` sıfıra eşit, yönetilmeyen kod çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-141">Next, determine whether the register context points to unmanaged code by calling [ICorProfilerInfo::GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — if it returns a `FunctionID` equal to zero, the frame is unmanaged code.</span></span> <span data-ttu-id="f3ee7-142">Şimdi, ilk yönetilen çerçeve erişmek ve bu çerçeve kaydı bağlamının temel çekirdek bağlamı hesaplamak kadar yığın yol.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-142">Now, walk the stack until you reach the first managed frame, and then calculate the seed context based on the register context for that frame.</span></span>  
  
 <span data-ttu-id="f3ee7-143">Çağrı `DoStackSnapshot` zaman uyumsuz yığın ilerlemesi başlamak için çekirdek bağlamına sahip.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-143">Call `DoStackSnapshot` with your seed context to begin the asynchronous stack walk.</span></span> <span data-ttu-id="f3ee7-144">Bir çekirdek belirtmezseniz `DoStackSnapshot` yığının üst yönetilen çerçeveler atla ve sonuç olarak, bir eksik yığın ilerlemesi verecektir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-144">If you do not supply a seed, `DoStackSnapshot` might skip managed frames at the top of the stack and, consequently, will give you an incomplete stack walk.</span></span> <span data-ttu-id="f3ee7-145">Çekirdek sağlarsanız, JIT derleme ya da yerel Görüntü Oluşturucu'için (Ngen.exe) işaret etmelidir-oluşturulan kodda; Aksi takdirde, `DoStackSnapshot` CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX hata kodu döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-145">If you do supply a seed, it must point to JIT-compiled or Native Image Generator (Ngen.exe)-generated code; otherwise, `DoStackSnapshot` returns the failure code, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.</span></span>  
  
 <span data-ttu-id="f3ee7-146">Zaman uyumsuz yığını yetenekte kolayca kilitlenmeleri neden veya bu yönergelere uymanızı sürece ihlalleri, erişim:</span><span class="sxs-lookup"><span data-stu-id="f3ee7-146">Asynchronous stack walks can easily cause deadlocks or access violations, unless you follow these guidelines:</span></span>  
  
-   <span data-ttu-id="f3ee7-147">Doğrudan iş parçacıklarını askıya alma, yalnızca yönetilen kod çalıştırılmadı bir iş parçacığı başka bir iş parçacığı askıya alabilirsiniz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-147">When you directly suspend threads, remember that only a thread that has never run managed code can suspend another thread.</span></span>  
  
-   <span data-ttu-id="f3ee7-148">Her zaman engelleyin, [Icorprofilercallback::threaddestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) parçacığının yığın ilerlemesi tamamlanana kadar geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-148">Always block in your [ICorProfilerCallback::ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) callback until that thread's stack walk is complete.</span></span>  
  
-   <span data-ttu-id="f3ee7-149">Çöp toplama tetikleyebilir bir CLR işlevini oluşturucunuz çağırır kilit tutarken değil.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-149">Do not hold a lock while your profiler calls into a CLR function that can trigger a garbage collection.</span></span> <span data-ttu-id="f3ee7-150">Diğer bir deyişle, sahibi olan iş parçacığı çöp toplama tetikleyen bir arama yapabilir, kilit tutmayın.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-150">That is, do not hold a lock if the owning thread might make a call that triggers a garbage collection.</span></span>  
  
 <span data-ttu-id="f3ee7-151">Olup olmadığını da kilitlenme riski çağırmanız `DoStackSnapshot` oluşturucunuz oluşturdu ve böylece ayrı hedef iş parçacığı yığınını yol akıştan.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-151">There is also a risk of deadlock if you call `DoStackSnapshot` from a thread that your profiler has created so that you can walk the stack of a separate target thread.</span></span> <span data-ttu-id="f3ee7-152">İlk kez oluşturduğunuz iş parçacığı girer belirli `ICorProfilerInfo*` yöntemleri (de dahil olmak üzere `DoStackSnapshot`), CLR iş parçacığı başına, bu iş parçacığında CLR özel başlatma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-152">The first time the thread you created enters certain `ICorProfilerInfo*` methods (including `DoStackSnapshot`), the CLR will perform per-thread, CLR-specific initialization on that thread.</span></span> <span data-ttu-id="f3ee7-153">Oluşturucunuz yığını yol çalıştığınız hedef iş parçacığı askıya aldı ve bu hedef iş parçacığı bir kilidi bu iş parçacığı başına başlatma gerçekleştirmek için gereken kendi oldu, kilitlenme meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-153">If your profiler has suspended the target thread whose stack you are trying to walk, and if that target thread happened to own a lock necessary for performing this per-thread initialization, a deadlock will occur.</span></span> <span data-ttu-id="f3ee7-154">Bu kilitlenmeyi önlemek için bir başlangıç çağrısına olun `DoStackSnapshot` yürütmek için Profil Oluşturucu tarafından oluşturulan iş parçacığı ayrı bir hedef iş parçacığı, ancak hedef iş parçacığı ilk askıya değil.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-154">To avoid this deadlock, make an initial call into `DoStackSnapshot` from your profiler-created thread to walk a separate target thread, but do not suspend the target thread first.</span></span> <span data-ttu-id="f3ee7-155">Bu ilk çağrı başına iş parçacığı başlatma kilitlenme tamamlayabilirsiniz sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-155">This initial call ensures that the per-thread initialization can complete without deadlock.</span></span> <span data-ttu-id="f3ee7-156">Varsa `DoStackSnapshot` başarılı ve en az bir çerçeve, raporlar bu noktadan sonra herhangi bir hedef iş parçacığı ve çağrı askıya almak bu profil oluşturucu tarafından oluşturulan iş parçacığı güvenli olacaktır `DoStackSnapshot` o hedef iş parçacığı yığınını yürütmek için.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-156">If `DoStackSnapshot` succeeds and reports at least one frame, after that point, it will be safe for that profiler-created thread to suspend any target thread and call `DoStackSnapshot` to walk the stack of that target thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3ee7-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3ee7-157">Requirements</span></span>  
 <span data-ttu-id="f3ee7-158">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3ee7-158">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3ee7-159">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3ee7-159">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3ee7-160">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3ee7-160">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3ee7-161">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3ee7-161">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ee7-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3ee7-162">See Also</span></span>  
 [<span data-ttu-id="f3ee7-163">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3ee7-163">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="f3ee7-164">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3ee7-164">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
