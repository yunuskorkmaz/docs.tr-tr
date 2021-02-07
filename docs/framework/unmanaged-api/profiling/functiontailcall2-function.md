---
description: 'Daha fazla bilgi edinin: FunctionTailcall2 Işlevi'
title: FunctionTailcall2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: 03547537d43a76f26d6946666589f38ca4e02ec4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687434"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="218c4-103">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="218c4-103">FunctionTailcall2 Function</span></span>

<span data-ttu-id="218c4-104">Şu anda yürütülmekte olan işlevin başka bir işleve bir tail çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesi hakkında bilgi sağladığını bildiren Profiler öğesine bildirir.</span><span class="sxs-lookup"><span data-stu-id="218c4-104">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="218c4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="218c4-105">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="218c4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="218c4-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="218c4-107">\[' de] Şu anda yürütülmekte olan işlevin bir kuyruk çağrısını yapmak üzere olan tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="218c4-107">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="218c4-108">\[' de] bir kuyruk çağrısını yapmak üzere olan şu anda yürütülmekte olan işlevin [FunctionIDMapper](functionidmapper-function.md)aracılığıyla belirtilen profil oluşturucunun önceden eşlenen işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="218c4-108">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="218c4-109">\[' de] `COR_PRF_FRAME_INFO` yığın çerçevesi hakkındaki bilgileri gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="218c4-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="218c4-110">Profil Oluşturucu bunu [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yönteminde yürütme motoruna geri geçirilebilecek donuk bir tanıtıcı olarak kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="218c4-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="218c4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="218c4-111">Remarks</span></span>  

 <span data-ttu-id="218c4-112">Tail çağrısının hedef işlevi geçerli yığın çerçevesini kullanır ve doğrudan kuyruk çağrısını yapan işlevin çağıranına döndürülür.</span><span class="sxs-lookup"><span data-stu-id="218c4-112">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="218c4-113">Bu, bir kuyruk çağrısının hedefi olan bir işlev için [FunctionLeave2](functionleave2-function.md) geri çağrısının yayımlanmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="218c4-113">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="218c4-114">Parametrenin değeri, `func` `FunctionTailcall2` değer değişeceğinden veya yok edileceği için döndüğünde geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="218c4-114">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="218c4-115">`FunctionTailcall2`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="218c4-115">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="218c4-116">Uygulamanın `__declspec` ( `naked` ) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="218c4-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="218c4-117">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="218c4-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="218c4-118">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="218c4-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="218c4-119">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="218c4-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="218c4-120">, `FunctionTailcall2` Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="218c4-120">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="218c4-121">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="218c4-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="218c4-122">Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall2` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="218c4-122">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="218c4-123">Ayrıca, `FunctionTailcall2` işlev yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="218c4-123">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="218c4-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="218c4-124">Requirements</span></span>  

 <span data-ttu-id="218c4-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="218c4-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="218c4-126">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="218c4-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="218c4-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="218c4-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="218c4-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="218c4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="218c4-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="218c4-129">See also</span></span>

- [<span data-ttu-id="218c4-130">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="218c4-130">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="218c4-131">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="218c4-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="218c4-132">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="218c4-132">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="218c4-133">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="218c4-133">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
