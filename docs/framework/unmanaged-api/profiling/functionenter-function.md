---
title: FunctionEnter İşlevi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77de59de8fcf3797237245ce42c7f0eaa96d3d24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451788"
---
# <a name="functionenter-function"></a><span data-ttu-id="3eeca-102">FunctionEnter İşlevi</span><span class="sxs-lookup"><span data-stu-id="3eeca-102">FunctionEnter Function</span></span>
<span data-ttu-id="3eeca-103">Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="3eeca-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3eeca-104">`FunctionEnter` İşlevi, .NET Framework sürüm 2.0 kullanım dışıdır ve kullanımını performans cezasına sebep olabilir.</span><span class="sxs-lookup"><span data-stu-id="3eeca-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="3eeca-105">Kullanım [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) yerine işlev.</span><span class="sxs-lookup"><span data-stu-id="3eeca-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eeca-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3eeca-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3eeca-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3eeca-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="3eeca-108">[in] Denetim geçirilen işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3eeca-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3eeca-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3eeca-109">Remarks</span></span>  
 <span data-ttu-id="3eeca-110">`FunctionEnter` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3eeca-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="3eeca-111">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3eeca-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="3eeca-112">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="3eeca-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="3eeca-113">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3eeca-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="3eeca-114">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3eeca-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3eeca-115">Uygulaması `FunctionEnter` çöp toplama geciktirir çünkü engelleyebilir miyim değil.</span><span class="sxs-lookup"><span data-stu-id="3eeca-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="3eeca-116">Yığın bir atık toplama kolay durumda olmayabileceğinden uygulama çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3eeca-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3eeca-117">Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionEnter` döndürür.</span><span class="sxs-lookup"><span data-stu-id="3eeca-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="3eeca-118">Ayrıca, `FunctionEnter` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="3eeca-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eeca-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3eeca-119">Requirements</span></span>  
 <span data-ttu-id="3eeca-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eeca-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eeca-121">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3eeca-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3eeca-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3eeca-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3eeca-123">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="3eeca-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eeca-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3eeca-124">See Also</span></span>  
 [<span data-ttu-id="3eeca-125">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="3eeca-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="3eeca-126">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="3eeca-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="3eeca-127">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="3eeca-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="3eeca-128">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3eeca-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="3eeca-129">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3eeca-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
