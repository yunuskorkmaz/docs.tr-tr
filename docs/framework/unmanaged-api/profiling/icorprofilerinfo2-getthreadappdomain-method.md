---
title: ICorProfilerInfo2::GetThreadAppDomain Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetThreadAppDomain
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4c8e16bc3d0a886e44bded3c274e5c53b43d75ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="3feaa-102">ICorProfilerInfo2::GetThreadAppDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="3feaa-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="3feaa-103">İçinde belirtilen iş parçacığı kod şu anda yürütüyor uygulama etki alanı Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="3feaa-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3feaa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3feaa-104">Syntax</span></span>  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3feaa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3feaa-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="3feaa-106">[in] İş parçacığı belirtme kimliği.</span><span class="sxs-lookup"><span data-stu-id="3feaa-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="3feaa-107">[out] Uygulama etki alanı kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3feaa-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3feaa-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3feaa-108">Requirements</span></span>  
 <span data-ttu-id="3feaa-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3feaa-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3feaa-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3feaa-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3feaa-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3feaa-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3feaa-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3feaa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3feaa-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3feaa-113">See Also</span></span>  
 [<span data-ttu-id="3feaa-114">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="3feaa-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="3feaa-115">Icorprofilerınfo2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3feaa-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
