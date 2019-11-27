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
ms.openlocfilehash: 774a5d4e48f00ea8c28977f3f685dcd5a8da3199
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440581"
---
# <a name="functionleave-function"></a><span data-ttu-id="301a4-102">FunctionLeave İşlevi</span><span class="sxs-lookup"><span data-stu-id="301a4-102">FunctionLeave Function</span></span>
<span data-ttu-id="301a4-103">Profiler öğesine bir işlevin çağırana dönmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="301a4-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="301a4-104">`FunctionLeave` işlevi, .NET Framework 2,0 ' de kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="301a4-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="301a4-105">Çalışmaya devam eder, ancak bir performans cezası olur.</span><span class="sxs-lookup"><span data-stu-id="301a4-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="301a4-106">Bunun yerine [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="301a4-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="301a4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="301a4-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="301a4-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="301a4-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="301a4-109">'ndaki Döndürülen işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="301a4-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="301a4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="301a4-110">Remarks</span></span>  
 <span data-ttu-id="301a4-111">`FunctionLeave` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="301a4-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="301a4-112">Uygulamanın `__declspec`(`naked`) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="301a4-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="301a4-113">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="301a4-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="301a4-114">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="301a4-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="301a4-115">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="301a4-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="301a4-116">`FunctionLeave` uygulanması çöp toplamayı ertelendirilemediğinden engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="301a4-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="301a4-117">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="301a4-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="301a4-118">Çöp toplama denendiğinde, çalışma zamanı `FunctionLeave` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="301a4-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="301a4-119">Ayrıca, `FunctionLeave` işlevi yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="301a4-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="301a4-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="301a4-120">Requirements</span></span>  
 <span data-ttu-id="301a4-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="301a4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="301a4-122">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="301a4-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="301a4-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="301a4-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="301a4-124">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="301a4-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="301a4-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="301a4-125">See also</span></span>

- [<span data-ttu-id="301a4-126">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="301a4-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="301a4-127">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="301a4-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="301a4-128">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="301a4-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="301a4-129">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="301a4-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="301a4-130">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="301a4-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
