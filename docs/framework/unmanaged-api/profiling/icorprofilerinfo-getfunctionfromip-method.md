---
title: ICorProfilerInfo::GetFunctionFromIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9fec1d1effbf900974327247078b65f60fef7e21
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466433"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="2e124-102">ICorProfilerInfo::GetFunctionFromIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e124-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="2e124-103">Yönetilen kod yönerge işaretçisi eşleyen bir `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="2e124-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e124-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e124-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e124-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e124-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="2e124-106">[in] Yönetilen kodda yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2e124-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="2e124-107">[out] Döndürülen işlevin kimliği.</span><span class="sxs-lookup"><span data-stu-id="2e124-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e124-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e124-108">Requirements</span></span>  
 <span data-ttu-id="2e124-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e124-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e124-110">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2e124-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e124-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e124-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e124-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e124-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e124-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e124-113">See also</span></span>
- [<span data-ttu-id="2e124-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e124-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
