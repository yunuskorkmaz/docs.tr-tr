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
ms.openlocfilehash: c509606995a0ddb00a8b586ce8b8cd54b7694cd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452516"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="5d704-102">ICorProfilerCallback::ModuleUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d704-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="5d704-103">Profil Oluşturucu modülü yüklenmemiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="5d704-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d704-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d704-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d704-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d704-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="5d704-106">[in] Boşaltılıyor modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="5d704-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d704-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d704-107">Remarks</span></span>  
 <span data-ttu-id="5d704-108">Değeri `moduleId` sonra bir bilgi isteği için geçerli değil `ModuleUnloadStarted` yöntemi döndürür — bu modül hakkında bilgi almak için Profil Oluşturucu'nın son fırsat budur.</span><span class="sxs-lookup"><span data-stu-id="5d704-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d704-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d704-109">Requirements</span></span>  
 <span data-ttu-id="5d704-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d704-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d704-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d704-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d704-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d704-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d704-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d704-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d704-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d704-114">See Also</span></span>  
 [<span data-ttu-id="5d704-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d704-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="5d704-116">ModuleUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d704-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
