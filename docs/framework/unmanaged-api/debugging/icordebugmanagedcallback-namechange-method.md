---
title: ICorDebugManagedCallback::NameChange Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c33f287cf7ccadeb75ba0bbccf9118aeedc1f942
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607442"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="1fb28-102">ICorDebugManagedCallback::NameChange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fb28-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="1fb28-103">Hata ayıklayıcı, bir uygulama etki alanı ya da bir iş parçacığı adı değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="1fb28-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb28-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1fb28-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fb28-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1fb28-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1fb28-106">[in] Bir işaretçi ya da bir ad değişikliği ya da sahip uygulama etki alanı temsil eden bir Icordebugappdomain nesne için bir ad değişikliği olan iş parçacığı içerir.</span><span class="sxs-lookup"><span data-stu-id="1fb28-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="1fb28-107">[in] Bir işaretçi Icordebugthread nesneye bir ad değişikliği olan iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1fb28-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fb28-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fb28-108">Requirements</span></span>  
 <span data-ttu-id="1fb28-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fb28-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fb28-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1fb28-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1fb28-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fb28-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fb28-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fb28-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb28-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fb28-113">See also</span></span>
- [<span data-ttu-id="1fb28-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1fb28-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
