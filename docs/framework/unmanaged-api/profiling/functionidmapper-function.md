---
title: FunctionIDMapper İşlevi
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175180"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="4980d-102">FunctionIDMapper İşlevi</span><span class="sxs-lookup"><span data-stu-id="4980d-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="4980d-103">Profiloluşturucuya, bir işlevin verilen tanımlayıcısının [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)ve [FunctionTailcall2](functiontailcall2-function.md) aramaları'nda kullanılmak üzere alternatif bir kimlikle yeniden eşlenebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4980d-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="4980d-104">`FunctionIDMapper`ayrıca profilleyicinin bu işlev için geri arama almak isteyip istemediğini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4980d-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4980d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4980d-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4980d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4980d-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="4980d-107">\[in] Yeniden alınacak işlev tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="4980d-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="4980d-108">\[out] `true` Profiloluşturucunun , `FunctionEnter2`ve `FunctionLeave2` `FunctionTailcall2` geri arama almak istiyorsa ayarladığını bir değere işaretçi; aksi takdirde, bu `false`değeri .</span><span class="sxs-lookup"><span data-stu-id="4980d-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="4980d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4980d-109">Return Value</span></span>  
 <span data-ttu-id="4980d-110">Profil oluşturucu, yürütme altyapısının alternatif işlev tanımlayıcısı olarak kullandığı bir değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="4980d-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="4980d-111">İade değeri iade edilmedikçe `false` null `pbHookFunction`olamaz.</span><span class="sxs-lookup"><span data-stu-id="4980d-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="4980d-112">Aksi takdirde, null bir iade değeri, büyük olasılıkla işlemi durdurmak da dahil olmak üzere öngörülemeyen sonuçlar üretecektir.</span><span class="sxs-lookup"><span data-stu-id="4980d-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4980d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4980d-113">Remarks</span></span>  
 <span data-ttu-id="4980d-114">İşlev `FunctionIDMapper` bir geri aramadır.</span><span class="sxs-lookup"><span data-stu-id="4980d-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="4980d-115">Bir işlev kimliğini profilci için daha kullanışlı olan başka bir tanımlayıcıya yeniden eşlemek için profiloluşturucu tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4980d-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="4980d-116">Herhangi `FunctionIDMapper` bir işlev için kullanılacak alternatif kimliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="4980d-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="4980d-117">Yürütme motoru daha sonra bu alternatif kimlik geçirerek profilci isteği onurlandırır, geleneksel işlev kimliğine `clientData` ek olarak, `FunctionEnter2` `FunctionLeave2`geri `FunctionTailcall2` parametre profilci için , ve kanca, kanca çağrıldığı işlevi tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="4980d-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="4980d-118">`FunctionIDMapper` İşlevin uygulanmasını belirtmek için [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4980d-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="4980d-119">Yöntemi yalnızca bir kez arayabilirsiniz ve [bunu ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback'de yapmanızı öneririz. `ICorProfilerInfo::SetFunctionIDMapper`</span><span class="sxs-lookup"><span data-stu-id="4980d-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="4980d-120">Varsayılan olarak, ICorProfilerInfo kullanarak COR_PRF_MONITOR_ENTERLEAVE bayrağı ayarlar bir profilci varsayılır::SetEventMask , ve [ICorProfilerInfo üzerinden kanca ayarlar::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) veya [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `FunctionEnter2`almak gerekir `FunctionLeave2`, ve `FunctionTailcall2` her fonksiyon için geri arama. [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md)</span><span class="sxs-lookup"><span data-stu-id="4980d-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="4980d-121">Ancak, profilciler `FunctionIDMapper` seçici olarak ayarlayarak `pbHookFunction` belirli işlevler için bu `false`geri aramaları almaktan kaçınmak için uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="4980d-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="4980d-122">Profilciler, profilli bir uygulamanın birden çok iş parçacığının aynı yöntem/işlevi aynı anda aradığı durumlara toleranslı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4980d-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="4980d-123">Bu gibi durumlarda, profil oluşturucu aynı `FunctionIDMapper` `FunctionID`için birden çok geri arama alabilir.</span><span class="sxs-lookup"><span data-stu-id="4980d-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="4980d-124">Profil oluşturucu, aynı `FunctionID`ile birden çok kez çağrıldığında bu geri arama aynı değerleri döndürmek için emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4980d-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4980d-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4980d-125">Requirements</span></span>  
 <span data-ttu-id="4980d-126">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4980d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4980d-127">**Üstbilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="4980d-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4980d-128">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4980d-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4980d-129">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4980d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4980d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4980d-130">See also</span></span>

- [<span data-ttu-id="4980d-131">SetFunctionIDMapper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4980d-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="4980d-132">FunctionIDMapper2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="4980d-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="4980d-133">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="4980d-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="4980d-134">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="4980d-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="4980d-135">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="4980d-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="4980d-136">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4980d-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
