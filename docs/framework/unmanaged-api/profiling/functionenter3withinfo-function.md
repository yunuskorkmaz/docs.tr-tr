---
title: FunctionEnter3WithInfo İşlevi
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16e086f54865307e116a9e522b2fbadee8502249
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105683"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="bf2c7-102">FunctionEnter3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="bf2c7-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="bf2c7-103">Denetim bir işleve geçirilen profil oluşturucu bildirir ve geçirilebilir bir tanıtıcı sağlar [Icorprofilerınfo3::getfunctionenter3ınfo metodu](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) yığın çerçeve ve işlev bağımsız değişkenlerini almak için.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf2c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf2c7-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf2c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf2c7-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="bf2c7-106">[in] Denetimin geçtiğini işlevi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="bf2c7-107">[in] Belirli bir yığın çerçevesi ilgili bilgileri temsil eder bir donuk tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="bf2c7-108">Bu işleyici, başarılı geri sırasında geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf2c7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf2c7-109">Remarks</span></span>  
 <span data-ttu-id="bf2c7-110">`FunctionEnter3WithInfo` Geri çağırma yöntemi, İşlevler olarak adlandırılır ve kullanmak, profil oluşturucunun sağlar profil oluşturucu bildirir [Icorprofilerınfo3::getfunctionenter3ınfo metodu](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) bağımsız değişken değerlerini incelemek için.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="bf2c7-111">Bağımsız değişken bilgilere erişmek için `COR_PRF_ENABLE_FUNCTION_ARGS` ayarlanacak bayrağı vardır.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="bf2c7-112">Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayraklarını ayarlayın ve ardından [Icorprofilerınfo3::setenterleavefunctionhooks3withınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kaydetmek için Bu işlev uygulaması.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="bf2c7-113">`FunctionEnter3WithInfo` Bir geri çağırma işlevidir; uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="bf2c7-114">Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="bf2c7-115">Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="bf2c7-116">Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="bf2c7-117">Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="bf2c7-118">Uygulamasını `FunctionEnter3WithInfo` çöp toplamanın gecikeceğini olduğundan, Engellemesi gereken değil.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="bf2c7-119">Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="bf2c7-120">Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionEnter3WithInfo` döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="bf2c7-121">`FunctionEnter3WithInfo` İşlevi gerekir değil yönetilen koda çağrı veya herhangi bir şekilde yönetilen bellek ayırma neden.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf2c7-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf2c7-122">Requirements</span></span>  
 <span data-ttu-id="bf2c7-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf2c7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf2c7-124">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="bf2c7-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="bf2c7-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf2c7-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf2c7-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf2c7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf2c7-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf2c7-127">See also</span></span>

- [<span data-ttu-id="bf2c7-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="bf2c7-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="bf2c7-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="bf2c7-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="bf2c7-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="bf2c7-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="bf2c7-131">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bf2c7-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
