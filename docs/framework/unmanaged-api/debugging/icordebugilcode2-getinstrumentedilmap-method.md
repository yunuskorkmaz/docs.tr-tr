---
title: ICorDebugILCode2::GetInstrumentedILMap Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a712ed9e3534ca6bb2962989f1ab3750a25d539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417908"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="8c0d8-102">ICorDebugILCode2::GetInstrumentedILMap Metodu</span><span class="sxs-lookup"><span data-stu-id="8c0d8-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="8c0d8-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="8c0d8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8c0d8-104">Bir harita Bu örnek için özgün yöntemi IL uzaklık profil oluşturucu izleme eklenmiş Ara dile (IL) uzaklıklarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c0d8-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c0d8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c0d8-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c0d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c0d8-106">Parameters</span></span>  
 <span data-ttu-id="8c0d8-107">cMap</span><span class="sxs-lookup"><span data-stu-id="8c0d8-107">cMap</span></span>  
 <span data-ttu-id="8c0d8-108">[in] Depolama kapasitesini `map` dizi.</span><span class="sxs-lookup"><span data-stu-id="8c0d8-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="8c0d8-109">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8c0d8-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="8c0d8-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="8c0d8-110">pcMap</span></span>  
 <span data-ttu-id="8c0d8-111">[out] Eşleme dizisine yazılan cor_ıl_map değer sayısı.</span><span class="sxs-lookup"><span data-stu-id="8c0d8-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="8c0d8-112">map</span><span class="sxs-lookup"><span data-stu-id="8c0d8-112">map</span></span>  
 <span data-ttu-id="8c0d8-113">[out] Eşlemesi profil oluşturucu izleme eklenmiş IL özgün yöntemi IL için bilgilerini cor_ıl_map değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="8c0d8-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c0d8-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c0d8-114">Remarks</span></span>  
 <span data-ttu-id="8c0d8-115">Profil Oluşturucu çağırarak eşleme ayarlarsa [Icorprofilerınfo::setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) yöntemi, hata ayıklayıcı eşleme almak ve IL hesaplamak için yığın kaydırır zaman eşleme dahili olarak kullanmak için bu yöntemi çağırabilirsiniz izlemeleri ve değişken yaşam süresi yok.</span><span class="sxs-lookup"><span data-stu-id="8c0d8-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="8c0d8-116">Varsa `cMap` 0'dır ve `pcMap` olan olmayan**null**, `pcMap` kullanılabilir cor_ıl_map değerlerin sayısını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8c0d8-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="8c0d8-117">Varsa `cMap` sıfır, değil depolama kapasitesini temsil `map` dizi.</span><span class="sxs-lookup"><span data-stu-id="8c0d8-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="8c0d8-118">Yöntem döndüğünde `map` en fazla içeren `cMap` öğeleri ve `pcMap` gerçekte yazılan cor_ıl_map değerlerin sayısını ayarlanır `map` dizi.</span><span class="sxs-lookup"><span data-stu-id="8c0d8-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="8c0d8-119">IL izlenmiş değiştirilmediğini veya eşleme Profil Oluşturucu tarafından sağlanmadı, bu yöntem `S_OK` ve ayarlar `pcMap` 0.</span><span class="sxs-lookup"><span data-stu-id="8c0d8-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c0d8-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c0d8-120">Requirements</span></span>  
 <span data-ttu-id="8c0d8-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c0d8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c0d8-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c0d8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c0d8-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c0d8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c0d8-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c0d8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c0d8-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c0d8-125">See Also</span></span>  
 [<span data-ttu-id="8c0d8-126">Icorprofilerınfo::setılınstrumentedcodemap</span><span class="sxs-lookup"><span data-stu-id="8c0d8-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)  
 [<span data-ttu-id="8c0d8-127">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c0d8-127">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [<span data-ttu-id="8c0d8-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8c0d8-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
