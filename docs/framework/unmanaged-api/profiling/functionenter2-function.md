---
description: 'Daha fazla bilgi edinin: FunctionEnter2 Işlevi'
title: FunctionEnter2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: f68aeffdd63222cd78d7dc361f09e0b4c3e5af51
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759397"
---
# <a name="functionenter2-function"></a><span data-ttu-id="1f755-103">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="1f755-103">FunctionEnter2 Function</span></span>

<span data-ttu-id="1f755-104">Profil oluşturucuyu denetimin bir işleve geçtiğini ve yığın çerçevesi ve işlev bağımsız değişkenleri hakkında bilgi sağladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="1f755-104">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="1f755-105">Bu işlev [FunctionEnter](functionenter-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="1f755-105">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f755-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f755-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f755-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f755-107">Parameters</span></span>

<span data-ttu-id="1f755-108">`funcId` 'ndaki Denetimin geçirildiği işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1f755-108">`funcId` [in] The identifier of the function to which control is passed.</span></span>

<span data-ttu-id="1f755-109">`clientData` 'ndaki Profil oluşturucunun daha önce [FunctionIDMapper](functionidmapper-function.md) işlevini kullanarak belirttiği, yeniden eşlenen işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1f755-109">`clientData` [in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
<span data-ttu-id="1f755-110">`func` 'ndaki `COR_PRF_FRAME_INFO` Yığın çerçevesi hakkındaki bilgileri gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="1f755-110">`func` [in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
<span data-ttu-id="1f755-111">Profil Oluşturucu bunu [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yönteminde yürütme motoruna geri geçirilebilecek donuk bir tanıtıcı olarak kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="1f755-111">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
<span data-ttu-id="1f755-112">`argumentInfo` 'ndaki İşlevin bağımsız değişkenlerinin belleğindeki konumları belirten [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f755-112">`argumentInfo` [in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

<span data-ttu-id="1f755-113">Bağımsız değişken bilgilerine erişebilmek için `COR_PRF_ENABLE_FUNCTION_ARGS` bayrağın ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f755-113">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="1f755-114">Profil Oluşturucu, olay bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="1f755-114">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f755-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f755-115">Remarks</span></span>  

 <span data-ttu-id="1f755-116">Ve parametrelerinin değerleri, `func` `argumentInfo` `FunctionEnter2` değerler değişeceğinden veya yok edileceği için döndüğünde geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="1f755-116">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="1f755-117">`FunctionEnter2`İşlev bir geri çağırmasıdır; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f755-117">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="1f755-118">Uygulamanın `__declspec` ( `naked` ) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f755-118">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="1f755-119">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="1f755-119">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="1f755-120">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="1f755-120">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="1f755-121">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f755-121">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="1f755-122">, `FunctionEnter2` Atık toplamayı ertelendirip, uygulamanın engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="1f755-122">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="1f755-123">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="1f755-123">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="1f755-124">Çöp toplama denendiğinde, çalışma zamanı `FunctionEnter2` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="1f755-124">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="1f755-125">Ayrıca, `FunctionEnter2` işlev yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="1f755-125">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f755-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f755-126">Requirements</span></span>  

 <span data-ttu-id="1f755-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f755-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f755-128">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="1f755-128">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1f755-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1f755-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f755-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f755-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f755-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f755-131">See also</span></span>

- [<span data-ttu-id="1f755-132">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="1f755-132">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="1f755-133">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="1f755-133">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="1f755-134">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f755-134">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="1f755-135">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1f755-135">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
