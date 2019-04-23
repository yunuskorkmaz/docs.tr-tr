---
title: Icorprofilercallback::appdomainshutdownstarted yöntemi
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
ms.openlocfilehash: f422e99a5f6a4153368304ff0b33bbc55381575a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177118"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="66e5b-102">Icorprofilercallback::appdomainshutdownstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="66e5b-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="66e5b-103">Profil Oluşturucu, bir uygulama etki alanı bir işlemden boşaltılıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="66e5b-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66e5b-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66e5b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66e5b-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="66e5b-106">[in] Uygulamanın derlemelerin saklandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66e5b-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66e5b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66e5b-107">Remarks</span></span>  
 <span data-ttu-id="66e5b-108">Değerini `appDomainId` sonra herhangi bir bilgi isteği için geçerli değil `AppDomainShutdownStarted` yöntemi döndürür; bu uygulama etki alanı hakkında bilgi almak için profil oluşturucunun son şans budur.</span><span class="sxs-lookup"><span data-stu-id="66e5b-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e5b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66e5b-109">Requirements</span></span>  
 <span data-ttu-id="66e5b-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66e5b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66e5b-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66e5b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66e5b-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66e5b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66e5b-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66e5b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e5b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66e5b-114">See also</span></span>

- [<span data-ttu-id="66e5b-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66e5b-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
