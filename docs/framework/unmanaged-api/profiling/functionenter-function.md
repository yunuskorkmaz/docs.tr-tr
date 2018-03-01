---
title: "FunctionEnter İşlevi"
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
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0387d6d5eee1c30cb1137072e2c4600f12479e8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="functionenter-function"></a><span data-ttu-id="83f5a-102">FunctionEnter İşlevi</span><span class="sxs-lookup"><span data-stu-id="83f5a-102">FunctionEnter Function</span></span>
<span data-ttu-id="83f5a-103">Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="83f5a-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83f5a-104">`FunctionEnter` İşlevi, .NET Framework sürüm 2.0 kullanım dışıdır ve kullanımını performans cezasına sebep olabilir.</span><span class="sxs-lookup"><span data-stu-id="83f5a-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="83f5a-105">Kullanım [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) yerine işlev.</span><span class="sxs-lookup"><span data-stu-id="83f5a-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f5a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83f5a-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83f5a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83f5a-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="83f5a-108">[in] Denetim geçirilen işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="83f5a-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83f5a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83f5a-109">Remarks</span></span>  
 <span data-ttu-id="83f5a-110">`FunctionEnter` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="83f5a-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="83f5a-111">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="83f5a-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="83f5a-112">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="83f5a-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="83f5a-113">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="83f5a-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="83f5a-114">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="83f5a-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="83f5a-115">Uygulaması `FunctionEnter` çöp toplama geciktirir çünkü engelleyebilir miyim değil.</span><span class="sxs-lookup"><span data-stu-id="83f5a-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="83f5a-116">Yığın bir atık toplama kolay durumda olmayabileceğinden uygulama çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="83f5a-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="83f5a-117">Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionEnter` döndürür.</span><span class="sxs-lookup"><span data-stu-id="83f5a-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="83f5a-118">Ayrıca, `FunctionEnter` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="83f5a-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83f5a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83f5a-119">Requirements</span></span>  
 <span data-ttu-id="83f5a-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83f5a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f5a-121">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="83f5a-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="83f5a-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83f5a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83f5a-123">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="83f5a-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f5a-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83f5a-124">See Also</span></span>  
 [<span data-ttu-id="83f5a-125">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="83f5a-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="83f5a-126">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="83f5a-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="83f5a-127">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="83f5a-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="83f5a-128">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83f5a-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="83f5a-129">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="83f5a-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
