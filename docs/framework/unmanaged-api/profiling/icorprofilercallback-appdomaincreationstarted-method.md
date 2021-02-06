---
description: ': ICorProfilerCallback:: AppDomainCreationStarted yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 00ebbe35f6f4446caeee5ebcd56b853d6e6dc80c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648265"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="06263-103">ICorProfilerCallback::AppDomainCreationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06263-103">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>

<span data-ttu-id="06263-104">Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="06263-104">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06263-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06263-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06263-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06263-106">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="06263-107">\[' de] oluşturulmakta olan etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06263-107">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="06263-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06263-108">Remarks</span></span>  

 <span data-ttu-id="06263-109">ID, [ICorProfilerCallback:: AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) yöntemi çağrılana kadar herhangi bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="06263-109">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06263-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06263-110">Requirements</span></span>  

 <span data-ttu-id="06263-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06263-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06263-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="06263-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06263-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="06263-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06263-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06263-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06263-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06263-115">See also</span></span>

- [<span data-ttu-id="06263-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06263-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
