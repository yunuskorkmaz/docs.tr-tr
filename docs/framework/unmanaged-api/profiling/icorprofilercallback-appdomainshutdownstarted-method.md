---
title: 'ICorProfilerCallback:: AppDomainShutdownStarted Yöntemi'
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
ms.openlocfilehash: d280b008b34befce04159d02dfbb3de37b262c3c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866671"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="f2f87-102">ICorProfilerCallback:: AppDomainShutdownStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2f87-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="f2f87-103">Profil Oluşturucu bir uygulama etki alanının bir işlemden kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="f2f87-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2f87-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2f87-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2f87-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="f2f87-106">\[içinde], uygulamanın derlemelerinin depolandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2f87-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2f87-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2f87-107">Remarks</span></span>  
 <span data-ttu-id="f2f87-108">`appDomainId` değeri `AppDomainShutdownStarted` yöntemi çağrıldıktan sonra herhangi bir bilgi isteği için geçerli değildir — bu, profil oluşturucunun bu uygulama etki alanı hakkında bilgi almak için son şansınız olur.</span><span class="sxs-lookup"><span data-stu-id="f2f87-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2f87-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2f87-109">Requirements</span></span>  
 <span data-ttu-id="f2f87-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2f87-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2f87-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f2f87-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2f87-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f2f87-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2f87-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2f87-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f87-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2f87-114">See also</span></span>

- [<span data-ttu-id="f2f87-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2f87-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
