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
ms.openlocfilehash: fd1e5daada8793e94980afc5f0cf509915bd288e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450935"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="6f7fa-102">ICorProfilerCallback::AppDomainShutdownStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f7fa-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="6f7fa-103">Profil Oluşturucu uygulama etki alanı bir işlemden yüklenmemiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="6f7fa-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f7fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f7fa-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f7fa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f7fa-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="6f7fa-106">[in] Uygulamanın derlemelerini depolandığı etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f7fa-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f7fa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f7fa-107">Remarks</span></span>  
 <span data-ttu-id="6f7fa-108">Değeri `appDomainId` sonra herhangi bir bilgi istek için geçerli değil `AppDomainShutdownStarted` yöntemi döndürür — bu bu uygulama etki alanı hakkında bilgi almak için Profil Oluşturucu'nın son şansınızdır.</span><span class="sxs-lookup"><span data-stu-id="6f7fa-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f7fa-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f7fa-109">Requirements</span></span>  
 <span data-ttu-id="6f7fa-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f7fa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f7fa-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f7fa-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f7fa-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f7fa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f7fa-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f7fa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7fa-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f7fa-114">See Also</span></span>  
 [<span data-ttu-id="6f7fa-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f7fa-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
