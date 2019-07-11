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
ms.openlocfilehash: a9d1cf182eaf6f245baa5d898bac3ca7d3190234
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763097"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="d24f8-102">Icorprofilercallback::appdomainshutdownstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="d24f8-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="d24f8-103">Profil Oluşturucu, bir uygulama etki alanı bir işlemden boşaltılıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="d24f8-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d24f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d24f8-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d24f8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d24f8-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="d24f8-106">[in] Uygulamanın derlemelerin saklandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d24f8-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d24f8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d24f8-107">Remarks</span></span>  
 <span data-ttu-id="d24f8-108">Değerini `appDomainId` sonra herhangi bir bilgi isteği için geçerli değil `AppDomainShutdownStarted` yöntemi döndürür; bu uygulama etki alanı hakkında bilgi almak için profil oluşturucunun son şans budur.</span><span class="sxs-lookup"><span data-stu-id="d24f8-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d24f8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d24f8-109">Requirements</span></span>  
 <span data-ttu-id="d24f8-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d24f8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d24f8-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d24f8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d24f8-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d24f8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d24f8-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d24f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d24f8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d24f8-114">See also</span></span>

- [<span data-ttu-id="d24f8-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d24f8-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
