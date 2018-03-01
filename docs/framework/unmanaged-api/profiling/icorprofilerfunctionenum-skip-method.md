---
title: "ICorProfilerFunctionEnum::Skip Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ddde6069072092cfc0441686ce4d53aa0a4bd534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="45394-102">ICorProfilerFunctionEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45394-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="45394-103">Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="45394-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45394-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45394-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45394-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45394-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="45394-106">[in] Atlanan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="45394-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45394-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="45394-107">Return Value</span></span>  
 <span data-ttu-id="45394-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="45394-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="45394-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45394-109">HRESULT</span></span>|<span data-ttu-id="45394-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45394-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45394-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="45394-111">S_OK</span></span>|<span data-ttu-id="45394-112">`celt`öğeleri atlandı.</span><span class="sxs-lookup"><span data-stu-id="45394-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="45394-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="45394-113">S_FALSE</span></span>|<span data-ttu-id="45394-114">Daha az `celt` öğeleri atlandı, daha fazla öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="45394-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45394-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45394-115">Remarks</span></span>  
 <span data-ttu-id="45394-116">Bu Numaralandırıcının imleç yeni konumunu (geçerli) konumdur + `celt`.</span><span class="sxs-lookup"><span data-stu-id="45394-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45394-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45394-117">Requirements</span></span>  
 <span data-ttu-id="45394-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45394-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45394-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45394-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45394-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45394-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45394-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45394-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45394-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45394-122">See Also</span></span>  
 [<span data-ttu-id="45394-123">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45394-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="45394-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="45394-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
