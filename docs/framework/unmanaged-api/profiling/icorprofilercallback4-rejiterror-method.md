---
title: "ICorProfilerCallback4::ReJITError Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITError
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8b1f3c5b206b2e6a108e784a206d597b69fd662
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="cdd19-102">ICorProfilerCallback4::ReJITError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdd19-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="cdd19-103">Profil Oluşturucu tam zamanında (JIT) derleyici derleme işlemindeki bir hata ile karşılaştı bildirir.</span><span class="sxs-lookup"><span data-stu-id="cdd19-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdd19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdd19-104">Syntax</span></span>  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdd19-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cdd19-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="cdd19-106">[in] `ModuleID` İçinde hangi başarısız yeniden derlenmek girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="cdd19-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="cdd19-107">[in] `MethodDef` Yönteminin başarısız yeniden derlenmek girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="cdd19-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="cdd19-108">[in] Derlenmiş veya için işaretlendi yeniden derlenmek yapılıyor işlevi örneği.</span><span class="sxs-lookup"><span data-stu-id="cdd19-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="cdd19-109">Bu değer olabilir `NULL` (örneğin, profil oluşturucu yöntemi derlenmesi için bir geçersiz meta veriler belirteci belirtilmişse) başına oluşturmada temel yerine yöntemi başına temelinde hatası durumunda.</span><span class="sxs-lookup"><span data-stu-id="cdd19-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="cdd19-110">[in] Hatanın yapısını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="cdd19-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="cdd19-111">Değerlerin listesi için durumu HRESULTS bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cdd19-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdd19-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cdd19-112">Return Value</span></span>  
 <span data-ttu-id="cdd19-113">Bu geri dönüş değerleri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="cdd19-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="cdd19-114">Durum HRESULTS</span><span class="sxs-lookup"><span data-stu-id="cdd19-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="cdd19-115">Durum dizi HRESULT</span><span class="sxs-lookup"><span data-stu-id="cdd19-115">Status array HRESULT</span></span>|<span data-ttu-id="cdd19-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cdd19-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="cdd19-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cdd19-117">E_INVALIDARG</span></span>|<span data-ttu-id="cdd19-118">`moduleID` Veya `methodDef` belirteci `NULL`.</span><span class="sxs-lookup"><span data-stu-id="cdd19-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="cdd19-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="cdd19-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="cdd19-120">Modül henüz tam olarak yüklü değil veya kaldırıldığında sürecinde olduğundan.</span><span class="sxs-lookup"><span data-stu-id="cdd19-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="cdd19-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="cdd19-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="cdd19-122">Belirtilen modül dinamik olarak oluşturulan (örneğin, `Reflection.Emit`) ve bu nedenle bu yöntem tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="cdd19-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="cdd19-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="cdd19-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="cdd19-124">Yöntemi, collectible derlemeye örneği ve bu nedenle derlenmesi mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="cdd19-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="cdd19-125">Türleri Not ve yansıma olmayan bağlamında tanımlanan işlevleri (örneğin, `List<MyCollectibleStruct>`) collectible derlemeye oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="cdd19-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="cdd19-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cdd19-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cdd19-127">CLR JIT yeniden derlenmek belirtilen yöntemini işaretlemek çalışırken yetersiz bellek tükendi.</span><span class="sxs-lookup"><span data-stu-id="cdd19-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="cdd19-128">Diğer</span><span class="sxs-lookup"><span data-stu-id="cdd19-128">Other</span></span>|<span data-ttu-id="cdd19-129">İşletim sistemi CLR denetimi dışında kalan bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="cdd19-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="cdd19-130">Örneğin, belleğin bir sayfası erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hatası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cdd19-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cdd19-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdd19-131">Requirements</span></span>  
 <span data-ttu-id="cdd19-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdd19-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdd19-133">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cdd19-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cdd19-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdd19-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdd19-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdd19-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd19-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cdd19-136">See Also</span></span>  
 [<span data-ttu-id="cdd19-137">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdd19-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="cdd19-138">Icorprofilercallback4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdd19-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
