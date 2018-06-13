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
ms.openlocfilehash: 2614ad988496a22f0e6234c2f3300e22ef548308
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452448"
---
# <a name="functionleave-function"></a><span data-ttu-id="40377-102">FunctionLeave İşlevi</span><span class="sxs-lookup"><span data-stu-id="40377-102">FunctionLeave Function</span></span>
<span data-ttu-id="40377-103">Profil Oluşturucu çağırana hakkında bilgi döndürmek için bir işlevi olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="40377-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40377-104">`FunctionLeave` İşlevi, .NET Framework 2. 0 ' kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="40377-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="40377-105">Çalışmaya devam edecek, ancak performans cezasına sebep olabilir.</span><span class="sxs-lookup"><span data-stu-id="40377-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="40377-106">Kullanım [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) yerine işlev.</span><span class="sxs-lookup"><span data-stu-id="40377-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40377-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40377-107">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40377-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40377-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="40377-109">[in] Döndürüyor işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="40377-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40377-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40377-110">Remarks</span></span>  
 <span data-ttu-id="40377-111">`FunctionLeave` İşlevi bir geri çağırma; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40377-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="40377-112">Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="40377-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="40377-113">Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="40377-113">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="40377-114">Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="40377-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="40377-115">Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="40377-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="40377-116">Uygulaması `FunctionLeave` çöp toplama geciktirir çünkü engelleyebilir miyim değil.</span><span class="sxs-lookup"><span data-stu-id="40377-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="40377-117">Yığın bir atık toplama kolay durumda olmayabileceğinden uygulama çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="40377-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="40377-118">Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionLeave` döndürür.</span><span class="sxs-lookup"><span data-stu-id="40377-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="40377-119">Ayrıca, `FunctionLeave` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.</span><span class="sxs-lookup"><span data-stu-id="40377-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40377-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40377-120">Requirements</span></span>  
 <span data-ttu-id="40377-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40377-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40377-122">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="40377-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="40377-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40377-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40377-124">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="40377-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40377-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40377-125">See Also</span></span>  
 [<span data-ttu-id="40377-126">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="40377-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="40377-127">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="40377-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="40377-128">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="40377-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="40377-129">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40377-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="40377-130">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="40377-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
