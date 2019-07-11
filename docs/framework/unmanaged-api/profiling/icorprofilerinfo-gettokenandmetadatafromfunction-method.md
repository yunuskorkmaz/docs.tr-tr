---
title: ICorProfilerInfo::GetTokenAndMetadataFromFunction Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b608b8818890bdb27a956a90c7987cf7c421304d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772275"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="97e9f-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="97e9f-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="97e9f-103">Meta veri belirteci ve belirteç karşı belirtilen işlev için kullanılabilecek bir meta veri arabirimi örneği alır.</span><span class="sxs-lookup"><span data-stu-id="97e9f-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e9f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97e9f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97e9f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97e9f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="97e9f-106">[in] İşlevi için meta verileri arabirimi ve meta veri belirteci almak için kimliği.</span><span class="sxs-lookup"><span data-stu-id="97e9f-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="97e9f-107">[in] Başvuru Kimliği örneğini almak meta verileri arabirimi.</span><span class="sxs-lookup"><span data-stu-id="97e9f-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="97e9f-108">[out] Belirteci karşı belirtilen işlev için kullanılabilir meta veri arabirimi örneği adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="97e9f-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="97e9f-109">[out] Belirtilen işlev için meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="97e9f-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97e9f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97e9f-110">Requirements</span></span>  
 <span data-ttu-id="97e9f-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97e9f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97e9f-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="97e9f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97e9f-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97e9f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97e9f-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97e9f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e9f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97e9f-115">See also</span></span>

- [<span data-ttu-id="97e9f-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97e9f-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
