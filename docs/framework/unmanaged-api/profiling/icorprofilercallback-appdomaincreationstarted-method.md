---
title: ICorProfilerCallback::AppDomainCreationStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 141fd99ab0a96b20bfe06f1eb8612dd92b6cccc0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451496"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="cbe29-102">ICorProfilerCallback::AppDomainCreationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbe29-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="cbe29-103">Profil Oluşturucu uygulama etki alanı oluşturulduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="cbe29-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbe29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbe29-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbe29-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cbe29-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="cbe29-106">[in] Oluşturulan etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cbe29-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbe29-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbe29-107">Remarks</span></span>  
 <span data-ttu-id="cbe29-108">Kimliği kadar herhangi bir bilgi istek için geçerli değil [Icorprofilercallback::appdomaincreationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cbe29-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbe29-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbe29-109">Requirements</span></span>  
 <span data-ttu-id="cbe29-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbe29-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbe29-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cbe29-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cbe29-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbe29-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbe29-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbe29-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe29-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbe29-114">See Also</span></span>  
 [<span data-ttu-id="cbe29-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbe29-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
