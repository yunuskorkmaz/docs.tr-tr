---
title: ICorProfilerFunctionEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62e70a2fe421651aac9a4921ca885c53c864c4f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101809"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="ce222-102">ICorProfilerFunctionEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce222-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="ce222-103">Belirtilen bitişik işlev sayısı dizideki geçerli konum Numaralandırıcının başlayan İşlevler, sıralı bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="ce222-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce222-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce222-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce222-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ce222-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ce222-106">[in] Alınacak işlev sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce222-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="ce222-107">[out] Bir dizi `COR_PRF_FUNCTION` değerler, her biri alınan bir işlevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ce222-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ce222-108">[out] Gerçekte döndürülen işlev sayısı için bir işaretçi `ids` dizisi.</span><span class="sxs-lookup"><span data-stu-id="ce222-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce222-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ce222-109">Return Value</span></span>  
 <span data-ttu-id="ce222-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="ce222-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ce222-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce222-111">HRESULT</span></span>|<span data-ttu-id="ce222-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce222-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce222-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce222-113">S_OK</span></span>|`celt` <span data-ttu-id="ce222-114">öğeleri döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="ce222-114">elements were returned.</span></span>|  
|<span data-ttu-id="ce222-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ce222-115">S_FALSE</span></span>|<span data-ttu-id="ce222-116">Az `celt` öğeleri döndürüldü, numaralandırma tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce222-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce222-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce222-117">Requirements</span></span>  
 <span data-ttu-id="ce222-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce222-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce222-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce222-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce222-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce222-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ce222-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ce222-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ce222-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce222-122">See also</span></span>

- [<span data-ttu-id="ce222-123">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce222-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="ce222-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ce222-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
