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
ms.openlocfilehash: 1cc05f4c10f4a5b042ff14c05f3c85a7b5935184
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497900"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="fd6ef-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="fd6ef-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="fd6ef-103">Belirtilen işlev için belirtece karşı kullanılabilecek meta veri belirtecini ve bir meta veri arabirim örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="fd6ef-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd6ef-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fd6ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd6ef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd6ef-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="fd6ef-106">'ndaki Meta veri belirtecinin ve meta veri arabiriminin alınacağı işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="fd6ef-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="fd6ef-107">'ndaki Örneğini almak için meta veri arabiriminin başvuru Kımlığı.</span><span class="sxs-lookup"><span data-stu-id="fd6ef-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="fd6ef-108">dışı Belirtilen işlev için belirtece karşı kullanılabilecek meta veri arabirimi örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fd6ef-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="fd6ef-109">dışı Belirtilen işlev için meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fd6ef-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd6ef-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd6ef-110">Requirements</span></span>  
 <span data-ttu-id="fd6ef-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd6ef-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd6ef-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fd6ef-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd6ef-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fd6ef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd6ef-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd6ef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6ef-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd6ef-115">See also</span></span>

- [<span data-ttu-id="fd6ef-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd6ef-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
