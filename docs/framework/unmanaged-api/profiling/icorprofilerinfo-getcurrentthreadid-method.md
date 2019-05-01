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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041216"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="32ba1-102">ICorProfilerInfo::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="32ba1-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="32ba1-103">Yönetilen iş parçacığı ise, geçerli iş parçacığı Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="32ba1-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ba1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32ba1-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32ba1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32ba1-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="32ba1-106">[out] Yönetilen iş parçacığı döndürülen kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="32ba1-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32ba1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32ba1-107">Remarks</span></span>  
 <span data-ttu-id="32ba1-108">Geçerli iş parçacığı bir iç çalışma zamanı iş parçacığı veya diğer yönetilmeyen iş parçacığı ise `GetCurrentThreadID` CORPROF_E_NOT_MANAGED_THREAD HRESULT ve döndürülen değeri döndürür `pThreadId` parametresi null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="32ba1-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32ba1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32ba1-109">Requirements</span></span>  
 <span data-ttu-id="32ba1-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32ba1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32ba1-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32ba1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32ba1-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32ba1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32ba1-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32ba1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ba1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32ba1-114">See also</span></span>

- [<span data-ttu-id="32ba1-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32ba1-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
