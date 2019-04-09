---
title: ICorProfilerCallback::ModuleUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb00a56b0d80b78867f70e64c1c9bdf0fc49e1be
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178405"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="e52e6-102">ICorProfilerCallback::ModuleUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e52e6-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="e52e6-103">Profil Oluşturucu, bir modül boşaltılıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="e52e6-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e52e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e52e6-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="e52e6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e52e6-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="e52e6-106">[in] Boşaltılıyor modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="e52e6-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e52e6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e52e6-107">Remarks</span></span>  
 <span data-ttu-id="e52e6-108">Değerini `moduleId` sonra bir bilgi isteği için geçerli değil `ModuleUnloadStarted` yöntemi — bu modül hakkında bilgi almak için profil oluşturucu son şans budur.</span><span class="sxs-lookup"><span data-stu-id="e52e6-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e52e6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e52e6-109">Requirements</span></span>  
 <span data-ttu-id="e52e6-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e52e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e52e6-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e52e6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e52e6-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e52e6-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e52e6-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e52e6-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e52e6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e52e6-114">See also</span></span>

- [<span data-ttu-id="e52e6-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e52e6-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e52e6-116">ModuleUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e52e6-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
