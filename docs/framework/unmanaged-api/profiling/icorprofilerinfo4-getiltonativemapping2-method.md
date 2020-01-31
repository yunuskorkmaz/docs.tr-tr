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
ms.openlocfilehash: 4fccee3b94efd65312206afb22c87f30609f9e6b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868466"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="882f5-102">ICorProfilerInfo4::GetILToNativeMapping2 Metodu</span><span class="sxs-lookup"><span data-stu-id="882f5-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="882f5-103">Belirtilen işlevin JıT yeniden derlenmiş sürümünde yer alan kodun yerel uzaklıklarından Microsoft ara dil (MSIL) uzaklıklarını bir harita alır.</span><span class="sxs-lookup"><span data-stu-id="882f5-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="882f5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="882f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="882f5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="882f5-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="882f5-106">'ndaki Kodu içeren işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="882f5-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="882f5-107">'ndaki JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="882f5-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="882f5-108">Kimlik .NET Framework 4,5 ' de sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="882f5-108">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="882f5-109">'ndaki `map` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="882f5-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="882f5-110">dışı Kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="882f5-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="882f5-111">dışı Her biri uzaklıkları belirten `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="882f5-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="882f5-112">`GetILToNativeMapping2` yöntemi çağrıldıktan sonra, `map` `COR_DEBUG_IL_TO_NATIVE_MAP` yapıların bazılarını veya tümünü içerecektir.</span><span class="sxs-lookup"><span data-stu-id="882f5-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="882f5-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="882f5-113">Remarks</span></span>  
 <span data-ttu-id="882f5-114">`GetILToNativeMapping2`, [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) yöntemine benzer, ancak profil oluşturucunun sonraki sürümlerde yeniden derlenen işlevin kimliğini belirtmesini sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="882f5-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="882f5-115">[ICorProfilerFunctionControl:: SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) yöntemi, .NET Framework 4,5 ' de uygulanmıyor, bu nedenle JIT yeniden derlenecek olan işlevlerin ilk derlenmiş işlevden farklı bir IL-yerel eşlemesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="882f5-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="882f5-116">Bu nedenle, `GetILToNativeMapping2` .NET Framework 4,5 ' de sıfır olmayan bir JıT KIMLIĞI ile çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="882f5-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="882f5-117">`GetILToNativeMapping2` yöntemi `COR_DEBUG_IL_TO_NATIVE_MAP` yapılarından oluşan bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="882f5-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="882f5-118">Belirli yerel yönergeler aralıklarının özel kod bölgelerine (örneğin, giriş) karşılık gelmesini sağlamak için dizideki bir girdinin, `ilOffset` alanı [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) numaralandırması değerine ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="882f5-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="882f5-119">`GetILToNativeMapping2` çağrıldıktan sonra, `map` arabelleğinin tüm `COR_DEBUG_IL_TO_NATIVE_MAP` yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="882f5-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="882f5-120">Bunu yapmak için `cMap` değerini `pcMap` parametresinin değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="882f5-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="882f5-121">`pcMap` değeri, bir `COR_DEBUG_IL_TO_NATIVE_MAP` yapısının boyutuyla çarpıldığı zaman, `cMap`daha büyükse, daha büyük bir `map` arabelleği ayırın, yeni, daha büyük boyutlu `cMap` güncelleştirin ve `GetILToNativeMapping2` çağırın.</span><span class="sxs-lookup"><span data-stu-id="882f5-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="882f5-122">Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetILToNativeMapping2` sıfır uzunluklu `map` arabelleği ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="882f5-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="882f5-123">Daha sonra arabellek boyutunu `pcMap` döndürülen değere ayarlayabilir ve `GetILToNativeMapping2` tekrar çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="882f5-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="882f5-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="882f5-124">Requirements</span></span>  
 <span data-ttu-id="882f5-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="882f5-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="882f5-126">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="882f5-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="882f5-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="882f5-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="882f5-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="882f5-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="882f5-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="882f5-129">See also</span></span>

- [<span data-ttu-id="882f5-130">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="882f5-130">GetILToNativeMapping Method</span></span>](icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="882f5-131">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="882f5-131">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="882f5-132">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="882f5-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="882f5-133">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="882f5-133">Profiling</span></span>](index.md)
