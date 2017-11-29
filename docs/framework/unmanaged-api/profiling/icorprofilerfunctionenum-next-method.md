---
title: "ICorProfilerFunctionEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.Next Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6cf37beced15305de60c3f57edb701adc7379a1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="89e93-102">ICorProfilerFunctionEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89e93-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="89e93-103">Bitişik işlevleri belirtilen sayıda Numaralandırıcının geçerli konumu sırada başlayarak işlevlerin sıralı bir koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="89e93-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e93-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89e93-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89e93-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89e93-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="89e93-106">[in] Alınacak işlevleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="89e93-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="89e93-107">[out] Bir dizi `COR_PRF_FUNCTION` değerleri, her biri alınan bir işlevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="89e93-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="89e93-108">[out] Gerçekte döndürülen işlev sayısı için bir işaretçi `ids` dizi.</span><span class="sxs-lookup"><span data-stu-id="89e93-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89e93-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="89e93-109">Return Value</span></span>  
 <span data-ttu-id="89e93-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="89e93-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="89e93-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89e93-111">HRESULT</span></span>|<span data-ttu-id="89e93-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89e93-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89e93-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="89e93-113">S_OK</span></span>|<span data-ttu-id="89e93-114">`celt`öğeleri döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="89e93-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="89e93-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="89e93-115">S_FALSE</span></span>|<span data-ttu-id="89e93-116">Daha az `celt` öğeleri döndürülen numaralandırması tam olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="89e93-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89e93-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89e93-117">Requirements</span></span>  
 <span data-ttu-id="89e93-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89e93-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89e93-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="89e93-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89e93-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89e93-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89e93-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89e93-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e93-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89e93-122">See Also</span></span>  
 [<span data-ttu-id="89e93-123">Icorprofilerfunctionenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="89e93-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="89e93-124">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="89e93-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
