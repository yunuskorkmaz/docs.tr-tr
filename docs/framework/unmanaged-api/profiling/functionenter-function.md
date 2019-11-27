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
ms.openlocfilehash: ad34592223433f0bf541c390674bcf96839b6ca8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440821"
---
# <a name="functionenter-function"></a><span data-ttu-id="28e87-102">FunctionEnter İşlevi</span><span class="sxs-lookup"><span data-stu-id="28e87-102">FunctionEnter Function</span></span>
<span data-ttu-id="28e87-103">Profil oluşturucuya denetimin bir işleve geçtiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="28e87-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28e87-104">`FunctionEnter` işlevi, .NET Framework sürüm 2,0 ' de kullanımdan kaldırılmıştır ve kullanımı bir performans cezası olur.</span><span class="sxs-lookup"><span data-stu-id="28e87-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="28e87-105">Bunun yerine [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="28e87-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28e87-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28e87-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28e87-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28e87-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="28e87-108">'ndaki Denetimin geçirildiği işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="28e87-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28e87-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28e87-109">Remarks</span></span>  
 <span data-ttu-id="28e87-110">`FunctionEnter` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="28e87-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="28e87-111">Uygulamanın `__declspec`(`naked`) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="28e87-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="28e87-112">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="28e87-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="28e87-113">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="28e87-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="28e87-114">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="28e87-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="28e87-115">`FunctionEnter` uygulanması çöp toplamayı ertelendirilemediğinden engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="28e87-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="28e87-116">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="28e87-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="28e87-117">Çöp toplama denendiğinde, çalışma zamanı `FunctionEnter` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="28e87-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="28e87-118">Ayrıca, `FunctionEnter` işlevi yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="28e87-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28e87-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28e87-119">Requirements</span></span>  
 <span data-ttu-id="28e87-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28e87-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28e87-121">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="28e87-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="28e87-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="28e87-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28e87-123">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="28e87-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e87-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28e87-124">See also</span></span>

- [<span data-ttu-id="28e87-125">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="28e87-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="28e87-126">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="28e87-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="28e87-127">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="28e87-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="28e87-128">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28e87-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="28e87-129">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="28e87-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
