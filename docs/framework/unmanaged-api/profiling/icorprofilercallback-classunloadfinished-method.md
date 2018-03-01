---
title: "ICorProfilerCallback::ClassUnloadFinished Yöntemi"
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
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9801113e23474fa0aae461d356e4aa57a203bd6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="e898b-102">ICorProfilerCallback::ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e898b-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="e898b-103">Profil Oluşturucu bir sınıf kaldırılması tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="e898b-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e898b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e898b-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e898b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e898b-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e898b-106">[in] Kaldırıldı sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e898b-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="e898b-107">[in] Sınıf başarıyla kaldırıldı olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="e898b-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e898b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e898b-108">Remarks</span></span>  
 <span data-ttu-id="e898b-109">Sınıf kaldırılması, bazı bölümleri sonra devam edebilir `ClassUnloadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="e898b-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="e898b-110">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="e898b-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="e898b-111">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk sınıfı kaldırılması parçası başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e898b-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e898b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e898b-112">Requirements</span></span>  
 <span data-ttu-id="e898b-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e898b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e898b-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e898b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e898b-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e898b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e898b-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e898b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e898b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e898b-117">See Also</span></span>  
 [<span data-ttu-id="e898b-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e898b-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="e898b-119">ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e898b-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
