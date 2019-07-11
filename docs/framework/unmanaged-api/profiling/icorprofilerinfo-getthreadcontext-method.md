---
title: ICorProfilerInfo::GetThreadContext Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b8afe10563d61e3ddab93e8d1b57eee4b6765c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766839"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="b5da5-102">ICorProfilerInfo::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="b5da5-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="b5da5-103">Şu anda belirtilen iş parçacığıyla ilişkilendirilmiş bağlam kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="b5da5-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5da5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5da5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5da5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5da5-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="b5da5-106">[in] İş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5da5-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="b5da5-107">[out] Şu anda belirtilen iş parçacığıyla ilişkilendirilmiş bağlam Kimliğini bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b5da5-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="b5da5-108">İş parçacığı kendisiyle ilişkili bir bağlam yok varsa, bu işlev CORPROF_E_DATAINCOMPLETE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b5da5-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5da5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5da5-109">Requirements</span></span>  
 <span data-ttu-id="b5da5-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5da5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5da5-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b5da5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5da5-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5da5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5da5-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5da5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5da5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5da5-114">See also</span></span>

- [<span data-ttu-id="b5da5-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5da5-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
