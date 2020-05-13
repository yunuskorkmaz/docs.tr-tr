---
title: ICorDebugILCode2::GetInstrumentedILMap Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
ms.openlocfilehash: c6fdb7040620bb7a5b6aea6e0dc41e08d6f346d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210364"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="534d8-102">ICorDebugILCode2::GetInstrumentedILMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="534d8-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="534d8-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="534d8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="534d8-104">Bu örnek için profil oluşturucu tarafından işaretlenmiş ara dil (IL) uzaklıklarını orijinal Yöntem Il uzaklıklarından bir eşleme döndürür.</span><span class="sxs-lookup"><span data-stu-id="534d8-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="534d8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="534d8-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="534d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="534d8-106">Parameters</span></span>  
 <span data-ttu-id="534d8-107">cMap</span><span class="sxs-lookup"><span data-stu-id="534d8-107">cMap</span></span>  
 <span data-ttu-id="534d8-108">'ndaki Dizinin depolama kapasitesi `map` .</span><span class="sxs-lookup"><span data-stu-id="534d8-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="534d8-109">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="534d8-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="534d8-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="534d8-110">pcMap</span></span>  
 <span data-ttu-id="534d8-111">dışı Harita dizisine yazılan COR_IL_MAP değerlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="534d8-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="534d8-112">map</span><span class="sxs-lookup"><span data-stu-id="534d8-112">map</span></span>  
 <span data-ttu-id="534d8-113">dışı Profil Oluşturucu tarafından izlenen Il 'den özgün yöntemin Il 'ye eşlemeler hakkında bilgi sağlayan COR_IL_MAP değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="534d8-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="534d8-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="534d8-114">Remarks</span></span>  
 <span data-ttu-id="534d8-115">Profil Oluşturucu [ICorProfilerInfo:: SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metodunu çağırarak eşlemeyi ayarlarsa, hata ayıklayıcı eşlemeyi almak için bu yöntemi çağırabilir ve yığın izlemeleri ve değişken yaşam SÜRELERI için Il farklarını hesaplarken dahili eşlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="534d8-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="534d8-116">`cMap`0 ise ve `pcMap` **null**değilse, `pcMap` kullanılabilir COR_IL_MAP değeri sayısı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="534d8-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="534d8-117">`cMap`Sıfır olmayan ise, dizinin depolama kapasitesini temsil eder `map` .</span><span class="sxs-lookup"><span data-stu-id="534d8-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="534d8-118">Yöntemi döndürüldüğünde, `map` en fazla `cMap` öğe içerir ve `pcMap` gerçekten diziye yazılan COR_IL_MAP değerlerinin sayısına ayarlanır `map` .</span><span class="sxs-lookup"><span data-stu-id="534d8-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="534d8-119">Il düzenlenmemişse veya eşleme bir profil oluşturucu tarafından sağlanmamışsa, bu yöntem döndürür `S_OK` ve `pcMap` 0 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="534d8-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="534d8-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="534d8-120">Requirements</span></span>  
 <span data-ttu-id="534d8-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="534d8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="534d8-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="534d8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="534d8-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="534d8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="534d8-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="534d8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="534d8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="534d8-125">See also</span></span>

- [<span data-ttu-id="534d8-126">ICorProfilerInfo:: Setilınstrumentedcodemap</span><span class="sxs-lookup"><span data-stu-id="534d8-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="534d8-127">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="534d8-127">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="534d8-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="534d8-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
