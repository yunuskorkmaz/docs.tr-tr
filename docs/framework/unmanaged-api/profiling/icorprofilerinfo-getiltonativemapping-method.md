---
description: ': ICorProfilerInfo:: GetILToNativeMapping Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ce3473365eb98beca4d2e9116251200d7539e4c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647394"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="cafe9-103">ICorProfilerInfo::GetILToNativeMapping Metodu</span><span class="sxs-lookup"><span data-stu-id="cafe9-103">ICorProfilerInfo::GetILToNativeMapping Method</span></span>

<span data-ttu-id="cafe9-104">Microsoft ara dili (MSIL) uzaklıklarından, belirtilen işlevde bulunan kodun yerel uzaklıklarından bir harita alır.</span><span class="sxs-lookup"><span data-stu-id="cafe9-104">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cafe9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cafe9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cafe9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cafe9-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="cafe9-107">'ndaki Kodu içeren işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="cafe9-107">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="cafe9-108">'ndaki Dizinin en büyük boyutu `map` .</span><span class="sxs-lookup"><span data-stu-id="cafe9-108">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="cafe9-109">dışı Kullanılabilir COR_DEBUG_IL_TO_NATIVE_MAP yapılarının toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="cafe9-109">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="cafe9-110">dışı `COR_DEBUG_IL_TO_NATIVE_MAP` Her biri uzaklıkları belirten yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="cafe9-110">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="cafe9-111">`GetILToNativeMapping`Yöntem döndüğünde, `map` yapıların bazılarını veya tümünü içerir `COR_DEBUG_IL_TO_NATIVE_MAP` .</span><span class="sxs-lookup"><span data-stu-id="cafe9-111">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cafe9-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cafe9-112">Remarks</span></span>  

 <span data-ttu-id="cafe9-113">`GetILToNativeMapping`Yöntemi bir yapı dizisini döndürür `COR_DEBUG_IL_TO_NATIVE_MAP` .</span><span class="sxs-lookup"><span data-stu-id="cafe9-113">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="cafe9-114">Belirli yerel yönergeler aralıklarının özel kod bölgelerine (örneğin, giriş) karşılık gelmesini sağlamak için dizideki bir girdinin, `ilOffset` alanı [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) numaralandırması değerine ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="cafe9-114">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="cafe9-115">`GetILToNativeMapping`Geri döndüğünde, `map` arabelleğin tüm yapıları içerecek kadar büyük olduğunu doğrulamanız gerekir `COR_DEBUG_IL_TO_NATIVE_MAP` .</span><span class="sxs-lookup"><span data-stu-id="cafe9-115">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="cafe9-116">Bunu yapmak için değerini `cMap` parametresinin değeriyle karşılaştırın `pcMap` .</span><span class="sxs-lookup"><span data-stu-id="cafe9-116">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="cafe9-117">`pcMap`Değer, bir yapının boyutuyla çarpıldığı zaman, daha büyüktür `COR_DEBUG_IL_TO_NATIVE_MAP` `cMap` , daha büyük bir `map` arabellek ayırır, `cMap` Yeni, daha büyük boyutla güncelleştirin ve `GetILToNativeMapping` yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="cafe9-117">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="cafe9-118">Alternatif olarak, `GetILToNativeMapping` `map` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cafe9-118">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="cafe9-119">Daha sonra arabellek boyutunu içinde döndürülen değere ayarlayabilir `pcMap` ve `GetILToNativeMapping` yeniden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cafe9-119">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cafe9-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cafe9-120">Requirements</span></span>  

 <span data-ttu-id="cafe9-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cafe9-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cafe9-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cafe9-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cafe9-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cafe9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cafe9-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cafe9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cafe9-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cafe9-125">See also</span></span>

- [<span data-ttu-id="cafe9-126">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cafe9-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="cafe9-127">GetILToNativeMapping2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cafe9-127">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="cafe9-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cafe9-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cafe9-129">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cafe9-129">Profiling</span></span>](index.md)
