---
title: ICorProfilerInfo2::GetThreadAppDomain Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c6e596a4610052d7586978a4e770d5df60b38ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="011cf-102">ICorProfilerInfo2::GetThreadAppDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="011cf-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="011cf-103">İçinde belirtilen iş parçacığı kod şu anda yürütüyor uygulama etki alanı Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="011cf-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="011cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="011cf-104">Syntax</span></span>  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="011cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="011cf-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="011cf-106">[in] İş parçacığı belirtme kimliği.</span><span class="sxs-lookup"><span data-stu-id="011cf-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="011cf-107">[out] Uygulama etki alanı kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="011cf-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="011cf-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="011cf-108">Requirements</span></span>  
 <span data-ttu-id="011cf-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="011cf-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="011cf-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="011cf-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="011cf-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="011cf-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="011cf-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="011cf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="011cf-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="011cf-113">See Also</span></span>  
 [<span data-ttu-id="011cf-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="011cf-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="011cf-115">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="011cf-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
