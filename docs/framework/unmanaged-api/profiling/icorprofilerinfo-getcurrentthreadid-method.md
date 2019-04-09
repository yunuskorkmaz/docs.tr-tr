---
title: ICorProfilerInfo::GetCurrentThreadID Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 802072f3a0151aabc5ca5796df57ea7c694a2070
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179042"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="beb13-102">ICorProfilerInfo::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="beb13-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="beb13-103">Yönetilen iş parçacığı ise, geçerli iş parçacığı Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="beb13-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb13-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="beb13-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beb13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="beb13-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="beb13-106">[out] Yönetilen iş parçacığı döndürülen kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="beb13-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beb13-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="beb13-107">Remarks</span></span>  
 <span data-ttu-id="beb13-108">Geçerli iş parçacığı bir iç çalışma zamanı iş parçacığı veya diğer yönetilmeyen iş parçacığı ise `GetCurrentThreadID` CORPROF_E_NOT_MANAGED_THREAD HRESULT ve döndürülen değeri döndürür `pThreadId` parametresi null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="beb13-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beb13-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="beb13-109">Requirements</span></span>  
 <span data-ttu-id="beb13-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="beb13-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beb13-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="beb13-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="beb13-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="beb13-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="beb13-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="beb13-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="beb13-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="beb13-114">See also</span></span>

- [<span data-ttu-id="beb13-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="beb13-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
