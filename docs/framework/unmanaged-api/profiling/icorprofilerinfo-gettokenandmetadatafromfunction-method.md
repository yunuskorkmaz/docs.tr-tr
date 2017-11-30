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
ms.openlocfilehash: 585b28161814045777cf2294f78bafc3229bfae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="20d7a-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="20d7a-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="20d7a-103">Meta veri simgesi ve belirteci karşı belirtilen işlevi için kullanılabilir bir meta veri arabirimi örneği alır.</span><span class="sxs-lookup"><span data-stu-id="20d7a-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20d7a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20d7a-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20d7a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20d7a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="20d7a-106">[in] İşlevi için meta veri simgesi ve meta veri arabirimi almak istediğiniz kimliği.</span><span class="sxs-lookup"><span data-stu-id="20d7a-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="20d7a-107">[in] Başvuru Kimliği örneğini almak meta veri arabirimi.</span><span class="sxs-lookup"><span data-stu-id="20d7a-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="20d7a-108">[out] Belirteci karşı belirtilen işlevi için kullanılabilir meta veri arabirim örneğinin adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20d7a-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="20d7a-109">[out] Belirtilen işlev için meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20d7a-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20d7a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20d7a-110">Requirements</span></span>  
 <span data-ttu-id="20d7a-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20d7a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20d7a-112">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="20d7a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20d7a-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20d7a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20d7a-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20d7a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d7a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20d7a-115">See Also</span></span>  
 [<span data-ttu-id="20d7a-116">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="20d7a-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
