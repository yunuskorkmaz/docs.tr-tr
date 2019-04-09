---
title: FunctionTailcall2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06dd3b028f4f43ca8681c80a5caa4716104068dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080897"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="f1787-102">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1787-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="f1787-103">Profil Oluşturucu bildirir: yürütülmekte olan işlevin başka bir işleve bir kuyruk çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1787-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1787-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1787-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1787-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1787-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="f1787-106">[in] Bir kuyruk çağrısı yapmak üzere olan yürütülmekte olan işlevin tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="f1787-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `clientData`  
 <span data-ttu-id="f1787-107">[in] Profil Oluşturucu ile daha önce belirtilen işlevi yeniden eşlenen tanımlayıcı [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), bir kuyruk çağrısı yapmak için şu anda yürütülen işlevinin.</span><span class="sxs-lookup"><span data-stu-id="f1787-107">[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>  
  
 `func`  
 <span data-ttu-id="f1787-108">[in] A `COR_PRF_FRAME_INFO` yığın çerçevesi hakkında bilgi gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="f1787-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="f1787-109">Profil Oluşturucu bu geri yürütme altyapısı geçirilebilir donuk bir işleyici olarak düşünmelisiniz [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f1787-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1787-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1787-110">Remarks</span></span>  
 <span data-ttu-id="f1787-111">Tail çağrısı hedef işlevi, geçerli yığın çerçevesi kullanır ve doğrudan çağrı kuyruğunu yapılan işlev çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="f1787-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="f1787-112">Diğer bir deyişle bir [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) geri çağırma hedefi olan kuyruk çağrısı için bir işlev değil gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="f1787-112">This means that a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="f1787-113">Değerini `func` parametresi sonra geçerli değil `FunctionTailcall2` değeri değiştirebilir veya yok nedeniyle işlevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f1787-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="f1787-114">`FunctionTailcall2` Bir geri çağırma işlevidir; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1787-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="f1787-115">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f1787-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="f1787-116">Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="f1787-116">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="f1787-117">Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1787-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="f1787-118">Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f1787-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="f1787-119">Uygulamasını `FunctionTailcall2` çöp toplamanın gecikeceğini çünkü engellemelisiniz değil.</span><span class="sxs-lookup"><span data-stu-id="f1787-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="f1787-120">Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1787-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="f1787-121">Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionTailcall2` döndürür.</span><span class="sxs-lookup"><span data-stu-id="f1787-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="f1787-122">Ayrıca, `FunctionTailcall2` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="f1787-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1787-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1787-123">Requirements</span></span>  
 <span data-ttu-id="f1787-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1787-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1787-125">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="f1787-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f1787-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1787-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f1787-127">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f1787-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f1787-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1787-128">See also</span></span>

- [<span data-ttu-id="f1787-129">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1787-129">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="f1787-130">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1787-130">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="f1787-131">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1787-131">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="f1787-132">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f1787-132">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
