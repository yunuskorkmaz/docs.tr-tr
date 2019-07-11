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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b01f38fbcf1cb0439b82a933b37971515b06ac4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758153"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="87c7d-102">ICorProfilerCallback4::ReJITError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87c7d-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="87c7d-103">Profil Oluşturucu, just-ın-time (JIT) derleyici yeniden derleme işleminde bir hata ile karşılaştı bildirir.</span><span class="sxs-lookup"><span data-stu-id="87c7d-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87c7d-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87c7d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87c7d-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="87c7d-106">[in] `ModuleID` İçinde başarısız bir yeniden derleme girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="87c7d-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="87c7d-107">[in] `MethodDef` Yönteminin başarısız güncellemelerden denemesi yapıldı.</span><span class="sxs-lookup"><span data-stu-id="87c7d-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="87c7d-108">[in] Znovu veya için işaretlendi yeniden derleme yapılıyor işlevi örneği.</span><span class="sxs-lookup"><span data-stu-id="87c7d-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="87c7d-109">Bu değer olabilir `NULL` (örneğin, profil oluşturucu yöntemi derlenmesi için bir geçersiz meta veri belirteci belirtilmişse) örnekleme başına temel yerine yöntemi başına temelinde hatası durumunda.</span><span class="sxs-lookup"><span data-stu-id="87c7d-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="87c7d-110">[in] Hatanın yapısını gösteren HRESULT.</span><span class="sxs-lookup"><span data-stu-id="87c7d-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="87c7d-111">Değerlerin bir listesi için durumu HRESULTS bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="87c7d-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87c7d-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="87c7d-112">Return Value</span></span>  
 <span data-ttu-id="87c7d-113">Bu geri arama dönüş değerleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="87c7d-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="87c7d-114">Durum HRESULTS</span><span class="sxs-lookup"><span data-stu-id="87c7d-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="87c7d-115">Durum dizi HRESULT</span><span class="sxs-lookup"><span data-stu-id="87c7d-115">Status array HRESULT</span></span>|<span data-ttu-id="87c7d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87c7d-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="87c7d-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="87c7d-117">E_INVALIDARG</span></span>|<span data-ttu-id="87c7d-118">`moduleID` Veya `methodDef` belirteç `NULL`.</span><span class="sxs-lookup"><span data-stu-id="87c7d-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="87c7d-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="87c7d-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="87c7d-120">Modül henüz tam yüklü değil veya yüklenmemiş sürecinde olduğundan.</span><span class="sxs-lookup"><span data-stu-id="87c7d-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="87c7d-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="87c7d-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="87c7d-122">Belirtilen modül dinamik olarak oluşturulan (örneğin, `Reflection.Emit`) ve bu nedenle bu yöntem tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="87c7d-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="87c7d-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="87c7d-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="87c7d-124">Yöntem bir toplanabilir bütünleştirilmiş koda örneği ve derlenmesi mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="87c7d-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="87c7d-125">Türleri unutmayın ve yansıma olmayan bağlamda tanımlı işlevler (örneğin, `List<MyCollectibleStruct>`) toplanabilir derlemeye oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="87c7d-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="87c7d-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="87c7d-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="87c7d-127">CLR JIT yeniden derlemesi için belirtilen yöntemi işaretlemek çalışırken belleği yetersiz kaldı.</span><span class="sxs-lookup"><span data-stu-id="87c7d-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="87c7d-128">Diğer</span><span class="sxs-lookup"><span data-stu-id="87c7d-128">Other</span></span>|<span data-ttu-id="87c7d-129">İşletim sistemi CLR denetimin dışında kalan bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="87c7d-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="87c7d-130">Örneğin, belleğin bir sayfası erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hata görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="87c7d-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87c7d-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87c7d-131">Requirements</span></span>  
 <span data-ttu-id="87c7d-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87c7d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87c7d-133">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87c7d-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87c7d-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87c7d-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87c7d-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87c7d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c7d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87c7d-136">See also</span></span>

- [<span data-ttu-id="87c7d-137">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87c7d-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="87c7d-138">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87c7d-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
