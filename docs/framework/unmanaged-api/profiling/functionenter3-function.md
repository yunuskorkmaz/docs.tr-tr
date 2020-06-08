---
title: FunctionEnter3 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: b435e1a3504dd623421f977ffc48264f8b0dcb5a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500708"
---
# <a name="functionenter3-function"></a><span data-ttu-id="a143f-102">FunctionEnter3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="a143f-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="a143f-103">Profil oluşturucuya denetimin bir işleve geçtiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="a143f-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a143f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a143f-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a143f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a143f-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="a143f-106">\[' de] denetimin geçirildiği işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a143f-106">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a143f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a143f-107">Remarks</span></span>  
 <span data-ttu-id="a143f-108">`FunctionEnter3`Geri çağırma işlevi, profil oluşturucuyu işlevler çağrılmakta olduğunu ancak bağımsız değişken incelemesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a143f-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="a143f-109">Bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 metodunu](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a143f-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="a143f-110">`FunctionEnter3`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a143f-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="a143f-111">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a143f-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="a143f-112">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="a143f-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a143f-113">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a143f-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a143f-114">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a143f-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a143f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a143f-115">Requirements</span></span>  
 <span data-ttu-id="a143f-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a143f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a143f-117">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="a143f-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a143f-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a143f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a143f-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a143f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a143f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a143f-120">See also</span></span>

- [<span data-ttu-id="a143f-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="a143f-121">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="a143f-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="a143f-122">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="a143f-123">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="a143f-123">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="a143f-124">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="a143f-124">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="a143f-125">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="a143f-125">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a143f-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="a143f-126">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="a143f-127">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="a143f-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="a143f-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="a143f-128">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="a143f-129">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="a143f-129">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="a143f-130">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a143f-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
