---
description: ': ICorProfilerInfo:: GetFunctionFromIP yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1acea6943e74e65e4359c7da590d3888736dbd6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647602"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="f940e-103">ICorProfilerInfo::GetFunctionFromIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f940e-103">ICorProfilerInfo::GetFunctionFromIP Method</span></span>

<span data-ttu-id="f940e-104">Yönetilen bir kod yönerge işaretçisini bir ile eşler `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="f940e-104">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f940e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f940e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f940e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f940e-106">Parameters</span></span>

- `ip`

  <span data-ttu-id="f940e-107">\[' de] Yönetilen koddaki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f940e-107">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="f940e-108">\[out] döndürülen işlev KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f940e-108">\[out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="f940e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f940e-109">Requirements</span></span>  

 <span data-ttu-id="f940e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f940e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f940e-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f940e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f940e-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f940e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f940e-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f940e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f940e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f940e-114">See also</span></span>

- [<span data-ttu-id="f940e-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f940e-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
