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
ms.openlocfilehash: 728a6c83dc321fa28dc4ff84c4e874d886524b36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788566"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="3c589-102">ICorDebugILCode2::GetInstrumentedILMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c589-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="3c589-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="3c589-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3c589-104">Bu örnek için profil oluşturucu tarafından işaretlenmiş ara dil (IL) uzaklıklarını orijinal Yöntem Il uzaklıklarından bir eşleme döndürür.</span><span class="sxs-lookup"><span data-stu-id="3c589-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c589-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c589-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c589-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c589-106">Parameters</span></span>  
 <span data-ttu-id="3c589-107">cMap</span><span class="sxs-lookup"><span data-stu-id="3c589-107">cMap</span></span>  
 <span data-ttu-id="3c589-108">'ndaki `map` dizisinin depolama kapasitesi.</span><span class="sxs-lookup"><span data-stu-id="3c589-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="3c589-109">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3c589-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="3c589-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="3c589-110">pcMap</span></span>  
 <span data-ttu-id="3c589-111">dışı Harita dizisine yazılan COR_IL_MAP değerlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="3c589-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="3c589-112">map</span><span class="sxs-lookup"><span data-stu-id="3c589-112">map</span></span>  
 <span data-ttu-id="3c589-113">dışı Profil Oluşturucu tarafından izlenen Il 'den özgün yöntemin Il 'ye eşlemeler hakkında bilgi sağlayan COR_IL_MAP değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="3c589-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c589-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c589-114">Remarks</span></span>  
 <span data-ttu-id="3c589-115">Profil Oluşturucu [ICorProfilerInfo:: SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metodunu çağırarak eşlemeyi ayarlarsa, hata ayıklayıcı eşlemeyi almak için bu yöntemi çağırabilir ve yığın izlemeleri ve değişken yaşam SÜRELERI için Il farklarını hesaplarken dahili eşlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="3c589-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="3c589-116">`cMap` 0 ise ve `pcMap`**null**değilse `pcMap` kullanılabilir COR_IL_MAP değer sayısına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3c589-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="3c589-117">Sıfır olmayan `cMap`, `map` dizisinin depolama kapasitesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3c589-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="3c589-118">Yöntemi döndürüldüğünde, `map` en fazla `cMap` öğesi içerir ve `pcMap` aslında `map` dizisine yazılmış COR_IL_MAP değerlerinin sayısına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3c589-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="3c589-119">Il düzenlenmemişse veya eşleme bir profil oluşturucu tarafından sağlanmamışsa, bu yöntem `S_OK` döndürür ve `pcMap` 0 olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3c589-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c589-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c589-120">Requirements</span></span>  
 <span data-ttu-id="3c589-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c589-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c589-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3c589-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c589-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3c589-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c589-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c589-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c589-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c589-125">See also</span></span>

- [<span data-ttu-id="3c589-126">ICorProfilerInfo:: Setilınstrumentedcodemap</span><span class="sxs-lookup"><span data-stu-id="3c589-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="3c589-127">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c589-127">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="3c589-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3c589-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
