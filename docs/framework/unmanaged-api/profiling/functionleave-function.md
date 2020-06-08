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
ms.openlocfilehash: 836e4843ead940bc9f76ff6bdd0433e21e400afd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500643"
---
# <a name="functionleave-function"></a><span data-ttu-id="c4294-102">FunctionLeave İşlevi</span><span class="sxs-lookup"><span data-stu-id="c4294-102">FunctionLeave Function</span></span>
<span data-ttu-id="c4294-103">Profiler öğesine bir işlevin çağırana dönmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="c4294-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4294-104">`FunctionLeave`İşlev .NET Framework 2,0 ' de kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c4294-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="c4294-105">Çalışmaya devam eder, ancak bir performans cezası olur.</span><span class="sxs-lookup"><span data-stu-id="c4294-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="c4294-106">Bunun yerine [FunctionLeave2](functionleave2-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4294-106">Use the [FunctionLeave2](functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4294-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c4294-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4294-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4294-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="c4294-109">\[içinde] döndüren işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c4294-109">\[in] The identifier of the function that is returning.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4294-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4294-110">Remarks</span></span>  
 <span data-ttu-id="c4294-111">`FunctionLeave`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4294-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="c4294-112">Uygulamanın `__declspec` ( `naked` ) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4294-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="c4294-113">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="c4294-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="c4294-114">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c4294-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="c4294-115">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4294-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c4294-116">, `FunctionLeave` Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="c4294-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="c4294-117">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="c4294-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c4294-118">Çöp toplama denendiğinde, çalışma zamanı `FunctionLeave` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="c4294-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="c4294-119">Ayrıca, `FunctionLeave` işlev yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="c4294-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4294-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4294-120">Requirements</span></span>  
 <span data-ttu-id="c4294-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4294-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4294-122">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="c4294-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c4294-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c4294-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4294-124">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="c4294-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4294-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4294-125">See also</span></span>

- [<span data-ttu-id="c4294-126">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c4294-126">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="c4294-127">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c4294-127">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="c4294-128">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c4294-128">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="c4294-129">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4294-129">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="c4294-130">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c4294-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
