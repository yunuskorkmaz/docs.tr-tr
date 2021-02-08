---
description: ': ICorProfilerInfo:: GetTokenAndMetadataFromFunction yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0cea6564df15c7a7f4c46097714cc0956002599b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783852"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="7cdce-103">ICorProfilerInfo::GetTokenAndMetadataFromFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="7cdce-103">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>

<span data-ttu-id="7cdce-104">Belirtilen işlev için belirtece karşı kullanılabilecek meta veri belirtecini ve bir meta veri arabirim örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="7cdce-104">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cdce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cdce-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cdce-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cdce-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="7cdce-107">'ndaki Meta veri belirtecinin ve meta veri arabiriminin alınacağı işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="7cdce-107">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="7cdce-108">'ndaki Örneğini almak için meta veri arabiriminin başvuru Kımlığı.</span><span class="sxs-lookup"><span data-stu-id="7cdce-108">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="7cdce-109">dışı Belirtilen işlev için belirtece karşı kullanılabilecek meta veri arabirimi örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7cdce-109">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="7cdce-110">dışı Belirtilen işlev için meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7cdce-110">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cdce-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cdce-111">Requirements</span></span>  

 <span data-ttu-id="7cdce-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cdce-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cdce-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7cdce-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cdce-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7cdce-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cdce-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cdce-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cdce-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cdce-116">See also</span></span>

- [<span data-ttu-id="7cdce-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7cdce-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
