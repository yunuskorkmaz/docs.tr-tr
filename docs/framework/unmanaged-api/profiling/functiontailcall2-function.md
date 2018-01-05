---
title: "FunctionTailcall2 İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall2
helpviewer_keywords: FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9d6ccb08bc09bea2ec9e9a49333c92da8cb5695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="134ec-102">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="134ec-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="134ec-103">Profil Oluşturucu şu anda yürütülen işlevi başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere ve yığın çerçevesi hakkında bilgi sağlar bildirir.</span><span class="sxs-lookup"><span data-stu-id="134ec-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="134ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="134ec-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="134ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="134ec-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="134ec-106">[in] Bir kuyruk çağrısı yapmak için şu anda yürütülen işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="134ec-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `clientData`  
 <span data-ttu-id="134ec-107">[in] Profil oluşturucu aracılığıyla daha önce belirtilen açmayla işlevi tanımlayıcı [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), bir kuyruk çağrısı yapmak için şu anda yürütülen işlevinin.</span><span class="sxs-lookup"><span data-stu-id="134ec-107">[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>  
  
 `func`  
 <span data-ttu-id="134ec-108">[in] A `COR_PRF_FRAME_INFO` noktalarını yığın çerçevesi hakkında bilgi için değer.</span><span class="sxs-lookup"><span data-stu-id="134ec-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="134ec-109">Profil Oluşturucu uygulamasında bu yürütme altyapısında dön geçirilen bir donuk tanıtıcısı düşünmelisiniz [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="134ec-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="134ec-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="134ec-110">Remarks</span></span>  
 <span data-ttu-id="134ec-111">Kuyruk çağrısı hedef işlevinin geçerli yığın çerçevesini kullanır ve doğrudan yapılan çağrı tail işlevi çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="134ec-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="134ec-112">Bunun anlamı bir [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) geri çağırma bir kuyruk çağrısı hedefi için bir işlev değil verilir.</span><span class="sxs-lookup"><span data-stu-id="134ec-112">This means that a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="134ec-113">Değeri `func` parametresi geçerli değil sonra `FunctionTailcall2` değeri değiştirebilir veya yok edilmesi olmadığından işlevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="134ec-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="134ec-114">`FunctionTailcall2` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="134ec-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="134ec-115">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="134ec-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="134ec-116">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="134ec-116">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="134ec-117">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="134ec-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="134ec-118">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="134ec-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="134ec-119">Uygulaması `FunctionTailcall2` çöp toplama geciktirir çünkü engelleyebilir miyim değil.</span><span class="sxs-lookup"><span data-stu-id="134ec-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="134ec-120">Yığın bir atık toplama kolay durumda olmayabileceğinden uygulama çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="134ec-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="134ec-121">Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionTailcall2` döndürür.</span><span class="sxs-lookup"><span data-stu-id="134ec-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="134ec-122">Ayrıca, `FunctionTailcall2` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="134ec-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="134ec-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="134ec-123">Requirements</span></span>  
 <span data-ttu-id="134ec-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="134ec-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="134ec-125">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="134ec-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="134ec-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="134ec-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="134ec-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="134ec-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="134ec-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="134ec-128">See Also</span></span>  
 [<span data-ttu-id="134ec-129">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="134ec-129">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="134ec-130">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="134ec-130">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="134ec-131">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="134ec-131">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="134ec-132">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="134ec-132">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
