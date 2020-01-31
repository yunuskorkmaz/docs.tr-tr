---
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
ms.openlocfilehash: 6cd35c180b8a322b3402b050c6d6840073010b1f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866989"
---
# <a name="functionenter2-function"></a><span data-ttu-id="c4d9d-102">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c4d9d-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="c4d9d-103">Profil oluşturucuyu denetimin bir işleve geçtiğini ve yığın çerçevesi ve işlev bağımsız değişkenleri hakkında bilgi sağladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="c4d9d-104">Bu işlev [FunctionEnter](functionenter-function.md) işlevinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-104">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d9d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4d9d-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4d9d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4d9d-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="c4d9d-107">\[içinde] denetimin geçirildiği işlevin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-107">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="c4d9d-108">içinde \[], profil oluşturucunun daha önce [FunctionIDMapper](functionidmapper-function.md) işlevini kullanarak belirttiği yeniden eşlenen işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-108">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="c4d9d-109">\[içinde, yığın çerçevesi hakkındaki bilgileri gösteren bir `COR_PRF_FRAME_INFO` değeri.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="c4d9d-110">Profil Oluşturucu bunu [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yönteminde yürütme motoruna geri geçirilebilecek donuk bir tanıtıcı olarak kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="c4d9d-111">\[içinde) işlevin bağımsız değişkenlerinin belleğindeki konumları belirten [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) yapısına yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="c4d9d-112">Bağımsız değişken bilgilerine erişebilmek için `COR_PRF_ENABLE_FUNCTION_ARGS` bayrağının ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="c4d9d-113">Profil Oluşturucu, olay bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4d9d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4d9d-114">Remarks</span></span>  
 <span data-ttu-id="c4d9d-115">Değerler değişeceğinden veya yok edileceği için, `FunctionEnter2` işlevi döndüğünde `func` ve `argumentInfo` parametrelerinin değerleri geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="c4d9d-116">`FunctionEnter2` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="c4d9d-117">Uygulamanın `__declspec`(`naked`) depolama sınıfı özniteliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="c4d9d-118">Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="c4d9d-119">Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="c4d9d-120">Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c4d9d-121">`FunctionEnter2` uygulanması çöp toplamayı ertelendirilemediğinden engellenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="c4d9d-122">Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c4d9d-123">Çöp toplama denendiğinde, çalışma zamanı `FunctionEnter2` dönüşene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="c4d9d-124">Ayrıca, `FunctionEnter2` işlevi yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4d9d-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4d9d-125">Requirements</span></span>  
 <span data-ttu-id="c4d9d-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4d9d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4d9d-127">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="c4d9d-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c4d9d-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c4d9d-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4d9d-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4d9d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d9d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4d9d-130">See also</span></span>

- [<span data-ttu-id="c4d9d-131">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c4d9d-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="c4d9d-132">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="c4d9d-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="c4d9d-133">SetEnterLeaveFunctionHooks2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4d9d-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="c4d9d-134">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c4d9d-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
