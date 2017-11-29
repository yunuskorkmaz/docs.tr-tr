---
title: "ICorProfilerCallback::ModuleLoadStarted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleLoadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ad525b44169a85e61140c9e2a8d83c967945b2f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="89947-102">ICorProfilerCallback::ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89947-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="89947-103">Profil Oluşturucu bir modül yüklendiği bildirir.</span><span class="sxs-lookup"><span data-stu-id="89947-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89947-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89947-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89947-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89947-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="89947-106">[in] Yüklenmekte modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="89947-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89947-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89947-107">Remarks</span></span>  
 <span data-ttu-id="89947-108">Değeri `moduleId` kadar bilgi isteği için geçerli değil [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="89947-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89947-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89947-109">Requirements</span></span>  
 <span data-ttu-id="89947-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89947-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89947-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="89947-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89947-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89947-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89947-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89947-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89947-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89947-114">See Also</span></span>  
 [<span data-ttu-id="89947-115">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="89947-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
