---
description: 'Daha fazla bilgi edinin: FunctionEnter3 Işlevi'
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
ms.openlocfilehash: 664b0ca5b40937eaa129e6843e55024802befbb7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648681"
---
# <a name="functionenter3-function"></a><span data-ttu-id="335e7-103">FunctionEnter3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="335e7-103">FunctionEnter3 Function</span></span>

<span data-ttu-id="335e7-104">Profil oluşturucuya denetimin bir işleve geçtiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="335e7-104">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="335e7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="335e7-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="335e7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="335e7-106">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="335e7-107">\[' de] denetimin geçirildiği işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="335e7-107">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="335e7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="335e7-108">Remarks</span></span>  

 <span data-ttu-id="335e7-109">`FunctionEnter3`Geri çağırma işlevi, profil oluşturucuyu işlevler çağrılmakta olduğunu ancak bağımsız değişken incelemesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="335e7-109">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="335e7-110">Bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 metodunu](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="335e7-110">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="335e7-111">`FunctionEnter3`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="335e7-111">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="335e7-112">Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="335e7-112">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="335e7-113">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="335e7-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="335e7-114">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="335e7-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="335e7-115">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="335e7-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="335e7-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="335e7-116">Requirements</span></span>  

 <span data-ttu-id="335e7-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="335e7-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="335e7-118">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="335e7-118">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="335e7-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="335e7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="335e7-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="335e7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="335e7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="335e7-121">See also</span></span>

- [<span data-ttu-id="335e7-122">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="335e7-122">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="335e7-123">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="335e7-123">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="335e7-124">Functionenter3withınfo</span><span class="sxs-lookup"><span data-stu-id="335e7-124">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="335e7-125">Functionleave3withınfo</span><span class="sxs-lookup"><span data-stu-id="335e7-125">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="335e7-126">Functiontailcall3withınfo</span><span class="sxs-lookup"><span data-stu-id="335e7-126">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="335e7-127">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="335e7-127">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="335e7-128">Setenterleavefunctionhooks3withınfo</span><span class="sxs-lookup"><span data-stu-id="335e7-128">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="335e7-129">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="335e7-129">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="335e7-130">Setfunctionıdmapper2</span><span class="sxs-lookup"><span data-stu-id="335e7-130">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="335e7-131">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="335e7-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
