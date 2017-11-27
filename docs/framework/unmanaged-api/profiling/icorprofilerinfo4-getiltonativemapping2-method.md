---
title: ICorProfilerInfo4::GetILToNativeMapping2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetILToNativeMapping2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: eda88ca0ba30c85889198e11e3f465b85d1019b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="faf1d-102">ICorProfilerInfo4::GetILToNativeMapping2 Metodu</span><span class="sxs-lookup"><span data-stu-id="faf1d-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="faf1d-103">Belirtilen işlev JIT yeniden derlenmesi sürümünde yer alan kodu için yerel uzaklık için Ara dili (MSIL) kaydırır Microsoft'tan bir harita alır.</span><span class="sxs-lookup"><span data-stu-id="faf1d-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf1d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="faf1d-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="faf1d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="faf1d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="faf1d-106">[in] Kod içeren işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="faf1d-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="faf1d-107">[in] JIT yeniden derlenmesi işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="faf1d-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="faf1d-108">Kimliği sıfır olmalıdır [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="faf1d-108">The identity must be zero in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 `cMap`  
 <span data-ttu-id="faf1d-109">[in] En büyük boyutunu `map` dizi.</span><span class="sxs-lookup"><span data-stu-id="faf1d-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="faf1d-110">[out] Kullanılabilir cor_debug_ıl_to_natıve_map yapıları toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="faf1d-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="faf1d-111">[out] Bir dizi `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları, her biri uzaklıkları belirtir.</span><span class="sxs-lookup"><span data-stu-id="faf1d-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="faf1d-112">Sonra `GetILToNativeMapping2` yöntemi döndürür `map` bazılarını veya tümünü içerecek `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları.</span><span class="sxs-lookup"><span data-stu-id="faf1d-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faf1d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="faf1d-113">Remarks</span></span>  
 <span data-ttu-id="faf1d-114">`GetILToNativeMapping2`benzer [Icorprofilerınfo::getıltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) derlenmiş işlevi kimliği gelecekte belirtmek profil oluşturucu izin verir ancak bu yöntem, serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="faf1d-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="faf1d-115">[Icorprofilerfunctioncontrol::setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) yöntemi uygulanan değil [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]JIT yeniden derlenmesi işlevler farklı bir IL yerel eşlemesi olamaz nedenle ilk olarak derlenmiş işlevi.</span><span class="sxs-lookup"><span data-stu-id="faf1d-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="faf1d-116">Bu nedenle, `GetILToNativeMapping2` sıfır olmayan bir JIT yeniden derlenmesi kimliği ile çağrılamaz [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="faf1d-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 <span data-ttu-id="faf1d-117">`GetILToNativeMapping2` Yöntemi bir dizi döndürür `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları.</span><span class="sxs-lookup"><span data-stu-id="faf1d-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="faf1d-118">Belirli yerel yönergeler aralıklarını kod (örneğin, giriş) özel bölgeler için karşılık gelen iletmek için dizi bir girişe sahip olabilir, `ilOffset` alan için bir değer kümesi [Cordebugıltonativemappingtypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="faf1d-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="faf1d-119">Sonra `GetILToNativeMapping2` döndürür, doğrulamalısınız `map` arabellek tüm içerecek şekilde büyük `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları.</span><span class="sxs-lookup"><span data-stu-id="faf1d-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="faf1d-120">Bunu yapmak için değeri ile karşılaştırın `cMap` değeriyle `pcMap` parametresi.</span><span class="sxs-lookup"><span data-stu-id="faf1d-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="faf1d-121">Varsa `pcMap` boyutuyla çarpılır olduğunda değeri bir `COR_DEBUG_IL_TO_NATIVE_MAP` yapısı, büyük `cMap`, daha geniş bir ayırma `map` arabellek, güncelleştirme `cMap` yeni, büyük boyutu ve çağrı `GetILToNativeMapping2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="faf1d-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="faf1d-122">Alternatif olarak, ilk çağırabilirsiniz `GetILToNativeMapping2` sıfır uzunluklu ile `map` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="faf1d-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="faf1d-123">Döndürülen değer için arabellek boyutu ayarlayabilirsiniz `pcMap` ve arama `GetILToNativeMapping2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="faf1d-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faf1d-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="faf1d-124">Requirements</span></span>  
 <span data-ttu-id="faf1d-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faf1d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faf1d-126">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="faf1d-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="faf1d-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="faf1d-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="faf1d-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faf1d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf1d-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="faf1d-129">See Also</span></span>  
 [<span data-ttu-id="faf1d-130">Getıltonativemapping yöntemi</span><span class="sxs-lookup"><span data-stu-id="faf1d-130">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)  
 [<span data-ttu-id="faf1d-131">Icorprofilerınfo4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="faf1d-131">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="faf1d-132">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="faf1d-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="faf1d-133">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="faf1d-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
