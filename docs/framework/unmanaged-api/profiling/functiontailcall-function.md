---
description: ': Function, Call Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: aeb6e7dcbf52fc57ebb7b6dca22331c27cadc186
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760034"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="d87ad-103">FunctionTailcall İşlevi</span><span class="sxs-lookup"><span data-stu-id="d87ad-103">FunctionTailcall Function</span></span>

<span data-ttu-id="d87ad-104">Profil oluşturucuyu Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="d87ad-104">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d87ad-105">`FunctionTailcall`İşlev 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d87ad-105">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d87ad-106">Çalışmaya devam eder, ancak bir performans cezası olur.</span><span class="sxs-lookup"><span data-stu-id="d87ad-106">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="d87ad-107">Bunun yerine [FunctionTailcall2](functiontailcall2-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d87ad-107">Use the [FunctionTailcall2](functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d87ad-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d87ad-108">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d87ad-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d87ad-109">Parameters</span></span>

<span data-ttu-id="d87ad-110">`funcID` 'ndaki Bir tail çağrısı yapmak üzere olan şu anda yürütülmekte olan işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d87ad-110">`funcID` [in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="d87ad-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d87ad-111">Remarks</span></span>  

 <span data-ttu-id="d87ad-112">Tail çağrısının hedef işlevi geçerli yığın çerçevesini kullanır ve doğrudan kuyruk çağrısını yapan işlevin çağıranına döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d87ad-112">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="d87ad-113">Bu, bir tail çağrısının hedefi olan bir işlev için [FunctionLeave](functionleave-function.md) geri çağrısının verilmeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d87ad-113">This means that a [FunctionLeave](functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="d87ad-114">`FunctionTailcall`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d87ad-114">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="d87ad-115">Uygulamanın `__declspec` ( `naked` ) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d87ad-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="d87ad-116">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="d87ad-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="d87ad-117">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d87ad-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="d87ad-118">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d87ad-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="d87ad-119">, `FunctionTailcall` Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="d87ad-119">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="d87ad-120">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="d87ad-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="d87ad-121">Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="d87ad-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="d87ad-122">Ayrıca, `FunctionTailcall` işlev yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="d87ad-122">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d87ad-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d87ad-123">Requirements</span></span>  

 <span data-ttu-id="d87ad-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d87ad-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d87ad-125">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="d87ad-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d87ad-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d87ad-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d87ad-127">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="d87ad-127">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d87ad-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d87ad-128">See also</span></span>

- [<span data-ttu-id="d87ad-129">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="d87ad-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="d87ad-130">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="d87ad-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="d87ad-131">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d87ad-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="d87ad-132">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d87ad-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
