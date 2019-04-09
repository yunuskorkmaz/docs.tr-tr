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
ms.openlocfilehash: 44595229eaefa0d8fc8ca7bf15a88d0fbf1ee0d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104318"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="a40b1-102">ICorProfilerThreadEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a40b1-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="a40b1-103">İş parçacıkları Numaralandırıcının dizideki geçerli konum başlayarak, sıralı bir koleksiyonu belirtilen bitişik iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a40b1-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a40b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a40b1-104">Syntax</span></span>  
  
```  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a40b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a40b1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a40b1-106">[in] Alınacak iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="a40b1-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="a40b1-107">[out] Bir dizi `ThreadID` değerler, her biri alınan bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a40b1-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a40b1-108">[out] Gerçekte döndürülen iş parçacığı sayısı için bir işaretçi `ids` dizisi.</span><span class="sxs-lookup"><span data-stu-id="a40b1-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a40b1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a40b1-109">Return Value</span></span>  
 <span data-ttu-id="a40b1-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="a40b1-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a40b1-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a40b1-111">HRESULT</span></span>|<span data-ttu-id="a40b1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a40b1-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a40b1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a40b1-113">S_OK</span></span>|`celt` <span data-ttu-id="a40b1-114">öğeleri döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="a40b1-114">elements were returned.</span></span>|  
|<span data-ttu-id="a40b1-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a40b1-115">S_FALSE</span></span>|<span data-ttu-id="a40b1-116">Az `celt` öğeleri döndürüldü, numaralandırma tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a40b1-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a40b1-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a40b1-117">Requirements</span></span>  
 <span data-ttu-id="a40b1-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a40b1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a40b1-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a40b1-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a40b1-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a40b1-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a40b1-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="a40b1-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a40b1-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a40b1-122">See also</span></span>

- [<span data-ttu-id="a40b1-123">ICorProfilerThreadEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a40b1-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="a40b1-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a40b1-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
