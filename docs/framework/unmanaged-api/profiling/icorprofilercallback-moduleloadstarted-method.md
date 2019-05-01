---
title: ICorProfilerCallback::ModuleLoadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3503aa1eb86246365e31f52313893ad8713f5748
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992192"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="9b9be-102">ICorProfilerCallback::ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b9be-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="9b9be-103">Profil Oluşturucu, bir modül yüklenmekte olduğuna dair bildirir.</span><span class="sxs-lookup"><span data-stu-id="9b9be-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b9be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b9be-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b9be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b9be-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="9b9be-106">[in] Yüklenmekte modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="9b9be-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b9be-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b9be-107">Remarks</span></span>  
 <span data-ttu-id="9b9be-108">Değerini `moduleId` kadar bir bilgi isteği için geçerli değil [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9b9be-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b9be-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b9be-109">Requirements</span></span>  
 <span data-ttu-id="9b9be-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b9be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b9be-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b9be-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b9be-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b9be-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b9be-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b9be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b9be-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b9be-114">See also</span></span>

- [<span data-ttu-id="9b9be-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b9be-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
