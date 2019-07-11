---
title: ICorDebugManagedCallback::ExitAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1e045c475b57f863071eb81194868b7db3c5a3c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755800"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="d8260-102">ICorDebugManagedCallback::ExitAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8260-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="d8260-103">Hata ayıklayıcı, bir uygulama etki alanı çıkıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="d8260-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8260-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8260-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8260-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8260-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="d8260-106">[in] Belirli uygulama etki alanını içeren işlemini temsil eden bir Icordebugprocess nesnesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8260-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="d8260-107">[in] Bir işaretçi Icordebugappdomain nesneye çıkıldı uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d8260-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8260-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8260-108">Requirements</span></span>  
 <span data-ttu-id="d8260-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8260-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8260-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8260-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8260-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8260-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8260-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8260-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8260-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8260-113">See also</span></span>

- [<span data-ttu-id="d8260-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8260-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
