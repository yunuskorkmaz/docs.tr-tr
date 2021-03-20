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
ms.openlocfilehash: b21b8ad10c76b2e9eaad773315122c3635845a78
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760255"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="12812-103">ICorProfilerInfo::GetFunctionFromIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12812-103">ICorProfilerInfo::GetFunctionFromIP Method</span></span>

<span data-ttu-id="12812-104">Yönetilen bir kod yönerge işaretçisini bir ile eşler `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="12812-104">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12812-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12812-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12812-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12812-106">Parameters</span></span>

<span data-ttu-id="12812-107">`ip` 'ndaki Yönetilen koddaki yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="12812-107">`ip` [in] The instruction pointer in managed code.</span></span>

<span data-ttu-id="12812-108">`pFunctionId` dışı Döndürülen işlev KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="12812-108">`pFunctionId` [out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="12812-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12812-109">Requirements</span></span>  

 <span data-ttu-id="12812-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12812-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12812-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="12812-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12812-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="12812-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12812-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12812-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12812-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12812-114">See also</span></span>

- [<span data-ttu-id="12812-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12812-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
