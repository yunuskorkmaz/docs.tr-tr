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
ms.openlocfilehash: ec6472a33c49d9345793d73ac2f78f8896dc218b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454824"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="0f877-102">ICorProfilerCallback4::ReJITError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f877-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="0f877-103">Profil Oluşturucu tam zamanında (JIT) derleyici derleme işlemindeki bir hata ile karşılaştı bildirir.</span><span class="sxs-lookup"><span data-stu-id="0f877-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f877-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f877-104">Syntax</span></span>  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f877-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f877-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="0f877-106">[in] `ModuleID` İçinde hangi başarısız yeniden derlenmek girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="0f877-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="0f877-107">[in] `MethodDef` Yönteminin başarısız yeniden derlenmek girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="0f877-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="0f877-108">[in] Derlenmiş veya için işaretlendi yeniden derlenmek yapılıyor işlevi örneği.</span><span class="sxs-lookup"><span data-stu-id="0f877-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="0f877-109">Bu değer olabilir `NULL` (örneğin, profil oluşturucu yöntemi derlenmesi için bir geçersiz meta veriler belirteci belirtilmişse) başına oluşturmada temel yerine yöntemi başına temelinde hatası durumunda.</span><span class="sxs-lookup"><span data-stu-id="0f877-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="0f877-110">[in] Hatanın yapısını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0f877-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="0f877-111">Değerlerin listesi için durumu HRESULTS bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0f877-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f877-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0f877-112">Return Value</span></span>  
 <span data-ttu-id="0f877-113">Bu geri dönüş değerleri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="0f877-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="0f877-114">Durum HRESULTS</span><span class="sxs-lookup"><span data-stu-id="0f877-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="0f877-115">Durum dizi HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f877-115">Status array HRESULT</span></span>|<span data-ttu-id="0f877-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f877-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="0f877-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0f877-117">E_INVALIDARG</span></span>|<span data-ttu-id="0f877-118">`moduleID` Veya `methodDef` belirteci `NULL`.</span><span class="sxs-lookup"><span data-stu-id="0f877-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="0f877-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="0f877-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="0f877-120">Modül henüz tam olarak yüklü değil veya kaldırıldığında sürecinde olduğundan.</span><span class="sxs-lookup"><span data-stu-id="0f877-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="0f877-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="0f877-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="0f877-122">Belirtilen modül dinamik olarak oluşturulan (örneğin, `Reflection.Emit`) ve bu nedenle bu yöntem tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="0f877-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="0f877-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="0f877-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="0f877-124">Yöntemi, collectible derlemeye örneği ve bu nedenle derlenmesi mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="0f877-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="0f877-125">Türleri Not ve yansıma olmayan bağlamında tanımlanan işlevleri (örneğin, `List<MyCollectibleStruct>`) collectible derlemeye oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="0f877-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="0f877-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0f877-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0f877-127">CLR JIT yeniden derlenmek belirtilen yöntemini işaretlemek çalışırken yetersiz bellek tükendi.</span><span class="sxs-lookup"><span data-stu-id="0f877-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="0f877-128">Diğer</span><span class="sxs-lookup"><span data-stu-id="0f877-128">Other</span></span>|<span data-ttu-id="0f877-129">İşletim sistemi CLR denetimi dışında kalan bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="0f877-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="0f877-130">Örneğin, belleğin bir sayfası erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hatası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0f877-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f877-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f877-131">Requirements</span></span>  
 <span data-ttu-id="0f877-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f877-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f877-133">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0f877-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f877-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f877-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f877-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f877-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f877-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f877-136">See Also</span></span>  
 [<span data-ttu-id="0f877-137">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f877-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="0f877-138">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f877-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
