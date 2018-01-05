---
title: ICorProfilerInfo::GetTokenAndMetadataFromFunction Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33522d55383b1137d8591c74c988903655eba5f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="a163a-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="a163a-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="a163a-103">Meta veri simgesi ve belirteci karşı belirtilen işlevi için kullanılabilir bir meta veri arabirimi örneği alır.</span><span class="sxs-lookup"><span data-stu-id="a163a-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a163a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a163a-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a163a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a163a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a163a-106">[in] İşlevi için meta veri simgesi ve meta veri arabirimi almak istediğiniz kimliği.</span><span class="sxs-lookup"><span data-stu-id="a163a-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="a163a-107">[in] Başvuru Kimliği örneğini almak meta veri arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a163a-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="a163a-108">[out] Belirteci karşı belirtilen işlevi için kullanılabilir meta veri arabirim örneğinin adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a163a-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="a163a-109">[out] Belirtilen işlev için meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a163a-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a163a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a163a-110">Requirements</span></span>  
 <span data-ttu-id="a163a-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a163a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a163a-112">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a163a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a163a-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a163a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a163a-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a163a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a163a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a163a-115">See Also</span></span>  
 [<span data-ttu-id="a163a-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a163a-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
