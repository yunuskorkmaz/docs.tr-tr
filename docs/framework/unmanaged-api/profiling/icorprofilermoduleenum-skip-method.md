---
title: "ICorProfilerModuleEnum::Skip Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Skip Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7331c5221de1dc1bfdbbce77f8c40f4fbc95aea2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="ddbab-102">ICorProfilerModuleEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ddbab-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="ddbab-103">Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="ddbab-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddbab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddbab-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddbab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ddbab-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ddbab-106">[in] Atlanan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="ddbab-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddbab-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ddbab-107">Return Value</span></span>  
 <span data-ttu-id="ddbab-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="ddbab-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ddbab-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ddbab-109">HRESULT</span></span>|<span data-ttu-id="ddbab-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddbab-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ddbab-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ddbab-111">S_OK</span></span>|<span data-ttu-id="ddbab-112">`celt`öğeleri atlandı.</span><span class="sxs-lookup"><span data-stu-id="ddbab-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="ddbab-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ddbab-113">S_FALSE</span></span>|<span data-ttu-id="ddbab-114">Daha az `celt` öğeleri atlandı, daha fazla öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ddbab-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddbab-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ddbab-115">Remarks</span></span>  
 <span data-ttu-id="ddbab-116">Bu Numaralandırıcının imleç yeni konumunu (geçerli) konumdur + `celt`.</span><span class="sxs-lookup"><span data-stu-id="ddbab-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddbab-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ddbab-117">Requirements</span></span>  
 <span data-ttu-id="ddbab-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddbab-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddbab-119">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ddbab-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ddbab-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddbab-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddbab-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddbab-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddbab-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ddbab-122">See Also</span></span>  
 [<span data-ttu-id="ddbab-123">Icorprofilermoduleenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="ddbab-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="ddbab-124">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ddbab-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
