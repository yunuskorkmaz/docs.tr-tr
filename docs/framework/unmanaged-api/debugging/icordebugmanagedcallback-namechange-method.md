---
title: "ICorDebugManagedCallback::NameChange Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 31539413597c65b553794f07b1eeecdf3943f908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="2aca6-102">ICorDebugManagedCallback::NameChange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2aca6-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="2aca6-103">Hata ayıklayıcı uygulama etki alanı veya bir iş parçacığı adı değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="2aca6-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aca6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2aca6-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2aca6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2aca6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="2aca6-106">[in] Icordebugappdomain nesneye ya da ad değişikliği ya da sahip uygulama etki alanını gösteren bir işaretçi bir ad değişikliği sahip iş parçacığı içerir.</span><span class="sxs-lookup"><span data-stu-id="2aca6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="2aca6-107">[in] Bir işaretçi Icordebugthread nesneye bir ad değişikliği sahip iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2aca6-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aca6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2aca6-108">Requirements</span></span>  
 <span data-ttu-id="2aca6-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2aca6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aca6-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2aca6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2aca6-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2aca6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2aca6-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aca6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aca6-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2aca6-113">See Also</span></span>  
 [<span data-ttu-id="2aca6-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2aca6-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
