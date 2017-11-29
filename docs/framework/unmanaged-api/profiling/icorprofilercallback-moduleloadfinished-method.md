---
title: "ICorProfilerCallback::ModuleLoadFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22533187da02d34ac2990f351b13bd892a760620
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="1fcee-102">ICorProfilerCallback::ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fcee-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="1fcee-103">Profil Oluşturucu bir modül yüklenmesini tamamladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="1fcee-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fcee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1fcee-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fcee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1fcee-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1fcee-106">[in] Yükleme Tamamlandı modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="1fcee-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="1fcee-107">[in] Modül başarıyla yüklü olup olmadığını belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1fcee-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fcee-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1fcee-108">Remarks</span></span>  
 <span data-ttu-id="1fcee-109">Değeri `moduleId` kadar bilgi isteği için geçerli değil `ModuleLoadFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1fcee-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="1fcee-110">Modül yükleme bazı bölümleri sonra devam edebilir `ModuleLoadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="1fcee-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="1fcee-111">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="1fcee-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="1fcee-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk bölümü modülü yükleme başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1fcee-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fcee-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fcee-113">Requirements</span></span>  
 <span data-ttu-id="1fcee-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fcee-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fcee-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1fcee-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1fcee-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fcee-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fcee-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fcee-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fcee-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1fcee-118">See Also</span></span>  
 [<span data-ttu-id="1fcee-119">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="1fcee-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="1fcee-120">ModuleLoadStarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fcee-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
