---
title: ICorProfilerCallback4::ReJITError Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: 6ea9dee6e83870d1f2e0fdccffa53f16e6f18dba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430102"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="0525e-102">ICorProfilerCallback4::ReJITError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0525e-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="0525e-103">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin yeniden derleme sürecinde bir hatayla karşılaşdığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="0525e-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0525e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0525e-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0525e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0525e-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="0525e-106">'ndaki Başarısız yeniden derleme denemesinin yapıldığı `ModuleID`.</span><span class="sxs-lookup"><span data-stu-id="0525e-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="0525e-107">'ndaki Başarısız yeniden derleme denemesinin yapıldığı yöntemin `MethodDef`.</span><span class="sxs-lookup"><span data-stu-id="0525e-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="0525e-108">'ndaki Yeniden derleme için yeniden Derlenmekte olan veya işaretlenmiş işlev örneği.</span><span class="sxs-lookup"><span data-stu-id="0525e-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="0525e-109">Bu değer, hata oluşturma temelinde hata temelinde oluştuysa (örneğin, profil oluşturucu yeniden derlenecek Yöntem için geçersiz bir meta veri belirteci belirtilmişse) `NULL` olabilir.</span><span class="sxs-lookup"><span data-stu-id="0525e-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="0525e-110">'ndaki Hatanın doğasını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0525e-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="0525e-111">Değerlerin listesi için durum HRESULTS bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0525e-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0525e-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0525e-112">Return Value</span></span>  
 <span data-ttu-id="0525e-113">Bu geri aramadan döndürülen değerler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="0525e-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="0525e-114">Durum HRESULTS</span><span class="sxs-lookup"><span data-stu-id="0525e-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="0525e-115">Durum dizisi HRESULT</span><span class="sxs-lookup"><span data-stu-id="0525e-115">Status array HRESULT</span></span>|<span data-ttu-id="0525e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0525e-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="0525e-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0525e-117">E_INVALIDARG</span></span>|<span data-ttu-id="0525e-118">`moduleID` veya `methodDef` belirteci `NULL`.</span><span class="sxs-lookup"><span data-stu-id="0525e-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="0525e-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="0525e-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="0525e-120">Modül henüz tam olarak yüklenmedi veya kaldırılıyor sürecinde.</span><span class="sxs-lookup"><span data-stu-id="0525e-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="0525e-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="0525e-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="0525e-122">Belirtilen modül dinamik olarak üretildi (örneğin, `Reflection.Emit`ile) ve bu nedenle bu yöntem tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0525e-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="0525e-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="0525e-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="0525e-124">Yöntemi toplanabilir bir derlemeye örneklenmiştir ve bu nedenle yeniden derlenmesi mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="0525e-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="0525e-125">Yansıma dışı bir bağlamda (örneğin, `List<MyCollectibleStruct>`) tanımlanan türlerin ve işlevlerin toplanabilir bir derlemede örneklenebilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0525e-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="0525e-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0525e-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0525e-127">JıT yeniden derleme için belirtilen yöntem işaretlenmeye çalışılırken CLR 'nin belleği tükendi.</span><span class="sxs-lookup"><span data-stu-id="0525e-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="0525e-128">Diğer</span><span class="sxs-lookup"><span data-stu-id="0525e-128">Other</span></span>|<span data-ttu-id="0525e-129">İşletim sistemi, CLR denetimi dışında bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="0525e-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="0525e-130">Örneğin, bir bellek sayfasının erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hatası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0525e-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0525e-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0525e-131">Requirements</span></span>  
 <span data-ttu-id="0525e-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0525e-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0525e-133">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0525e-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0525e-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0525e-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0525e-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0525e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0525e-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0525e-136">See also</span></span>

- [<span data-ttu-id="0525e-137">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0525e-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="0525e-138">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0525e-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
