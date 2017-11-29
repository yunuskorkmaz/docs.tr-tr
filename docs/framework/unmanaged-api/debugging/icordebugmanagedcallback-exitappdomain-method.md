---
title: "ICorDebugManagedCallback::ExitAppDomain Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ExitAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07f76d8add6c8b0e44eba241b7787b8e8a2de570
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="84b86-102">ICorDebugManagedCallback::ExitAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84b86-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="84b86-103">Hata ayıklayıcı uygulama etki alanı yaptı bildirir.</span><span class="sxs-lookup"><span data-stu-id="84b86-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84b86-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84b86-104">Syntax</span></span>  
  
```  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84b86-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84b86-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="84b86-106">[in] Bir işaretçi Icordebugprocess nesneye verilen uygulama etki alanını içeren işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="84b86-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="84b86-107">[in] Bir işaretçi Icordebugappdomain nesneye yaptı uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="84b86-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84b86-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84b86-108">Requirements</span></span>  
 <span data-ttu-id="84b86-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84b86-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84b86-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84b86-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84b86-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84b86-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84b86-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84b86-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b86-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84b86-113">See Also</span></span>  
 [<span data-ttu-id="84b86-114">Icordebugmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="84b86-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
