---
title: ICorProfilerInfo2::GetThreadAppDomain Metodu
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 690dbb5659ce991b7c4921fbd85c246da54eff0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453047"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="088b8-102">ICorProfilerInfo2::GetThreadAppDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="088b8-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="088b8-103">İçinde belirtilen iş parçacığı kod şu anda yürütüyor uygulama etki alanı Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="088b8-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="088b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="088b8-104">Syntax</span></span>  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="088b8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="088b8-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="088b8-106">[in] İş parçacığı belirtme kimliği.</span><span class="sxs-lookup"><span data-stu-id="088b8-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="088b8-107">[out] Uygulama etki alanı kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="088b8-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="088b8-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="088b8-108">Requirements</span></span>  
 <span data-ttu-id="088b8-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="088b8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="088b8-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="088b8-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="088b8-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="088b8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="088b8-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="088b8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="088b8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="088b8-113">See Also</span></span>  
 [<span data-ttu-id="088b8-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="088b8-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="088b8-115">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="088b8-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
