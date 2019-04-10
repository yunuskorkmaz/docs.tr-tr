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
ms.openlocfilehash: f26fd93d42a709249936815d3c29ae572482f427
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224630"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="479f0-102">ICorProfilerInfo::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="479f0-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="479f0-103">Şu anda belirtilen iş parçacığıyla ilişkilendirilmiş bağlam kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="479f0-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="479f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="479f0-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="479f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="479f0-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="479f0-106">[in] İş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="479f0-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="479f0-107">[out] Şu anda belirtilen iş parçacığıyla ilişkilendirilmiş bağlam Kimliğini bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="479f0-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="479f0-108">İş parçacığı kendisiyle ilişkili bir bağlam yok varsa, bu işlev CORPROF_E_DATAINCOMPLETE döndürür.</span><span class="sxs-lookup"><span data-stu-id="479f0-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="479f0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="479f0-109">Requirements</span></span>  
 <span data-ttu-id="479f0-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="479f0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="479f0-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="479f0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="479f0-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="479f0-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="479f0-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="479f0-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="479f0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="479f0-114">See also</span></span>

- [<span data-ttu-id="479f0-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="479f0-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
