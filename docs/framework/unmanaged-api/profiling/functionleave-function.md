---
title: FunctionLeave İşlevi
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b84b4b7ba96d39693abe238427983da086e62b1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634850"
---
# <a name="functionleave-function"></a><span data-ttu-id="cd648-102">FunctionLeave İşlevi</span><span class="sxs-lookup"><span data-stu-id="cd648-102">FunctionLeave Function</span></span>
<span data-ttu-id="cd648-103">Profil Oluşturucu bir işlev hakkında çağırana döndürmesi olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="cd648-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd648-104">`FunctionLeave` İşlevi, .NET Framework 2.0 sürümünde kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="cd648-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="cd648-105">Çalışmaya devam eder ancak performans cezasına sebep olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd648-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="cd648-106">Kullanım [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) işlevini.</span><span class="sxs-lookup"><span data-stu-id="cd648-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd648-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd648-107">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd648-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd648-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="cd648-109">[in] Döndüren işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="cd648-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd648-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd648-110">Remarks</span></span>  
 <span data-ttu-id="cd648-111">`FunctionLeave` Bir geri çağırma işlevidir; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd648-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="cd648-112">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cd648-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="cd648-113">Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="cd648-113">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="cd648-114">Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd648-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="cd648-115">Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="cd648-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="cd648-116">Uygulamasını `FunctionLeave` çöp toplamanın gecikeceğini çünkü engellemelisiniz değil.</span><span class="sxs-lookup"><span data-stu-id="cd648-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="cd648-117">Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd648-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="cd648-118">Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionLeave` döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd648-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="cd648-119">Ayrıca, `FunctionLeave` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="cd648-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd648-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd648-120">Requirements</span></span>  
 <span data-ttu-id="cd648-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd648-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd648-122">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="cd648-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="cd648-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd648-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd648-124">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="cd648-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd648-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd648-125">See also</span></span>
- [<span data-ttu-id="cd648-126">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="cd648-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="cd648-127">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="cd648-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="cd648-128">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="cd648-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="cd648-129">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd648-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="cd648-130">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cd648-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
