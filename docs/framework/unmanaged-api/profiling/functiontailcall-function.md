---
title: "FunctionTailcall İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall
helpviewer_keywords: FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8bc0d72ad9c11cb36803cc606b460181b44033f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="functiontailcall-function"></a><span data-ttu-id="e91dc-102">FunctionTailcall İşlevi</span><span class="sxs-lookup"><span data-stu-id="e91dc-102">FunctionTailcall Function</span></span>
<span data-ttu-id="e91dc-103">Profil Oluşturucu şu anda yürütülen işlevi başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e91dc-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e91dc-104">`FunctionTailcall` İşlevi, .NET Framework sürüm 2.0 kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e91dc-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="e91dc-105">Çalışmaya devam edecek, ancak performans cezasına sebep olabilir.</span><span class="sxs-lookup"><span data-stu-id="e91dc-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="e91dc-106">Kullanım [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) yerine işlev.</span><span class="sxs-lookup"><span data-stu-id="e91dc-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e91dc-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e91dc-107">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e91dc-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e91dc-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="e91dc-109">[in] Bir kuyruk çağrısı yapmak için şu anda yürütülen işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e91dc-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e91dc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e91dc-110">Remarks</span></span>  
 <span data-ttu-id="e91dc-111">Kuyruk çağrısı hedef işlevinin geçerli yığın çerçevesini kullanır ve doğrudan yapılan çağrı tail işlevi çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="e91dc-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="e91dc-112">Bunun anlamı bir [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) geri çağırma bir kuyruk çağrısı hedefi için bir işlev değil verilir.</span><span class="sxs-lookup"><span data-stu-id="e91dc-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="e91dc-113">`FunctionTailcall` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e91dc-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="e91dc-114">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e91dc-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="e91dc-115">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="e91dc-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="e91dc-116">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e91dc-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="e91dc-117">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e91dc-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="e91dc-118">Uygulaması `FunctionTailcall` çöp toplama geciktirir çünkü engelleyebilir miyim değil.</span><span class="sxs-lookup"><span data-stu-id="e91dc-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="e91dc-119">Yığın bir atık toplama kolay durumda olmayabileceğinden uygulama çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e91dc-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="e91dc-120">Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionTailcall` döndürür.</span><span class="sxs-lookup"><span data-stu-id="e91dc-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="e91dc-121">Ayrıca, `FunctionTailcall` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="e91dc-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e91dc-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e91dc-122">Requirements</span></span>  
 <span data-ttu-id="e91dc-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e91dc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e91dc-124">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="e91dc-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e91dc-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e91dc-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e91dc-126">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="e91dc-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91dc-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e91dc-127">See Also</span></span>  
 [<span data-ttu-id="e91dc-128">FunctionEnter2 işlevi</span><span class="sxs-lookup"><span data-stu-id="e91dc-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="e91dc-129">FunctionLeave2 işlevi</span><span class="sxs-lookup"><span data-stu-id="e91dc-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="e91dc-130">SetEnterLeaveFunctionHooks2 yöntemi</span><span class="sxs-lookup"><span data-stu-id="e91dc-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="e91dc-131">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="e91dc-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
