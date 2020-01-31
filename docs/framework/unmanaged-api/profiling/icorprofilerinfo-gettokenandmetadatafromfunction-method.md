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
ms.openlocfilehash: d924dbf21a0f0b046c8d8f8f294e91bc5ff6c015
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869430"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="7d8a1-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="7d8a1-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="7d8a1-103">Belirtilen işlev için belirtece karşı kullanılabilecek meta veri belirtecini ve bir meta veri arabirim örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="7d8a1-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d8a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d8a1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d8a1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d8a1-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7d8a1-106">'ndaki Meta veri belirtecinin ve meta veri arabiriminin alınacağı işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="7d8a1-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="7d8a1-107">'ndaki Örneğini almak için meta veri arabiriminin başvuru Kımlığı.</span><span class="sxs-lookup"><span data-stu-id="7d8a1-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="7d8a1-108">dışı Belirtilen işlev için belirtece karşı kullanılabilecek meta veri arabirimi örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d8a1-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="7d8a1-109">dışı Belirtilen işlev için meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d8a1-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d8a1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d8a1-110">Requirements</span></span>  
 <span data-ttu-id="7d8a1-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d8a1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d8a1-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7d8a1-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7d8a1-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7d8a1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d8a1-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d8a1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d8a1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d8a1-115">See also</span></span>

- [<span data-ttu-id="7d8a1-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d8a1-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
