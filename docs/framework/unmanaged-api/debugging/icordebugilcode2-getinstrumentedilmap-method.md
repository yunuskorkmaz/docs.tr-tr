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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4197b018ea85402762a8591b40f3503c02af3974
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673137"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="0f39f-102">ICorDebugILCode2::GetInstrumentedILMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f39f-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="0f39f-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="0f39f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0f39f-104">Bir harita Bu örnek için özgün yöntemi IL uzaklık profil oluşturucu izleme eklenmiş Ara dil (IL) uzaklıklarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f39f-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f39f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f39f-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f39f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f39f-106">Parameters</span></span>  
 <span data-ttu-id="0f39f-107">CMap</span><span class="sxs-lookup"><span data-stu-id="0f39f-107">cMap</span></span>  
 <span data-ttu-id="0f39f-108">[in] Depolama kapasitesini `map` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0f39f-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="0f39f-109">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0f39f-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="0f39f-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="0f39f-110">pcMap</span></span>  
 <span data-ttu-id="0f39f-111">[out] Eşleme dizisine yazılan cor_ıl_map değer sayısı.</span><span class="sxs-lookup"><span data-stu-id="0f39f-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="0f39f-112">map</span><span class="sxs-lookup"><span data-stu-id="0f39f-112">map</span></span>  
 <span data-ttu-id="0f39f-113">[out] Eşleşmeleri profil oluşturucu izleme eklenmiş IL özgün metodun IL için bilgilerini cor_ıl_map değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="0f39f-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f39f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f39f-114">Remarks</span></span>  
 <span data-ttu-id="0f39f-115">Profil Oluşturucu çağırarak eşleme ayarlarsa [Icorprofilerınfo::setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) yöntemi, hata ayıklayıcı eşleme alınması ve eşleme, dahili olarak IL hesaplamak için yığın kaydırır kullanacağınız için bu yöntemi çağırabilir izlemeleri ve değişken yaşam süresi yok.</span><span class="sxs-lookup"><span data-stu-id="0f39f-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="0f39f-116">Varsa `cMap` 0'dır ve `pcMap` olan olmayan**null**, `pcMap` kullanılabilir cor_ıl_map değerlerinin bir sayıya ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0f39f-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="0f39f-117">Varsa `cMap` sıfır olan depolama kapasitesini temsil ettiği `map` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0f39f-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="0f39f-118">Yöntem döndürüldüğünde `map` en çok içeren `cMap` öğeleri ve `pcMap` gerçekte yazılan cor_ıl_map değerlerin sayısını ayarlanır `map` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0f39f-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="0f39f-119">IL haline getirilmiş dolmadığından veya eşleme bir profil oluşturucu tarafından sağlanan değildi, bu yöntemi döndürür `S_OK` ve ayarlar `pcMap` 0.</span><span class="sxs-lookup"><span data-stu-id="0f39f-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f39f-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f39f-120">Requirements</span></span>  
 <span data-ttu-id="0f39f-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f39f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f39f-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f39f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f39f-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f39f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f39f-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f39f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f39f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f39f-125">See also</span></span>

- [<span data-ttu-id="0f39f-126">Icorprofilerınfo::setılınstrumentedcodemap</span><span class="sxs-lookup"><span data-stu-id="0f39f-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="0f39f-127">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f39f-127">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)
- [<span data-ttu-id="0f39f-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0f39f-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
