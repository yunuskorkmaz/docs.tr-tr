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
ms.openlocfilehash: a9ab8c81c995bbec41db217c904e03dd70351aee
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866890"
---
# <a name="functionleave-function"></a><span data-ttu-id="c22c7-102">FunctionLeave İşlevi</span><span class="sxs-lookup"><span data-stu-id="c22c7-102">FunctionLeave Function</span></span>
<span data-ttu-id="c22c7-103">Profiler öğesine bir işlevin çağırana dönmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="c22c7-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c22c7-104">`FunctionLeave` işlevi, .NET Framework 2,0 ' de kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c22c7-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="c22c7-105">Çalışmaya devam eder, ancak bir performans cezası olur.</span><span class="sxs-lookup"><span data-stu-id="c22c7-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="c22c7-106">Bunun yerine [FunctionLeave2](functionleave2-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c22c7-106">Use the [FunctionLeave2](functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c22c7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c22c7-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c22c7-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c22c7-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="c22c7-109">\[içinde] döndüren işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c22c7-109">\[in] The identifier of the function that is returning.</span></span>

## <a name="remarks"></a><span data-ttu-id="c22c7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c22c7-110">Remarks</span></span>  
 <span data-ttu-id="c22c7-111">`FunctionLeave` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c22c7-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="c22c7-112">Uygulamanın `__declspec`(`naked`) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c22c7-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="c22c7-113">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="c22c7-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="c22c7-114">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c22c7-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="c22c7-115">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c22c7-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c22c7-116">`FunctionLeave` uygulanması çöp toplamayı ertelendirilemediğinden engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="c22c7-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="c22c7-117">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="c22c7-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c22c7-118">Çöp toplama denendiğinde, çalışma zamanı `FunctionLeave` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="c22c7-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="c22c7-119">Ayrıca, `FunctionLeave` işlevi yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="c22c7-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c22c7-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c22c7-120">Requirements</span></span>  
 <span data-ttu-id="c22c7-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c22c7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c22c7-122">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="c22c7-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c22c7-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c22c7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c22c7-124">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="c22c7-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c22c7-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c22c7-125">See also</span></span>

- [<span data-ttu-id="c22c7-126">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c22c7-126">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="c22c7-127">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c22c7-127">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="c22c7-128">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c22c7-128">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="c22c7-129">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c22c7-129">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="c22c7-130">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c22c7-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
