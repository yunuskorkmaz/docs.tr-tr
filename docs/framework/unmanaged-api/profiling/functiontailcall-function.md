---
title: "FunctionTailcall İşlevi"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 223f112ba405e29b800456adca2f83e0cef6e7b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall-function"></a><span data-ttu-id="3a31c-102">FunctionTailcall İşlevi</span><span class="sxs-lookup"><span data-stu-id="3a31c-102">FunctionTailcall Function</span></span>
<span data-ttu-id="3a31c-103">Profil Oluşturucu şu anda yürütülen işlevi başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="3a31c-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a31c-104">`FunctionTailcall` İşlevi, .NET Framework sürüm 2.0 kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="3a31c-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3a31c-105">Çalışmaya devam edecek, ancak performans cezasına sebep olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a31c-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="3a31c-106">Kullanım [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) yerine işlev.</span><span class="sxs-lookup"><span data-stu-id="3a31c-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a31c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a31c-107">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a31c-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3a31c-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="3a31c-109">[in] Bir kuyruk çağrısı yapmak için şu anda yürütülen işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3a31c-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a31c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a31c-110">Remarks</span></span>  
 <span data-ttu-id="3a31c-111">Kuyruk çağrısı hedef işlevinin geçerli yığın çerçevesini kullanır ve doğrudan yapılan çağrı tail işlevi çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a31c-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="3a31c-112">Bunun anlamı bir [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) geri çağırma bir kuyruk çağrısı hedefi için bir işlev değil verilir.</span><span class="sxs-lookup"><span data-stu-id="3a31c-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="3a31c-113">`FunctionTailcall` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a31c-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="3a31c-114">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3a31c-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="3a31c-115">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="3a31c-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="3a31c-116">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a31c-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="3a31c-117">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a31c-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3a31c-118">Uygulaması `FunctionTailcall` çöp toplama geciktirir çünkü engelleyebilir miyim değil.</span><span class="sxs-lookup"><span data-stu-id="3a31c-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="3a31c-119">Yığın bir atık toplama kolay durumda olmayabileceğinden uygulama çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3a31c-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3a31c-120">Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionTailcall` döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a31c-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="3a31c-121">Ayrıca, `FunctionTailcall` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="3a31c-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a31c-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a31c-122">Requirements</span></span>  
 <span data-ttu-id="3a31c-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a31c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a31c-124">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3a31c-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3a31c-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a31c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a31c-126">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="3a31c-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a31c-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a31c-127">See Also</span></span>  
 [<span data-ttu-id="3a31c-128">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="3a31c-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="3a31c-129">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="3a31c-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="3a31c-130">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3a31c-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="3a31c-131">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3a31c-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
