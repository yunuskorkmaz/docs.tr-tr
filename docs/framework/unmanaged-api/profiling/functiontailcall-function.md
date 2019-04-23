---
title: FunctionTailcall İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 656f2498c7dd9ba165ab6759d8ca3b26e0d7c93f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207051"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="13881-102">FunctionTailcall İşlevi</span><span class="sxs-lookup"><span data-stu-id="13881-102">FunctionTailcall Function</span></span>
<span data-ttu-id="13881-103">Profil Oluşturucu, yürütülmekte olan işlevin başka bir işleve bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="13881-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13881-104">`FunctionTailcall` İşlevi, .NET Framework 2.0 sürümünde kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="13881-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="13881-105">Çalışmaya devam eder ancak performans cezasına sebep olabilir.</span><span class="sxs-lookup"><span data-stu-id="13881-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="13881-106">Kullanım [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) işlevini.</span><span class="sxs-lookup"><span data-stu-id="13881-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13881-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13881-107">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13881-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13881-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="13881-109">[in] Bir kuyruk çağrısı yapmak üzere olan yürütülmekte olan işlevin tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="13881-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13881-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13881-110">Remarks</span></span>  
 <span data-ttu-id="13881-111">Tail çağrısı hedef işlevi, geçerli yığın çerçevesi kullanır ve doğrudan çağrı kuyruğunu yapılan işlev çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="13881-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="13881-112">Diğer bir deyişle bir [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) geri çağırma hedefi olan kuyruk çağrısı için bir işlev değil gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="13881-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="13881-113">`FunctionTailcall` Bir geri çağırma işlevidir; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="13881-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="13881-114">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="13881-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="13881-115">Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="13881-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="13881-116">Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="13881-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="13881-117">Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="13881-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="13881-118">Uygulamasını `FunctionTailcall` çöp toplamanın gecikeceğini çünkü engellemelisiniz değil.</span><span class="sxs-lookup"><span data-stu-id="13881-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="13881-119">Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="13881-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="13881-120">Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionTailcall` döndürür.</span><span class="sxs-lookup"><span data-stu-id="13881-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="13881-121">Ayrıca, `FunctionTailcall` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="13881-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13881-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13881-122">Requirements</span></span>  
 <span data-ttu-id="13881-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13881-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13881-124">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="13881-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="13881-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13881-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13881-126">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="13881-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13881-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13881-127">See also</span></span>

- [<span data-ttu-id="13881-128">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="13881-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="13881-129">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="13881-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="13881-130">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13881-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="13881-131">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="13881-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
