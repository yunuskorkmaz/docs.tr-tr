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
ms.openlocfilehash: bd03eccc923049c4a49062d18bd11659f3316e8a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866829"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="72ee5-102">FunctionTailcall İşlevi</span><span class="sxs-lookup"><span data-stu-id="72ee5-102">FunctionTailcall Function</span></span>
<span data-ttu-id="72ee5-103">Profil oluşturucuyu Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="72ee5-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72ee5-104">`FunctionTailcall` işlevi, .NET Framework sürüm 2,0 ' de kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="72ee5-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="72ee5-105">Çalışmaya devam eder, ancak bir performans cezası olur.</span><span class="sxs-lookup"><span data-stu-id="72ee5-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="72ee5-106">Bunun yerine [FunctionTailcall2](functiontailcall2-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="72ee5-106">Use the [FunctionTailcall2](functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ee5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72ee5-107">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72ee5-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72ee5-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="72ee5-109">\[in] Şu anda yürütülmekte olan işlevin tanıtıcısı, kuyruk çağrısını yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72ee5-109">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="72ee5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72ee5-110">Remarks</span></span>  
 <span data-ttu-id="72ee5-111">Tail çağrısının hedef işlevi geçerli yığın çerçevesini kullanır ve doğrudan kuyruk çağrısını yapan işlevin çağıranına döndürülür.</span><span class="sxs-lookup"><span data-stu-id="72ee5-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="72ee5-112">Bu, bir tail çağrısının hedefi olan bir işlev için [FunctionLeave](functionleave-function.md) geri çağrısının verilmeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="72ee5-112">This means that a [FunctionLeave](functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="72ee5-113">`FunctionTailcall` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="72ee5-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="72ee5-114">Uygulamanın `__declspec`(`naked`) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="72ee5-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="72ee5-115">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="72ee5-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="72ee5-116">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="72ee5-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="72ee5-117">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="72ee5-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="72ee5-118">`FunctionTailcall` uygulanması çöp toplamayı ertelendirilemediğinden engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="72ee5-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="72ee5-119">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="72ee5-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="72ee5-120">Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="72ee5-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="72ee5-121">Ayrıca, `FunctionTailcall` işlevi yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="72ee5-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72ee5-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72ee5-122">Requirements</span></span>  
 <span data-ttu-id="72ee5-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72ee5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72ee5-124">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="72ee5-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="72ee5-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="72ee5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72ee5-126">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="72ee5-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ee5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72ee5-127">See also</span></span>

- [<span data-ttu-id="72ee5-128">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="72ee5-128">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="72ee5-129">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="72ee5-129">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="72ee5-130">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72ee5-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="72ee5-131">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="72ee5-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
