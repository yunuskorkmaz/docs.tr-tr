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
ms.openlocfilehash: aed6ccd938761385aafd21802829bd741847b4ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110246"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="f6f87-102">ICorDebugManagedCallback::ExitAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6f87-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="f6f87-103">Hata ayıklayıcı, bir uygulama etki alanı çıkıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="f6f87-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6f87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6f87-104">Syntax</span></span>  
  
```  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6f87-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6f87-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="f6f87-106">[in] Belirli uygulama etki alanını içeren işlemini temsil eden bir Icordebugprocess nesnesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f6f87-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="f6f87-107">[in] Bir işaretçi Icordebugappdomain nesneye çıkıldı uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f6f87-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6f87-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6f87-108">Requirements</span></span>  
 <span data-ttu-id="f6f87-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6f87-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6f87-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6f87-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6f87-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6f87-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f6f87-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f6f87-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6f87-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6f87-113">See also</span></span>

- [<span data-ttu-id="f6f87-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6f87-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
