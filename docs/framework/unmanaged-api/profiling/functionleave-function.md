---
description: ': FunctionLeave Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 619c1ecd92d2cc53512687d542becb3a2636b8af
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759501"
---
# <a name="functionleave-function"></a><span data-ttu-id="98f27-103">FunctionLeave İşlevi</span><span class="sxs-lookup"><span data-stu-id="98f27-103">FunctionLeave Function</span></span>

<span data-ttu-id="98f27-104">Profiler öğesine bir işlevin çağırana dönmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="98f27-104">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98f27-105">`FunctionLeave`İşlev .NET Framework 2,0 ' de kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="98f27-105">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="98f27-106">Çalışmaya devam eder, ancak bir performans cezası olur.</span><span class="sxs-lookup"><span data-stu-id="98f27-106">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="98f27-107">Bunun yerine [FunctionLeave2](functionleave2-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="98f27-107">Use the [FunctionLeave2](functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98f27-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98f27-108">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98f27-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98f27-109">Parameters</span></span>

<span data-ttu-id="98f27-110">`funcID` 'ndaki Döndürülen işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="98f27-110">`funcID` [in] The identifier of the function that is returning.</span></span>

## <a name="remarks"></a><span data-ttu-id="98f27-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98f27-111">Remarks</span></span>  

 <span data-ttu-id="98f27-112">`FunctionLeave`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="98f27-112">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="98f27-113">Uygulamanın `__declspec` ( `naked` ) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="98f27-113">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="98f27-114">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="98f27-114">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="98f27-115">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="98f27-115">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="98f27-116">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="98f27-116">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="98f27-117">, `FunctionLeave` Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="98f27-117">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="98f27-118">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="98f27-118">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="98f27-119">Çöp toplama denendiğinde, çalışma zamanı `FunctionLeave` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="98f27-119">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="98f27-120">Ayrıca, `FunctionLeave` işlev yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="98f27-120">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98f27-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98f27-121">Requirements</span></span>  

 <span data-ttu-id="98f27-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98f27-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98f27-123">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="98f27-123">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="98f27-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="98f27-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98f27-125">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="98f27-125">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98f27-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98f27-126">See also</span></span>

- [<span data-ttu-id="98f27-127">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="98f27-127">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="98f27-128">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="98f27-128">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="98f27-129">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="98f27-129">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="98f27-130">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98f27-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="98f27-131">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="98f27-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
