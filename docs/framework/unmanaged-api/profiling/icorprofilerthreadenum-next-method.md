---
title: ICorProfilerThreadEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a014a4e06464f461af25103037b349b2f18a2a5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488714"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="73247-102">ICorProfilerThreadEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73247-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="73247-103">İş parçacıkları Numaralandırıcının dizideki geçerli konum başlayarak, sıralı bir koleksiyonu belirtilen bitişik iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="73247-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73247-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73247-104">Syntax</span></span>  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73247-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73247-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="73247-106">[in] Alınacak iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="73247-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="73247-107">[out] Bir dizi `ThreadID` değerler, her biri alınan bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73247-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="73247-108">[out] Gerçekte döndürülen iş parçacığı sayısı için bir işaretçi `ids` dizisi.</span><span class="sxs-lookup"><span data-stu-id="73247-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73247-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="73247-109">Return Value</span></span>  
 <span data-ttu-id="73247-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="73247-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="73247-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73247-111">HRESULT</span></span>|<span data-ttu-id="73247-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73247-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73247-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="73247-113">S_OK</span></span>|<span data-ttu-id="73247-114">`celt` öğeleri döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="73247-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="73247-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="73247-115">S_FALSE</span></span>|<span data-ttu-id="73247-116">Az `celt` öğeleri döndürüldü, numaralandırma tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="73247-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73247-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73247-117">Requirements</span></span>  
 <span data-ttu-id="73247-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73247-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73247-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73247-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73247-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73247-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73247-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73247-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73247-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73247-122">See also</span></span>
- [<span data-ttu-id="73247-123">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73247-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="73247-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="73247-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
