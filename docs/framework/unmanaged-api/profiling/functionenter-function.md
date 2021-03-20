---
description: ': FunctionEnter Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 0f5c9f0dde405aaadf50a7da476bbae664ef8ef7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759384"
---
# <a name="functionenter-function"></a><span data-ttu-id="91733-103">FunctionEnter İşlevi</span><span class="sxs-lookup"><span data-stu-id="91733-103">FunctionEnter Function</span></span>

<span data-ttu-id="91733-104">Profil oluşturucuya denetimin bir işleve geçtiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="91733-104">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91733-105">`FunctionEnter`İşlev 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır ve kullanımı bir performans cezası olur.</span><span class="sxs-lookup"><span data-stu-id="91733-105">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="91733-106">Bunun yerine [FunctionEnter2](functionenter2-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="91733-106">Use the [FunctionEnter2](functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91733-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91733-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91733-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91733-108">Parameters</span></span>

<span data-ttu-id="91733-109">`funcID` 'ndaki Denetimin geçirildiği işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="91733-109">`funcID` [in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="91733-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91733-110">Remarks</span></span>  

 <span data-ttu-id="91733-111">`FunctionEnter`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="91733-111">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="91733-112">Uygulamanın `__declspec` ( `naked` ) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="91733-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="91733-113">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="91733-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="91733-114">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="91733-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="91733-115">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="91733-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="91733-116">, `FunctionEnter` Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="91733-116">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="91733-117">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="91733-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="91733-118">Çöp toplama denendiğinde, çalışma zamanı `FunctionEnter` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="91733-118">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="91733-119">Ayrıca, `FunctionEnter` işlev yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="91733-119">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91733-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91733-120">Requirements</span></span>  

 <span data-ttu-id="91733-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91733-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91733-122">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="91733-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="91733-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="91733-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91733-124">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="91733-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91733-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91733-125">See also</span></span>

- [<span data-ttu-id="91733-126">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="91733-126">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="91733-127">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="91733-127">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="91733-128">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="91733-128">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="91733-129">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91733-129">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="91733-130">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="91733-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
