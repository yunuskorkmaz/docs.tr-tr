---
title: FunctionTailcall3WithInfo İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f1c64615dae205161583c7a79575204932cd17b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586859"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="f0465-102">FunctionTailcall3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="f0465-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="f0465-103">Yürütülmekte olan işlevin başka bir işleve bir kuyruk çağrısı gerçekleştirmek üzere olan profil oluşturucu bildirir ve geçirilebilir bir tanıtıcı sağlar [Icorprofilerınfo3::getfunctiontailcall3ınfo metodu](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) almak için yığın çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="f0465-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0465-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0465-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0465-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0465-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="f0465-106">[in] Bir kuyruk çağrısı yapmak üzere olan yürütülmekte olan işlevin tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="f0465-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="f0465-107">[in] Belirli bir yığın çerçevesi ilgili bilgileri temsil eder bir donuk tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="f0465-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="f0465-108">Bu işleyici, başarılı geri sırasında geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="f0465-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0465-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0465-109">Remarks</span></span>  
 <span data-ttu-id="f0465-110">`FunctionTailcall3WithInfo` Geri çağırma yöntemi, profil oluşturucu işlevleri olarak adlandırılır ve kullanmak profil oluşturucu sağlar bildirir [Icorprofilerınfo3::getfunctiontailcall3ınfo metodu](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) yığın çerçevesini incelemek için.</span><span class="sxs-lookup"><span data-stu-id="f0465-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="f0465-111">Yığın çerçeve bilgilere erişmek için `COR_PRF_ENABLE_FRAME_INFO` ayarlanacak bayrağı vardır.</span><span class="sxs-lookup"><span data-stu-id="f0465-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="f0465-112">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayraklarını ayarlayın ve ardından [Icorprofilerınfo3::setenterleavefunctionhooks3withınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kaydetmek için Bu işlev uygulaması.</span><span class="sxs-lookup"><span data-stu-id="f0465-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="f0465-113">`FunctionTailcall3WithInfo` Bir geri çağırma işlevidir; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0465-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="f0465-114">Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f0465-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="f0465-115">Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="f0465-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="f0465-116">Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0465-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="f0465-117">Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f0465-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="f0465-118">Uygulamasını `FunctionTailcall3WithInfo` çöp toplamanın gecikeceğini olduğundan, Engellemesi gereken değil.</span><span class="sxs-lookup"><span data-stu-id="f0465-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="f0465-119">Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0465-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="f0465-120">Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionTailcall3WithInfo` döndürür.</span><span class="sxs-lookup"><span data-stu-id="f0465-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="f0465-121">Ayrıca, Functiontailcall3withınfo işlevi gerekir değil yönetilen koda çağrı veya herhangi bir şekilde yönetilen bellek ayırma neden.</span><span class="sxs-lookup"><span data-stu-id="f0465-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0465-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0465-122">Requirements</span></span>  
 <span data-ttu-id="f0465-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0465-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0465-124">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="f0465-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f0465-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0465-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0465-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0465-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0465-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0465-127">See also</span></span>

- [<span data-ttu-id="f0465-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="f0465-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="f0465-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="f0465-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="f0465-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="f0465-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="f0465-131">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="f0465-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="f0465-132">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="f0465-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="f0465-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="f0465-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="f0465-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f0465-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="f0465-135">Setfunctionıdmapper</span><span class="sxs-lookup"><span data-stu-id="f0465-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="f0465-136">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="f0465-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="f0465-137">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f0465-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
