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
ms.openlocfilehash: b3e14230888e9bf846879d5728c2b20883fb8d53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438733"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="bf838-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="bf838-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="bf838-103">Belirtilen işlev için belirtece karşı kullanılabilecek meta veri belirtecini ve bir meta veri arabirim örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="bf838-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf838-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf838-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf838-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf838-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="bf838-106">'ndaki Meta veri belirtecinin ve meta veri arabiriminin alınacağı işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bf838-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="bf838-107">'ndaki Örneğini almak için meta veri arabiriminin başvuru Kımlığı.</span><span class="sxs-lookup"><span data-stu-id="bf838-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="bf838-108">dışı Belirtilen işlev için belirtece karşı kullanılabilecek meta veri arabirimi örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bf838-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="bf838-109">dışı Belirtilen işlev için meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bf838-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf838-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf838-110">Requirements</span></span>  
 <span data-ttu-id="bf838-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf838-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf838-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bf838-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf838-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bf838-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf838-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf838-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf838-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf838-115">See also</span></span>

- [<span data-ttu-id="bf838-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf838-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
