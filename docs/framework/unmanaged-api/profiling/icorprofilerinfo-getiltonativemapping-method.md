---
title: ICorProfilerInfo::GetILToNativeMapping Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
ms.openlocfilehash: f9abb3ae9cd3f9c70485e584399a6ed32b32a572
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870656"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="14f00-102">ICorProfilerInfo::GetILToNativeMapping Metodu</span><span class="sxs-lookup"><span data-stu-id="14f00-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="14f00-103">Microsoft ara dili (MSIL) uzaklıklarından, belirtilen işlevde bulunan kodun yerel uzaklıklarından bir harita alır.</span><span class="sxs-lookup"><span data-stu-id="14f00-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14f00-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14f00-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14f00-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14f00-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="14f00-106">'ndaki Kodu içeren işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="14f00-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="14f00-107">'ndaki `map` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="14f00-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="14f00-108">dışı Kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="14f00-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="14f00-109">dışı Her biri uzaklıkları belirten `COR_DEBUG_IL_TO_NATIVE_MAP` yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="14f00-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="14f00-110">`GetILToNativeMapping` yöntemi çağrıldıktan sonra, `map` `COR_DEBUG_IL_TO_NATIVE_MAP` yapıların bazılarını veya tümünü içerecektir.</span><span class="sxs-lookup"><span data-stu-id="14f00-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14f00-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14f00-111">Remarks</span></span>  
 <span data-ttu-id="14f00-112">`GetILToNativeMapping` yöntemi `COR_DEBUG_IL_TO_NATIVE_MAP` yapılarından oluşan bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="14f00-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="14f00-113">Belirli yerel yönergeler aralıklarının özel kod bölgelerine (örneğin, giriş) karşılık gelmesini sağlamak için dizideki bir girdinin, `ilOffset` alanı [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) numaralandırması değerine ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="14f00-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="14f00-114">`GetILToNativeMapping` çağrıldıktan sonra, `map` arabelleğinin tüm `COR_DEBUG_IL_TO_NATIVE_MAP` yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="14f00-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="14f00-115">Bunu yapmak için `cMap` değerini `pcMap` parametresinin değeri ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="14f00-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="14f00-116">`pcMap` değeri, bir `COR_DEBUG_IL_TO_NATIVE_MAP` yapısının boyutuyla çarpıldığı zaman, `cMap`daha büyükse, daha büyük bir `map` arabelleği ayırın, yeni, daha büyük boyutlu `cMap` güncelleştirin ve `GetILToNativeMapping` çağırın.</span><span class="sxs-lookup"><span data-stu-id="14f00-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="14f00-117">Alternatif olarak, doğru arabellek boyutunu elde etmek için ilk olarak `GetILToNativeMapping` sıfır uzunluklu `map` arabelleği ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14f00-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="14f00-118">Daha sonra arabellek boyutunu `pcMap` döndürülen değere ayarlayabilir ve `GetILToNativeMapping` tekrar çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14f00-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14f00-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14f00-119">Requirements</span></span>  
 <span data-ttu-id="14f00-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14f00-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14f00-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="14f00-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="14f00-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="14f00-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14f00-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14f00-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14f00-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14f00-124">See also</span></span>

- [<span data-ttu-id="14f00-125">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="14f00-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="14f00-126">GetILToNativeMapping2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14f00-126">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="14f00-127">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="14f00-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="14f00-128">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="14f00-128">Profiling</span></span>](index.md)
