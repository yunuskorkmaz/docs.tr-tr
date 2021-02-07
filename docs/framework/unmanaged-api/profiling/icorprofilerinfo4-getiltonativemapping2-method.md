---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo4:: Getıltonativemapping2 yöntemi'
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
ms.openlocfilehash: f548dbef3444c6e63e51cd5f3db79e567b2630b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686797"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="d6ee9-103">ICorProfilerInfo4::GetILToNativeMapping2 Metodu</span><span class="sxs-lookup"><span data-stu-id="d6ee9-103">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>

<span data-ttu-id="d6ee9-104">Belirtilen işlevin JıT yeniden derlenmiş sürümünde yer alan kodun yerel uzaklıklarından Microsoft ara dil (MSIL) uzaklıklarını bir harita alır.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-104">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ee9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6ee9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6ee9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6ee9-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="d6ee9-107">'ndaki Kodu içeren işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-107">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="d6ee9-108">'ndaki JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-108">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="d6ee9-109">Kimlik .NET Framework 4,5 ' de sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-109">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="d6ee9-110">'ndaki Dizinin en büyük boyutu `map` .</span><span class="sxs-lookup"><span data-stu-id="d6ee9-110">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="d6ee9-111">dışı Kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-111">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="d6ee9-112">dışı `COR_DEBUG_IL_TO_NATIVE_MAP` Her biri uzaklıkları belirten yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-112">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="d6ee9-113">`GetILToNativeMapping2`Yöntem döndüğünde, `map` yapıların bazılarını veya tümünü içerir `COR_DEBUG_IL_TO_NATIVE_MAP` .</span><span class="sxs-lookup"><span data-stu-id="d6ee9-113">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6ee9-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6ee9-114">Remarks</span></span>  

 <span data-ttu-id="d6ee9-115">`GetILToNativeMapping2` , [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) yöntemine benzerdir, ancak profil oluşturucunun gelecek sürümlerde yeniden derlenen işlevin kimliğini belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-115">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6ee9-116">[ICorProfilerFunctionControl:: SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) yöntemi, .NET Framework 4,5 ' de uygulanmıyor, bu nedenle JIT yeniden derlenecek olan işlevlerin ilk derlenmiş işlevden farklı bir IL-yerel eşlemesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-116">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="d6ee9-117">Bu nedenle, `GetILToNativeMapping2` .NET Framework 4,5 ' de sıfır olmayan BIR JıT kimliği ile çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-117">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="d6ee9-118">`GetILToNativeMapping2`Yöntemi bir yapı dizisini döndürür `COR_DEBUG_IL_TO_NATIVE_MAP` .</span><span class="sxs-lookup"><span data-stu-id="d6ee9-118">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="d6ee9-119">Belirli yerel yönergeler aralıklarının özel kod bölgelerine (örneğin, giriş) karşılık gelmesini sağlamak için dizideki bir girdinin, `ilOffset` alanı [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) numaralandırması değerine ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-119">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="d6ee9-120">`GetILToNativeMapping2`Geri döndüğünde, `map` arabelleğin tüm yapıları içerecek kadar büyük olduğunu doğrulamanız gerekir `COR_DEBUG_IL_TO_NATIVE_MAP` .</span><span class="sxs-lookup"><span data-stu-id="d6ee9-120">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="d6ee9-121">Bunu yapmak için değerini `cMap` parametresinin değeriyle karşılaştırın `pcMap` .</span><span class="sxs-lookup"><span data-stu-id="d6ee9-121">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="d6ee9-122">`pcMap`Değer, bir yapının boyutuyla çarpıldığı zaman, daha büyüktür `COR_DEBUG_IL_TO_NATIVE_MAP` `cMap` , daha büyük bir `map` arabellek ayırır, `cMap` Yeni, daha büyük boyutla güncelleştirin ve `GetILToNativeMapping2` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-122">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="d6ee9-123">Alternatif olarak, `GetILToNativeMapping2` `map` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-123">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d6ee9-124">Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcMap` ve `GetILToNativeMapping2` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-124">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6ee9-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6ee9-125">Requirements</span></span>  

 <span data-ttu-id="d6ee9-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6ee9-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6ee9-127">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d6ee9-127">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6ee9-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d6ee9-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6ee9-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6ee9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ee9-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6ee9-130">See also</span></span>

- [<span data-ttu-id="d6ee9-131">GetILToNativeMapping Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6ee9-131">GetILToNativeMapping Method</span></span>](icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="d6ee9-132">ICorProfilerInfo4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6ee9-132">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="d6ee9-133">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d6ee9-133">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d6ee9-134">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6ee9-134">Profiling</span></span>](index.md)
