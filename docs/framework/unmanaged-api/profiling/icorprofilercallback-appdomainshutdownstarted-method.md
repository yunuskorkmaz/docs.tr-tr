---
title: ICorProfilerCallback::AppDomainShutdownStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 174ac8b66c8127c16398de442a7067b742ab58ab
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465575"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="d909a-102">ICorProfilerCallback::AppDomainShutdownStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d909a-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="d909a-103">Profil Oluşturucu, bir uygulama etki alanı bir işlemden boşaltılıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="d909a-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d909a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d909a-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d909a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d909a-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="d909a-106">[in] Uygulamanın derlemelerin saklandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d909a-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d909a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d909a-107">Remarks</span></span>  
 <span data-ttu-id="d909a-108">Değerini `appDomainId` sonra herhangi bir bilgi isteği için geçerli değil `AppDomainShutdownStarted` yöntemi döndürür; bu uygulama etki alanı hakkında bilgi almak için profil oluşturucunun son şans budur.</span><span class="sxs-lookup"><span data-stu-id="d909a-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d909a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d909a-109">Requirements</span></span>  
 <span data-ttu-id="d909a-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d909a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d909a-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d909a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d909a-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d909a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d909a-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d909a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d909a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d909a-114">See also</span></span>
- [<span data-ttu-id="d909a-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d909a-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
