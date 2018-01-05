---
title: "ICorProfilerCallback::ModuleUnloadFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f9f048d60d2d463e3d846fadda91932a9a2a091
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="3ef9e-102">ICorProfilerCallback::ModuleUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ef9e-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="3ef9e-103">Profil Oluşturucu bir modül kaldırılması tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="3ef9e-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ef9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ef9e-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ef9e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ef9e-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="3ef9e-106">[in] Kaldırıldı modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="3ef9e-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="3ef9e-107">[in] Modül başarıyla kaldırıldı olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="3ef9e-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ef9e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ef9e-108">Remarks</span></span>  
 <span data-ttu-id="3ef9e-109">Değeri `moduleId` sonra bir bilgi isteği için geçerli değil [Icorprofilercallback::moduleunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ef9e-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="3ef9e-110">Sınıf kaldırılması, bazı bölümleri sonra devam edebilir `ModuleUnloadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="3ef9e-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="3ef9e-111">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ef9e-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="3ef9e-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk modülü kaldırılması parçası başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ef9e-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ef9e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ef9e-113">Requirements</span></span>  
 <span data-ttu-id="3ef9e-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ef9e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ef9e-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3ef9e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ef9e-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ef9e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ef9e-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ef9e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef9e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ef9e-118">See Also</span></span>  
 [<span data-ttu-id="3ef9e-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ef9e-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
