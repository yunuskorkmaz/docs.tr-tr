---
title: "ICorProfilerThreadEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Next
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfefb140b49a606487f1fe2bbdfb8c6a3b5c6fc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="a9046-102">ICorProfilerThreadEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9046-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="a9046-103">İş parçacığı, Numaralandırıcının geçerli konumu sırada başlayarak sıralı bir koleksiyonu belirtilen bitişik iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a9046-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9046-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9046-104">Syntax</span></span>  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9046-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9046-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a9046-106">[in] Almak için iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="a9046-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="a9046-107">[out] Bir dizi `ThreadID` değerleri, her biri alınan bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a9046-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a9046-108">[out] Gerçekte döndürülen iş parçacığı sayısını gösteren bir işaretçi `ids` dizi.</span><span class="sxs-lookup"><span data-stu-id="a9046-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9046-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9046-109">Return Value</span></span>  
 <span data-ttu-id="a9046-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="a9046-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a9046-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9046-111">HRESULT</span></span>|<span data-ttu-id="a9046-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9046-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9046-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9046-113">S_OK</span></span>|<span data-ttu-id="a9046-114">`celt`öğeleri döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="a9046-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="a9046-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a9046-115">S_FALSE</span></span>|<span data-ttu-id="a9046-116">Daha az `celt` öğeleri döndürülen numaralandırması tam olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9046-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9046-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9046-117">Requirements</span></span>  
 <span data-ttu-id="a9046-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9046-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9046-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a9046-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9046-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9046-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9046-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9046-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9046-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9046-122">See Also</span></span>  
 [<span data-ttu-id="a9046-123">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9046-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="a9046-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a9046-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
