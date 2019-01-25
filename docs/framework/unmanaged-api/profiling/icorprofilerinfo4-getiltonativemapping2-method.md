---
title: ICorProfilerInfo4::GetILToNativeMapping2 Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd3ccbe2b6b33e873bdb647987b38aeef74c1b2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552495"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="75f64-102">ICorProfilerInfo4::GetILToNativeMapping2 Metodu</span><span class="sxs-lookup"><span data-stu-id="75f64-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="75f64-103">Harita, Microsoft Ara dil (MSIL) için belirtilen işlev JIT yeniden derlenen sürümünde yer alan kodun yerel uzaklıklar uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="75f64-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f64-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75f64-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75f64-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75f64-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="75f64-106">[in] Kodu içeren işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="75f64-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="75f64-107">[in] JIT yeniden derlenen işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="75f64-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="75f64-108">Kimliğin sıfır olmalıdır [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75f64-108">The identity must be zero in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 `cMap`  
 <span data-ttu-id="75f64-109">[in] En büyük boyutunu `map` dizisi.</span><span class="sxs-lookup"><span data-stu-id="75f64-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="75f64-110">[out] Kullanılabilir cor_debug_ıl_to_natıve_map yapıları toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="75f64-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="75f64-111">[out] Bir dizi `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları, her biri uzaklıkları belirtir.</span><span class="sxs-lookup"><span data-stu-id="75f64-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="75f64-112">Sonra `GetILToNativeMapping2` yöntemi döndüğünde, `map` bazılarını veya tümünü içerecektir `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları.</span><span class="sxs-lookup"><span data-stu-id="75f64-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75f64-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75f64-113">Remarks</span></span>  
 <span data-ttu-id="75f64-114">`GetILToNativeMapping2` benzer [Icorprofilerınfo::getıltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) yöntemi znovu işlevi Kimliğini gelecekte belirtmek profil oluşturucu sağlayacak dışında serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="75f64-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75f64-115">[Icorprofilerfunctioncontrol::setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) yöntemi içinde uygulanmamıştır [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]JIT yeniden derlenen işlevleri farklı bir IL yerel eşleme olamaz. Bu nedenle başlangıçta derlenmiş işlevi.</span><span class="sxs-lookup"><span data-stu-id="75f64-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="75f64-116">Bu nedenle, `GetILToNativeMapping2` sıfır olmayan bir JIT yeniden derlenen kimliği ile çağrılamaz [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="75f64-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
 <span data-ttu-id="75f64-117">`GetILToNativeMapping2` Yöntemi, bir dizi döndürür `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları.</span><span class="sxs-lookup"><span data-stu-id="75f64-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="75f64-118">Belirli aralıkları yerel yönergeleri için kod (örneğin, giriş) özel bölgeleri karşılık gelen iletmek için bir giriş dizisinde olabilir, `ilOffset` alan için bir değer kümesi [Cordebugıltonativemappingtypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="75f64-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="75f64-119">Sonra `GetILToNativeMapping2` döndürür, doğrulamalısınız `map` arabellek tüm içerecek şekilde büyük `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları.</span><span class="sxs-lookup"><span data-stu-id="75f64-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="75f64-120">Bunu yapmak için değeri ile karşılaştırmak `cMap` değeriyle `pcMap` parametresi.</span><span class="sxs-lookup"><span data-stu-id="75f64-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="75f64-121">Varsa `pcMap` boyutu tarafından çarpıldığında değeri bir `COR_DEBUG_IL_TO_NATIVE_MAP` yapısı, büyüktür `cMap`, daha büyük bir ayırma `map` arabellek, güncelleştirme `cMap` yeni, daha büyük bir boyut ve çağrı `GetILToNativeMapping2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="75f64-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="75f64-122">Alternatif olarak, ilk çağırabilirsiniz `GetILToNativeMapping2` sıfır uzunluklu ile `map` arabellek doğru arabellek boyutu elde edilir.</span><span class="sxs-lookup"><span data-stu-id="75f64-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="75f64-123">Arabellek boyutu döndürülen değere ayarlayabilirsiniz `pcMap` ve çağrı `GetILToNativeMapping2` yeniden.</span><span class="sxs-lookup"><span data-stu-id="75f64-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75f64-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75f64-124">Requirements</span></span>  
 <span data-ttu-id="75f64-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75f64-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75f64-126">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="75f64-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75f64-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75f64-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75f64-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75f64-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f64-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75f64-129">See also</span></span>
- [<span data-ttu-id="75f64-130">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75f64-130">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="75f64-131">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75f64-131">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="75f64-132">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="75f64-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="75f64-133">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="75f64-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
