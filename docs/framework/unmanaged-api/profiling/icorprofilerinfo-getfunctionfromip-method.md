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
ms.openlocfilehash: 14b152474cd71dc3ff7b59c94b6ec4fa0cd7ce0c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439200"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="ba039-102">ICorProfilerInfo::GetFunctionFromIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba039-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="ba039-103">Yönetilen bir kod yönerge işaretçisini `FunctionID`eşler.</span><span class="sxs-lookup"><span data-stu-id="ba039-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba039-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba039-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba039-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba039-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="ba039-106">'ndaki Yönetilen koddaki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ba039-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="ba039-107">dışı Döndürülen işlev KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="ba039-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba039-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba039-108">Requirements</span></span>  
 <span data-ttu-id="ba039-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba039-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba039-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ba039-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ba039-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ba039-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba039-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba039-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba039-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba039-113">See also</span></span>

- [<span data-ttu-id="ba039-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba039-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
