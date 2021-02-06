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
ms.openlocfilehash: cc0db68df8976ce86197cc9b7570b00c6f662cb5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648486"
---
# <a name="functionleave-function"></a><span data-ttu-id="3d3e6-103">FunctionLeave İşlevi</span><span class="sxs-lookup"><span data-stu-id="3d3e6-103">FunctionLeave Function</span></span>

<span data-ttu-id="3d3e6-104">Profiler öğesine bir işlevin çağırana dönmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-104">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d3e6-105">`FunctionLeave`İşlev .NET Framework 2,0 ' de kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-105">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="3d3e6-106">Çalışmaya devam eder, ancak bir performans cezası olur.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-106">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="3d3e6-107">Bunun yerine [FunctionLeave2](functionleave2-function.md) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-107">Use the [FunctionLeave2](functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d3e6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d3e6-108">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d3e6-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d3e6-109">Parameters</span></span>

- `funcID`

  <span data-ttu-id="3d3e6-110">\[içinde] döndüren işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-110">\[in] The identifier of the function that is returning.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d3e6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d3e6-111">Remarks</span></span>  

 <span data-ttu-id="3d3e6-112">`FunctionLeave`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-112">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="3d3e6-113">Uygulamanın `__declspec` ( `naked` ) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-113">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="3d3e6-114">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-114">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="3d3e6-115">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-115">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="3d3e6-116">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-116">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3d3e6-117">, `FunctionLeave` Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-117">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="3d3e6-118">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-118">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3d3e6-119">Çöp toplama denendiğinde, çalışma zamanı `FunctionLeave` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-119">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="3d3e6-120">Ayrıca, `FunctionLeave` işlev yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-120">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d3e6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d3e6-121">Requirements</span></span>  

 <span data-ttu-id="3d3e6-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d3e6-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d3e6-123">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="3d3e6-123">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3d3e6-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3d3e6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d3e6-125">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="3d3e6-125">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d3e6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d3e6-126">See also</span></span>

- [<span data-ttu-id="3d3e6-127">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="3d3e6-127">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="3d3e6-128">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="3d3e6-128">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="3d3e6-129">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="3d3e6-129">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="3d3e6-130">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d3e6-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="3d3e6-131">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3d3e6-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
